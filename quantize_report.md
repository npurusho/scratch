
```
(vitis-ai-tensorflow) Vitis-AI /workspace/examples/DPUCVDX8H/tf_inception_v1 > vai_q_tensorflow quantize --input_frozen_graph inception_v1_inference.pb --input_nodes input --output_nodes InceptionV1/Logits/Predictions/Reshape_1 --input_fn utils.input_fn_inception_v1_tf --input_shapes ?,224,224,3 --calib_iter 50
INFO: Checking Float Graph...
/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000001.JPEG
INFO: Float Graph Check Done.
2022-11-11 12:10:06.692390: W tensorflow/contrib/decent_q/utils/quantize_utils.cc:752] [DECENT_WARNING] Scale output of avg_pool node InceptionV1/Logits/AvgPool_0a_7x7/AvgPool to simulate DPU. Kernel size is 7 * 7
INFO: Calibrating for 50 iterations...
  0% (0 of 50) |                         | Elapsed Time: 0:00:00 ETA:  --:--:--/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000001.JPEG
  2% (1 of 50) |                         | Elapsed Time: 0:00:00 ETA:   0:00:24/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000002.JPEG
  4% (2 of 50) |#                        | Elapsed Time: 0:00:00 ETA:   0:00:22/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000003.JPEG
  6% (3 of 50) |#                        | Elapsed Time: 0:00:01 ETA:   0:00:20/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000004.JPEG
  8% (4 of 50) |##                       | Elapsed Time: 0:00:01 ETA:   0:00:19/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000005.JPEG
 10% (5 of 50) |##                       | Elapsed Time: 0:00:02 ETA:   0:00:19/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000006.JPEG
 12% (6 of 50) |###                      | Elapsed Time: 0:00:02 ETA:   0:00:18/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000007.JPEG
 14% (7 of 50) |###                      | Elapsed Time: 0:00:02 ETA:   0:00:17/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000008.JPEG
 16% (8 of 50) |####                     | Elapsed Time: 0:00:03 ETA:   0:00:17/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000009.JPEG
 18% (9 of 50) |####                     | Elapsed Time: 0:00:03 ETA:   0:00:16/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000010.JPEG
 20% (10 of 50) |####                    | Elapsed Time: 0:00:04 ETA:   0:00:16/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000011.JPEG
 22% (11 of 50) |#####                   | Elapsed Time: 0:00:04 ETA:   0:00:16/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000012.JPEG
 24% (12 of 50) |#####                   | Elapsed Time: 0:00:05 ETA:   0:00:15/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000013.JPEG
 26% (13 of 50) |######                  | Elapsed Time: 0:00:05 ETA:   0:00:15/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000014.JPEG
 28% (14 of 50) |######                  | Elapsed Time: 0:00:05 ETA:   0:00:15/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000015.JPEG
 30% (15 of 50) |#######                 | Elapsed Time: 0:00:06 ETA:   0:00:14/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000016.JPEG
 32% (16 of 50) |#######                 | Elapsed Time: 0:00:06 ETA:   0:00:14/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000017.JPEG
 34% (17 of 50) |########                | Elapsed Time: 0:00:07 ETA:   0:00:13/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000018.JPEG
 36% (18 of 50) |########                | Elapsed Time: 0:00:07 ETA:   0:00:13/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000019.JPEG
 38% (19 of 50) |#########               | Elapsed Time: 0:00:07 ETA:   0:00:12/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000020.JPEG
 40% (20 of 50) |#########               | Elapsed Time: 0:00:08 ETA:   0:00:12/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000021.JPEG
 42% (21 of 50) |##########              | Elapsed Time: 0:00:08 ETA:   0:00:12/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000022.JPEG
 44% (22 of 50) |##########              | Elapsed Time: 0:00:09 ETA:   0:00:11/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000023.JPEG
 46% (23 of 50) |###########             | Elapsed Time: 0:00:09 ETA:   0:00:11/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000024.JPEG
 48% (24 of 50) |###########             | Elapsed Time: 0:00:10 ETA:   0:00:10/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000025.JPEG
 50% (25 of 50) |############            | Elapsed Time: 0:00:10 ETA:   0:00:10/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000026.JPEG
 52% (26 of 50) |############            | Elapsed Time: 0:00:10 ETA:   0:00:09/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000027.JPEG
 54% (27 of 50) |############            | Elapsed Time: 0:00:11 ETA:   0:00:09/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000028.JPEG
 56% (28 of 50) |#############           | Elapsed Time: 0:00:11 ETA:   0:00:09/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000029.JPEG
 58% (29 of 50) |#############           | Elapsed Time: 0:00:12 ETA:   0:00:08/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000030.JPEG
 60% (30 of 50) |##############          | Elapsed Time: 0:00:12 ETA:   0:00:08/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000031.JPEG
 62% (31 of 50) |##############          | Elapsed Time: 0:00:12 ETA:   0:00:08/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000032.JPEG
 64% (32 of 50) |###############         | Elapsed Time: 0:00:13 ETA:   0:00:07/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000033.JPEG
 66% (33 of 50) |###############         | Elapsed Time: 0:00:13 ETA:   0:00:07/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000034.JPEG
 68% (34 of 50) |################        | Elapsed Time: 0:00:14 ETA:   0:00:06/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000035.JPEG
 70% (35 of 50) |################        | Elapsed Time: 0:00:14 ETA:   0:00:06/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000036.JPEG
 72% (36 of 50) |#################       | Elapsed Time: 0:00:15 ETA:   0:00:05/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000037.JPEG
 74% (37 of 50) |#################       | Elapsed Time: 0:00:15 ETA:   0:00:05/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000038.JPEG
 76% (38 of 50) |##################      | Elapsed Time: 0:00:15 ETA:   0:00:05/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000039.JPEG
 78% (39 of 50) |##################      | Elapsed Time: 0:00:16 ETA:   0:00:04/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000040.JPEG
 80% (40 of 50) |###################     | Elapsed Time: 0:00:16 ETA:   0:00:04/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000041.JPEG
 82% (41 of 50) |###################     | Elapsed Time: 0:00:17 ETA:   0:00:03/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000042.JPEG
 84% (42 of 50) |####################    | Elapsed Time: 0:00:17 ETA:   0:00:03/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000043.JPEG
 86% (43 of 50) |####################    | Elapsed Time: 0:00:18 ETA:   0:00:02/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000044.JPEG
 88% (44 of 50) |#####################   | Elapsed Time: 0:00:18 ETA:   0:00:02/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000045.JPEG
 90% (45 of 50) |#####################   | Elapsed Time: 0:00:18 ETA:   0:00:02/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000046.JPEG
 92% (46 of 50) |######################  | Elapsed Time: 0:00:19 ETA:   0:00:01/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000047.JPEG
 94% (47 of 50) |######################  | Elapsed Time: 0:00:19 ETA:   0:00:01/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000048.JPEG
 96% (48 of 50) |####################### | Elapsed Time: 0:00:20 ETA:   0:00:00/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000049.JPEG
 98% (49 of 50) |####################### | Elapsed Time: 0:00:20 ETA:   0:00:00/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000050.JPEG
100% (50 of 50) |########################| Elapsed Time: 0:00:20 Time:  0:00:20
INFO: Calibration Done.
/home/vitis-ai-user/CK-TOOLS/dataset-imagenet-ilsvrc2012-val-min/ILSVRC2012_val_00000001.JPEG
********************* Quantization Summary *********************      
INFO: Output:       
  quantize_eval_model: ./quantize_results/quantize_eval_model.pb 
(vitis-ai-tensorflow) Vitis-AI /workspace/examples/DPUCVDX8H/tf_inception_v1 > 

```
