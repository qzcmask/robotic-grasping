# Antipodal Robotic Grasping
We present a novel generative residual convolutional neural network based model architecture which detects objects in the camera’s field of view and predicts a suitable antipodal grasp configuration for the objects in the image.

This repository contains the implementation of the Generative Residual Convolutional Neural Network (GR-ConvNet) from the paper:

#### Antipodal Robotic Grasping using Generative Residual Convolutional Neural Network

Sulabh Kumra, Shirin Joshi, Ferat Sahin

[arxiv](https://arxiv.org/abs/1909.04810) | [video](https://youtu.be/cwlEhdoxY4U)

[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/antipodal-robotic-grasping-using-generative/robotic-grasping-on-cornell-grasp-dataset)](https://paperswithcode.com/sota/robotic-grasping-on-cornell-grasp-dataset?p=antipodal-robotic-grasping-using-generative)

If you use this project in your research or wish to refer to the baseline results published in the paper, please use the following BibTeX entry:

```
@article{kumra2019antipodal,
  title={Antipodal Robotic Grasping using Generative Residual Convolutional Neural Network},
  author={Kumra, Sulabh and Joshi, Shirin and Sahin, Ferat},
  journal={arXiv preprint arXiv:1909.04810},
  year={2019}
}
```

## Requirements

- numpy
- opencv-python
- matplotlib
- scikit-image
- imageio
- torch
- torchvision
- torchsummary
- tensorboardX
- pyrealsense2
- Pillow

## Installation
- Checkout the robotic grasping package
```bash
$ git clone https://github.com/skumra/robotic-grasping.git
```

- Create a virtual environment
```bash
$ python3.6 -m venv --system-site-packages venv
```

- Source the virtual environment
```bash
$ source venv/bin/activate
```

- Install the requirements
```bash
$ cd robotic-grasping
$ pip install -r requirements.txt
```

## Datasets

This repository supports both the [Cornell Grasping Dataset](http://pr.cs.cornell.edu/grasping/rect_data/data.php) and
[Jacquard Dataset](https://jacquard.liris.cnrs.fr/).

#### Cornell Grasping Dataset

1. Download the and extract [Cornell Grasping Dataset](http://pr.cs.cornell.edu/grasping/rect_data/data.php). 
2. Convert the PCD files to depth images by running `python -m utils.dataset_processing.generate_cornell_depth <Path To Dataset>`

#### Jacquard Dataset

1. Download and extract the [Jacquard Dataset](https://jacquard.liris.cnrs.fr/).


## Model Training

A model can be trained using the `train_network.py` script.  Run `train_network.py --help` to see a full list of options.

For example:

```bash
python train_network.py --dataset cornell --dataset-path <Path To Dataset> --description training_cornell
```

## Model Evaluation

The trained network can be evaluated using the `evaluate.py` script.  Run `evaluate.py --help` for a full set of options.

For example:

```bash
python evaluate.py --network <Path to Trained Network> --dataset cornell --dataset-path <Path to Dataset> --iou-eval
```

## Run Tasks
A task can be executed using the relevant run script. All task scripts are named as `run_<task name>.py`. For example, to run the grasp generator run:
```bash
python run_grasp_generator.py
```

## Run on a Robot
To run the grasp generator with a robot, please use our ROS implementation for Baxter robot. It is available at: https://github.com/skumra/baxter-pnp
