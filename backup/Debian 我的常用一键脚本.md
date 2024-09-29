萌咖大佬一键DD脚本
更新
```
apt-get update
```

安装必备工具
```
apt-get install -y xz-utils openssl gawk file
```

全自动一键安装 debian 12
```
bash <(wget --no-check-certificate -qO- 'https://moeclub.org/attachment/LinuxShell/InstallNET.sh') -d 12 -v 64 -p 登录密码 -a

```
更多参考:https://github.com/Tasle/InstallNET

一键更新系统
```
apt update -y && apt full-upgrade -y && apt autoremove -y && apt autoclean -y
```

查看 Debian 版本
```
cat /etc/debian_version
```

一键安装 wget curl git
```
apt install sudo curl wget 

```

一键替换最新内核 BBR (卸载内核版本)
```
wget -O tcp.sh "https://github.com/ylx2016/Linux-NetSpeed/raw/master/tcp.sh" && chmod +x tcp.sh && ./tcp.sh

```
我一般选择 BBRplus 5 -> 19
弹出提示选择 NO


一键 IP 质量体检和解锁检测
```
bash <(curl -Ls IP.Check.Place)

```
融合怪
```
curl -L https://gitlab.com/spiritysdx/za/-/raw/main/ecs.sh -o ecs.sh && chmod +x ecs.sh && bash ecs.sh

```

科技lion脚本工具箱
```
bash <(curl -sL kejilion.sh)
```

我一般选择
13 -> 2 修改登录密码
13 -> 6 修改SSH连接端口
13 -> 12 修改虚拟内存大小
13 -> 15 系统时区调整
13 -> 22 fail2banSSH防御程序
13 -> 26 修复OpenSSH高危漏洞（岫源）


参考资料 [2024年最全面VPS调优教程](https://www.youtube.com/watch?v=OR73PNaJmbk)

安装 Docker
```
https://igeekbb.com/2023/04/20/DockerCompose/
```

转载自：[Geek大佬的Debian 我的常用一键脚本]（https://www.igeekbb.com/2024/09/18/debian/）