# Person Re-identification (person-reid)
A framewrok enabled mixed precision person re-identification. Currently it supports two ResNet-50 and MobileNet-V2. The pre-trained networks for both half-precision and single precision are avaialable in `expt_res` folder.
![POWERED BY TeCSAR](https://raw.githubusercontent.com/TeCSAR-UNCC/Deep_RACE/master/logo/tecsarPowerBy.png)
## Prerequisites
* PyTorch (V 1.0.0)
* Apex: available [here](https://github.com/NVIDIA/apex)
* Python 3
## Installation
### Datasets and pre-requirements
The core of this code is based on provided framework available [here](https://github.com/huanghoujing/person-reid-triplet-loss-baseline). Please follow the mentioned instruction about datasets and switches. 
### Different networks
I added two switches named `--net`, and `--net_pretrained_path` for seclecting the network model and pre-trained model based on ImageNet dataset respectively. The `--net` switch can be assigned to `mobilenetV2` and `resnet50` options. I also provided a pretrained `mobilenet-v2` file named `mobilenet_v2.pth.tar` from [here](http://sceneparsing.csail.mit.edu/model/pretrained_resnet/). 
### Mixed precision
A new added switch named `--opt-level` selects the precision as follows:
* `O0`: pure 32-bit (single precision) training and inference.
* `O2`: Assigned error-tollorant operations, such as GeMM ,to 16-bit (half) precision.

Training will not converge for `O3` opttions. Morover, even for `O2` options, loss function should be calculated in single precision. More information can be find [here](https://nvidia.github.io/apex/amp.html). 

## Demo
I have provided a shell script for each of the following tasks:
### Train
Run the `trainMe.sh`:
```bash
./trainMe.sh
```
### Test
Run the `testMe.sh`:
```bash
./testMe.sh
```
### Visualization
Run the `vis_res.sh`:
```bash
./vis_res.sh
```
### Extracting witghts model and exporting ONNX file
Run the `extractModels.sh`:
```bash
./extractModels.sh
```


## License
Copyright (c) 2018, University of North Carolina at Charlotte. All rights reserved. - see the [LICENSE](https://raw.githubusercontent.com/TeCSAR-UNCC/Deep_RACE/master/LICENSE) file for details.

## Acknowledgments
* [Triplet loss baseline in person re-identification](https://github.com/huanghoujing/person-reid-triplet-loss-baseline)
* [Nvidia Apex](https://github.com/NVIDIA/apex)