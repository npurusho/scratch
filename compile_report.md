```
(vitis-ai-tensorflow) Vitis-AI /workspace/examples/DPUCVDX8H/tf_inception_v1 > vai_c_tensorflow --arch /opt/vitis_ai/compiler/arch/DPUCVDX8H/VCK50008PE/arch.json --frozen_pb quantize_results/quantize_eval_model.pb --output_dir out --net_name tf_inception_v1_compiled --options '{"input_shape": "1,224,224,3"}'
**************************************************
* VITIS_AI Compilation - Xilinx Inc.
**************************************************
[INFO] Namespace(batchsize=1, inputs_shape=['1,224,224,3'], layout='NHWC', model_files=['quantize_results/quantize_eval_model.pb'], model_type='tensorflow', named_inputs_shape=None, out_filename='/tmp/tf_inception_v1_compiled_DPUCVDX8H_ISA1_F2W2_8PE_org.xmodel', proto=None)
in_shapes: [[1, 224, 224, 3]]
[INFO] tensorflow model: /workspace/examples/DPUCVDX8H/tf_inception_v1/quantize_results/quantize_eval_model.pb
[INFO] parse raw model     :100%|█| 286/286 [00:00<00:00, 12912.08it/s]         
[INFO] infer shape (NHWC)  :100%|█| 356/356 [00:00<00:00, 10441.62it/s]         
[INFO] perform level-0 opt :100%|█| 3/3 [00:00<00:00, 173.67it/s]               
[INFO] perform level-1 opt :100%|█| 7/7 [00:00<00:00, 197.38it/s]               
[INFO] generate xmodel     :100%|█| 231/231 [00:00<00:00, 3537.62it/s]          
[INFO] dump xmodel: /tmp/tf_inception_v1_compiled_DPUCVDX8H_ISA1_F2W2_8PE_org.xmodel
[UNILOG][INFO] Compile mode: dpu
[UNILOG][INFO] Debug mode: function
[UNILOG][INFO] Target architecture: DPUCVDX8H_ISA1_F2W2_8PE
[UNILOG][INFO] Graph name: quantize_eval_model, with op num: 463
[UNILOG][INFO] Begin to compile...
[UNILOG][INFO] Total device subgraph number 3, DPU subgraph number 1
[UNILOG][INFO] Compile done.
[UNILOG][INFO] The meta json is saved to "/workspace/examples/DPUCVDX8H/tf_inception_v1/out/meta.json"
[UNILOG][INFO] The compiled xmodel is saved to "/workspace/examples/DPUCVDX8H/tf_inception_v1/out/tf_inception_v1_compiled.xmodel"
[UNILOG][INFO] The compiled xmodel's md5sum is dfe432389239c83382b2f43f79033000, and has been saved to "/workspace/examples/DPUCVDX8H/tf_inception_v1/out/md5sum.txt"

```
