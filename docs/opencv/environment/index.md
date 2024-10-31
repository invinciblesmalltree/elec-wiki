# 环境配置

## 一、安装 Python

[Python 安装地址](https://www.python.org/downloads/)

![alt text](1.png)

???+ "提示"
    注意 Add PATH

完成。

## 二、PyCharm

[PyCharm windows 版本下载地址](https://www.jetbrains.com/pycharm/download/#section=windows)

选择社区版下载安装（日常学习使用够用了）（PyCharm Community Edition）

也可以选择专业版，使用学校邮箱进行认证。

![alt text](2.png)

![alt text](3.png)

可自选路径

![alt text](4.png)

![alt text](5.png)

![alt text](6.png)

重启

中文包：

![alt text](7.png)

## 三、Anaconda 环境

### 1、conda 的安装

[conda 安装（清华大学开源镜像站）](https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/)

![alt text](8.png)

根据自己电脑选择合适版本

![alt text](9.png)

???+ "提示"
    注意 Add PATH

如果没有勾选，后续需要自行添加环境变量。

等待安装完成即可。

![alt text](10.png)

打开pycharm，使用conda环境新建项目

![alt text](11.png)

在设置中查看解释器：

![alt text](12.png)

添加解释器可添加自己创建的虚拟环境：

![alt text](13.png)

### 2、创建 conda 虚拟环境的方法

打开 Anaconda Prompt

![alt text](10.png)

```cmd
conda create -n xxx python=3.8
# xxx改成你的虚拟环境名字 python=版本号
conda activate xxx
# 激活创建的虚拟环境
```

```cmd
Downloading and Extracting Packages:

Preparing transaction: done
Verifying transaction: done
Executing transaction: done
#
# To activate this environment, use
#
#     $ conda activate opencv
#
# To deactivate an active environment, use
#
#     $ conda deactivate


(base) C:\Users\kevin>conda activate opencv

(opencv) C:\Users\kevin>
```

前面的 base 变成你创建的虚拟环境名称即为成功。

[具体conda使用的常用指令可以参考大神的博客](http://t.csdnimg.cn/KNZfl)

## 四、OpenCV

先安装 numpy

`pip install numpy`

pip 安装

`pip install opencv-python`
`pip install opencv-contrib-python`

验证一下有没有安装成功

```cmd
C:\Users\kevin>python
Python 3.11.7 | packaged by Anaconda, Inc. | (main, Dec 15 2023, 18:05:47) [MSC v.1916 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> import cv2
>>> print(cv2.__version__)
4.9.0
```

## 五、Pytorch（深度学习环境）

前提：你的电脑有GPU

### 1、cmd 终端输入 nvidia-smi，查看你的显卡适配的 CUDA 版本

```cmd
C:\Users\kevin>nvidia-smi
Tue Aug  6 18:26:06 2024
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 546.92                 Driver Version: 546.92       CUDA Version: 12.3     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                     TCC/WDDM  | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce RTX 4060 ...  WDDM  | 00000000:01:00.0 Off |                  N/A |
| N/A   45C    P8              4W /  102W |   1367MiB /  8188MiB |      2%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+

+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|  No running processes found                                                           |
+---------------------------------------------------------------------------------------+
```

### 2、conda 创建虚拟环境

Anaconda Prompt 输入

`conda create -n pytorch python=3.8`

`conda activate pytorch`

### 3、下载地址： [PyTorch](https://pytorch.org/)

![alt text](14.png)

根据你电脑支持的 CUDA 版本安装，我的电脑是 CUDA12.1

```cmd
(pytorch) C:\Users\kevin>conda install pytorch torchvision torchaudio pytorch-cuda=12.1 -c pytorch -c nvidia
```

验证一下：

```cmd
python
import torch
torch.cuda.is_available()
```

```cmd
(pytorch) C:\Users\kevin>python
Python 3.11.9 | packaged by Anaconda, Inc. | (main, Apr 19 2024, 16:40:41) [MSC v.1916 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> import torch
>>> torch.cuda.is_available()
True
>>>
```

如果返回值是 True，代表成功啦。恭喜你，安装完成，可以开始快乐的炼丹啦。

## 六、yolov8

[ultralytics/ultralytics: NEW - YOLOv8 🚀 in PyTorch > ONNX > OpenVINO > CoreML > TFLite (github.com)](https://github.com/ultralytics/ultralytics)

根据官方的 README 安装使用

Install

>Pip install the ultralytics package including all requirements in a Python>=3.8 environment with PyTorch>=1.8.

在有 pytorch 的 conda 虚拟环境中输入

`pip install ultralytics`

跑一个官方例程测试

`yolo predict model=yolov8n.pt source='https://ultralytics.com/images/bus.jpg'`

![alt text](15.png)

恭喜你，完成了 yolov8 的安装。
