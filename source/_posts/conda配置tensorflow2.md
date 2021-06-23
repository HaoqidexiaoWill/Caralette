---
title: conda配置tensorflow2
date: 2020-04-20 23:20:05
tags: 环境配置
---

## Conda环境安装

首先wget 下载conda 的bash 脚本：

```bash
wget https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/Anaconda3-2020.02-Linux-x86_64.sh
```

得到`Anaconda3-2020.02-Linux-x86_64.sh` bash文件以后，使用bash 命令编译他：

```bash
bash Anaconda3-2020.02-Linux-x86_64.sh
```

接下来一顿回车，记得把anconda3 安装在自己的根目录下即可

如果shell命令下没有source命令的话

![](https://raw.githubusercontent.com/UriBoyka2020 /Picture/master/file2/20200420233303.png)

就把source换成bash

![](https://raw.githubusercontent.com/UriBoyka2020 /Picture/master/file2/20200420233618.png)

然后配置环境变量，并编译,如果rc文件不存在的话先touch 一下

```bash
export PATH="/data00/home/songyan.liu2020/anaconda3/bin:$PATH"
touch ~/.bash.rc
source  ~/.bash.rc
```

最后`conda list`检查一下，没问题的话，conda的环境就安装成功了

## 安装tensorflow2

创建虚拟环境

```bash
conda create -n conda-gpu python=3.7
```

创建好了以后切到对应的conda 虚拟环境中

```bash
conda activate xxx
```

这个时候再pip是默认安装在conda的环境中

几个不同的pip的源：

```bash
pip install tensorflow-gpu==2  -i https://mirrors.aliyun.com/pypi/simple/
pip install tensorflow --index-url=http://pypi.byted.org/simple/pypi/+simple --trusted-host=pypi.byted.org
pip install tensorflow-gpu==1.12.0 -i  https://pypi.tuna.tsinghua.edu.cn/simple
```

到这步基本tensorflow就安装完成

但是我在调用的时候会报错误：模型只能跑在CPU上，GPU空转

![](https://raw.githubusercontent.com/UriBoyka2020 /Picture/master/file2/20200420234804.png)

这个时候需要加入对应的库的路径：

```bash
export LD_LIBRARY_PATH=/usr/local/cuda/lib64:/usr/local/lib/:$LD_LIBRARY_PATH
export CUDA_HOME=/usr/local/cuda
export OPENMPI_HOME=/usr/local/openmpi
export PATH=$CUDA_HOME/bin:$OPENMPI_HOME/bin:$PATH
export LD_LIBRARY_PATH=$OPENMPI_HOME/lib/:$LD_LIBRARY_PATH
```

然后tensorflow 可以正常跑了

![](https://raw.githubusercontent.com/UriBoyka2020 /Picture/master/file2/20200420235029.png)

