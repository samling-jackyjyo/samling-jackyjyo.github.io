转载自：[Cloudflare Workers优秀项目收集（持续更新） - iGdu (igdux.com)](https://www.igdux.com/workers)


Cloudflare 是一家伟大的互联网公司，她致力于建立更好的互联网。目前她提供的服务强大而又高效，同时很多项目都可以免费使用，诸如免费提供 CDN、DNS 服务以及本文即将介绍的 Worker 服务。

## 1. 什么是 Cloudflare Workers[#](https://www.igdux.com/workers#user-content-1-%E4%BB%80%E4%B9%88%E6%98%AF-cloudflare-workers)

Cloudflare Workers 是一个可以让你运行 Javascript 的（无服务器）平台，具体详情请看[官网介绍](https://blog.cloudflare.com/cloudflare-workers-unleashed/)。

## 2. 为什么用 Cloudflare Workers[#](https://www.igdux.com/workers#user-content-2-%E4%B8%BA%E4%BB%80%E4%B9%88%E7%94%A8-cloudflare-workers)

因为它比较强大，而且免费。它强大的地方，包括抗 DDOS 攻击，在线率高；同时，它也提供了免费版和收费版，其中免费版一般足够个人使用；而且，它可以分配一个域名，不需要额外购买域名。  
当然，如果遇到 Cloudflare Worker 打不开的情形，可以考虑绑定自己的域名，这里推荐购买一个便宜的.xyz 域名或申请 eu.org 免费域名。

## 3.Cloudflare Workers 可以做什么[#](https://www.igdux.com/workers#user-content-3cloudflare-workers-%E5%8F%AF%E4%BB%A5%E5%81%9A%E4%BB%80%E4%B9%88)

Cloudflare Workers 可以做 Javascript 能做的事情。注意：Cloudflare Workers 每天限制 10W 次免费请求，个人使用，一般都够了。同时，Cloudflare 也提供了收费版，每月 5$/1000 万次请求。

## 4.Cloudflare Workers 优秀项目集景[#](https://www.igdux.com/workers#user-content-4cloudflare-workers-%E4%BC%98%E7%A7%80%E9%A1%B9%E7%9B%AE%E9%9B%86%E6%99%AF)

### 4.1 节点[#](https://www.igdux.com/workers#user-content-41-%E8%8A%82%E7%82%B9)

3K 大佬改写的项目：[https://github.com/3Kmfi6HP/EDtunnel](https://github.com/3Kmfi6HP/EDtunnel)

Zizifn 大佬原创的项目：[https://github.com/zizifn/edgetunnel/blob/main/src/worker-vless.js](https://github.com/zizifn/edgetunnel/blob/main/src/worker-vless.js)  
CMliu 等大佬分享的项目：[https://github.com/cmliu/epeius](https://github.com/cmliu/epeius) 和[https://github.com/ca110us/epeius](https://github.com/ca110us/epeius)

部署自定义订阅服务：[https://github.com/mjjonone/sub-worker/blob/main/_worker.js](https://github.com/mjjonone/sub-worker/blob/main/_worker.js)

### 4.2 建站[#](https://www.igdux.com/workers#user-content-42-%E5%BB%BA%E7%AB%99)

#### 通过 Workers 搭建博客：[#](https://www.igdux.com/workers#user-content-%E9%80%9A%E8%BF%87-workers-%E6%90%AD%E5%BB%BA%E5%8D%9A%E5%AE%A2)

方案一：采用[OXeu 大佬](https://github.com/OXeu)开发的[Rin 项目](https://github.com/OXeu/Rin)，该项目基于 Cloudflare Pages + Workers + D1 + R2 搭建博客（需要一个托管于 Cloudflare 的域名），Rin 实例：[https://xeu.life/](https://xeu.life/) 。  
方案二：采用基于 Cloudflare Pages + D1 + R2+ Zero Trust 的 Microfeed 项目：[https://github.com/microfeed/microfeed](https://github.com/microfeed/microfeed) 。

方案三：利用 worker 的 KV 作为数据库搭建博客：源码：[gdtool/Cloudflare-workers-blog](https://github.com/gdtool/cloudflare-workers-blog)，安装教程，[在这里](https://cfblog.661212.xyz/article/000003/cfblog-plus.html) ，实例：[https://blog.gezhong.vip/](https://blog.gezhong.vip/) ;  
方案四：利用 workers+github 搭建博客系统，源码:[kasuganosoras/cloudflare-worker-blog](https://github.com/kasuganosoras/cloudflare-worker-blog) ；

#### 通过 Workers 搭建导航站：[#](https://www.igdux.com/workers#user-content-%E9%80%9A%E8%BF%87-workers-%E6%90%AD%E5%BB%BA%E5%AF%BC%E8%88%AA%E7%AB%99)

利用 worker 搭建导航站，源码：[sleepwood/CF-Worker-Dir](https://github.com/sleepwood/CF-Worker-Dir)

#### 利用 Workers 搭建图床：[#](https://www.igdux.com/workers#user-content-%E5%88%A9%E7%94%A8-workers-%E6%90%AD%E5%BB%BA%E5%9B%BE%E5%BA%8A)

源码：[x-dr/telegraph-Image](https://github.com/x-dr/telegraph-Image)，实例：[https://img.131213.xyz/](https://img.131213.xyz/)   
源码：[igengdu/telegraph-Image](https://github.com/igengdu/telegraph-Image)，实例：[https://img.231516.xyz/](https://img.231516.xyz/)   
源码：[missuo/Telegraph-Image-Hosting](https://github.com/missuo/Telegraph-Image-Hosting)，实例：[https://missuo.ru/](https://missuo.ru/)  
源码：[ifyour/cf-image-hosting](https://github.com/ifyour/cf-image-hosting)，实例：[https://images.mingming.dev/](https://images.mingming.dev/)  
源码：[cf-pages/Telegraph-Image](https://github.com/cf-pages/Telegraph-Image)，实例：[https://im.gurl.eu.org/](https://im.gurl.eu.org/)  
源码：[csznet/tgState](https://github.com/csznet/tgState)，实例：[https://tgstate.vercel.app](https://tgstate.vercel.app/) 或 [https://tgstate.ikun123.com/](https://tgstate.ikun123.com/) （基于 Telegram，存在封号风险，需谨慎）  
源码：[beilunyang/img-mom](https://github.com/beilunyang/img-mom)，可（同时）搭建于 R2，Backblaze B2 或 Telegram 的图床，实例：[https://t.me/img_mom_bot](https://t.me/img_mom_bot) （基于 Telegram 的图床，存在封号风险，需谨慎）。  
源码：[iiop123/workers-image-hosting](https://github.com/iiop123/workers-image-hosting)，实例：[点击查看](https://img.giao111.workers.dev/index.html)

#### 通过 Workers 搭建 Pastebin 服务[#](https://www.igdux.com/workers#user-content-%E9%80%9A%E8%BF%87-workers-%E6%90%AD%E5%BB%BA-pastebin-%E6%9C%8D%E5%8A%A1)

源码：[SharzyL/pastebin-worker](https://github.com/SharzyL/pastebin-worker)，实例：[https://shz.al/](https://shz.al/)  
源码：[igdume/pastebin-worker](https://github.com/igdume/pastebin-worker)（基于 SharzyL 项目修改），实例：[https://igdux.top](https://igdux.top/)   
源码：[yllhwa/FileWorker](https://github.com/yllhwa/FileWorker)  
源码：[iiop123/dingding](https://github.com/iiop123/dingding)

#### 通过 Workers+R2 搭建网盘服务[#](https://www.igdux.com/workers#user-content-%E9%80%9A%E8%BF%87-workersr2-%E6%90%AD%E5%BB%BA%E7%BD%91%E7%9B%98%E6%9C%8D%E5%8A%A1)

源码：[longern/FlareDrive](https://github.com/longern/FlareDrive) ，实例：[https://drive.longern.com/](https://drive.longern.com/) （基于 R2）；  
源码：[ljxi/Cloudflare-R2-oss](https://github.com/ljxi/Cloudflare-R2-oss)，基于[FlareDrive 项目](https://github.com/longern/FlareDrive)汉化、完善，基于 Cloudflare 的 R2+Workers。

#### 通过 Workers 搭建短网址服务：[#](https://www.igdux.com/workers#user-content-%E9%80%9A%E8%BF%87-workers-%E6%90%AD%E5%BB%BA%E7%9F%AD%E7%BD%91%E5%9D%80%E6%9C%8D%E5%8A%A1)

源码 1：[https://github.com/x-dr/short](https://github.com/x-dr/short) ，实例：[https://d.131213.xyz/](https://d.131213.xyz/) （推荐）；  
源码 2：基于[x-dr 大佬](https://github.com/x-dr)的[short 项目](https://github.com/x-dr/short)修改[https://github.com/igengdu/short/](https://github.com/igengdu/short/) ，实例：[https://d.igdu.xyz](https://d.igdu.xyz/)。  
源码 3：基于[x-dr 大佬](https://github.com/x-dr)的[short 项目](https://github.com/x-dr/short)修改：[https://github.com/harrisonwang/linklet](https://github.com/harrisonwang/linklet) ，实例：[https://t.xiaowangye.org/](https://t.xiaowangye.org/) ；  
源码 4：[Crazypeace 大佬](https://github.com/crazypeace)的[Url-Shorten-Worker](https://github.com/crazypeace/Url-Shorten-Worker)，[教程](https://zelikk.blogspot.com/2022/07/url-shorten-worker-hide-tutorial.html)（推荐）  
源码 5：[xyTom/Url-Shorten-Worker](https://github.com/xyTom/Url-Shorten-Worker/)，实例：[https://lnks.eu.org/](https://lnks.eu.org/)  
源码 6：[Short-url](https://github.com/Likenttt/eastlake-cloudflare-worker-short-url)，[教程](https://blog.661212.xyz/index.php/archives/4/)，实例：[https://cf-url-admin.li2niu.com/](https://cf-url-admin.li2niu.com/) （Username: li2niu，Password: li2niu）  
源码 7：[Closty/duanwangzhi](https://github.com/Closty/duanwangzhi)，原实例网址已经注销；

#### 通过 workers 等监控网站状态：[#](https://www.igdux.com/workers#user-content-%E9%80%9A%E8%BF%87-workers-%E7%AD%89%E7%9B%91%E6%8E%A7%E7%BD%91%E7%AB%99%E7%8A%B6%E6%80%81)

源码：[eidam/cf-workers-status-page](https://github.com/eidam/cf-workers-status-page)，实例：[https://status-page.eidam.dev/](https://status-page.eidam.dev/) ，（也可以通过 Uptimerobot 实现网站健康状态监控，源码：[yb/uptime-status](https://github.com/yb/uptime-status)），[教程](https://linux.do/t/topic/10601)。  
源码：[benvinegar/counterscale](https://github.com/benvinegar/counterscale)，实例：[https://counterscale.dev/](https://counterscale.dev/) ；  
源码：[lyc8503/UptimeFlare](https://github.com/lyc8503/UptimeFlare)，实例：[https://uptimeflare.pages.dev/](https://uptimeflare.pages.dev/) ，[博客](https://blog.lyc8503.site/)；  
源码：[yestool/analytics_with_cloudflare](https://github.com/yestool/analytics_with_cloudflare)，实例：[https://webviso.yestool.org/](https://webviso.yestool.org/) ；

#### 通过 workers 等搭建临时邮箱：[#](https://www.igdux.com/workers#user-content-%E9%80%9A%E8%BF%87-workers-%E7%AD%89%E6%90%AD%E5%BB%BA%E4%B8%B4%E6%97%B6%E9%82%AE%E7%AE%B1)

源码，已删除，实例：[https://email.ml/](https://email.ml/) ；  
源码：[akazwz/smail](https://github.com/akazwz/smail)，实例：[https://smail.pw/](https://smail.pw/) ；  
源码：[oiov/vmail](https://github.com/oiov/vmail)，实例：[https://vmail.dev/](https://vmail.dev/) ；  
源码：基于[oiov/vmail](https://github.com/oiov/vmail)，实例：[https://idu.one](https://idu.one/) （本站提供）；  
源码：[dreamhunter2333/cloudflare_temp_email](https://github.com/dreamhunter2333/cloudflare_temp_email)，实例：[https://mail.awsl.uk/](https://mail.awsl.uk/) ；

源码：[TBXark/mail2telegram](https://github.com/TBXark/mail2telegram)，将 Email 转发至 TG；

#### 通过 workers 等搭建 RSS 订阅生成器：[#](https://www.igdux.com/workers#user-content-%E9%80%9A%E8%BF%87-workers-%E7%AD%89%E6%90%AD%E5%BB%BA-rss-%E8%AE%A2%E9%98%85%E7%94%9F%E6%88%90%E5%99%A8)

源码：[https://github.com/yllhwa/RSSWorker](https://github.com/yllhwa/RSSWorker) 内含教程。

#### 通过 workers 搭建获取 IP 和地理位置信息[#](https://www.igdux.com/workers#user-content-%E9%80%9A%E8%BF%87-workers-%E6%90%AD%E5%BB%BA%E8%8E%B7%E5%8F%96-ip-%E5%92%8C%E5%9C%B0%E7%90%86%E4%BD%8D%E7%BD%AE%E4%BF%A1%E6%81%AF)

源码：[ccbikai/ip-api](https://github.com/ccbikai/ip-api)，实例：[https://html.zone/ip](https://html.zone/ip)

#### 通过 workers 等部署 Copilot 服务：[#](https://www.igdux.com/workers#user-content-%E9%80%9A%E8%BF%87-workers-%E7%AD%89%E9%83%A8%E7%BD%B2-copilot-%E6%9C%8D%E5%8A%A1)

Copilot（原 New Bing）可以试用 ChatGPT４，目前通过 Workers 就可以部署本地可用的 Copilot 服务。  
源码：[Harry-zklcdc/go-proxy-bingai](https://github.com/Harry-zklcdc/go-proxy-bingai)　内含教程；  
Demo，[试用](https://bingai-cfwk.zklcdc.xyz/web/#/)；  
[其他方式部署 Copilot 的试用网址](https://github.com/Harry-zklcdc/go-proxy-bingai/wiki/%E6%BC%94%E7%A4%BA%E7%AB%99)。

#### 通过 workers 等部署 Telegram Bot 服务：[#](https://www.igdux.com/workers#user-content-%E9%80%9A%E8%BF%87-workers-%E7%AD%89%E9%83%A8%E7%BD%B2-telegram-bot-%E6%9C%8D%E5%8A%A1)

源码：[Tsuk1ko/cfworker-telegraf](https://github.com/Tsuk1ko/cfworker-telegraf-template) ，[教程](https://moe.best/tutorial/cfworker-telegraf-tgbot.html)；

### 4.3 中转[#](https://www.igdux.com/workers#user-content-43-%E4%B8%AD%E8%BD%AC)

源码：[https://github.com/cmliu/CF-Workers-docker.io](https://github.com/cmliu/CF-Workers-docker.io) ，实例：[https://docker.fxxk.dedyn.io/](https://docker.fxxk.dedyn.io/) （Docker 镜像）  
源码：[WisdomSky/Cloudflared-web](https://github.com/WisdomSky/Cloudflared-web)（Docker 镜像）  
源码：[hunshcn/gh-proxy](https://github.com/hunshcn/gh-proxy) ，实例：[https://gh.api.99988866.xyz/](https://gh.api.99988866.xyz/) （Github 加速）  
源码：[EtherDream/jsproxy](https://github.com/EtherDream/jsproxy/tree/master/cf-worker)  
源码：[klightso/Workers-Proxy-1](https://github.com/klightso/Workers-Proxy-1)，[参考教程](https://www.locmjj.com/274.html)；

Workers 加速 Github，[参考教程](https://xiaowangye.org/posts/using-cloudflare-worker-proxy-github/)

### 4.４ 网盘文件列表[#](https://www.igdux.com/workers#user-content-4%EF%BC%94-%E7%BD%91%E7%9B%98%E6%96%87%E4%BB%B6%E5%88%97%E8%A1%A8)

#### 利用 Workers 搭建 Google Drive 列表服务[#](https://www.igdux.com/workers#user-content-%E5%88%A9%E7%94%A8-workers-%E6%90%AD%E5%BB%BA-google-drive-%E5%88%97%E8%A1%A8%E6%9C%8D%E5%8A%A1)

源码 1：[https://github.com/xunyixiangchao/goindex；](https://github.com/xunyixiangchao/goindex%EF%BC%9B)  
源码 2：[https://github.com/yanzai/goindex；](https://github.com/yanzai/goindex%EF%BC%9B)  
源码 3：[Aicirou/goindex-theme-acrou](https://github.com/Aicirou/goindex-theme-acrou)；  
源码 4：[https://github.com/maple3142/GDIndex](https://github.com/maple3142/GDIndex)

#### OneDrive-index: 利用 Workers 搭建 OneDrive 列表服务[#](https://www.igdux.com/workers#user-content-onedrive-index-%E5%88%A9%E7%94%A8-workers-%E6%90%AD%E5%BB%BA-onedrive-%E5%88%97%E8%A1%A8%E6%9C%8D%E5%8A%A1)

源码 1：[spencerwooo/onedrive-cf-index](https://github.com/spencerwooo/onedrive-cf-index)  
源码 2：[Eggsmemory/OneDrive Index Cloudflare Worker](https://github.com/Eggsmemory/OneDrive-Index-Cloudflare-Worker-Cht)

#### 说明[#](https://www.igdux.com/workers#user-content-%E8%AF%B4%E6%98%8E)

根据近期（20240703）出现[Cloudflare 用户出现账户使用问题](https://igdux.com/cloudflare)可知，通过 Workers 搭建网盘列表服务，可能会违反 Cloudflare 公司的条款，使用时建议慎重选择。

#### 更新说明[#](https://www.igdux.com/workers#user-content-%E6%9B%B4%E6%96%B0%E8%AF%B4%E6%98%8E)

本文最初写于 2023 年 6 月，收集当时所有能够收集到的 Workers 项目，增删查补，得以成文，[原文网址](https://www.igengdu.com/2023/06/cloudflare-workers.html)；  
2023 年 12 月 30 日，修改整理部分链接和失效代码；  
2024 年 3 月 9 日，新增部分内容、调整项目顺序：  
新增利用 Workers 搭建自定义订阅、搭建 RSS 订阅生成器、代理 Coplilot 部分内容。  
2024 年 6 月 17 日、6 月 21 日更新。

如果你觉得有新的优秀的 Workers 项目或失效的链接等，都可以联系我。

## 参考：[#](https://www.igdux.com/workers#user-content-%E5%8F%82%E8%80%83)

#### [Cloudflare 使用问题及其应对方法、建议](https://igdux.com/cloudflare)[#](https://www.igdux.com/workers#user-content-cloudflare-%E4%BD%BF%E7%94%A8%E9%97%AE%E9%A2%98%E5%8F%8A%E5%85%B6%E5%BA%94%E5%AF%B9%E6%96%B9%E6%B3%95%E5%BB%BA%E8%AE%AE)

#### [Source 1：Workers 优秀项目收集 lists](https://github.com/irazasyed/awesome-cloudflare)；[#](https://www.igdux.com/workers#user-content-source-1workers-%E4%BC%98%E7%A7%80%E9%A1%B9%E7%9B%AE%E6%94%B6%E9%9B%86-lists)

#### [Source 2: Vipkj.net](https://www.vipkj.net/post-3645.html)；[#](https://www.igdux.com/workers#user-content-source-2-vipkjnet)

#### [Source 3: Littlefox.me](https://blog.littlefox.me/archives/408)；[#](https://www.igdux.com/workers#user-content-source-3-littlefoxme)

#### [Source 4：Linux.do](https://linux.do/t/topic/24849)；[#](https://www.igdux.com/workers#user-content-source-4linuxdo)

#### [Source 5：iGengdu.com](https://www.igengdu.com/2023/06/cloudflare-workers.html)；[#](https://www.igdux.com/workers#user-content-source-5igengducom)

#### [Source 6：zhuima：awesome-cloudflare](https://github.com/zhuima/awesome-cloudflare)[#](https://www.igdux.com/workers#user-content-source-6zhuimaawesome-cloudflare)