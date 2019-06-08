# AIROBOT
Humanoid Robotic interface/ System Development for simplified control and managment based on intel Architectures

<h2>Overview / Usage</h2>
The project when complete creates and an easily replicatable completely offline robot with extended capabilities of Processing the environment and interacting accordingly. It could easily be used as a receptionist or a welcoming assistant or a home robot or if developed further even a robot that can aid in Hazardous operations.

<h2>Methodology / Approach</h2>
Speech Recognition: Speech to Text conversion on the basis of Baidu Deep speech model using Intel optimized tensorflow and trained with Audiobooks of at least 5000 Books and its text files alongside available open datasets available for speech training including the tedlium, mozilla speech corpus.

Image recognition: Derivative of Imagenet trained with a dataset of 5Million plus images and added gesture recognition capabilities. Using Tensorflow, Open CV.

The project shall primarily Be run on Devcloud to train huge datasets and then the trained model shall be executed on the robot utilizing Intel Processor based boards and Movidius NCS. Thereby considerably reducing the compute requirements and device cost, Power Requirement for the AI element in the robot.

Response system: A Self-developed and trained model to initiate responses and actions from self-learned or Online Responses to Refined and understood Queries.

Sensory Modules: The system utilizes Gyromagnetic domains to Balance the robot and at the same time record the coordinates and movements alongside Recognition of obstacles and mapping the space around 3dimentionally.

Robot Movement: Each degree of freedom and its movements are coupled and synchronized to work using twin Arduino mega boards externally controlled by our compute server(Upsquared board with Movidius)

<h2>Technologies Used</h2>
IOT, Embedded Computing, Movidius Neural Compute Stick, Theano, Tensorflow, OpenCV, Devcloud, Linux, Kinect Sensor, Openvino, DeepSpeech, Linux

<h2>Required hardware</h2>
Movidius Neural Compute stick-4
Realsense camera(or any other webcam)-1
Upsquared Developer board-1(preferably quad core models with atleast 8gb ram and ssd of 128gb)
Microphone (Multimicrophone array recomended)
Speaker- any bluetooth speaker
wifi module.

PyTorch implementation of convolutional networks-based text-to-speech synthesis models:

1. [arXiv:1710.07654](https://arxiv.org/abs/1710.07654): Deep Voice 3: Scaling Text-to-Speech with Convolutional Sequence Learning.
2. [arXiv:1710.08969](https://arxiv.org/abs/1710.08969): Efficiently Trainable Text-to-Speech System Based on Deep Convolutional Networks with Guided Attention.

Audio samples are available at https://r9y9.github.io/deepvoice3_pytorch/.

## Online TTS demo

Notebooks supposed to be executed on https://colab.research.google.com are available:

- [DeepVoice3: Single-speaker text-to-speech demo](https://colab.research.google.com/drive/1Yea4GJIx59bXMukNcElqvrWf61LANNsU)

## Highlights

- Convolutional sequence-to-sequence model with attention for text-to-speech synthesis
- Multi-speaker and single speaker versions of DeepVoice3
- Audio samples and pre-trained models
- Preprocessor for [LJSpeech (en)](https://keithito.com/LJ-Speech-Dataset/), [JSUT (jp)](https://sites.google.com/site/shinnosuketakamichi/publication/jsut) and [VCTK](http://homepages.inf.ed.ac.uk/jyamagis/page3/page58/page58.html) datasets, as well as [carpedm20/multi-speaker-tacotron-tensorflow](https://github.com/carpedm20/multi-Speaker-tacotron-tensorflow) compatible custom dataset (in JSON format)
- Language-dependent frontend text processor for English 

### Samples

- [Ja Step000380000 Predicted](https://soundcloud.com/user-623907374/ja-step000380000-predicted)
- [Ja Step000370000 Predicted](https://soundcloud.com/user-623907374/ja-step000370000-predicted)
- [Ko_single Step000410000 Predicted](https://soundcloud.com/user-623907374/ko-step000410000-predicted)
- [Ko_single Step000400000 Predicted](https://soundcloud.com/user-623907374/ko-step000400000-predicted)
- [Ko_multi Step001680000 Predicted](https://soundcloud.com/user-623907374/step001680000-predicted)
- [Ko_multi Step001700000 Predicted](https://soundcloud.com/user-623907374/step001700000-predicted)

## Notes on hyper parameters

- Default hyper parameters, used during preprocessing/training/synthesis stages, are turned for English TTS using LJSpeech dataset. You will have to change some of parameters if you want to try other datasets. See `hparams.py` for details.
- `builder` specifies which model you want to use. `deepvoice3`, `deepvoice3_multispeaker` [1] and `nyanko` [2] are surpprted.
- Hyper parameters described in DeepVoice3 paper for single speaker didn't work for LJSpeech dataset, so I changed a few things. Add dilated convolution, more channels, more layers and add guided attention loss, etc. See code for details. The changes are also applied for multi-speaker model.
- Multiple attention layers are hard to learn. Empirically, one or two (first and last) attention layers seems enough.
- With guided attention (see https://arxiv.org/abs/1710.08969), alignments get monotonic more quickly and reliably if we use multiple attention layers. With guided attention, I can confirm five attention layers get monotonic, though I cannot get speech quality improvements.
- Binary divergence (described in https://arxiv.org/abs/1710.08969) seems stabilizes training particularly for deep (> 10 layers) networks.
- Adam with step lr decay works. However, for deeper networks, I find Adam + noam's lr scheduler is more stable.

## Requirements

- Python 3 (<= 3.6)
- CUDA >= 8.0
- PyTorch >= v0.4.0

## Installation

Please install packages listed above first, and then 


