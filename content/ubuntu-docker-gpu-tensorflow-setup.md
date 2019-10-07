Title: 在Ubuntu上使用docker运行带有gpu的tensorflow
Date: 2019-09-28
Category: Misc
Modified: 2019-09-28 17:23
Tags: Ubuntu, docker, tensorflow, nvidia

# 具体步骤
具体步骤参考tensorflow官网的[教程](https://www.tensorflow.org/install/docker)基本就行了，不过要注意下：新版的docker在配置完Nvidia的Cuda driver以后不需要在用什么`runtime=nvidia`了。

# Cheat sheet

* 运行jupyter: `docker run --gpus all -it -p 8888:8888 tensorflow/tensorflow:nightly-gpu-py3-jupyter`

* 运行tensorflow bash: `docker run --gpus all -it tensorflow/tensorflow:nightly-gpu-py3 bash`

* 查看是否启用gpu，出现了的话会显示CPU和GPU的: `sess = tf.Session(config=tf.ConfigProto(log_device_placement=True))`

* 查看已经安装的images: `docker images -a`

* `--rm`: 临时的容器，用后删除



