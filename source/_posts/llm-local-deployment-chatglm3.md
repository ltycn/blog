---
title: 本地部署大语言模型ChatGLM3-6B
date: 2023-12-19 15:33:37
tags:
---

## 前言

人工智能浪潮我们迎头赶上，在中文的大语言模型的领域里，开源模型如雨后春笋一般涌现。在各类Benchmark榜单的头部，能看到越来越多中文开源模型的身影。而在具体使用中，隐私保护一直是我们对在线使用大语言模型时令人担忧的一点。在这里我们选择各项成绩都表现不错的ChatGLM3-6B-Base模型作为参考，为大家详细阐述如何在本地部署中文大语言模型。

参考榜单：https://www.datalearner.com/ai-models/llm-evaluation?modelSize=7b

ChatGLM3 是智谱AI和清华大学 KEG 实验室联合发布的新一代对话预训练模型。ChatGLM3-6B 是 ChatGLM3 系列中的开源模型，在保留了前两代模型对话流畅、部署门槛低等众多优秀特性的基础上，ChatGLM3-6B 引入了如下特性：

1. **更强大的基础模型：** ChatGLM3-6B 的基础模型 ChatGLM3-6B-Base 采用了更多样的训练数据、更充分的训练步数和更合理的训练策略。在语义、数学、推理、代码、知识等不同角度的数据集上测评显示，**ChatGLM3-6B-Base 具有在 10B 以下的基础模型中最强的性能**。
2. **更完整的功能支持：** ChatGLM3-6B 采用了全新设计的 [Prompt 格式](https://github.com/THUDM/ChatGLM3/blob/main/PROMPT.md)，除正常的多轮对话外。同时原生支持[工具调用](https://github.com/THUDM/ChatGLM3/blob/main/tool_using/README.md)（Function Call）、代码执行（Code Interpreter）和 Agent 任务等复杂场景。
3. **更全面的开源序列：** 除了对话模型 [ChatGLM3-6B](https://huggingface.co/THUDM/chatglm3-6b) 外，还开源了基础模型 [ChatGLM3-6B-Base](https://huggingface.co/THUDM/chatglm3-6b-base)、长文本对话模型 [ChatGLM3-6B-32K](https://huggingface.co/THUDM/chatglm3-6b-32k)。以上所有权重对学术研究**完全开放**，在填写[问卷](https://open.bigmodel.cn/mla/form)进行登记后**亦允许免费商业使用**。

## 环境准备

### 硬件要求

默认情况下，运行chatglm3-6b模型需要用到显存不低于13GB的显卡，如果 GPU 显存有限，可以尝试以量化方式或多显卡部署的方法加载模型

![]()
<img src="nvidia-smi.png" width="70%" height="70%">

### 安装NVDriver

可以在Nvidia官网，或通过Windows Update安装最新Nvidia显卡驱动

![](wu-check.png)

### 安装Python

依据官网文档，项目需要Python 3.10或更高版本的支持。此处我们直接使用winget安装python 3.11

`winget install Python.Python.3.11`

![](winget-install-python.png)


### 安装CUDA

https://developer.nvidia.com/cuda-downloads

请根据自己显卡所支持的CUDA版本选择CUDA安装包（使用nvidia-smi命令检查CUDA Version）

`winget install Nvidia.CUDA`

![](winget-install-cuda.png)

### 安装Git

https://git-scm.com/download/win

直接使用winget安装Git

`winget install Git.Git`

![](winget-install-git.png)

### 安装conda

https://docs.conda.io/en/latest/

anaconda是一个环境管理工具，直接使用winget安装anaconda

`winget install Anaconda.Anaconda3`

## 模型准备

### Clone ChatGLM3项目

使用Git CloneChatGLM3项目，然后进入仓库目录使用pip安装依赖项

打开一个你想要将项目放入的路径

`git clone https://github.com/THUDM/ChatGLM3.git`

cd Chat

### Clone ChatGLM3模型

在项目文件夹中创建Models目录

`git clone https://www.modelscope.cn/ZhipuAI/chatglm3-6b.git`

`git clone https://www.modelscope.cn/ZhipuAI/chatglm3-6b-base.git`

`git clone https://www.modelscope.cn/ZhipuAI/chatglm3-6b-32k.git`

## 部署

### 检查

由于requirements.txt默认安装的依赖中pytorch的版本不正确，所以我们需要重新选择正确的版本进行安装。

`conda install pytorch torchvision torchaudio pytorch-cuda=12.1 -c pytorch -c nvidia`
`pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121`







### 部署为命令行

### 部署为网页版

### 部署为API