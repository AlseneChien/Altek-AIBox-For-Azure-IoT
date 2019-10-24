
How to have AI model running at AIBox
===
---

# Table of Contents

-   [Introduction](#Introduction)
-   [Part 1: Prepare your AI Models for AIBox](#part_1)
-   [Part 2: Deply AI Model and Start Inference Running](#part_2)
-   [Part 3: Troubleshooting](#Step-5-Troubleshooting)


<a name="Introduction"></a>
# Introduction

**About this document**

This document describes how to cover your AI Models, then deploy models to your AIBox via Azure Iot Hub.

<a name="part_1"></a>
# Part 1: Prepare your AI Models for AIBox
## 1.1 Install SNPE SDK

AIBox support edge computing for vision inference, basing on Qualcomm Snapdragon Neural Processing Engine (SNPE). You can refer to [SNPE SDK document](https://developer.qualcomm.com/docs/snpe/overview.html) for more detail

User have to get SNPE SDK from [Qualcomm SNPE website](https://developer.qualcomm.com/software/qualcomm-neural-processing-sdk) in advance. 

Then, follow [Setup at SDK document](https://developer.qualcomm.com/docs/snpe/usergroup0.html) to install SDK at your PC side.

## 1.2 Convert AI Model
<a name="1_2_Convert_A_Model"></a>

The AI Models, tarined by Caffe/Caffe2, TensorFlow, and ONNX, are allowable to be convered as deep learning container (DLC) format to run at SNPE hardware. [Model Conversion at SDK document](https://developer.qualcomm.com/docs/snpe/usergroup2.html) would include relative descriptions

Here is a [list](https://azure.github.io/Vision-AI-DevKit-Pages/docs/frameworks/) to show neural networks and runtimes, run at device DSP (SNPE)

## 1.3 Vision AI Model layout
<a name="1_3_Vision_AI_Model_layout"></a>

Vision AI models, which run on AIBox, consists of three files. Need prepare these 3 files and push into device (/data/misc/camera) before AI running

- .DLC file - containing the model. Refer to [1.2 Convert AI Model](#1_2_Convert_A_Model)
- .TXT file - [containing a list of the objects recognized by the model](./VAM/labels.txt)
- .json file - [containing the VAM engine configuration](./VAM/va-snpe-engine-library_config.json)

Some key attributes of .json file breakdowb as below. User have to customize attributes, depending on AI models' need.
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

## 1.4 Tutorials and Examples

This section show how user would use docker to build / convert one object detection model (TensorFlow) to DLC.

#### Install Docker to your host (ex. ubuntu)
You may searh relative informathin how to install docker at your host.

#### Download and run tensorflow docker images
To simplify dependences installion of tensorflow, we choose docker container with tensorflow as practice at this scection. 
- Download 
```
docker pull tensorflow/tensorflow
```
- Run 
```
docker run -it tensorflow/tensorflow bash
```

#### Download SPNE SDK to host and copy to container
SPNE SDK have to be installed at the same environment as tensorflow. At this section, we would install SNPE SDK inside docker container.
- Download SDK from https://developer.qualcomm.com/software/qualcomm-neural-processing-sdk
- Copy SDK to container 
```
docker cp /path/to/file1 DOCKER_ID:path/to/file2
```

#### Check and Install SDK dependences to container
You can use Qualcomm's tool to check dependences installation.
(https://developer.qualcomm.com/docs/snpe/setup.html)

```
source snpe-X.Y.Z/bin/dependencies.sh
source snpe-X.Y.Z/bin/check_python_depends.sh 
source bin/envsetup.sh -t $TENSORFLOW_DIR
```

#### Convert Tensort flow MNet model to DLC format
Refer to below link to conver tensorflow model to DLC
https://developer.qualcomm.com/docs/snpe/convert_mobilenetssd.html

Then, you have to modify your own lable.txt and va-snpe-engine-library_config.json to fit model's need, referring to [1.3 Vision AI Model layout](#1_3_Vision_AI_Model_layout)


<a name="part_2"></a>
# Part 2: Deply AI Model and Start Inference Running

## 2.1 Prepare DLC/Config Json/Lable text 

You have to prepare your DLC/Config Json/Lable text as [Part 1: Prepare your AI Models for AIBox](#part_1) in advance.
Then, prepare config file to link camera streaming with inference engine.

## 2.2 Prepare docker container to deploy AI Models

## 2.3 Deploy by Azure Iot Hub


<a name="Step-5-Troubleshooting"></a>
# Step 3: Troubleshooting

Please contact engineering support on **<alsenechien@altek.com.tw>** for help with troubleshooting.
  