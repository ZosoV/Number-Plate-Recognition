# Number-Plate-Recognition

This project is based in the following project [Blog Post](http://matthewearl.github.io/2016/05/06/cnn-anpr/)
[Repo Link](https://github.com/matthewearl/deep-anpr) 

Usage is as follows:

1. `./extractbgs.py SUN397.tar.gz`: Extract ~3GB of background images from the [SUN database](http://groups.csail.mit.edu/vision/SUN/)
   into `bgs/`. (`bgs/` must not already exist.) The tar file (36GB) can be [downloaded here](http://vision.princeton.edu/projects/2010/SUN/SUN397.tar.gz).
   This step may take a while as it will extract 108,634 images.

2. `./gen.py 1000`: Generate 1000 test set images in `test/`. (`test/` must not
    already exist.) This step requires `UKNumberPlate.ttf` to be in the
    `fonts/` directory, which can be
    [downloaded here](http://www.dafont.com/uk-number-plate.font).

3. `./train.py`: Train the model. A GPU is recommended for this step. It will
   take around 100,000 batches to converge. When you're satisfied that the
   network has learned enough press `Ctrl+C` and the process will write the
   weights to `weights.npz` and return.

4. `./detect.py in.jpg weights.npz out.jpg`: Detect number plates in an image.

Instructions to run with the GPU (Nvidia GeForce GTX 1060):

Note: if you install tensorflow-gpu with anaconda the programs CUDA Tool Kit and Cudnn comes by default.
Note: if you install tensorflow-gpu with pip follow the instructions of the oficial site of tensorflow.

The project has the following dependencies:
* [Nvidia Drivers 410](https://www.nvidia.com/Download/index.aspx?lang=en-us)
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt install nvidia-driver-410
sudo reboot
nvidia-smi
```
* [Tensorflow GPU](https://www.tensorflow.org/install/gpu) or with [Anaconda](https://anaconda.org/conda-forge/tensorflow)

Pip installation
```
pip install tensorflow-gpu 
```
Anaconda Installation
```
conda install -c conda-forge tensorflow 
```

* [CUDA Tool Kit 10.0](https://developer.nvidia.com/cuda-downloads) (TensorFlow >= 1.13.0)
* [Cudnn SDK >=7.4.1](https://developer.nvidia.com/cudnn)


