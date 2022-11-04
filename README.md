# scratch

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


mv tf_inceptionv1_imagenet_224_224_3G_1.4.zip /workspace/examples/DPUCVDX8H/tf_inception_v1/
cd /workspace/examples/DPUCVDX8H/tf_inception_v1/
unzip tf_inceptionv1_imagenet_224_224_3G_1.4.zip

cp tf_inceptionv1_imagenet_224_224_3G_1.4/float/inception_v1_inference.pb .

vai_q_tensorflow quantize --input_frozen_graph inception_v1_inference.pb --input_nodes input --output_nodes InceptionV1/Logits/Predictions/Reshape_1 --input_fn utils.input_fn_inception_v1_tf --input_shapes ?,224,224,3 --calib_iter 50

vai_c_tensorflow --arch /opt/vitis_ai/compiler/arch/DPUCADF8H/U200/arch.json --frozen_pb quantize_results/quantize_eval_model.pb --output_dir out --net_name tf_inception_v1_compiled --options '{"input_shape": "4,224,224,3"}'

./build.sh

./inception_example ./out/tf_inception_v1_compiled.xmodel ~/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min![image](https://user-images.githubusercontent.com/15679370/200009938-755844ab-ed83-4f9e-b64e-c7f89eeb1842.png)
```
