# 深度学习训练与练习
## 关于李沐的课程m1环境安装
### 引用自文章：
[李沐-动手学深度学习d2l包安装及m1 gpu加速踩坑记录
](https://zhuanlan.zhihu.com/p/549737512)
### 首先必须确保自己的mac系统版本在12.3以上
#### 注意:本项目已经集成了d2l无需再次安装了。
```python
import platform
platform.platform()
```
### 创建指定环境
`CONDA_SUBDIR=osx-arm64 conda create -n ml python=3.9 -c conda-forge`
### 修改 CONDA_SUBDIR 为 osx-arm64
`conda env config vars set CONDA_SUBDIR=osx-arm64`
### 重新对conda环境进行激活
`conda activate` \
`conda activate ml`
### 安装支持m1加速版本的pytorch，mac系统不低于12.3
#### MPS acceleration is available on MacOS 12.3+
`pip3 install --pre torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/nightly/cpu`
### transformers的安装也需要先安装环境
#### 直接在 ARM64 环境中安装可能会导致错误, 这里最好先构建rust环境
`curl — proto ‘=https’ — tlsv1.2 -sSf https://sh.rustup.rs | sh`
#### 安装transformers
`pip install transformers datasets`
### 测试是否已经支持mps
```python
import torch
torch.has_mps
```
### 最后下载一些本项目的相关依赖
`pip install -r requirements.txt`