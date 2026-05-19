---
author: 可乐
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzkxNDIzNDI4OQ==&mid=2247484374&idx=1&sn=4c098f99de8fc4382deb1862be9703ef&chksm=c0a24199cc593c91e3b1fe5d945c0761d048ca580767f9dde3de269f0de67fc654862430a42f&mpshare=1&scene=1&srcid=0519vjEljyXpHPjyhguXYZih&sharer_shareinfo=674742acb22d3354cdef9f007e7c63e7&sharer_shareinfo_first=674742acb22d3354cdef9f007e7c63e7#rd
saved: 2026-05-19 08:21:54
tags:
  - 笔记同步助手
id: 09dd99f7-ed5c-42ab-baa2-b0840cce1fbe
---

公众号名称：太空中的蔬菜

作者名称：可乐

发布时间：2026-04-01 18:01

感谢月大分享

一、准备工作 安装Obsidian

首先你需要先安装好Obsidian笔记软件，这是一款很基础的本地笔记工具，所有笔记都会保存在你的电脑里。

安装非常简单，直接在这里 https://obsidian.md/zh/ 下载就可以。

![[笔记同步助手/images/664d3f367dd1fb5a49725d86e88b5875_MD5.png]]

---

## 二、第一步：安装 Obsidian AI 插件

安装好Obsidian后，我们需要给它安装一个名为**Copilot**的插件，就用它来调用AI模型：

1.  打开Obsidian，点击左下角的**设置图标**（齿轮形状）
    
2.  在左侧菜单找到**社区插件**，确保「安全模式」是关闭的
    
3.  点击**浏览**，在搜索框里输入`Copilot`
    
4.  对应找到的插件（作者是 Logan Yang），点击**安装**
    
5.  安装完成后，把这个插件启用
    

![[笔记同步助手/images/dafed8f07b655bf67590367c66628650_MD5.png]]

![[笔记同步助手/images/4d2575952097f8e6121e99e3d30c9059_MD5.png]]

---

## 三、第二步：注册OpenRouter账号

OpenRouter是一个AI模型聚合平台，它提供了很多免费的AI模型供我们使用：

1.  开放官网：https://openrouter.ai/
    
2.  点击右上角的**登录**，推荐用**GitHub账号直接登录**（非常方便，很多AI平台都支持GitHub登录）
    

![[笔记同步助手/images/d76710f32e51568a8cb052ee73f6ae13_MD5.png]]

---

## 四、第三步：创建API密钥（非常重要！）

这个步骤让 Obsidian 连接到 OpenRouter 的 AI 模型的关键：

1.  登录OpenRouter后，点击右上角**你的头像**
    
2.  在下拉菜单里选择第一个“活动”
    
3.  点击**Create API Key**（创建密钥）
    
4.  给这个钥匙起一个你能看懂的名字，比如`“Obsidian-AI”或者“牛马”，`只要你能认出来他就行啦，没必要太纠结。
    
5.  点击创建，系统会生成一串很长的钥匙字符串
    
6.  **立刻把这串钥匙复制下来，找个安全的地方保存好！**
    

-   这个只显示一次，关闭页面之后就再也看不到了！如果弄丢了，只能重新生成新的。  
    

![[笔记同步助手/images/457d45c0bcef022d93ca092df846da73_MD5.png]]

![[笔记同步助手/images/70882965f19abc800d4c705443b60d1c_MD5.png]]

---

## 五、第四步：挑选免费的AI模型

OpenRouter 里有很多免费的模型，我们可以挑一个好用的免费模型来用：

1.  回到OpenRouter的首页，点击顶部的**Models**（模型列表）
    
2.  在页面里，你可以把排序改成**Pricing:** Low to High（价格从低到高），这样免费的模型就会排在最前面
    
3.  找标注了`Free`的模型，推荐几个好用的免费模型：
    
    ![[笔记同步助手/images/024ae659f542faa06264380530ba660f_MD5.png]]
    

找到你想要的模型后，点击它旁边的**复制模型id**，把这个模型的ID复制下来，后面用到。  

或者直接在搜索框里搜索“free”，这样就能找到一大堆免费模型，更直接更方便。

![[笔记同步助手/images/2d8661aa3cb4a8f04f28b3844232792d_MD5.png]]

  

> 注意：这些免费模型是厂商用来做测试的，你的输入内容厂商是可以看到的，所以不要把非常隐私的内容发给这些免费模型哦。

---

## 六、第五步：在Obsidian里配置AI连接

现在我们把前面得到的信息，配置到 Copilot 插件里：

1.  回到 Obsidian 的设置，在右侧找到刚才安装的**Copilot**插件设置
    
2.  找到**模型**这个标签页，点击右上角的**添加模型**
    
    ![[笔记同步助手/images/617507b6106ead3adc7bca96fbf197c2_MD5.png]]
    
3.  在弹出的窗口里，按照下面的图片填写
    
    ![[笔记同步助手/images/4b885e3e5a649b7b66a90330c3e33a39_MD5.png]]
    

4.  填写完成后，点击**保存**保存
    
5.  然后点击设置，把**默认聊天模型**改成你刚添加的这个模型。
    
    ![[笔记同步助手/images/84cd19c5ec6c9ebfaf0029a4c880ff65_MD5.png]]
    

---

## 七、开始使用AI功能

配置完成后，你就可以在Obsidian里使用AI了：

1.  点击Obsidian左边栏的Copilot图标（一个对话框的图标），就会打开AI对话窗口
    
    ![[笔记同步助手/images/b8c4e2cbb2bf98f9fb6303a010108875_MD5.png]]
    
2.  你可以直接在这里和AI对话，问问题、写东西
    
3.  也可以在你的笔记里，看到选中的文本，右键点击，就可以 Copilot 的选项
    
    ![[笔记同步助手/images/8855502be05a110e80e0eb5956871ee5_MD5.png]]

---

## 八、常见问题解决

如果配置完用不了，可以按照下面的方法排查：

**API调用失败**：

-   检查你的API键有没有复制错，有没有多复制空格或者换行
    
-   检查模型ID有没有完全复制对，不能写错
    
-   检查您的网络能否正常访问 OpenRouter
    

**AI 的回答是英文的**：

-   在你的提问里加上`请用中文回答`就可以了

**响应很慢**：

-   可以更换一个免费模型尝试，不同的模型速度不一样

**提示余额不足**：

-   确认你选择的是免费的免费模型，不要选择付费的了

---

## 九、注意事项

1.  **API 密钥安全**：这个密钥就像你的账号密码，不要随便发给别人，也不要传到公开的地方，否则别人会盗用你的额度
    
2.  **隐私问题**：免费模型的服务商会看到你输入的内容，不要把身份证、密码之类非常隐私的内容发给AI
    
3.  **免费限额限制**：免费模型有调用次数和流量的限制，如果用不了，可以换一个免费模型继续用
    
4.  如果你只是用来做笔记总结、日常写作，这些免费模型完全够用了，不需要花钱买付费模型。
    

配置好之后，你就拥有了一个带AI能力的本地笔记工具，不用再单独打开AI网站，直接在写笔记的时候就可以让AI干活啦！

搞定！撒花🎉

  

---

![[笔记同步助手/images/cb1f1436f64bf70e94fe29ff21210fcb_MD5.jpg|cover_image]]

Original 可乐 太空中的蔬菜

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/ff949da8_1779150113922?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzkxNDIzNDI4OQ%3D%3D%26mid%3D2247484374%26idx%3D1%26sn%3D4c098f99de8fc4382deb1862be9703ef%26chksm%3Dc0a24199cc593c91e3b1fe5d945c0761d048ca580767f9dde3de269f0de67fc654862430a42f%26mpshare%3D1%26scene%3D1%26srcid%3D0519vjEljyXpHPjyhguXYZih%26sharer_shareinfo%3D674742acb22d3354cdef9f007e7c63e7%26sharer_shareinfo_first%3D674742acb22d3354cdef9f007e7c63e7%23rd&s=obsidian)