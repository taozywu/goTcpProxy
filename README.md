## goTcpProxy 

[![Go Report Card](https://goreportcard.com/badge/github.com/zheng-ji/goTcpProxy)](https://goreportcard.com/report/github.com/zheng-ji/goTcpProxy)

一个支持负载均衡，健康检查的 TcpProxy 

![smailltcp](https://cloud.githubusercontent.com/assets/1414745/19109474/2eea5e56-8b28-11e6-80ba-be5ed9117f9e.jpg)

### Description

#### English
* A tcp proxy service
* Supprot multi backend severs 
* Consistent Hash Load Balance
* Auto detect down server, and remove it.
* Monitor backend health status

#### 中文

* TCP 代理服务
* 后端支持多个服务器
* 支持一致性哈希的负载均衡
* 自动检测失败的后端服务器，并移除
* 后端服务的健康检查接口

### How To Compile

```
cd $GOPATH;
git clone https://github.com/zheng-ji/goTcpProxy.git;
cd goTcpProxy
```
说明下
1.事先我并没有安装go；然后在安装go过程中发现不少地方巨坑！
2.install go-go1.4（你这个程序跑go高版本会报错！）
3.需要配置$GOROOT $GOPATH $PATH
4.缺失依赖包
  go get stathat.com/c/consistent
  go get launchpad.net/goyaml
  go get github.com/Sirupsen/logrus
5.编译 make
```

### How To Use

配置文件详解

```
bind: 0.0.0.0:9999      // 代理服务监听端口
wait_queue_len: 100     // 等待队列长度
max_conn: 10000         // 并发最大连接
timeout: 5              // 请求超时时间
failover: 3             // 后端服务允许失败次数 
stats: 0.0.0.0:19999    // 健康检查接口
backend:                // 后端服务列表
    - 127.0.0.1:80
    - 127.0.0.1:81
log:
    level: "info"
    path: "/Users/zj/proxy.log"
```

```
// 运行服务
./goTcpProxy -c=etc/conf.yaml
```

![gotcp](https://cloud.githubusercontent.com/assets/1414745/19108922/68eeab00-8b25-11e6-903a-864a19e2d9c5.png)

License
-------

Copyright (c) 2015 released under a MIT style license.
