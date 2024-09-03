# 项目官方文档

[https://temp-mail-docs.awsl.uk/zh/guide/config-send-mail](https://temp-mail-docs.awsl.uk/zh/guide/config-send-mail)

# 项目github仓库

[https://github.com/dreamhunter2333/cloudflare_temp_email](https://github.com/dreamhunter2333/cloudflare_temp_email)

# 安装过程

## 首先要定义两个域名

- 前端url webmail.0808888.xyz
- 后端url cfmail-api.0808888.xyz

## 1.数据库设置

- 在works和pages中选D1数据库
- 创建数据库起名字dev
- 创建后进入到dev数据库,然后打开consol标签  
    -把 [https://github.com/dreamhunter2333/cloudflare_temp_email/blob/main/db/schema.sql](https://github.com/dreamhunter2333/cloudflare_temp_email/blob/main/db/schema.sql)这个schema.sql文件中的内容复制到donsol中,然后点击Execute按钮
- 数据库创建完成

---

## 2.后台程序部署

- 还是在在works和pages中,创建应用程序,选workers
- 起名字cfmail-api,保存,然后点右下角完成.
- 然后界面中右上角点edit code.
- 然后再左边点击文件按钮,右键点works.js然后删除.
- **再下载[works.js](https://github.com/dreamhunter2333/cloudflare_temp_email/releases/latest/download/worker.js)**
- 右键点击,出现上传,把下载的works.js上传上去,然后右上角部署
- 再来到项目的settings-->Variables中,添加变量
- 开始部署时我们只添加4个变量,文章结尾我附带了可设置的变量代码示例说明.
    
    - ADMIN_PASSWORDS = ["1234"]
    - PASSWORDS = ["1234"]
    - DOMAINS = ["milaone.app"]
    - JWT_SECRET =["xxxyyyzzz"]
- 在KV Namespace Bindings中添加一个KV
    
    - 创建一个KV,起名字dev
    - 然后在这里Variable name填 KV 大写.
    - KV Namespace选择创建的KV库dev
- 添加D1数据库
    
    - 同样在settings-->Variable中,找到D1 Database,添加上一步创建的数据库dev
- 最后再进行部署一次.

- 后端验证
    
    - 后端设置完成后,可以通过访问后端域名的url及目录进行验证,例如我的域名
    - cfmail-api.0808888.xyz 返回结果OK
    - cfmail-api.0808888.xyz/health_check 返回结果OK
    - 则说明后端配置完成.后期可随时在变量中增删内容以达到配置效果

---

## 3.前台程序部署

- 还是在在works和pages中,创建应用程序,选Pages
- 选择Create using direct upload,然后再选择Upload assets按钮
- 然后来到作者的官方文档中 [点击这里生成配置文件](https://temp-mail-docs.awsl.uk/zh/guide/ui/pages.html)
- 在该页面中的地址栏输入后端的域名的https地址,比如我使用的地址是[https://cfmail-api.0808888.xyz](https://cfmail-api.0808888.xyz/) 生成配置,得到下载一个frontend.zip文件,上传到pages中.  
    ![2024-06-06T02:47:55.png](https://www.milaone.com/usr/uploads/2024/06/1764034871.png "2024-06-06T02:47:55.png")
- 最后在Custom Domain给前端自定义一个域名,例如我使用的是webmail.0808888.xyz
- 前端验证,访问前端[https://webmail.milaone.com](https://webmail.milaone.com/),此时应该出现界面并提示输入密码

## 3.邮件路由设置

- 来到[https://dash.cloudflare.com](https://dash.cloudflare.com/) 面板首页,然后选择需要使用的域名进入.
- 左边选择Email菜单,在Email Routing中选择Routing ruls中Catch-all address  
    激活,并且edit.
- 其中的Action选择的是Send to a Worker ,目标选择后端的worker名字
- 验证:截止到现在登录前端url已经可以

## 4.发送邮件设置

- [https://resend.com/domains](https://resend.com/domains)进行域名验证
- 然后在API-Key 中创建一个api,全部权限,然后把密码拷贝
- 到后端的Worker中Settings-->Environment Variables-->添加一个变量
- RESEND_TOKEN = re_PxW46o6o_HJrmMYARCGdhMtB3JHD(上一步拷贝出来的密码)

## 截止到以上步骤,就可以完整的收发邮件了.

## 如果需要更方便的朋友,强烈建议挂上Telegram机器人

## 5.Telegram机器人

- 创建机器人(具体方法自己搜.)
- 拿到用于这个项目的机器人token,还有telegram的账户id.
- 到后端的Worker中Settings-->Environment Variables-->添加一个变量
- TELEGRAM_BOT_TOKEN = 机器人token
- 在邮件的管理后台,机器人中填入账户id.

# 附1:变量说明

```
[vars]
# TITLE = "Custom Title" # 自定义网站标题
PREFIX = "tmp" # 要处理的邮箱名称前缀，不需要后缀可配置为空字符串
# 如果你想要你的网站私有，取消下面的注释，并修改密码
# PASSWORDS = ["123", "456"]
# admin 控制台密码, 不配置则不允许访问控制台
# ADMIN_PASSWORDS = ["123", "456"]
# admin 联系方式，不配置则不显示，可配置任意字符串
# ADMIN_CONTACT = "xx@xx.xxx"
DOMAINS = ["xxx.xxx1" , "xxx.xxx2"] # 你的域名, 支持多个域名
JWT_SECRET = "xxx" # 用于生成 jwt 的密钥, jwt 用于给用户登录以及鉴权
BLACK_LIST = "" # 黑名单，用于过滤发件人，逗号分隔
# 是否允许用户创建邮件, 不配置则不允许
ENABLE_USER_CREATE_EMAIL = true
# 允许用户删除邮件, 不配置则不允许
ENABLE_USER_DELETE_EMAIL = true
# 允许自动回复邮件
ENABLE_AUTO_REPLY = false
# 是否启用 webhook
# ENABLE_WEBHOOK = true
# 前端界面页脚文本
# COPYRIGHT = "Dream Hunter"
# 默认发送邮件余额，如果不设置，将为 0
# DEFAULT_SEND_BALANCE = 1
# Turnstile 人机验证配置
# CF_TURNSTILE_SITE_KEY = ""
# CF_TURNSTILE_SECRET_KEY = ""
# dkim config
# DKIM_SELECTOR = "mailchannels" # 参考 DKIM 部分 mailchannels._domainkey 的 mailchannels
# DKIM_PRIVATE_KEY = "" # 参考 DKIM 部分 priv_key.txt 的内容
# telegram bot 最多绑定邮箱数量
# TG_MAX_ACCOUNTS = 5
# 全局转发地址列表，如果不配置则不启用，启用后所有邮件都会转发到列表中的地址
# FORWARD_ADDRESS_LIST = ["xxx@xxx.com"]