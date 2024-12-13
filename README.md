# TORCH_WHL_CPU

This repository contains the pre-compiled .whl file for CPU-version Pytorch. 

This whl is bascially used to install pytorch on a aarch64 machine, which uses CPU to infer the model. Similar whl files have been provided by [NVIDIA](https://forums.developer.nvidia.com/t/pytorch-for-jetson/72048) and [pip](https://pypi.org/project/torch/2.5.0/#files).

However, the whl file provided by NVIDIA uses CUDA to compile, which means you can only use it on a machine with CUDA. Meanwhile, the whl file provided by pip has set `_GLIBCXX_USE_CXX11_ABI = 0`, which results in conficts with ROS. Therefore, I created this whl file to provide a CPU-version Pytorch which is compatible with ROS.

## Compilation details

- **Machine**: NVIDIA Jetson Orin NX 16GB(100 TOPS)
- **OS**: ubuntu 20.04
- **Architecture**: aarch64
- **Python version**: 3.10
- **Pytorch version**: 2.6.0
- `_GLIBCXX_USE_CXX11_ABI = 1`
- `USE_CUDA = 0`

The compilation takes around **4h30min** on the Jetson Orin NX 16GB, whose CPU max clock speed is 2.0GHz.

## How to use

I personally use this whl file to install pytorch, and use the libtorch C++ API in it.

The validity of this whl file has been verified on a [RDK X5 board](https://developer.d-robotics.cc/rdkx5). Theoretically, it should work on other aarch64 machines with CPU.