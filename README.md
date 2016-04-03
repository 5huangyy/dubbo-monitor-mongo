# Dubbo Monitor for MongoDB

## 项目介绍

![Dubbo monitor screenshot](https://github.com/handuyishe/dubbo-monitor/wiki/images/screenshot.png)

Dubbo Monitor是针对Dubbo开发的监控系统，基于dubbo-monitor-simple改进而成，可以理解为其演化版本。该系统用数据库记录日志的方式替代了dubbo-monitor-simple写文件的方式。

## 升级日志

>### 2016-04-03
> 1. 发布1.0.1版本（by [菩提树下的杨过](http://yjmyzz.cnblogs.com)）
> 2. 将zkclient升级成[0.8.1](https://github.com/yjmyzz/zkclient)。
> 3. 将依赖的dubbox版本升级成[2.8.4a](https://github.com/yjmyzz/dubbox)
> 4. 将log4j升级为log4j2
> 5. 修正consumer为null时,写入mongodb失败的bug

>### 2015-12-23
>
> 1. 发布Dubbo Monitor for Mongo版本1.0.0，版本分支为mongo。

## Dubbo Monitor使用帮助

### Dubbo-Monitor配置介绍

`第一步`：创建数据库
首先搭建MongoDB，创建名称为dubbo_monitor数据库。

`第二步`：编辑项目中application.properties，配置如下：

```
####Dubbo Settings
dubbo.application.name=dubbo-monitor
dubbo.application.owner=handu.com
dubbo.registry.address=zookeeper://127.0.0.1:2181
dubbo.protocol.port=6060

####MongoDB Settings
db.url=127.0.0.1
db.port=27017
db.username=
db.database=
db.password=

####System Manager
manager.username=admin
manager.password=admin
```

`第三步`：打包运行项目
执行maven命令：mvn clean package
target文件夹下生成的dubbo-monitor.war即为项目部署文件，将其放置到对应服务器目录下，启动服务器即可。例如：tomcat的webapps文件夹下。

`第四步`：访问项目
访问项目 启动web服务器后，访问地址：http://IP:[port]/dubbo-moniotor，采用配置文件中manager.username和manager.password设置值进行登录。

## 服务提供端配置

[Dubbo服务提供端监控配置](http://dubbo.io/User+Guide-zh.htm#UserGuide-zh-%3Cdubbo%3Amonitor%2F%3E)