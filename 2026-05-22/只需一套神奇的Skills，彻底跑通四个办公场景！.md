---
author: ASI启示录
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzI3MTA0MTk1MA==&mid=2652702121&idx=1&sn=e3d1794e6e0ac40a3640989386050a1d&chksm=f0eab05b2831dd602402c2a0f0e686b77fddbb65f22531590531242ac0039e0a84a6fd7a2eb8&mpshare=1&scene=1&srcid=0522MxG3OBjf5MZnrjtB01sD&sharer_shareinfo=904be0cc1a7894c8485792b082f0da6a&sharer_shareinfo_first=904be0cc1a7894c8485792b082f0da6a#rd
saved: 2026-05-22 07:54:49
tags:
  - 笔记同步助手
id: 3985435c-271f-4fe9-9b48-48b86b0d1d00
---

公众号名称：新智元

作者名称：ASI启示录

发布时间：2026-05-21 15:05

### 

![[笔记同步助手/images/85e6c8130c88c416a9b19974718736bb_MD5.jpg]]

### 

**新智元报道**

![[笔记同步助手/images/c99b71b9fa832d99ffa494ba4e5548fd_MD5.png]]

##### **【新智元导读】**光有强大的模型本身还不够，从脏数据到分析报告到汇报PPT，中间那条自动化链路谁来跑？GitHub上刚开源的SenseNova-Skills给出了一个答案，我们实测了四个真实场景，效果有点超出预期。

就在最近，第三方榜单Claw-Eval上出现了一个有意思的名字。

SenseNova 6.7 Flash-Lite，一个轻量级模型，冲进了前十。

紧跟DeepSeek V4 Pro和GPT-5.4，压过了Gemini 3.1 Pro和DeepSeek V4 Flash。

![[笔记同步助手/images/05a1bb18b8106eb484e42f0c6ee6d679_MD5.png]]

有趣的是，行业巨头们也在同一周有了新动作。

ChatGPT for Excel全球上线，GPT-5.5驱动，直接在Excel里嵌了一个侧边栏。

两天后，Claude把Excel、Word、PowerPoint三件套转正GA，Outlook同步开了公测。跨四个Office应用保持对话上下文不断，从邮件到表格到PPT一路跟着你走。

两大巨头都急着把大模型塞进办公套件，为什么？

![[笔记同步助手/images/eeecd5e8b013bf07fed169678bc266d7_MD5.gif]]

实际上，要真正解决你工作的问题，只靠模型是不够的。

如果你想做到跨环节、全链路的办公自动化——从一堆脏数据，到分析报告，到汇报PPT ——得有专门的Agent和Skills来实现。**让大模型从「会聊天」变成「会交作业」，靠的就是这一层。**

最近GitHub上出了一套开源的办公Skills跟的就是这波趋势，并且迅速斩获了4位数的Star。

抱着试试看的心态，我们亲自实测了一波，发现效果有点超出预期。

![[笔记同步助手/images/ce4af955c6f0a6136887372e3b5bd7b0_MD5.png]]

项目地址：https://github.com/OpenSenseNova/SenseNova-Skills

![[笔记同步助手/images/b1434a42c5780be91afab09c71ed6cf8_MD5.png]]

**一句话出一张图，零乱码**

第一次出国旅游，面对签证、机票、海关、转机一堆流程，大多数人的第一反应是上小红书翻攻略。

现在换个思路。

把需求扔给装了Skills的Agent，它自动生成一张完整的流程图解。

步骤清晰，层级分明，中文排版零乱码，风格直接对标小红书爆款。

![[笔记同步助手/images/dbb78cb63776bacfa73016873735b5e7_MD5.png]]

一句提示词，一遍成，不抽卡。

![[笔记同步助手/images/fca9a4e160e3b77966b7ad34b87b9da6_MD5.png||267]]

![[笔记同步助手/images/342ff934980cc67e66146e393cc8eb02_MD5.png||267]]

![[笔记同步助手/images/e8c689e6e6dcdd96c8d07678bda055f1_MD5.png||267]]

![[笔记同步助手/images/871dd885edd2026ab510506e054eda79_MD5.png||267]]

![[笔记同步助手/images/5904743d2b7f50479b6be9cb3759cf95_MD5.png||267]]

左右滑动查看

客户端点开大图后点击下一张(>)

![[笔记同步助手/images/b1434a42c5780be91afab09c71ed6cf8_MD5.png]]

**从数据到报告到PPT，三个真实办公场景**

开胃菜吃完，上硬菜。

**![[笔记同步助手/images/9dc00a4ca889295d0b0143e0b0d3b4bb_MD5.png]]**

**6家厂商13种品类混着来，抗噪才是真本事**

下一个测试任务：存储芯片价格分析。

做过采购和分析的朋友肯定懂这种烂账，7个月的报价记录，6家厂商，从DDR4到HBM3e到企业级SSD，13种细分品类全搅在一张表里，厂商名大小写不统一，空值东一个西一个，离群值占了13%。

![[笔记同步助手/images/15153d91a8212926bcf24373e57787af_MD5.png]]

不光是数据多，更恼人的是数据杂。

品类之间价格量级差了几十倍，你要是不分层处理，一算均价直接就是垃圾。

换作真人，洗数据加写报告，起码熬一天半。

对于这套内容，Agent的处理堪称老手。

它首先跑了一轮「数据审计」，把厂商命名不规范的、报价空值的，全部清理了一遍。

光厂商名就揪出4个问题，什么「 sk hynix」前面多个空格、「 samsung」大小写乱飞，这种脏数据你不清，后面按厂商聚合的时候同一家会被拆成两条线。

尤其值得一提的，是它对离群值的处理。

110条数据被标记为离群值，占了13%，比例不小。

但Agent没有一刀切全删。

它分析了一下发现，其中一部分对应的是真实业务场景，比如渠道清库存促销带来的低价，以及HBM现货紧缺时的溢价，然后果断选择保留数据并单独做了标记，后续分析里分层处理。

数据审计完，紧接着是多维拆解。

按「品类×应用场景×厂商」交叉分析，准确捕捉到2026年2月下旬的价格拐点。HBM3e和企业级SSD周涨幅明显抬升，消费类DDR4与eMMC只是温和跟涨。

最终结论很犀利：本轮上涨是AI服务器需求带动的结构性修复，不是普涨。

![[笔记同步助手/images/3cb721e6ea3500f07ed474cf2cc6d508_MD5.png]]

上下滑动查看

数据分析能跑通了，更长的链路呢？

**![[笔记同步助手/images/9dc00a4ca889295d0b0143e0b0d3b4bb_MD5.png]]**

**给Agent一个行业名，它交回一份调研报告**

低空经济行业调研。

只给了一个题目，没有提供任何参考资料。

![[笔记同步助手/images/a3f145ac1cb17834a19fb2e3559457eb_MD5.png]]

Agent先锚定了一个核心判断，2025到2026年是中国低空经济商业化的关键窗口期。

然后，它开始自主检索国内外主流厂商的最新进展，逐一比对机型、适航进展和订单数据。

这里有个细节。面对大量口径不一的公关稿和重复信息源，Agent精准提取出了UAM落地节奏、eVTOL核心零部件国产化率和关键环节成本占比。

随后，它又在此基础上自动生成了产业链结构图、成本占比饼图，并用TAM/SAM/SOM框架测算2025、2027、2030年市场规模。

最终给出的调研报告，有判断框架、有数据支撑、有可视化图表，远超「网上搜一圈拼在一起」的信息堆砌。

![[笔记同步助手/images/885a68a01d005300b4c47e9181a8e0a5_MD5.png]]

上下滑动查看

整个过程是sn-deep-research这个Skill在编排。

规划→分维度取证→综合→成稿，支持断点续跑。

**![[笔记同步助手/images/9dc00a4ca889295d0b0143e0b0d3b4bb_MD5.png]]**

**23页PPT，连配色都替你想好了**

城市新能源汽车充电基础设施布局与运营方案。

首先，内容结构上搭建了完整的七段式框架，行业背景、需求测算、选址模型、技术方案、运营模式、投资测算、政策建议。

**最终交付的是一份23页的完整 PPT。**

其次，每一部分都匹配了对应的视觉表达。选址模型页自动配置GIS热力示意图，运营模式页生成三种模式的对比矩阵，投资测算页给出利用率与回收期之间的敏感性分析图。

最后一页还给出了3条具体到行动主体和时间节点的落地建议。

生成即交付，打开就能编辑。

![[笔记同步助手/images/18fc838b9498334c50bcf133f4cc3c9c_MD5.png]]

上下滑动查看

重点来了。

这份PPT不仅在OpenClaw里跑通了，同样的Skill拖进ChatGPT也能用。

把SenseNova-Skills仓库克隆到本地，通过ChatGPT的Skills入口导入，搭配GPT的原生能力，同样能跑出高质量的PPT。

![[笔记同步助手/images/4a7894c6d55c6e1d4a81971cc518f840_MD5.png]]

![[笔记同步助手/images/9ab564fe2b364d09fe8dca1739a8697a_MD5.png]]

![[笔记同步助手/images/b1434a42c5780be91afab09c71ed6cf8_MD5.png]]

**四大类任务，不挑模型**

到这里该揭底牌了。

前面四个场景背后跑的，是同一套东西，SenseNova-Skills。

来自商汤的团队把办公场景里最高频的能力拆成了四大类任务入口，每个入口底下挂着一串具体的Skills各司其职，刚在GitHub开源，MIT协议，覆盖了办公场景里最高频的需求。

**1\. 数据分析**，sn-da-excel-workflow，多表读取、大文件超过1万行自动触发Parquet优化、清洗聚合导出，全流程编排。还有专门处理图片表格OCR的sn-da-image-caption。

![[笔记同步助手/images/2bc0921065ccc40200482f830117552d_MD5.png]]

**2\. 深度研究**，sn-deep-research，下面挂了6个子Skills分别负责规划、取证、综合、成稿、格式发现、HTML转换，中间产物持久化，断点可续。

![[笔记同步助手/images/148050016f72d06dad22eba4f3c7da09_MD5.png]]

**3\. PPT生成**，从sn-ppt-entry统一入口进入，支持标准模式和创意模式。标准模式的链路是大纲→逐页HTML→逐页VLM评审（不合格自动重写）→PPTX导出。

![[笔记同步助手/images/4d6f87e08df4d75e663ad111172eabfb_MD5.png]]

**4\. 搜索**，聚合了arXiv、Semantic Scholar、PubMed、GitHub、Stack Overflow、Hacker News、HuggingFace、Reddit、Twitter、YouTube、B站、知乎、抖音，学术+开发者+中英文社交全覆盖。

![[笔记同步助手/images/cacd0cf0bdbf04907ac90991a5d884bd_MD5.png]]

另外，SenseNova-Skills还能通过调用SenseNova U1模型，完成高密度复杂的信息图生成，包含自动提示词扩写+VLM质检+质量排序。

![[笔记同步助手/images/990f274e3f4dc2f5a62decea99fc627e_MD5.png]]

每个Skill都是独立目录，通过SKILL.md声明什么时候触发、什么时候不触发。

Agent会根据指令自动选择和编排，不需要手动指定调哪个。

这套Skills在Claude Code、Codex CLI、ChatGPT、OpenClaw、Hermes Agent等常见Agent工具里都能跑。

Skills提供流程知识和工具链编排，模型提供推理和决策。

![[笔记同步助手/images/b1434a42c5780be91afab09c71ed6cf8_MD5.png]]

**怎么用，怎么装**

**![[笔记同步助手/images/9dc00a4ca889295d0b0143e0b0d3b4bb_MD5.png]]**

**模型搭子：SenseNova 6.7 Flash-Lite**

虽说有了好用的Skills搭什么模型都可以，但最简单的还是日日新SenseNova 6.7 Flash-Lite——同量级第一，专门为Agent场景优化的轻量多模态模型。

Flash-Lite采用原生多模态架构，视觉信号和文本放在统一的感知链路中，看懂网页布局、文档结构、图表关系之后一步到位做决策，中间不经过文字转译。

![[笔记同步助手/images/bb5788011a7cff9ac80c60f5eeb03248_MD5.png]]

这个架构带来两个直接结果。

**1\.** **Token消耗在信息搜索等场景中直降60%。**任务越长省得越多，对于需要跑完整工作流的Agent来说，这是实打实的成本优势。

2\. Agent基准测试成绩也很能打。**PinchBench 92分同量级第一，Deep Planning 66分同量级第一，NovaPPTBench 92.4分第一**，还在τ²-bench、GPQA-diamond、AA-LCR、MathVision、OCRBenchV2等多个维度领先同级别国内外模型。

![[笔记同步助手/images/f8f88fb03e322776207daa215ad1f35b_MD5.png]]

项目地址：https://github.com/OpenSenseNova/SenseNova6.7

模型API接入时，还有一个限时福利可以薅。

商汤通过SenseNova平台发放的Token Plan，活动首月可享每5小时1500次免费调用配额，相当于零成本上手。

![[笔记同步助手/images/80020cd4a9e904d7d4cfb7bd02829788_MD5.png]]

https://www.sensenova.cn/

模型选好了，接下来是部署。

**![[笔记同步助手/images/9dc00a4ca889295d0b0143e0b0d3b4bb_MD5.png]]**

**两种方式，看你更喜欢哪种**

想用这套Skills，两条路。

**第一条，本地安装，自己配。**

Skills仓库MIT协议开源，你可以用Agent Pack一键装，它集成了Hermes Agent和OpenClaw框架加全套Skills，配合免费Token Plan，装完就能跑。

![[笔记同步助手/images/4c14ab52cca318292c6a5f3b1eb9888b_MD5.png]]

项目地址：https://github.com/OpenSenseNova/agent\_pack

也可以更灵活一点，直接克隆Skills仓库，把Skills目录拷进你自己的Agent框架就行。

甚至可以让Agent自己装，跟它说：

请帮我把https://github.com/OpenSenseNova/SenseNova-Skills安装到你的Skills目录。

它自己就能克隆、拷贝、加载。

API兼容OpenAI格式，主流开源Agent框架平滑接入。

**第二条，云端产品，开箱即用。**

商汤的办公小浣熊目前已经把商汤全系SenseNova-Skills和U1信息图生成打包好了，1500万个人用户、数千家企业客户在用。

![[笔记同步助手/images/1ef8f1f1c52a691817a78e2e805043f9_MD5.png]]

https://xiaohuanxiong.com/

本地的好处是自由度高，想怎么魔改怎么魔改，适合折腾型选手。

云端的好处是省心，不用碰代码不用配环境，适合想直接用的人。

![[笔记同步助手/images/b1434a42c5780be91afab09c71ed6cf8_MD5.png]]

**大模型竞争，回到交付**

真实的未来不是「Agent取代人」，而是周一早晨：

分析师打开电脑，上周840条新报价已经清洗完毕；产品经理刚定完选题，调研报告草稿已经在桌面；总监还在路上，下午的汇报PPT已经生成，配色都替你想好了。

让这件事发生的，不是更大的模型，而是模型背后那套已经被打磨过的Skills。

代码在GitHub，MIT协议，我们先装上了。

SenseNova-Skills GitHub仓库：

https://github.com/OpenSenseNova/SenseNova-Skills

**秒追ASI**

**⭐****点赞、转发、在看一键三连****⭐**

**点亮星标，锁定新智元极速推送！**

![[笔记同步助手/images/a40edb088471f17721b6b4c73f3b3096_MD5.jpg]]

![[笔记同步助手/images/c26ed28e61d6f8a52c6e76ce21c0c1ed_MD5.jpg]]

---

![[笔记同步助手/images/c826455542da0bf2d20d429c348858d3_MD5.jpg|cover_image]]

ASI启示录 新智元

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/953d62c3_1779407688118?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI3MTA0MTk1MA%3D%3D%26mid%3D2652702121%26idx%3D1%26sn%3De3d1794e6e0ac40a3640989386050a1d%26chksm%3Df0eab05b2831dd602402c2a0f0e686b77fddbb65f22531590531242ac0039e0a84a6fd7a2eb8%26mpshare%3D1%26scene%3D1%26srcid%3D0522MxG3OBjf5MZnrjtB01sD%26sharer_shareinfo%3D904be0cc1a7894c8485792b082f0da6a%26sharer_shareinfo_first%3D904be0cc1a7894c8485792b082f0da6a%23rd&s=obsidian)