
AI Model to AIBox via Azure Cloud
===
---

# Table of Contents

-   [Introduction](#Introduction)
-   [Step 1: Prepare your AI Models for AIBox](#Prerequisites)
-   [Step 2: Deploy your AI Model to Device](#PrepareDevice)
-   [Step 3: Manual Test for Azure IoT Edge on device](#Manual)
-   [Step 4: Next Steps](#NextSteps)
-   [Step 5: Troubleshooting](#Step-5-Troubleshooting)


<a name="Introduction"></a>
# Introduction

**About this document**

This document describes how to cover your AI Models, then deploy models to your AIBox via Azure Iot Hub.

<a name="Prerequisites"></a>
# Part 1: Prepare your AI Models for AIBox
## 1.1 Install SNPE SDK

AIBox support edge computing for vision inference, basing on Qualcomm Snapdragon Neural Processing Engine (SNPE).

User have to get SNPE SDK from [Qualcomm SNPE website](https://developer.qualcomm.com/software/qualcomm-neural-processing-sdk) in advance. You can refer to [SDK document](https://developer.qualcomm.com/docs/snpe/overview.html) for more detail

Then, follow [Setup at SDK document](https://developer.qualcomm.com/docs/snpe/usergroup0.html) to install SDK at your PC side.


## 1.2 Convert AI Model
<a name="1_2_Convert_A_Model"></a>

The AI Models, tarined by Caffe/Caffe2, TensorFlow, and ONNX, are allowable to be convered as deep learning container (DLC) format to run at SNPE hardware. [Model Conversion at SDK document](https://developer.qualcomm.com/docs/snpe/usergroup2.html) would include relative descriptions

Here is a [list](https://azure.github.io/Vision-AI-DevKit-Pages/docs/frameworks/) to show neural networks and runtimes, run at device DSP (SNPE)

## 1.3 Vision AI Model layout
Vision AI models, which run on AIBox, consists of three files. These 3 files need be pushed into device (/data/misc/camera) before AI running

- .DLC file - [containing the model](#Introduction)
- .TXT file - [containing a list of the objects recognized by the model](./VAM/labels.txt)
- .json file - [containing the VAM engine configuration](./VAM/va-snpe-engine-library_config.json)

Some key attributes of .json file breakdowb as below
- "Engine", 0: Mnet / 1: Mnet_SSD / 2: Squeezenet
- “NetworkIO”, 0: UserBufer / 1: ITensor
- “ScaleWidth” / “ScaleHeight”, ScaleWidth / ScaleHeight
- "BlueMean", Blue Mean and Mean Range [0 - 255]
- "GreenMean", Green Mean and Mean Range [0 - 255]
- "RedMean", Red Mean and Mean Range [0 - 255]
- “UseNorm”, 0: Do not use normalization / 1: Use normalization
- “TargetFPS”, Target Frames Per Second (ex. 30)
- “ConfThreshold”, 0.0: ConfThreshold, percentage of confidence needed for labeling an object Range [0.0 - 1.0]
- “DLC_NAME”, ”.dlc”: dlc file name 
- “LABELS_NAME”, ”.txt”: labels file name
- “InputLayers” / “OutputLayers”, Input layers / Output layers - array of strings. It is possible to have single entry
- “ResultLayers”, Used for comparing the results. It is possible to have single entry. For ComplexEngine, use the following convention: ‘[ ]’
- “Runtime”, 0: CPU / 1: DSP


<a name="PrepareDevice"></a>
# Part 2: Deply AI Model and Start Inference Running

T..

<a name="Manual"></a>
# Part 3: Manual Test for Azure IoT Edge on device

...

<a name="NextSteps"></a>
# Step 4: Next steps

...

<a name="Step-5-Troubleshooting"></a>
# Step 5: Troubleshooting

Please contact engineering support on **<alsenechien@altek.com.tw>** for help with troubleshooting.
  