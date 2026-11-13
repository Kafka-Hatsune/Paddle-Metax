# PaddlePaddle for Metax GPU

English | [简体中文](./README_cn.md)

Please refer to the following steps to compile, install and verify paddlepaddle_metax.

## Compilation and Installation

```bash
# Please contact Metax customer support (https://sw-download.metax-tech.com) to obtain the SDK image

# Clone PaddleCustomDevice source code
git clone https://github.com/PaddlePaddle/Paddle-Metax.git

# Pull Paddle dependencies and third-party libraries
git submodule sync --recursive && git submodule update --init --recursive

# Install
bash build_inc.sh
```
- Note passing/modifying WITH_CINN in build_inc.sh
- Note: mvcc on the Metax platform has a ccache bug. When building with ccache enabled, pure host .cc files are fed to mxcc via -x cu, compiling with zero errors and zero warnings, but the host function bodies in the resulting .o files are almost entirely dropped. Do not use ccache.

## Verification

```bash
# Run tests
cd tests
bash run_test.sh -j3
```
