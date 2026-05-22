---
author: ahworld
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzU1MDMyNzUyNQ==&mid=2247484788&idx=1&sn=1589f559d88f1bb7f86ecbda88349194&chksm=fabc28df8e58db639c67d61c82235fe80da8ef0f28177ece175bdb53bdb173d84cf4f24f8694&mpshare=1&scene=1&srcid=0522suKM6Gnvk4JmfGG4j0WG&sharer_shareinfo=d833d69d531b53648f020de21a224281&sharer_shareinfo_first=d833d69d531b53648f020de21a224281#rd
saved: 2026-05-22 08:50:40
tags:
  - 笔记同步助手
id: ea36c924-c1ae-4f07-b70c-0b7caae5be7c
---

公众号名称：seqyuan

作者名称：ahworld

发布时间：2026-05-20 15:11

# 我现在的生信工作已经离不开Codex智能体，DeepSeek V4现在很能打，而且便宜，但是两者的适配有很多不方便的地方，我做了一个python包ds4codex，能让大家方便的在codex里用上deepseek最新的模型，而且能像gpt系列一样切换low xhigh这种thik模式。

## 它解决了什么问题

Codex 自定义模型 provider 使用的是：

wire\_api = "responses"

而 DeepSeek 提供的是 Chat Completions 兼容接口：

https://api.deepseek.com/v1/chat/completions

这两个协议并不能直接对接。ds4codex 就是中间的协议适配层。

它会处理：

-   Codex 请求到 DeepSeek 请求的转换
    
-   普通回复和流式回复的转换
    
-   tool calls 的结构转换
    
-   Codex reasoning level 到 DeepSeek thinking mode 的映射
    
-   Codex /model 菜单里的模型展示
    

最终效果是：你仍然在 Codex 里正常工作，但模型可以切换到 DeepSeek。

## 安装

直接从 PyPI 安装：

`pip install ds4codex -i https://pypi.org/simple`

初始化配置，并写入 DeepSeek API Key：

`ds4codex init --apikey sk-your-deepseek-api-key`

启动本地代理：

`ds4codex run`

保持 ds4codex run 运行，然后进入 Codex，就可以通过 /model 选择 DeepSeek 模型。

## 配置很简单

ds4codex 只需要一个用户主要关心的配置文件：

`～/.codex/config.toml`

初始化后会写入类似配置：

```
model = "deepseek-v4-flash"
  model_provider = "ds4codex"
  model_context_window = 1048576
  model_catalog_json = "/home/you/.codex/ds4codex-model-catalog.json"

  [ds4codex]
  port = 8099
  target_url = "https://api.deepseek.com/v1/chat/completions"
  thinking = "disabled"

  [model_providers.ds4codex]
  name = "DeepSeek via ds4codex"
  base_url = "http://127.0.0.1:8099/v1"
  wire_api = "responses"
  experimental_bearer_token = "sk-your-deepseek-api-key"
```

其中 \[ds4codex\] 只保留三个核心参数：

-   port
    
-   target\_url
    
-   thinking
    

不再额外维护 ～/.config/ds4codex/config.toml，配置入口更清晰。

## 支持 Codex /model 选择

ds4codex init 会生成一个 model catalog 文件：

`～/.codex/ds4codex-model-catalog.json`

这个文件用于让 Codex 的 /model 菜单识别 DeepSeek 模型。目前会显示：

-   DeepSeek V4 Flash
    
-   DeepSeek V4 Pro
    

也就是说，用户不需要手动写复杂的 \[models.xxx\] 配置，就可以在 Codex 里直接切换模型。

## Thinking Mode 也做了适配

Codex 里常见的 reasoning level 包括：

-   low
    
-   medium
    
-   high
    
-   xhigh
    

DeepSeek 当前主要使用：

-   high
    
-   max
    

ds4codex 会自动做兼容映射：

low / medium / minimal -> high high -> high xhigh -> max

如果 Codex 没有显式传 reasoning level，则使用 \[ds4codex\] 里的默认 thinking 配置。

  

---

![[笔记同步助手/images/a01c6ab601cf6d6767b4c48b399be44e_MD5.jpg|cover_image]]

Original ahworld seqyuan

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/c0db5e1a_1779411039733?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzU1MDMyNzUyNQ%3D%3D%26mid%3D2247484788%26idx%3D1%26sn%3D1589f559d88f1bb7f86ecbda88349194%26chksm%3Dfabc28df8e58db639c67d61c82235fe80da8ef0f28177ece175bdb53bdb173d84cf4f24f8694%26mpshare%3D1%26scene%3D1%26srcid%3D0522suKM6Gnvk4JmfGG4j0WG%26sharer_shareinfo%3Dd833d69d531b53648f020de21a224281%26sharer_shareinfo_first%3Dd833d69d531b53648f020de21a224281%23rd&s=obsidian)