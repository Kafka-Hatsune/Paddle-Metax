# PaddlePaddle for Metax GPU

English | [简体中文](./README_cn.md)

请参考以下步骤进行编译、安装和验证 paddlepaddle_metax。

## 编译安装

```bash
# 请联系沐曦客户支持 (https://sw-download.metax-tech.com) 获取 SDK 镜像

# 克隆 PaddleCustomDevice 源代码
git clone https://github.com/PaddlePaddle/Paddle-Metax.git

# 拉取paddle依赖和三方库
git submodule sync --recursive && git submodule update --init --recursive

# 编译和安装
bash build_inc.sh
```
- build_inc.sh中注意传入/修改 WITH_CINN
- 注意，metax平台上mvcc存在ccache bug，开启ccache build时，纯 host 的 .cc 用 -x cu 喂给 mxcc，编译零报错零警告,但产出的 .o 里 host 函数体几乎全被丢掉，不要使用ccache

## 验证

```bash
# 运行测试
cd tests
bash run_test.sh -j3
```
