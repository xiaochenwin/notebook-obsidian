---
author: 门里门外说Ai
source: 微信公众号
url: https://mp.weixin.qq.com/s?__biz=MzI3MDEzNTMxNg==&mid=2247483751&idx=1&sn=d43cad4cccff2c6c9f66de6a700c2f1a&chksm=eb55b980de0a9526feccecb227d655133dde3b49a9d610ac30ecb1a3d10167e4a3a25413a68c&mpshare=1&scene=1&srcid=0528UCp09TZHro0q0udUtKU2&sharer_shareinfo=976424fb52804464da8f322c433cf58b&sharer_shareinfo_first=976424fb52804464da8f322c433cf58b#rd
saved: 2026-05-28 18:20:26
tags:
  - 笔记同步助手
id: b64e248d-108a-49cc-8e24-3e2d317a9d83
---

公众号名称：门里门外说Ai

作者名称：

发布时间：2026-05-28 08:52

> 导语

> 这篇文章适合零技术基础的职场人。下面按 **6 个真实场景**，讲清楚普通打工人怎么用 Codex 把重复工作交出去。每个场景都附带可直接复制使用的 Prompt。

什么样的工作适合交给 Codex？

<table style="border-collapse: collapse"><tbody><tr><td style="font-size: 14px; color: rgb(17, 24, 39); border: 1px solid #ddd; padding: 6px 10px"><span style="color: rgb(37, 99, 235); font-weight: bold"><span>✓</span></span><span class="color-break">​</span><div style="color: rgb(0, 0, 0)"><span>有固定格式</span></div></td><td style="font-size: 14px; color: rgb(17, 24, 39); border: 1px solid #ddd; padding: 6px 10px"><span style="color: rgb(37, 99, 235); font-weight: bold"><span>✓</span></span><span class="color-break">​</span><div style="color: rgb(0, 0, 0)"><span>有重复步骤</span></div></td></tr><tr><td style="font-size: 14px; color: rgb(17, 24, 39); border: 1px solid #ddd; padding: 6px 10px"><span style="color: rgb(37, 99, 235); font-weight: bold"><span>✓</span></span><span class="color-break">​</span><div style="color: rgb(0, 0, 0)"><span>有清晰规则</span></div></td><td style="font-size: 14px; color: rgb(17, 24, 39); border: 1px solid #ddd; padding: 6px 10px"><span style="color: rgb(37, 99, 235); font-weight: bold"><span>✓</span></span><span class="color-break">​</span><div style="color: rgb(0, 0, 0)"><span>有大量零散信息</span></div></td></tr></tbody></table>

01自动生成周报、月报和汇报文档

很多人每周五都在做同一件事：翻聊天记录、看任务清单、回忆这周做了什么、复制上周周报格式、重新组织语言、检查语气是否得体。

这类工作最适合 Codex，因为它本质上是**「把已有素材整理成固定格式」**。

最简单的用法

把本周完成事项、会议记录、项目进度、遇到的问题直接丢给 Codex，让它生成周报初稿。

> Prompt 示例

请根据下面的素材，帮我整理一份本周周报。

要求：

## 1\. 结构：本周完成事项、进行中事项、遇到的问题、下周计划

## 2\. 语气正式、简洁，适合发给直属领导

## 3\. 不要夸大成果，不要写空话

## 4\. 信息不足请标注「待补充」

以下是本周素材：\[粘贴聊天记录、任务清单、会议纪要\]

更省事的用法

如果素材已经是文件（会议纪要 PDF、任务 Excel、项目文档），可以直接上传给 Codex，让它读取后生成报告。

最高阶的用法

如果工作记录长期存在 Google Calendar、Gmail、Slack、Notion 或 Google Drive 里，可以用 Automation 定时生成工作简报或周报。比如每周五下午自动读取本周日历、邮件、项目进度，生成周报草稿，你只需要审一遍再发送。

02处理 Excel 和表格数据

很多打工人不是不会分析数据，而是卡在 Excel 函数、透视表、格式处理上。领导说「分析一下各渠道转化率趋势」，你知道要算，但不记得公式，半小时过去了，表还没动。

Codex 的价值是：**你用自然语言描述表格结构和目标，它帮你写公式、做分析，甚至直接处理文件。**

公式生成

> Prompt 示例

我有一个 Excel 表：

A 列是渠道名称

B 列是日期

C 列是访问人数

D 列是转化人数

请帮我写一个公式，计算每个渠道的转化率。

要求：

## 1\. 说明公式放在哪一列

## 2\. 解释公式含义

## 3\. 如果需要数据透视表，请告诉我操作步骤

数据分析

> Prompt 示例

请根据我上传的表格，分析本季度各渠道转化率趋势。

输出要求：

## 1\. 找出转化率最高和最低的渠道

## 2\. 找出变化最明显的渠道

## 3\. 用 3-5 条结论总结

## 4\. 给出可执行的优化建议

直接处理文件

也可以直接上传 Excel 文件，让 Codex 清洗数据、生成新表、增加公式、输出汇总结果。适合一次性处理表格、财务预测、销售数据汇总、运营报表。

> 注意
> 重要表格一定先备份，复杂处理先用小样本测试。

03批量处理文件

这类任务特别消耗时间：从 50 份合同里提取甲方、金额、日期；把多个渠道的销售数据合并成一张表；批量重命名文件；把 PDF 内容整理成 Excel。

这些任务的共同点是：**规则固定、输入重复、结果明确。**

批量提取合同信息

> Prompt 示例

我会上传一批合同 PDF。

请帮我从每份合同中提取以下字段：

## 1\. 合同名称

## 2\. 甲方名称

## 3\. 乙方名称

## 4\. 签约日期

## 5\. 合同金额

## 6\. 合同有效期

请整理成 Excel 表格。

如果某个字段没有找到，请填写「未提及」。

批量合并表格

> Prompt 示例

我会上传多个 Excel 文件，它们结构相同。

请帮我把它们合并成一个总表，并新增一列「来源文件名」。

最后输出：

## 1\. 合并后的 Excel 文件

## 2\. 数据总行数

## 3\. 是否发现重复记录

## 4\. 是否发现缺失字段

文件数量不多，直接上传给 Codex 最方便。如果这是每天都要做的固定任务，可以让 Codex 生成脚本，或通过自动化定期运行。如果数据在公司 OA、ERP 或内网系统里无法导出，才考虑让 Codex 通过 Computer Use 操作界面——但这种方式一定要加确认机制。

04写职场文档

很多职场文档难的不是内容，而是语气和结构：项目复盘不能像甩锅，向上汇报不能太啰嗦，跨部门邮件要客气但明确，绩效自评要突出成绩但不能太浮夸，会议纪要要抓重点不能漏关键决定。

Codex 很适合把你的零散素材整理成专业文档。

项目复盘报告

> Prompt 示例

请根据下面素材，帮我写一份项目复盘报告。

结构：项目背景、目标与结果、做得好的地方、出现的问题、原因分析、后续改进措施

要求：

## 1\. 语气客观，不甩锅

## 2\. 不夸大成绩

## 3\. 重点突出可改进项

## 4\. 适合发给团队和直属领导

素材：\[粘贴项目过程、结果、问题和数据\]

跨部门协作邮件

> Prompt 示例

请帮我写一封跨部门协作邮件。

背景：\[说明事情背景\]

我希望对方配合：\[说明具体需求\]

截止时间：\[填写时间\]

要求：

## 1\. 语气礼貌但明确

## 2\. 不要太长

## 3\. 明确对方需要做什么

## 4\. 结尾给出下一步动作

> 关键提醒
> 不要只说「帮我写一份报告」，而是把素材、对象、语气、结构、限制都告诉 Codex。你给的信息越具体，结果越像能直接用的职场文档。

05竞品分析和市场研究

竞品分析最耗时间的地方，不是写报告，而是到处找信息。你要打开官网、定价页、产品文档、App Store、新闻稿、用户评价，最后还要整理成表。Codex 可以帮你做三件事：

一次性研究

> Prompt 示例

> 请帮我做一份竞品分析报告。
> 
> 分析对象：我们的产品 + 竞品 A / B / C
> 
> 分析维度：核心功能、定价策略、目标用户、优势、劣势、用户评价、对我们的启发
> 
> 输出格式：先给对比表，再给 5 条结论。

实时网页抓取

如果需要最新价格、最新功能、最新用户评价，可以让 Codex 用浏览器打开目标网页，直接提取信息，而不是只依赖搜索摘要。

持续监控

如果所在行业竞品更新频繁，可以设置自动化：每周检查竞品官网、定价页、更新日志和社媒动态，对比上周变化，生成一份「本周竞品变化摘要」。这样老板突然问「竞品最近有什么动作」，你不需要临时翻网页。

06让 Codex 直接操作电脑

前五个场景里，Codex 主要是在「帮你想、帮你写、帮你整理」。更进一步，它可以「帮你做」：操作 Excel 桌面应用、在网页后台填写表单、从内网系统复制数据、多平台发布信息、定时生成简报、监控邮件和消息。

这类能力通常依赖 **Computer Use、内置浏览器和 Automations**。

Computer Use

适合处理没有 API、只能手动点击的系统：OA、ERP、内网后台、桌面 Excel、某些必须人工点击的流程。

> 安全提示
> 涉及提交、删除、覆盖、发送的操作，一定要求 Codex 每一步截图确认。只有在你回复「确认继续」后，才能进行下一步。

> Prompt 示例

> 请帮我操作当前系统，但不要自动提交任何内容。
> 
> 每完成一步，请截图并说明你做了什么。
> 
> 只有在我回复「确认继续」后，才能进行下一步。
> 
> 涉及保存、提交、删除、发送的动作，必须单独向我确认。

内置浏览器

适合后台跑网页任务，不影响你自己使用电脑：打开多个竞品网站抓取价格、填写多个平台的招聘信息、检查网页内容是否更新、提取网页表格数据。

Automations

适合定时任务：每天早上生成工作简报、每周生成项目进度汇总、定时检查邮件并分类、定时监控竞品更新、定时整理待办事项。

> 自动化的正确做法是：**先在普通对话里测试 Prompt，确认结果稳定后，再设置成定时任务。**

07写好 Prompt 的核心方法

Codex 能不能好用，关键看你能不能把任务说清楚。一个好的 Prompt 至少包含四件事：

> 操作步骤

<table style="border-collapse: collapse"><tbody><tr><td style="border: 1px solid #ddd; padding: 6px 10px"><div style="color: rgb(255, 255, 255); font-weight: bold; text-align: center; font-size: 14px"><span>1</span></div><p style="font-size: 15px; font-weight: bold; color: rgb(17, 24, 39)"><span>背景</span></p><span class="color-break">​</span><p style="font-size: 14px; color: rgb(71, 85, 105)"><span>告诉它你是谁、任务发生在什么场景。例如：「我是运营经理，要给直属领导写周报。」</span></p></td></tr><tr><td style="border: 1px solid #ddd; padding: 6px 10px"><br></td></tr><tr><td style="border: 1px solid #ddd; padding: 6px 10px"><div style="color: rgb(255, 255, 255); font-weight: bold; text-align: center; font-size: 14px"><span>2</span></div><p style="font-size: 15px; font-weight: bold; color: rgb(17, 24, 39)"><span>素材</span></p><span class="color-break">​</span><p style="font-size: 14px; color: rgb(71, 85, 105)"><span>把你已有的信息全部给它：聊天记录、会议纪要、Excel 表、邮件、网页链接、任务清单。</span></p></td></tr><tr><td style="border: 1px solid #ddd; padding: 6px 10px"><br></td></tr><tr><td style="border: 1px solid #ddd; padding: 6px 10px"><div style="color: rgb(255, 255, 255); font-weight: bold; text-align: center; font-size: 14px"><span>3</span></div><p style="font-size: 15px; font-weight: bold; color: rgb(17, 24, 39)"><span>输出格式</span></p><span class="color-break">​</span><p style="font-size: 14px; color: rgb(71, 85, 105)"><span>告诉它你要什么样的结果。「输出成表格」「写成 500 字以内」「分为背景、问题、建议三部分。」</span></p></td></tr><tr><td style="border: 1px solid #ddd; padding: 6px 10px"><br></td></tr><tr><td style="border: 1px solid #ddd; padding: 6px 10px"><div style="color: rgb(255, 255, 255); font-weight: bold; text-align: center; font-size: 14px"><span>4</span></div><p style="font-size: 15px; font-weight: bold; color: rgb(17, 24, 39)"><span>约束</span></p><span class="color-break">​</span><p style="font-size: 14px; color: rgb(71, 85, 105)"><span>告诉它不要做什么。「不要夸大」「不要自动发送」「遇到不确定信息请标注。」</span></p></td></tr></tbody></table>

总结

Codex 对打工人最大的价值，不是让你学会编程，而是把那些有规则、有结构、重复消耗精力的工作交出去。**你负责判断、确认和拍板；Codex 负责整理、生成、执行和复用。**用得好，它不是一个聊天工具，而是你工作流里的第二双手。

> 关注我，一起把 AI 用起来
> 分享 AI 教学、AI 科普、AI 提效方法，普通人也能用明白、用顺手、用出结果。

  

---

![[笔记同步助手/images/8b14eaad03949270bb81f0be43efdc8e_MD5.jpg|cover_image]]

门里门外说Ai

---

内容效果不满意？[点此反馈](https://feedback.notebooksyncer.com/feedback/d49174f9_1779963623742?u=https%3A%2F%2Fmp.weixin.qq.com%2Fs%3F__biz%3DMzI3MDEzNTMxNg%3D%3D%26mid%3D2247483751%26idx%3D1%26sn%3Dd43cad4cccff2c6c9f66de6a700c2f1a%26chksm%3Deb55b980de0a9526feccecb227d655133dde3b49a9d610ac30ecb1a3d10167e4a3a25413a68c%26mpshare%3D1%26scene%3D1%26srcid%3D0528UCp09TZHro0q0udUtKU2%26sharer_shareinfo%3D976424fb52804464da8f322c433cf58b%26sharer_shareinfo_first%3D976424fb52804464da8f322c433cf58b%23rd&s=obsidian)