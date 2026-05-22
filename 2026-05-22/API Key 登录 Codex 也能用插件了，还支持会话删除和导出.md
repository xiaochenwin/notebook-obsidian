---
author: 子昕
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzkwMjc1NTk3MQ==&mid=2247486815&idx=1&sn=25464ba35a5b7cd9163e9a90a35b03f7&chksm=c11ca49043b6594a7b8017c842a94133230f38dc01f43b201e3ed7ae10123823325b6f4ed80d&mpshare=1&scene=1&srcid=0522pG4jrA4vfjXxEL34tHnQ&sharer_shareinfo=24deabb135aadd4343a6c1c3410a1d0f&sharer_shareinfo_first=24deabb135aadd4343a6c1c3410a1d0f#rd
saved: 2026-05-22 13:58:31
tags:
  - 笔记同步助手
id: e0883781-afef-420f-bfdc-3dd231b8ebcc
---

公众号名称：子昕AI编程

作者名称：子昕

发布时间：2026-05-12 13:52

大家好，我是子昕。

上次 Codex Chrome Extension 出来之后，我就一直想体验。

但有个问题特别烦：

用 API Key 登录的话，插件入口是锁死的。

点进去就一行提示：需要登录 ChatGPT 账号。

![[笔记同步助手/images/b1e892c7afd13c7b79579a80ca843361_MD5.png]]

我用的是第三方中转站的 API Key，没有 ChatGPT 账号登录，也就意味着插件功能跟我完全没关系。

当时第一反应：能不能直接改 Codex 的安装文件，强行绕过去？

让 AI 帮我分析了一通。

结果越分析越复杂。

什么资源校验、签名、拦截……

最后 AI 给我列了一堆实现不了的原因。

我对这块也不熟，就没继续了。

后来看到一个开源项目 `Codex++`。

> GitHub：https://github.com/BigPizzaV3/CodexPlusPlus

借助 AI 把原理搞明白之后，我才发现：

我一开始的方向就完全错了。

因为这东西。

**根本不用改文件。**

​

## Codex++ 是什么

它是一个外部增强启动器，不碰 Codex 的任何原始文件。

通过外部 launcher 启动 Codex 的同时，把增强功能直接注入进去。

我体验了一下，最大的感受是：

Codex 原本那种「官方客户端」的封闭感，一下子没了。

API Key 用户终于能正常用插件了。

装上之后，左侧出现「插件 - 已解锁」：

![[笔记同步助手/images/1c1133239c57f5743b6800f837ee5800_MD5.png]]

Codex 顶部也注入了一个“Codex++”配置面板按钮。点开可以看到支持的功能：

![[笔记同步助手/images/fbb93f360a467de12cde6c3c0e216e72_MD5.png]]

-   **插件选项解锁**：API Key 模式下正常使用插件
    
-   **特殊插件强制安装**：解除前端「App unavailable」限制
    
-   **会话删除**：悬停显示删除按钮，支持撤销（Codex 原生没有）
    
-   **Markdown 导出**：导出带时间戳的对话记录
    
-   **会话项目移动**：把对话移到其他项目
    

![[笔记同步助手/images/49607d001591fcd2cbc5f46659a831c1_MD5.png]]

## 安装步骤

**前提：Python 3.11+，已安装 Codex App。**

先克隆仓库并安装依赖：

```
git clone https://github.com/BigPizzaV3/CodexPlusPlus.git
cd CodexPlusPlus
python -m pip install -e .
```

## macOS

```
python -m codex_session_delete setup
```

执行后自动生成 `/Applications/Codex++.app`，以后从这个 app 启动（启动台），不要再开原版 Codex。

卸载：

```
python -m codex_session_delete remove
```

## Windows

双击项目目录里的 `setup.bat`，按菜单选 Install，桌面生成 `Codex++.lnk` 快捷方式。

![[笔记同步助手/images/fc5fec130e35d5bdad8cd9b23bd49b7e_MD5.png]]

或命令行：

```
python -m codex_session_delete setup
```

注意：必须从 `Codex++` 快捷方式启动。直接开原版 Codex，注入不会生效。

​

## 它是怎么做到的（对原理不感兴趣可以跳过）

Codex 的桌面 App，底层其实是用网页技术做的——界面本质上就是一个跑在壳子里的网页。

这个壳子叫 Electron，很多你用过的桌面软件都是这么做的，比如 VS Code、Slack、Notion。

因为内核是浏览器，Chrome 官方有一套专门给开发者调试网页用的协议，叫 **CDP**。

它原本的用途是：让你用外部工具连进浏览器，检查代码、修改页面、注入脚本。

搞明白这个之后，我让 AI 帮我写了个最简单的验证脚本：往 Codex 页面中央，强行插一个紫色弹框。

如果真能弹出来，说明外部程序确实可以直接控制 Codex 的前端页面。

## 第一步：用调试模式启动 Codex

```
/Applications/Codex.app/Contents/MacOS/Codex \
    --remote-debugging-port=9229 \
    --remote-allow-origins=http://127.0.0.1:9229 \
    > /tmp/codex-debug.log 2>&1 &
```

这样 Codex 启动后，本地 9229 端口就可以接受外部连接了。

## 第二步：用 Python 连进去，塞一段 JS

```
import json
import urllib.request
import websocket

print("📡 正在连接 CDP...")
targets = json.loads(urllib.request.urlopen('http://127.0.0.1:9229/json').read())
page = [t for t in targets if t['type'] == 'page'][0]
print(f"✅ 找到页面: {page['title']}")

ws = websocket.create_connection(page['webSocketDebuggerUrl'], timeout=10)
print("✅ WebSocket 已连接")

print("💉 正在注入代码...")
script = """
(function() {
    const box = document.createElement('div');
    box.innerHTML = '🎉 成功!这是你注入的代码!';
    box.style.cssText = `
        position: fixed; top: 50%; left: 50%;
        transform: translate(-50%, -50%);
        background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        color: white; padding: 30px; border-radius: 15px;
        font-size: 20px; font-weight: bold;
        box-shadow: 0 20px 60px rgba(0,0,0,0.4); z-index: 999;
    `;
    document.body.appendChild(box);
    setTimeout(() => box.remove(), 5000);
    return '✅ 注入成功!';
})();
"""
payload = {
    "id": 1,
    "method": "Runtime.evaluate",
    "params": {
        "expression": script,
        "returnByValue": True,
        "allowUnsafeEvalBlockedByCSP": True
    }
}
ws.send(json.dumps(payload))
response = json.loads(ws.recv())
print(f"✅ {response['result']['result']['value']}")
print("\n💡 现在看你的 Codex 窗口，应该有一个紫色的通知框!")
ws.close()
```

脚本跑起来，终端里逐行打印连接状态：

![[笔记同步助手/images/3402cd760d04874d887373833d2c435e_MD5.png]]

结果下一秒，Codex 窗口中央，真的弹出了那个紫色框。

![[笔记同步助手/images/79a86244403a7930e077644394104f7c_MD5.png]]

那一刻我就明白 Codex++ 在干嘛了。

它本质上不是「修改 Codex」。 而是在运行中的 Codex 页面里，动态塞进去一层新能力。

相当于你在浏览器里按 F12 打开控制台、手动粘贴一段 JS。

Codex++ 把这件事自动化了，每次帮你启动 Codex 的时候都做一遍。

这件事真正有意思的地方，其实不是插件解锁。

而是：

Codex 发布没多久，社区已经开始给它做运行时增强层了。

不改文件，不破解，用官方协议。

这很像当年的浏览器插件生态。 只是这一次，被「增强」的对象，变成了 AI 客户端。

AI IDE 的下一阶段，可能不只是模型竞争。 而是谁先形成真正的增强生态。

---

点个关注呗，我会继续用我这半吊子水平为大家带来更多AI编程工具的第一手体验～

「点赞、转发、在看」  
和大家一起看

  

---

![[笔记同步助手/images/80e3305bab32ffca0b44ab208f7ff536_MD5.jpg|cover_image]]

Original 子昕 子昕AI编程

修改于

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/488c3fd2_1779429510328?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzkwMjc1NTk3MQ%3D%3D%26mid%3D2247486815%26idx%3D1%26sn%3D25464ba35a5b7cd9163e9a90a35b03f7%26chksm%3Dc11ca49043b6594a7b8017c842a94133230f38dc01f43b201e3ed7ae10123823325b6f4ed80d%26mpshare%3D1%26scene%3D1%26srcid%3D0522pG4jrA4vfjXxEL34tHnQ%26sharer_shareinfo%3D24deabb135aadd4343a6c1c3410a1d0f%26sharer_shareinfo_first%3D24deabb135aadd4343a6c1c3410a1d0f%23rd&s=obsidian)