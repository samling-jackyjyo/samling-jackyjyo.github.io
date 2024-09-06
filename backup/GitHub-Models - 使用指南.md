
## 一、GitHub Models

[GitHub Models 8](https://github.com/marketplace/models) 是 GitHub 最新推出的模型托管服务，提供免费的 AI 模型供开发者测试。可以使用的模型有 GPT-4o、Phi 3、Llama 3.1 等，可以说很全面的了。现在可以申请加入 [waitlist 10](https://github.com/marketplace/models/waitlist)，通过后就可以使用这些模型了。

## [](https://linux.do/t/topic/197275#p-1713259-h-2)二、模型调用

GitHub Models 提供了 Playground 进行调试，当然也可以直接使用 API。例如使用 cURL 请求:
```js
curl -X POST "https://models.inference.ai.azure.com/chat/completions" \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer $GITHUB_TOKEN" \
    -d '{
        "messages": [
            {
                "role": "system",
                "content": "You are a helpful assistant."
            },
            {
                "role": "user",
                "content": "What is the capital of France?"
            }
        ],
        "model": "gpt-4o"
    }'
```
调用方式和 OpenAI 基本一致，[只是请求地址从 api.openai.com/v1 变成了 models.inference.ai.azure.com，使用 1](http://xn--api-8p9dp7uxnfhdy30l4olej1f.openai.com/v1%E5%8F%98%E6%88%90%E4%BA%86models.inference.ai.azure.com%EF%BC%8C%E4%BD%BF%E7%94%A8)[GITHUB_TOKEN 5](https://github.com/settings/tokens) 作为 apikey。

## [](https://linux.do/t/topic/197275#p-1713259-one-api-3)三、接入 one-api

我喜欢用 one-api 来进行 api 管理。但是 GitHub Models 的请求地址因为少了 `/v1` 没办法直接接入 one-api。这里选择用 cloudflare workers 做一个接口转发，去除请求地址中的 `/v1`：
```js
addEventListener('fetch', event => {
  event.respondWith(handleRequest(event.request))
})

async function handleRequest(request) {
  const url = new URL(request.url)

  if (url.pathname.startsWith('/v1')) {
    const newUrl = new URL(request.url)
    newUrl.hostname = 'models.inference.ai.azure.com'
    newUrl.pathname = newUrl.pathname.replace('/v1', '') 

    const newRequest = new Request(newUrl, {
      method: request.method,
      headers: request.headers,
      body: request.body
    })

    return fetch(newRequest)
  }

  return fetch(request)
}
```
使用 worker 的 URL 作为 API 地址，GITHUB_TOKEN 作为 apikey 就可以将 GitHub Models 接入 one-api 了。

## [](https://linux.do/t/topic/197275#p-1713259-h-4)四、使用体验

因为已经集成到 one-api 了，所以可以很方便的在各种 AI 应用中调试，例如在 open-webui 里使用：

 [![](https://img.yohaman.pp.ua/file/35f47e402cbae016f09dd.png)


响应速度还是挺快的，不过和官方模型用起来有些差异，应该是版本有些不同。最后是模型使用限制，GPT-4o 免费用户上下文限制到了 8k，每分钟请求最大为 10，每天最多请求 50 次。用来测试应用的话应该是够用的。

原文：[GitHub Models 使用指南 - iOnosyne's Blog 5](https://blog.ionosyne.com/2024/08/10/GitHub-Models-%E4%BD%BF%E7%94%A8%E6%8C%87%E5%8D%97/)