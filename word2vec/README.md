# 如何运行？
## python环境准备
我们将通过jupyter notebook来展示整个过程，因此必须准备一个jupyter notebook的开发环境。笔者在docker hub上随便找了一个notebook的镜像kubeflownotebooks/jupyter-pytorch-cuda。可以通过以下命令获取该镜像并启动。
```bash
docker pull kubeflownotebooks/jupyter-pytorch-cuda
docker run -d --network host -v /home/linmao/notebookworkspace:/home/jovyan/workspace kubeflownotebooks/jupyter-pytorch-cuda
```
由于该jupyter notebook会使用8888端口作为服务端口，因此笔者直接使用宿主机端口--network host。同时注意到笔者将一个本地目录映射到/home/jovyan/workspace目录下，便于在该目录下共享文件。

启动镜像之后，可以通过浏览器访问http://localhost:8888进入notebook界面。这时我们需要安装一些python依赖包。由于该镜像使用conda，所以我们也通过conda进行依赖包安装。我们可以直接在notebook的首页点击Other -> Terminal可以打开一个终端。然后在终端上直接操作：

```bash
#安装sklearn，机器学习库
conda install -c anaconda scikit-learn
#安装gensim，支持单词向量操作的核心库
conda install gensim
#安装matplotlib，绘图组件
conda install matplotlib
```

## 下载单词向量包

我们将使用Glove项目提供的单词向量。Glove项目的官网是https://nlp.stanford.edu/projects/glove/，
github在https://github.com/stanfordnlp/GloVe。
如果嫌github太慢还可以看这个镜像：https://gitcode.net/mirrors/stanfordnlp/GloVe。
我们可以先下载最小的模型包玩一下。
```bash
wget https://huggingface.co/stanfordnlp/glove/resolve/main/glove.6B.zip
unzip glove.6B.zip
```

## 完整文章
https://blog.csdn.net/marlinlm/article/details/129645196
