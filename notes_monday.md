# Intel Architecture -- A Quick Refresher


intel má nástroje pro optimalizaci kodu, power tools


https://www.intel.ai/nervana-nnp/#gs.fus33e

https://mlperf.org/press#mlperf-inference-v0.5-results
https://mlperf.org/inference-results\

ark.intel.com


# AI Case Study
data publicly available

 Vehicle Make and Model Recognitiondataset(VMMRdb):
 ₋Large in scale and
 diversity₋Images are collected from Craigslist₋Contains 9170
 classes₋Identified 76 Car Manufacturers₋291,752 images in total₋Manufactured
 between1950-2016Car Manufacturer

not balanced

preprocessing 
 - downsampling - randomly!
 - upsampling - data augmentation
 (introducing bias)
 
 sample-wise centering - on one image 
 feature-wise centering - according to mean image 
 
 
RGB BRD ? keras expects 

? jak augmentovat numerická data

70% - 10% - 20% - division of data

test must be independent


preprocessing with opencv and keras

### :) 
NEVER COMPILE FRAMEWORK YOURSELF - you have to validate!!!

### Choice of framework 

official version of Tf optimised only for GPUs

Intel engeneer optimised it for Intel  --> intel version 

biggest community has Tensorflow and PyTorch



### Select Network

infernce speed - latency 
               - support  (img per second)


ResNet - good choice for images

Inception v3 - 1001 classes, extra class for "unknown class"


### Deployment 
OPENVIO
 - model optimiser
 - execute model 
 - running outside of tensorflow
 
FP16/FP32 quantization - addition on performance 

iv3_labels.txt - which class is which



# MOVIDIUS USP 

(missing slides on dropbox?)

computing stick 

needs always a host platform, can be more stick to one comp


Movidius research grant - see website  (no url) 
   - register project and get stick 
   
   
# SCIKIT LEARN 
improved scikit learn / via intel discro of python (rpm/apt, docker, anaconda)

conda install -c intel ipykernel matplotlib pillow scikit-learn daal4py=2019.5 python=3.6 # pulls in daal4py & mkl


intel numpy, scipy - mkl_rt

scikit learn does not support multinode 




todo: download docker file for Intel 

