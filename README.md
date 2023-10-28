简体中文 | [English](README_en.md)

## 项目简介

![License](https://img.shields.io/badge/License-Apache%202-red.svg)
![python version](https://img.shields.io/badge/Python-3.8+-blue.svg)
![support os](https://img.shields.io/badge/OS-Windows/macOS/Linux-green.svg)  

Video-subtitle-extractor (vse) 是一款将视频中的硬字幕提取为外挂字幕文件(srt格式)的软件。
主要实现了以下功能：

- 提取视频中的关键帧
- 检测视频帧中文本的所在位置
- 识别视频帧中文本的内容
- 过滤非字幕区域的文本（[去除水印、台标文本、原视频硬字幕可配合：video-subtitle-remover](https://github.com/YaoFANGUK/video-subtitle-remover/tree/main)）
- 去除重复字幕行，生成srt字幕文件
- 支持视频字幕**批量提取**（打开文件的时候选择多个视频）
- 多语言：支持**简体中文（中英双语）**、**繁体中文**、**英文**、**日语**、**韩语**、**越南语**、**阿拉伯语**、**法语**、**德语**、**俄语**、**西班牙语**、**葡萄牙语**、**意大利语**等**87种**语言的字幕提取
- 多模式：
  - **快速** - 快速提取字幕但可能丢字幕（推荐）
  - **精准** - 逐帧检测，不丢字幕但速度非常慢（非常不推荐）


**使用说明**：

- 有使用问题请加群讨论，QQ群：210150985

- 视频以及程序路径请**不要带中文和空格**，否则可能出现未知错误！！！

 > 如：以下存放视频和代码的路径都不行
 >
 > D:\下载\vse\运行程序.exe（路径含中文）
 >
 > E:\study\kaoyan\sanshang youya.mp4 （路径含空格） 

- 直接下载压缩包解压运行，如果不能运行再按照下面的教程，尝试源码安装conda环境运行

**下载地址**：

- Windows 绿色版本v2.0.0（CPU）： <a href="https://pan.baidu.com/s/1aUtZqGix1J0aqwGX4VRCWA?pwd=vse2" target=_blank>vse_windows_cpu_v2.0.0.zip</a> 提取码：**vse2** 

> **推荐使用，启动速度较快**

- Windows 单文件版本v2.0.0（CPU）： <a href=https://www.aliyundrive.com/s/uD5ZfoAbDcf target=_blank>vse.exe</a> 提取码：**rl02** 

> 双击直接运行，每次打开时会有一点慢，**若出现误报毒，使用绿色版**

- Windows GPU版本v2.0.0（GPU）： <a href="https://pan.baidu.com/s/1n_OxhFN-lYT_2ln1VeKv-A?pwd=vse2">vse_windows_gpu_v2.0.0.7z</a> 提取码：**vse2**

> **仅供具有Nvidia显卡的用户使用(AMD的显卡不行)，提取速度非常快**

- MacOS 版本v0.1.0（CPU）： <a href="https://pan.baidu.com/s/1WgZpr_8I3Dv7A8ThwcIPng">vse_macOS_CPU.dmg</a> 提取码：**7gbo** 

> PS: 若无法下载，请前往<a href="https://github.com/YaoFANGUK/video-subtitle-extractor/releases"> Release </a>下载


## 项目特色

- 采用本地进行OCR识别，无需设置调用任何API，不需要接入百度、阿里等在线OCR服务即可本地完成文本识别
- 支持GPU加速，GPU加速后可以获得更高的准确率与更快的提取速度
- (CLI版本) 无需用户手动设置字幕区域，项目通过文本检测模型自动检测字幕区域
- (GUI版本) 图形化界面

<p style="text-align:center;"><img src="https://github.com/YaoFANGUK/video-subtitle-extractor/raw/main/design/demo.png" alt="demo.png"/></p>


点击【打开】后选择视频文件，调整字幕区域，点击【运行】

> **有任何改进意见请在ISSUES中提出**



## 演示

- GUI版：

<p style="text-align:center;"><img src="https://github.com/YaoFANGUK/video-subtitle-extractor/raw/main/design/demo.gif" alt="demo.gif"/></p>

- 点击查看视频教程 👇

[![GPU版本安装教程](https://s1.ax1x.com/2022/04/15/L3KzLR.png)](https://www.bilibili.com/video/bv11L4y1Y7Tj "GUP版本安装教程")



## 在线运行

- 使用**Google Colab Notebook**(免费GPU): <a href="https://colab.research.google.com/github/YaoFANGUK/video-subtitle-extractor/blob/main/google_colab.ipynb"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"></a>

> PS: Google Colab只能运行CLI版本



## 源码使用说明

#### 1. 下载安装Miniconda 

- Windows: <a href="https://repo.anaconda.com/miniconda/Miniconda3-py38_4.11.0-Windows-x86_64.exe">Miniconda3-py38_4.11.0-Windows-x86_64.exe</a>


- MacOS：<a href="https://repo.anaconda.com/miniconda/Miniconda3-py38_4.11.0-MacOSX-x86_64.pkg">Miniconda3-py38_4.11.0-MacOSX-x86_64.pkg</a>


- Linux: <a href="https://repo.anaconda.com/miniconda/Miniconda3-py38_4.11.0-Linux-x86_64.sh">Miniconda3-py38_4.11.0-Linux-x86_64.sh</a>

#### 2. 创建并激活虚机环境

（1）切换到源码所在目录：
```shell
cd <源码所在目录>
```
> 例如：如果你的源代码放在D盘的tools文件下，并且源代码的文件夹名为video-subtitle-extractor，就输入 ```cd D:/tools/video-subtitle-extractor-main```

（2）创建激活conda环境
```shell
conda create -n videoEnv python=3.8
```

```shell
conda activate videoEnv
```

#### 3. 安装依赖文件

请确保你已经安装 python 3.8+，使用conda创建项目虚拟环境并激活环境 (建议创建虚拟环境运行，以免后续出现问题)

- CPU用户 (Mac用户) : 

  - 安装依赖：
    ```shell
    pip install -r requirements.txt
    ```

- GPU用户(有N卡)： **要达到高精度的识别率请使用GPU版**
  
  - 安装CUDA和cuDNN

    <details>
        <summary>Linux用户</summary>
        <h5>(1) 下载CUDA 11.7</h5>
        <pre><code>wget https://developer.download.nvidia.com/compute/cuda/11.7.0/local_installers/cuda_11.7.0_515.43.04_linux.run</code></pre>
        <h5>(2) 安装CUDA 11.7</h5>
        <pre><code>sudo sh cuda_11.7.0_515.43.04_linux.run</code></pre>
        <p>1. 输入accept</p>
        <img src="https://i.328888.xyz/2023/03/31/iwVoeH.png" width="500" alt="">
        <p>2. 选中CUDA Toolkit 11.7（如果你没有安装nvidia驱动则选中Driver，如果你已经安装了nvidia驱动请不要选中driver），之后选中install，回车</p>
        <img src="https://i.328888.xyz/2023/03/31/iwVThJ.png" width="500" alt="">
        <p>3. 添加环境变量</p>
        <p>在 ~/.bashrc 加入以下内容</p>
        <pre><code># CUDA
    export PATH=/usr/local/cuda-11.7/bin${PATH:+:${PATH}}
    export LD_LIBRARY_PATH=/usr/local/cuda-11.7/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}</code></pre>
        <p>使其生效</p>
        <pre><code>source ~/.bashrc</code></pre>
        <h5>(3) 下载cuDNN 8.4.1</h5>
        <p>国内：<a href="https://pan.baidu.com/s/1Gd_pSVzWfX1G7zCuqz6YYA">cudnn-linux-x86_64-8.4.1.50_cuda11.6-archive.tar.xz</a> 提取码：57mg</p>
        <p>国外：<a href="https://github.com/YaoFANGUK/video-subtitle-extractor/releases/download/1.0.0/cudnn-linux-x86_64-8.4.1.50_cuda11.6-archive.tar.xz">cudnn-linux-x86_64-8.4.1.50_cuda11.6-archive.tar.xz</a></p>
        <h5>(4) 安装cuDNN 8.4.1</h5>
        <pre><code> tar -xf cudnn-linux-x86_64-8.4.1.50_cuda11.6-archive.tar.xz
     mv cudnn-linux-x86_64-8.4.1.50_cuda11.6-archive cuda
     sudo cp ./cuda/include/* /usr/local/cuda-11.7/include/
     sudo cp ./cuda/lib/* /usr/local/cuda-11.7/lib64/
     sudo chmod a+r /usr/local/cuda-11.7/lib64/*
     sudo chmod a+r /usr/local/cuda-11.7/include/*</code></pre>
    </details>
  
    <details>
          <summary>Windows用户</summary>
          <h5>(1) 下载CUDA 11.7</h5>
          <a href="https://developer.download.nvidia.com/compute/cuda/11.7.0/local_installers/cuda_11.7.0_516.01_windows.exe">cuda_11.7.0_516.01_windows.exe</a>
          <h5>(2) 安装CUDA 11.7</h5>
          <h5>(3) 下载cuDNN 8.2.4</h5>
          <p><a href="https://github.com/YaoFANGUK/video-subtitle-extractor/releases/download/1.0.0/cudnn-windows-x64-v8.2.4.15.zip">cudnn-windows-x64-v8.2.4.15.zip</a></p>
          <h5>(4) 安装cuDNN 8.2.4</h5>
          <p>
             将cuDNN解压后的cuda文件夹中的bin, include, lib目录下的文件复制到C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.7\对应目录下
          </p>
      </details>


  - 安装paddlepaddle:

    - windows:

        ```shell 
        python -m pip install paddlepaddle-gpu==2.4.2.post117 -f https://www.paddlepaddle.org.cn/whl/windows/mkl/avx/stable.html
        ```

    - Linux:

        ```shell
        python -m pip install paddlepaddle-gpu==2.4.2.post117 -f https://www.paddlepaddle.org.cn/whl/linux/mkl/avx/stable.html
        ```

        > 如果安装cuda 10.2，请对应安装7.6.5的cuDNN，并使用对应cuda版本的paddlepaddle，**请不要使用cuDNN v8.x 和 cuda 10.2的组合**
 
        > 如果安装cuda 11.2，请对应安装8.1.1的cuDNN，并使用对应cuda版本的paddlepaddle，**30系列以上的显卡驱动可能不支持 cuda 11.2及以下版本的安装**  


  - 安装其他依赖:

    ```shell
    pip install -r requirements_gpu.txt
    ```
  

#### 4. 运行程序

- 运行图形化界面版本(GUI)

```shell
python gui.py
```

- 运行命令行版本(CLI)

```shell
python ./backend/main.py
```



## 常见问题与解决方案

#### 1. 运行不正常/没有结果/cuda及cudnn问题

解决方案：根据自己的显卡型号、显卡驱动版本，安装对应的cuda与cudnn


#### 2. CondaHTTPError

将项目中的.condarc放在用户目录下(C:\Users\\<你的用户名>)，如果用户目录已经存在该文件则覆盖

解决方案：<a href="https://zhuanlan.zhihu.com/p/260034241">https://zhuanlan.zhihu.com/p/260034241 </a>

#### 3. Windows下出现geos_c.dll错误

```text
    _lgeos = CDLL(os.path.join(sys.prefix, 'Library', 'bin', 'geos_c.dll'))
  File "C:\Users\Flavi\anaconda3\envs\subEnv\lib\ctypes\__init__.py", line 364, in __init__
    self._handle = _dlopen(self._name, mode)
OSError: [WinError 126] 找不到指定的模块。
```

解决方案：

(1) 卸载Shapely

```shell
pip uninstall Shapely -y
```

(2) 使用conda重新安装Shapely

```shell
conda install Shapely             
```

#### 4. 7z文件解压错误

解决方案：升级7-zip解压程序到最新版本

#### 5. Nuitka打包代码闪退

使用Nuitka版本```0.6.19```，将conda虚拟环境Lib文件夹下site-packages的所有文件复制到dependencies文件夹中，把paddle库dataset下image.py的有关subprocess代码全部注释了，使用以下打包命令：

```shell
 python -m nuitka --standalone --mingw64 --include-data-dir=D:\vse\backend=backend --include-data-dir=D:\vse\dependencies=dependencies  --nofollow-imports --windows-icon-from-ico=D:\vse\design\vse.ico --plugin-enable=tk-inter,multiprocessing --output-dir=out .\gui.py
```

编译成单个文件（pip安装zstandard可以减小体积）
```shell
python -m nuitka --standalone --windows-disable-console --mingw64 --lto no --include-data-dir=C:\Users\Yao\Downloads\vse\backend=backend --include-data-dir=C:\Users\Yao\Downloads\vse\design=design --include-data-dir=C:\Users\Yao\Downloads\vse\dependencies=dependencies  --nofollow-imports --windows-icon-from-ico=C:\Users\Yao\Downloads\vse\design\vse.ico --plugin-enable=tk-inter,multiprocessing --output-dir=C:\Users\Yao\Downloads\out --onefile .\gui.py
```

#### 6. GPU版本fast模式提取速度慢

> 为了保证字幕的准确率，自v2.0.0版本起，当您使用了GPU进行加速时，快速模式（fast模式）会切换为高精度模型，若您对精度无过高要求，可改为轻量模型

解决方案：

- 编辑backend文件下的config.py文件，将162-163行改为:

```shell
if USE_GPU:
    DET_MODEL_PATH = os.path.join(DET_MODEL_BASE, 'V4', 'ch_det_fast')
```

## 社区支持

#### Jetbrains 全家桶支持
本项目开发所使用的IDE由Jetbrains支持。
<div align=center>
  <a href="https://jb.gg/OpenSourceSupport"><img src="https://resources.jetbrains.com/storage/products/company/brand/logos/jb_beam.png" alt="JetBrains Logo (Main) logo." width="80"></a>
</div>

## 赞助
<img src="https://i.imgur.com/THE81jM.jpg" width="300">

| 捐赠者 | 累计捐赠金额 | 赞助席位 |
| --- | --- | --- |
| 爱东| 100.00 RMB | 金牌赞助席位 |
| [neoyxm](https://github.com/neoyxm) | 50.00 RMB | 银牌赞助席位 |
| [AcelXiao](https://github.com/acelxiao) | 20.00 RMB | 银牌赞助席位 |
| sky | 5.00 RMB | 铜牌赞助席位 |
