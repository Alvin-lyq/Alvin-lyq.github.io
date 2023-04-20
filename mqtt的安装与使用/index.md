# MQTT的安装与使用


![featured-image](https://raw.githubusercontent.com/Alvin-lyq/picture/main/2023/04/upgit_20230420_1681961077.png)

介绍在树莓派上如何使用MQTT.

<!--more-->

**本人情况：树莓派4b(armv7,32位,Debian11）**

## 一、安装emqx

```bash
sudo su
apt-get update
curl -sSL https://get.docker.com | sh  # 安装docker

docker pull emqx/emqx:v4.0.0  #通过 Docker Hub (opens new window)获取z`
wget -O emqx-docker.zip https://www.emqx.com/en/downloads/broker/v4.0.0/emqx-docker-v4.0.0-alpine3.10-arm32v7.zip #通过 emqx.io下载 Docker 镜像，并手动加载,这边要注意自己的实际情况
unzip emqx-docker.zip
docker load < emqx-docker-v4.0.0-alpine3.10-arm32v7 

#启动 docker 容器
docker run -d --name emqx -p 1883:1883 -p 8081:8081 -p 8083:8083 -p 8883:8883 -p 8084:8084 -p 18083:18083 emqx/emqx:v4.0.0-alpine3.10-arm32v7 
```

## 二、登录EMQ

打开浏览器，输入你的ip:18083
用户名admin 
密码public 
<img src="https://raw.githubusercontent.com/Alvin-lyq/picture/main/2023/04/upgit_20230419_1681891268.png" alt="1" style="zoom:80%;" />

简单设置下

<img src="https://raw.githubusercontent.com/Alvin-lyq/picture/main/2023/04/upgit_20230419_1681891286.png" alt="2" style="zoom: 67%;" />

在这查看订阅情况

<img src="https://raw.githubusercontent.com/Alvin-lyq/picture/main/2023/04/upgit_20230419_1681891297.png" alt="3" style="zoom:80%;" />


## 三、下载mqttbox

下载地址：http://workswithweb.com/mqttbox.html
<img src="https://raw.githubusercontent.com/Alvin-lyq/picture/main/2023/04/upgit_20230419_1681891322.png" alt="4" style="zoom:80%;" />
官网打不开的话
链接：https://pan.baidu.com/s/1cKPgbV7OeQisNyNbm-GZYw 
提取码：izaw 

## 四、简单使用mqtt

> 前提：已启动 MQTT 服务器

点击Create MQTT Client 按钮来创建一个 MQTT 客户端；

![5](https://raw.githubusercontent.com/Alvin-lyq/picture/main/2023/04/upgit_20230419_1681891343.png)

接下来对 MQTT 客户端进行配置，主要是配置好协议端口、连接用户名密码和 QoS 即可；
![6](https://raw.githubusercontent.com/Alvin-lyq/picture/main/2023/04/upgit_20230419_1681891353.png)

 - Client Name：随便填 
 - Protocol：选择 mqtt / tcp 
 - Host：MQTT服务器的IP地址和端口 
 - Username和 Password：也是问服务端要

再配置一个订阅者，订阅者订阅 testTopicA 这个主题，我们会向这个主题发送消息；
<img src="https://raw.githubusercontent.com/Alvin-lyq/picture/main/2023/04/upgit_20230419_1681891365.png" alt="7" style="zoom:70%;" />

点击顶部 Connection 按钮进行连接，绿色表示连接上了，红色是连接断开。你也可以添加更多的发布者和订阅者。
发布者向主题中发布消息，订阅者可以实时接收到。
<img src="https://raw.githubusercontent.com/Alvin-lyq/picture/main/2023/04/upgit_20230419_1681891377.gif" alt="8" style="zoom:70%;" />

## 五、EMQ的启动和结束

因为我们是用docker下载的，所以需要用docker的一些命令启动和停止EMQ

```bash
docker ps -a #查看所有容器
docker start <CONTAINER ID>
docker stop <CONTAINER ID>
docker restart <CONTAINER ID>
```

![9](https://raw.githubusercontent.com/Alvin-lyq/picture/main/2023/04/upgit_20230419_1681891438.png)

> 参考：
> 1.https://docs.emqx.cn/broker/v4.3/getting-started/install.html#%E9%80%9A%E8%BF%87-docker-%E8%BF%90%E8%A1%8C-%E5%8C%85%E5%90%AB%E7%AE%80%E5%8D%95%E7%9A%84-docker-compose-%E9%9B%86%E7%BE%A4
> 2.https://www.bilibili.com/video/BV1aV411h7Y2 （https://www.bilibili.com/read/cv8824727?spm_id_from=333.999.0.0）
> 3.https://blog.csdn.net/zuozewei/article/details/118052978

