这个非常简单啊，几步就完成了

# [](https://linux.do/t/topic/220086#p-1965202-h-1serv00-1)1. 将域名托管到 serv00

![image.png](https://easyimage.01011205.xyz/i/0/2024/09/30/dqdiyu-0.webp)


可以通过回源方式解决 IP 被墙问题  
参考：

![](https://linux.do/user_avatar/linux.do/xjfkkk/48/12365_2.png) [给 serv00 添加优质域名并加速网站](https://linux.do/t/topic/174317) [资源荟萃](https://linux.do/c/resource/14)

> serv00 不加速网站的情况下延迟比较高，而且自带的域名也很不美观。有很多免费高大上但是不能托管 cloudflare 的域名，要充分将其利用请见下文 ![wink](https://linux.do/images/emoji/apple/wink.png?v=12 "wink") [](https://linux.do/t/topic/220086#p-1392492-h-1)开始前准备 1.serv00 账号申请 [https://www.serv00.com/](https://www.serv00.com/) 2. 注册一个添加到 serv00 的免费域名 [changeip.com](https://www.changeip.com/) 注册参考： [https://linux.do/t/topic/17025…](https://linux.do/t/topic/170258)

# [](https://linux.do/t/topic/220086#p-1965202-h-2mysql-2)2. 创建一个 MySQL
![image.png](https://easyimage.01011205.xyz/i/0/2024/09/30/dqs8rs-0.webp)
![image.png](https://easyimage.01011205.xyz/i/0/2024/09/30/dqvtiy-0.webp)


# [](https://linux.do/t/topic/220086#p-1965202-h-3www-websites-3)3. 进入 WWW websites 设置权限

![image.png](https://easyimage.01011205.xyz/i/0/2024/09/30/drd92u-0.webp)


# [](https://linux.do/t/topic/220086#p-1965202-h-4freshrss-4)4. 下载 FreshRSS 包

进入 `public_html` 文件下

```
cd /usr/home/你的serv名字/domains/域名/public_html
```

下载 FreshRSS 包

```
git clone https://github.com/FreshRSS/FreshRSS.git && mv FreshRSS/* ./ && rm -rf FreshRSS
```

# [](https://linux.do/t/topic/220086#p-1965202-h-5-5)5. 开始安装

访问你的 serv00 域名  
填入相关参数  
![image.png](https://easyimage.01011205.xyz/i/0/2024/09/30/dryhza-0.webp)
![image.png](https://easyimage.01011205.xyz/i/0/2024/09/30/drzv50-0.webp)
![image.png](https://easyimage.01011205.xyz/i/0/2024/09/30/ds57wv-0.webp)

![image.png](https://easyimage.01011205.xyz/i/0/2024/09/30/ds3636-0.webp)
![image.png](https://easyimage.01011205.xyz/i/0/2024/09/30/ds8pfz-0.webp)

转载自：[在 serv00 上搭建 FreshRSS](https://linux.do/t/topic/220086)