# 关于
langchain-vectorstore-agent是关于使用langchain vectorstore来实现一个问答系统的demo。这个问答系统可以通过vectorstore查询与当前话题相关的一些预先存储的文档资料，然后将查询到的信息反馈给调用者。如果查询的问题超过了vectorestore中存储的内容，那么回答I don't know。

# 准备
* 安装python 3.8以上，目前的最新版本是3.11：
  https://www.python.org/downloads/release/python-3111/
* 本例采用jupyter-lab作为开发环境，因此需要在电脑上安装jupyter-lab。
  https://jupyter.org/ 

* 注册openai账户，并设置OPENAI_API_KEY环境变量
* redis服务需要安装redis-stack
  ```bash
  docker run -d -p 13333:8001 -p 10001:6379 redis/redis-stack:latest
  ```
* 然后安装相关的python依赖包
  ```bash
  pip install openai
  pip install langchain
  pip install urllib
  pip install redis
  ```


# 其他
本demo涉及到使用爬虫技术获取一些网络上的公共信息，由于爬虫并非本文主要介绍的内容，处于网络安全方面的考虑，本例将去掉爬虫相关的内容。
