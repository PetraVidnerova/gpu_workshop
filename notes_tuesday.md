# Nvidia GPU Architecture for AI

https://docs.it4i.cz/

not CUDA course 

brain float - more bits for exponents 
	- quantization fp32 to fp16, precision and resolution comes down 
	- google find out that resolution does not matter in some cases
	-> invented this new data type 

nvidia does not support bfloat, google TPU implemented bfp, intel is working
on it

integer data types / int4, int8, ... - you can have nn using integers


prohozeni NCHW na NHWC (delo se v benchmarku)

https://mlperf.org/inference-results


NCCL 
 -- version < 2.4 - ring communication 
 -- 2.4 changed to double binary tree -> improved latency
 -- supported by TF, pytorch
 
 ngc.nvidia.com (nvididia gpu cloud)
   - you can download prepared containers

	ngc.nvidia.com/catalog/containers/nvidia:tensorflow/tags 
	
 
 singularity - substutite for docker (because security reasons)
   (in most cases it is working) 


 CUDA drivers - on anselm you have to download them
  + cuDNN
  + cuML ? - machine learning algs
  + cuDF - something like pandas , cuGraph neco na grafy
   https://github.com/rapidsai
   
 nvidia tensorRT - optimise infernece  

# Deep Learning Training on Nvdidia GPUs with Tensorflow

now: ai winter or singularity

relu - is sufficiently non-linear :) (paper exist)

use model ZOOs
	https://github.com/tensorflow/models
	

staleness - different models trained in paraller, lack / sometimes you 
  have to wait -> stale-synchronous 


if insterested distrubuted computing ---> Horovod


### practial excersice 
(using vncviewer, on anselm)

https://github.com/tensorflow/models

```
$ml Singularity/3.4.1           # module load 
$ml CUDA/10.1.105-GCC....

$singularity run --nv /scratch/dd-19-37/tensorflow.sif
```
do qsub:
-q qnvidia 

# Model Optimization and Deployment using Nvidia TensorRT

counterpart of openvio

demo - neni cas :(

most of nvidia packages are open source (available on github)

both c++ and python api

optimisation only for target supported architectures, not possible to move it to
another device 

# Get Started with Nvidia V100 on IT4Innovations’ clusters


salomon, not anselm / NEFUNGUJE, VYPRSELA REZERVACE :(


https://www.tensorflow.org/guide/gpu

MULTIPLE GPU 

 - mirror strategy - copy data for every gpu 
 - specify scope 
 
 
 ```
 tf.debugging.set_log_device_placement(True)

strategy = tf.distribute.MirroredStrategy()
with strategy.scope():

  #	+ data creation 

  inputs = tf.keras.layers.Input(shape=(1,))
  predictions = tf.keras.layers.Dense(1)(inputs)
  model = tf.keras.models.Model(inputs=inputs, outputs=predictions)
  model.compile(loss='mse',
                optimizer=tf.keras.optimizers.SGD(learning_rate=0.2))

  # + fit 
 ```

 --- you can specify devices, otherwise it uses all of them
 will run training on multiple gpus


using multi core helps only with very deep networks (since
after each batch we have to synchronise)
in time series excerice it didn't help

# ---------------- 

alnselm (16cores)
salomon 


openvio supported only by intel
tensorflow for nvidia
