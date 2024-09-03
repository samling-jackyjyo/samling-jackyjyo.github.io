## 一.搭建前的准备

1、域名一个，如果没有，购买一个com、net或者org，不推荐用不受信任的域名后缀。  
2、vps（要开启25端口），推荐使用netcup的1o机,但是netcup的1o机内存可能不够，最好用2g内存及以上的vps，不过1g内存的也不是不能用，可以通过添加swap解决内存不足问题.  
3.检测vps是否开启25端口

```undefined
telnet smtp.qq.com 25
```

如果出现一直超时，说明没有开放25端口，如图  
![6d4481dfb6193e2e77b9c.png](https://img.yohaman.pp.ua/file/6d4481dfb6193e2e77b9c.png)


开启25端口的vps测试结果如图  
![2d8d2bb7281cac7170f82.png](https://img.yohaman.pp.ua/file/2d8d2bb7281cac7170f82.png)


## 二.开始搭建

本次教程，我使用的vps系统为Debian11!  
1.域名解析

```objectivec
主机记录,记录类型,记录值
mail	A	    你的IP地址
smtp	CNAME	mail.**.com
pop	    CNAME	mail.**.com
imap	CNAME	mail.**.com
@	    MX	    mail.**.com
@	    TXT	    v=spf1 mx ~all
```

如果用的是cloudflare，可以参考一下我的图片  
![0f4b1d03a7a528a3b0395.png](https://img.yohaman.pp.ua/file/0f4b1d03a7a528a3b0395.png)

2.添加swap（内存低于2G的vps需要添加swap，大于2G的vps可以跳过）  
要添加2G(2048MB)的swap,添加swap脚本：

```ruby
wget https://www.moerats.com/usr/shell/swap.sh && bash swap.sh
```

3.更新系统，安装docker和screen；

```lua
apt  update && apt install screen docker.io -y
```

4.拉取镜像

```bash
docker pull analogic/poste.io
```

5.新建邮件目录

```bash
mkdir /home/mail
```

6.设置主机名(提高邮箱分值)

```cpp
sudo hostnamectl set-hostname mail.abc.com
```

注意:把 <font color="#c0504d">mail.abc.com</font> 修改为你的域名  
7.开启一个screen

```undefined
screen -S mailserver
```

8.在screen中启动容器，注意这里的：mail.abc.com要改成你的邮箱域名！

```bash
screen
docker run \
    --net=host \
    -e TZ=Europe/Prague \
    -v /home/mail:/data \
    --name "mailserver" \
    -h "mail.abc.com" \
    -t analogic/poste.io
```

出现以下界面就成功安装了！  
![182b189ccc9f1d5da5394.png](https://img.yohaman.pp.ua/file/182b189ccc9f1d5da5394.png)
出现这个界面之后，按下键盘上的 Ctrl+A+D，退出screen  
9.访问地址 mail.你的域名/admin/install/server（这里显示不安全，继续访问，下一步设置证书），设置域名，管理员邮箱和密码。  
![075f99dbfb685ce827e03.png](https://img.yohaman.pp.ua/file/075f99dbfb685ce827e03.png)

10.在系统设置中，在virtual domains中，点击你的域名，然后在域名详情中，点击生成redirect，生成后添加域名DKIM 解析，例如：  
![e5478101bad78490ff350.png](https://img.yohaman.pp.ua/file/e5478101bad78490ff350.png)
然后打开你的域名解析提供商，添加解析  
![image](https://speedtest.thya.tk/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202024-08-20%20145654.png)  
11.给邮箱添加tls  
（1）在系统设置中，点击 system settings,点击TLS Certificate  
![8e33501b159ab3205011e.png](https://img.yohaman.pp.ua/file/8e33501b159ab3205011e.png)  
（2）把前面的mail._**.com,pop.**_.com,imap._**.com,smtp.**_.com 添加到Alternative names里  
![5d4b1f46621c867c11f63.png](https://img.yohaman.pp.ua/file/5d4b1f46621c867c11f63.png)
（3）把Enabled 勾上，然后点击 Save changes,然后慢慢等待它自动申请证书  
出现这个界面就是申请成功了(没看到的多刷新几次)  
![9a00045881fbe1041a9c6.png](https://img.yohaman.pp.ua/file/9a00045881fbe1041a9c6.png)

## 三.登录邮箱

邮箱用户登陆地址为 mail.你的域名/webmail/，打开后输入你的账户密码，就可以测试发信了；检测邮箱健康 [https://www.mail-tester.com/](https://www.nodeseek.com/jump?to=https%3A%2F%2Fwww.mail-tester.com%2F)  
![7ae813cf2cdb7f8c7e189.png](https://img.yohaman.pp.ua/file/7ae813cf2cdb7f8c7e189.png)

然后你就可以快乐的发邮件了!