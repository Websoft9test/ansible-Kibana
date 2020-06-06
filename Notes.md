# Kibana Notes

组件名称：kibana  
安装文档：https://www.elastic.co/guide/en/kibana/7.6/rpm.html#rpm-repo
配置文档：https://www.elastic.co/guide/en/kibana/current/settings.html
支持平台：Debian家族 | RHEL家族 | Windows | macOS | Docker

责任人：zxc

## 概要

kibana 是开源的分析和可视化平台，是一个ES中间件,和ES一起工作，实现ES可视化，用来搜索，查看，并和存储在ES中的数据进行交互。

## 环境要求

* 程序语言：   js
* 应用服务器：自带
* 数据库:   
* 依赖组件：ES
* 其他：

## 安装说明

本项目通过kibana源码安装。

下面基于不同的安装平台，分别进行安装说明。

### CentOS

```shell
#安装java 8
yum install java-1.8.0-openjdk

#安装ES

#安装kibana
rpm --import https://artifacts.elastic.co/GPG-KEY-elasticsearch    #导入公钥
vim /etc/yum.repos.d/kibana.repo
[kibana-7.x]
name=Kibana repository for 7.x packages
baseurl=https://artifacts.elastic.co/packages/7.x/yum
gpgcheck=1
gpgkey=https://artifacts.elastic.co/GPG-KEY-elasticsearch
enabled=1
autorefresh=1
type=rpm-md

sudo yum install kibana 

#启动kibana,并设置开机自启
sudo systemctl daemon-reload
sudo systemctl enable kibana.service
sudo systemctl start kibana.service
```



## 路径

* 程序路径：      /usr/share/kibana
* 日志路径：      /var/log/kibana/path.logs
* 配置文件路径：  /etc/kibana/kibana.yml
* 启动路径:       /usr/share/kibana/bin        
* 其他...

## 配置

安装完成后，需要依次完成如下配置

```shell
#配置kibana
/etc/kibana/kibana.yml:
server.port: 5601
server.host: "0.0.0.0"
elasticsearch.hosts: ["0.0.0.0:9200"]
```

## 账号密码

### 数据库密码

如果有数据库

* 数据库安装方式：
* 账号密码：无

### 后台账号

如果有后台账号

* 登录地址  http://your ip:5601
* 账号密码    无
* 密码修改方案：最好是有命令行修改密码的方案


## 服务

本项目安装后有服务,可设置为开机自启

备注：

服务的模板如下：

```
[Unit]
Description=Kibana

[Service]
Type=simple
User=kibana
Group=kibana
# Load env vars from /etc/default/ and /etc/sysconfig/ if they exist.
# Prefixing the path with '-' makes it try to load, but if the file doesn't
# exist, it continues onward.
EnvironmentFile=-/etc/default/kibana
EnvironmentFile=-/etc/sysconfig/kibana
ExecStart=/usr/share/kibana/bin/kibana "-c /etc/kibana/kibana.yml"
Restart=on-failure
RestartSec=3
StartLimitBurst=3
StartLimitInterval=60
WorkingDirectory=/

[Install]
WantedBy=multi-user.target
~                           
```

## 环境变量

列出需要增加的环境变量以及增加环境变量的命令：无

* 名称 | 路径

## 版本号

通过如下的命令获取主要组件的版本号: 

```
# Check kibana version
 rpm -qa|grep kibana
```

## 常见问题

#### 有没有管理控制台？

*http:// 公网 IP:5601* 即可访问kibana控制台

#### 本项目需要开启哪些端口？

| item | port |
| ---- | ---- |
| node | 5601 |
| java | 9200 |
| java | 9300 |

#### 有没有CLI工具？

无  

## 日志

* 2020-04-22 完成CentOS安装研究