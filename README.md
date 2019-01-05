---
搭建属于你自己的梯子
---

# 前言

本文基于clowwindy开发的ss技术以及teddysun的脚本进行ss服务器的搭建,bbr算法优化

VPS系统:**centos7**

本教程主要分为**两步**:

* 修改内核bbr优化
* 安装ss程序

# 开始

##### 1.首先用teddysun的[一键安装最新内核并开启 BBR 脚本](https://teddysun.com/489.html)对内核进行修改,使用bbr算法优化

```linux
wget --no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh && chmod +x bbr.sh && ./bbr.sh
```

完成后需要重启服务器

##### 测试是否开启成功:

```
sysctl net.ipv4.tcp_congestion_control
```

返回值一般为:

```
net.ipv4.tcp_congestion_control = bbr
```

如果一致则代表bbr优化成功

##### 2.基于teddysun的[Shadowsocks 一键安装脚本（四合一）](https://shadowsocks.be/11.html)安装ss服务端

```
wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-all.sh
chmod +x shadowsocks-all.sh
./shadowsocks-all.sh 2>&1 | tee shadowsocks-all.log
```

会要求提示输入密码,端口

安装完成后会将服务器配置信息显示出来,即可使用各种客户端进行连接

# 卸载方法

使用root用户登录执行以下命令

```
./shadowsocks-all.sh uninstall
```

#### 参考页面:

再次感谢clowwindy和teddysun,站在巨人的肩膀上才能让我们走的更远

 [Shadowsocks 一键安装脚本（四合一）](https://shadowsocks.be/11.html)

 [一键安装最新内核并开启 BBR 脚本](https://teddysun.com/489.html)