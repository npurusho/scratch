# Steps to run Vitis AI  vitis-ai-tensorflow - model inceptionv1

```
conda activate vitis-ai-tensorflow
source /workspace/setup/vck5000/setup.sh DPUCVDX8H_8pe_normal


python -m ck pull repo:ck-env
python -m ck install package:imagenet-2012-val-min
python -m ck install package:imagenet-2012-aux --tags=from.berkeley
head -n 500 ~/CK-TOOLS/dataset-imagenet-ilsvrc2012-aux-from.berkeley/val.txt > ~/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/val.txt


cd /workspace/model-zoo/
python3 downloader.py
tf inceptionv1


mv tf_inceptionv1_imagenet_224_224_3G_2.5.zip /workspace/examples/DPUCVDX8H/tf_inception_v1/
cd /workspace/examples/DPUCVDX8H/tf_inception_v1/
unzip tf_inceptionv1_imagenet_224_224_3G_2.5.zip

cp tf_inceptionv1_imagenet_224_224_3G_2.5/float/inception_v1_inference.pb .

vai_q_tensorflow quantize --input_frozen_graph inception_v1_inference.pb --input_nodes input --output_nodes InceptionV1/Logits/Predictions/Reshape_1 --input_fn utils.input_fn_inception_v1_tf --input_shapes ?,224,224,3 --calib_iter 50

vai_c_tensorflow --arch /opt/vitis_ai/compiler/arch/DPUCVDX8H/VCK50008PE/arch.json --frozen_pb quantize_results/quantize_eval_model.pb --output_dir out --net_name tf_inception_v1_compiled --options '{"input_shape": "1,224,224,3"}'


./build.sh

./inception_example ./out/tf_inception_v1_compiled.xmodel ~/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

conda activate vitis-ai-tensorflow2
source /workspace/setup/vck5000/setup.sh DPUCVDX8H_8pe_normal


python -m ck pull repo:ck-env
python -m ck install package:imagenet-2012-val-min
python -m ck install package:imagenet-2012-aux --tags=from.berkeley
head -n 500 ~/CK-TOOLS/dataset-imagenet-ilsvrc2012-aux-from.berkeley/val.txt > ~/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/val.txt


cd /workspace/model-zoo/
python3 downloader.py
tf2 inceptionv3


mkdir /workspace/examples/DPUCVDX8H/tf2_inceptionv3
mv tf2_inceptionv3_imagenet_299_299_11.5G_2.5.zip /workspace/examples/DPUCVDX8H/tf2_inceptionv3/
cd /workspace/examples/DPUCVDX8H/tf2_inceptionv3/
unzip tf2_inceptionv3_imagenet_299_299_11.5G_2.5.zip

cd tf2_inceptionv3_imagenet_299_299_11.5G_2.5
mkdir vai_q_output
python ./code/com/train_eval_h5.py --model ./float/inception_v3_weights_tf.h5 --quantize=true --quantize_output_dir=./vai_q_output --eval_only=true --eval_images=true --eval_image_path=/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ --eval_image_list=/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/val.txt --label_offset=1 --gpus=0

vai_c_tensorflow2 -m ./vai_q_output/quantized.h5 -a /opt/vitis_ai/compiler/arch/DPUCVDX8H/VCK50008PE/arch.json -o ./vai_q_output -n inception_v3_tf2 --options '{"input_shape": "4,299,299,3"}'


cp -r ../../tf_inception_v1/build.sh .
./build.sh

./inception_example ./vai_q_output/inception_v3_tf2.xmodel ~/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


cd Vitis-AI
./docker_run.sh
source ./run-via-demo.sh

cd /usr/share/vitis_ai_library/models
tar xvfz inception_v1_tf-vck5000-DPUCVDX8H-8pe-r2.5.0.tar.gz
cd /workspace/examples/VART/inception_v1_mt_py/
python3 ./inception_v1.py 16 /usr/share/vitis_ai_library/models/inception_v1_tf/inception_v1_tf.xmodel


```
