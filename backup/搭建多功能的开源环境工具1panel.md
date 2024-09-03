![0bf209eb28da82a04aa1a.jpg](https://img.yohaman.pp.ua/file/0bf209eb28da82a04aa1a.jpg)
[转载：一瓶奶油1Panel搭建Wordpress](https://naiyous.com/5690.html)

准备工作

下载并安装SSH连接工具Finalshell：【[点击进入](https://www.hostbuf.com/t/988.html)】

准备一个域名并托管到Cloudflare：【[点击进入](https://dash.cloudflare.com/login)】

1、关闭防火墙/设置防火墙规则

ufw disable
2、更新系统

apt update -y  && apt upgrade -y
3、1Panel官网：【[点击进入](https://1panel.cn/)】

一键安装脚本
curl -sSL https://resource.fit2cloud.com/1panel/package/quick_start.sh -o quick_start.sh && sudo bash quick_start.sh
4、安装应用：OpenResty、MySQL、Redis、PHP8

5、创建数据库

点击创建数据库——自定义名称和用户名——密码随机——其它保持默认——点击确定
6、创建网站并申请证书

点击创建网站——点击运行环境——其它保持默认——输入解析好的域名——点击确定

点击证书——点击Acme账户——点击创建账户——输入邮箱（==你自己的邮箱==）——点击确定——点击返回——点击申请证书——输入解析好的域名——其它保持不变——验证方式选择HTTP——点击确定（==注意：这一步申请证书前，请检查防火墙是否关闭或者放行80端口==）

点击网站——点击网站名称——点击HTTPS——启用 HTTPS——Acme 账户点开——选择前面创建好的账户——点击保存

点击网站目录——点击“root目录”后面的蓝色文件夹图标——把index.php文件删掉——点击远程下载——Wordpress下载：【[点击进入](https://cn.wordpress.org/download/)】——复制链接地址过来——点击确认——下载完成后关掉——解压下载的文件——点击确认——得到wordpress文件夹——把压缩包删除——再点击到网站——点击网站名称——点击网站目录——点开运行目录——选择/wordpress——点击保存并重载

7、Wordpress登录并设置

新打开一个页面——输入网站域名——点击现在就开始——回到1panel面板——点击数据库——把数据库名称、用户名、密码复制过来——数据库主机输入：mysql——点击下一步——复制配置文件内容——回到1panel面板——点击网站——点击网站目录——打开wordpress——找到此“wp-config-sample.php”并打开——删除里面的内容——把复制的内容粘贴进去——点击确认——再把文件重命名为“wp-config.php”——再回到前端——点击运行安装程序——站点标题自定义——用户名自定义——密码自定义——输入自己的邮箱——点击安装WordPress——点击登录——输入设置好的邮箱和密码——即可完成安装