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


mv tf_inceptionv1_imagenet_224_224_3G_2.5.zip /workspace/examples/DPUCVDX8H/tf_inception_v1/
cd /workspace/examples/DPUCVDX8H/tf_inception_v1/
unzip tf_inceptionv1_imagenet_224_224_3G_2.5.zip

cp tf_inceptionv1_imagenet_224_224_3G_2.5/float/inception_v1_inference.pb .

vai_q_tensorflow quantize --input_frozen_graph inception_v1_inference.pb --input_nodes input --output_nodes InceptionV1/Logits/Predictions/Reshape_1 --input_fn utils.input_fn_inception_v1_tf --input_shapes ?,224,224,3 --calib_iter 50

vai_c_tensorflow --arch /opt/vitis_ai/compiler/arch/DPUCVDX8H/VCK50008PE/arch.json --frozen_pb quantize_results/quantize_eval_model.pb --output_dir out --net_name tf_inception_v1_compiled --options '{"input_shape": "1,224,224,3"}'


./build.sh

./inception_example ./out/tf_inception_v1_compiled.xmodel ~/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[UNILOG][INFO] Total device subgraph number 3, DPU subgraph number 1
[UNILOG][INFO] Compile done.
[UNILOG][INFO] The meta json is saved to "/workspace/examples/DPUCVDX8H/tf_inception_v1/out/meta.json"
[UNILOG][INFO] The compiled xmodel is saved to "/workspace/examples/DPUCVDX8H/tf_inception_v1/out/tf_inception_v1_compiled.xmodel"
[UNILOG][INFO] The compiled xmodel's md5sum is 51dca0e8b69573018370e5a887b0e9ca, and has been saved to "/workspace/examples/DPUCVDX8H/tf_inception_v1/out/md5sum.txt"
(vitis-ai-tensorflow) Vitis-AI /workspace/examples/DPUCVDX8H/tf_inception_v1 > 
(vitis-ai-tensorflow) Vitis-AI /workspace/examples/DPUCVDX8H/tf_inception_v1 > ./build.sh
No LSB modules are available.
No LSB modules are available.
g++ (Ubuntu 9.4.0-1ubuntu1~18.04) 9.4.0
Copyright (C) 2019 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

(vitis-ai-tensorflow) Vitis-AI /workspace/examples/DPUCVDX8H/tf_inception_v1 > 
(vitis-ai-tensorflow) Vitis-AI /workspace/examples/DPUCVDX8H/tf_inception_v1 > ./inception_example ./out/tf_inception_v1_compiled.xmodel ~/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min


WARNING: Logging before InitGoogleLogging() is written to STDERR
I1106 22:15:19.073873   399 main.cc:293] create running for subgraph: subgraph_InceptionV1/InceptionV1/Conv2d_1a_7x7/Conv2D

terminate called after throwing an instance of 'std::runtime_error'
  what():  Error: Could not acquire CU
Aborted (core dumped)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~`

Vitis-AI /workspace >  conda activate vitis-ai-tensorflow
(vitis-ai-tensorflow) Vitis-AI /workspace > source /workspace/setup/vck5000/setup.sh DPUCVDX8H_8pe_normal
------------------
VAI_HOME = /vitis_ai_home
------------------
XILINX_XRT        : /opt/xilinx/xrt
PATH              : /opt/xilinx/xrt/bin:/opt/vitis_ai/conda/envs/vitis-ai-tensorflow/bin:/opt/vitis_ai/conda/bin:/opt/vitis_ai/conda/condabin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
LD_LIBRARY_PATH   : /opt/xilinx/xrt/lib:/opt/xilinx/xrt/lib:/usr/lib:/usr/lib/x86_64-linux-gnu
PYTHONPATH        : /opt/xilinx/xrt/python:
---------------------
XILINX_XRT = /opt/xilinx/xrt
---------------------
XILINX_XRM      : /opt/xilinx/xrm
PATH            : /opt/xilinx/xrm/bin:/opt/xilinx/xrt/bin:/opt/vitis_ai/conda/envs/vitis-ai-tensorflow/bin:/opt/vitis_ai/conda/bin:/opt/vitis_ai/conda/condabin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
LD_LIBRARY_PATH : /opt/xilinx/xrm/lib:/opt/xilinx/xrt/lib:/opt/xilinx/xrt/lib:/usr/lib:/usr/lib/x86_64-linux-gnu
---------------------
XILINX_XRM = /opt/xilinx/xrm
---------------------
---------------------
LD_LIBRARY_PATH = /opt/xilinx/xrm/lib:/opt/xilinx/xrt/lib:/opt/xilinx/xrt/lib:/usr/lib:/usr/lib/x86_64-linux-gnu
---------------------
  [0000:03:00.1] : xilinx_vck5000_gen3x16_xdma_base_1 user(inst=129) 
vck5000_ card detected
---------------------
XCLBIN_PATH = /opt/xilinx/overlaybins/DPUCVDX8H/8PE
XLNX_VART_FIRMWARE = /opt/xilinx/overlaybins/DPUCVDX8H/8PE/dpu_DPUCVDX8H_8PE_350M_xilinx_vck5000_gen3x16_xdma_base_1.xclbin
---------------------


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

/opt/xilinx/xrt/bin/xbutil program -d <id> -u ***xclbin


```
