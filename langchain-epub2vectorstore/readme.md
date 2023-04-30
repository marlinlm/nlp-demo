# 1. 这个demo实现了一个什么需求
本示例项目将实现一个机器人，这个机器人会从指定路径读取电子书内容（格式为epub），并根据所读取的书本内容回答用户问题。即题目中所说的书本解读机器人。

# 2. 准备开发环境

* 安装python 3.8以上，目前的最新版本是[3.11](https://www.python.org/downloads/release/python-3111/)。

* 本例采用jupyter-lab作为开发环境，因此需要在电脑上安装[jupyter-lab](https://jupyter.org/)。


* [注册openai账户](https://platform.openai.com)，并设置OPENAI_API_KEY环境变量。
* 我们使用redis来保存所加载的书本的内容，因此需要部署一个redis服务。不同于我们平时一般web应用使用的redis服务，我们这次需要安装redis-stack：
  ```bash
  docker run -d -p 13333:8001 -p 10001:6379 redis/redis-stack:latest
  ```
* 然后安装相关的python依赖包
  ```bash
  pip install openai
  pip install langchain
  pip install redis
  pip install unstructured
  ```

* 安装[pandoc](https://github.com/jgm/pandoc/releases)，加载epub电子书要用 。

# 最后
由于只是一个示例项目，因此本项目只是通过jupyter lab来实现，并非一个真实可以提供任何web服务的项目，其中的一些逻辑也简单化处理。例如只能读取笔者预先放置在项目工程目录下的epub格式的电子书，而不能由用户自由上传电子书并为用户提供解答服务。再例如如果连续运行两次加载电子书的操作，会在数据库中留下重复的数据，本例子中并未包含去重的逻辑。由于这个项目的主要目的是为了探讨langchain在大模型应用开发中的作用，而非巨细靡遗地实现一个可以商业化的机器人，笔者认为，增加很多处理细节的业务逻辑，会导致项目的最主要部分被很多非核心的代码掩埋，反而不利于读者对langchain建立一种清晰的认知。因此读者朋友在将本例中的代码应用于自己的项目中时，应该注意完善各种细节，以避免项目出现缺陷。  
