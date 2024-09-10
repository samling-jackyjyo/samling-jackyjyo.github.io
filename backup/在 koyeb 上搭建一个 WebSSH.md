自从 WARP 被强了以后，我们没有 IPV6 无法访问纯 IPV6 小鸡，还有就是 serv00 被墙了后也无法通过 SSH 连接，所以我们部署一个 WebSSH 解决这些问题 ![:wink:](https://linux.do/images/emoji/apple/wink.png?v=12 ":wink:")  
如图：
![image.png](https://easyimage.01011205.xyz/i/0/2024/09/10/nujrzu-0.png)

![](https://easyimage.01011205.xyz/i/0/2024/09/10/nutfjl-0.png)


项目地址：

[github.com](https://github.com/crazypeace/huashengdun-webssh)
![image.png](https://easyimage.01011205.xyz/i/0/2024/09/10/nvdwh0-0.png)


### [GitHub - crazypeace/huashengdun-webssh: 增加生成 sshlink 功能，方便收藏，下次使用不需要输入密码。 56](https://github.com/crazypeace/huashengdun-webssh)

增加生成 sshlink 功能，方便收藏，下次使用不需要输入密码。

部署文档说明：

![](https://linux.do/uploads/default/original/3X/b/a/bad411acb30e6927e9d5598084119eece8f8c2dc.png)[zelikk.blogspot.com](https://zelikk.blogspot.com/2023/10/huashengdun-webssh-codesandbox.html)

![image.png](https://easyimage.01011205.xyz/i/0/2024/09/10/nvukqf-0.png)


### [免费平台 CodeSandbox 上搭建 webssh 项目 huashengdun/webssh HAX/WOIDEN 同款 | Koyeb | Render |... 33](https://zelikk.blogspot.com/2023/10/huashengdun-webssh-codesandbox.html)

免费平台 CodeSandbox 上搭建 webssh 项目 huashengdun/webssh HAX/WOIDEN 同款 附 Koyeb | Render | Northflank | Replit 这些平台的设置


1.fork [该仓库 56](https://github.com/crazypeace/huashengdun-webssh) 到本地仓库

2. 进入 webssh/settings.py 修改代码

在 default 后面加上 `utf-8` 以防止代码输出中文乱码  

![image.png](https://easyimage.01011205.xyz/i/0/2024/09/10/nvyfna-0.png)


3. 在 koyeb 创建一个账号 **（IP 需要在美国）**

[https://app.koyeb.com 18](https://app.koyeb.com/)

4. 拉取仓库  

![image.png](https://easyimage.01011205.xyz/i/0/2024/09/10/nw2fl4-0.png)

![](https://easyimage.01011205.xyz/i/0/2024/09/10/nwd0m5-0.png)

![image.png](https://easyimage.01011205.xyz/i/0/2024/09/10/nxkidx-0.png)


将 python 代码放入其中

```python
python run.py --xsrf=False --xheaders=False --origin='*' --debug --delay=6
```

![image.png](https://easyimage.01011205.xyz/i/0/2024/09/10/nxos98-0.png)

设置端口为 `8888` ，协议为 `http`

![image.png](https://easyimage.01011205.xyz/i/0/2024/09/10/nxs4p6-0.png)


自定义改名后点击 Deploy

![image.png](https://easyimage.01011205.xyz/i/0/2024/09/10/nxu5pj-0.png)


5. 通过 cloudflare 进行反代

创建一个一个 worker，代码放入其中，只需要修改 `app.koyeb.com` 为你自己在 koyeb 的网址即可

```
addEventListener('fetch', (event) => {
  event.respondWith(handleRequest(event.request));
});

async function handleRequest(request) {
  let url = new URL(request.url);

  // 将 "app.koyeb.com" 替换为您的 Koyeb 应用域名
  const targetHostname = 'app.koyeb.com'; 

  // 获取 Worker 脚本的原始主机名，例如 "your-worker.your-account.workers.dev"
  const workerHostname = request.headers.get('host');

  // 检查请求主机名是否与 Worker 主机名匹配
  if (url.hostname === workerHostname) {
    // 将主机名替换为 Koyeb 应用域名
    url.hostname = targetHostname;

    // 可选：如果您的 Koyeb 应用部署在特定路径下，例如 "/app"，则取消注释以下行
    // url.pathname = '/app' + url.pathname;

    // 使用修改后的 URL 创建新的请求对象
    let newRequest = new Request(url, request);

    // 将请求转发到 Koyeb 应用
    return fetch(newRequest);
  } else {
    // 如果请求未使用 Worker 域名，则直接返回 404 错误
    return new Response('Not Found', { status: 404 });
  }
}
```


转载自： [在koyeb上搭建一个WebSSH - 资源荟萃 - LINUX DO](https://linux.do/t/topic/130852)和         [在Hugging Face上部署WebSSH - 资源荟萃 - LINUX DO](https://linux.do/t/topic/135264)
