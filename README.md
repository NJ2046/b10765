# b10765
key_word: iot、chatbot
# Introduction 
## iot
### Jetson Nano
是一款功能强大的小型计算机，专为支持入门级边缘 AI 应用程序和设备而设计。完善的 NVIDIA JetPack™ SDK 包含用于深度学习、计算机视觉、图形、多媒体等方面的加速库，可助您快速上手。
### Module
- 开关家电：家中电器多为220V，故需要继电器作为电灯泡和jetson的中转，来完成开关灯泡操作；如果仅作为实验使用建议买一些可直接连接jetson的小的led灯泡。
- 对外接口：restful、函数调用。如果单机性能强大或后面的对话机器人不太消耗jetson资源，考虑使用函数调用方式，否则使用restful提供web接口。考虑jetson特性，使用函数调用可能性较大。
## chatbot
### NLTK
Natural Language Toolkit，自然语言处理工具包，在NLP领域中，最常使用的一个Python库。
### Keras
Python编写的开源人工神经网络库，可以作为Tensorflow、Microsoft-CNTK和Theano的高阶应用程序接口，进行深度学习模型的设计、调试、评估、应用和可视化。
### Module
- 功能词汇表：定制功能词汇表，比如，打开灯泡，打开加湿器，打开窗帘；词典优先级最高，匹配到词汇后，调用jetson硬件接口。
- 闲聊机器人：如果没有匹配到词汇走闲聊机器人。
# Run
## Env
### jetson env
jetson env取决于student本地环境
### chatbot
1. mac安装conda
```
1. wget https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh -O ~/miniconda.sh
2. bash ~/miniconda.sh -b -p $HOME/miniconda
3. source $HOME/miniconda/bin/activate
4. conda init zsh
ref:https://docs.conda.io/projects/conda/en/latest/user-guide/install/macos.html#install-macos-silent
```
2. 使用conda创建chatbot运行环境
```
conda create -n cb python=3.5
source activate cb
pip install -r req.txt
```
3. 运行程序
```
python chatgui.py
```


# 就斤斤计较
```mermaid
   graph LR
          start[开始] --> input[输入A,B,C]
          input --> conditionA{A是否大于B}
          conditionA -- YES --> conditionC{A是否大于C}
          conditionA -- NO --> conditionB{B是否大于C}
          conditionC -- YES --> printA[输出A]
          conditionC -- NO --> printC[输出C]
          conditionB -- YES --> printB[输出B]
          conditionB -- NO --> printC[输出C]
          printA --> stop[结束]
          printC --> stop
          printB --> stop
```
