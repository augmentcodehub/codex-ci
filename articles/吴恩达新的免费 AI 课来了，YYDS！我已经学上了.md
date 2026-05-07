---
title: "吴恩达新的免费 AI 课来了，YYDS！我已经学上了"
author: "程序员鱼皮"
date: "2026年5月6日 06:28"
url: "https://mp.weixin.qq.com/s/lS2WlSUIOpyhUngyHesOGw"
---

# 吴恩达新的免费 AI 课来了，YYDS！我已经学上了

大家好，我是程序员鱼皮。如果你自学过 AI，那你大概率听过吴恩达老师（Andrew Ng）的名字。他是斯坦福大学的教授，Coursera 联合创始人，全球最知名的 AI 教育者之一。从最早的《Machine Learning》到后来的深度学习系列课程，全世界几百万人通过他的课入了 AI 的门。最近，吴恩达老师又出新课了，课程名叫《AI Prompting for Everyone》，一共 21 节视频课，总时长 3 小时出头，零门槛、免费学。课程指路：https://www.deeplearning.ai/courses/ai-prompting-for-everyone/![image](https://mmbiz.qpic.cn/sz_mmbiz_png/LlSQOKIxJ1FIYVkxcRZebBia9UvBIHUUHUKoL2yowqK0NAevk9Yjhh43EIMoibvcuJfW197jfwZwbMPOHFWICRLFPib7DZQjSGoO6IG1xDicGqo/640?wx_fmt=png&from=appmsg#imgIndex=0)刚看到「Prompting」这个词的时候，我第一反应是：都 2026 年了还讲提示词？这不是 23 年就卷烂了吗？但点进去看了几节课之后，我发现自己想错了。。。这门课真正在讲的，不是怎么写好一个提示词模板，而是怎么从一个 AI 新手变成 AI 高手。下面我帮大家拆解一下这门课到底在教什么，哪些内容最值得学，能帮你节省至少一个小时。建议收藏，我们开始~AI 新手和高手有啥区别？课程第一节就直接对比了 AI 新手和高手在使用 AI 方式上的差别。简单来说：新手把 AI 当搜索引擎，高手让 AI 当分析师。新手问 AI 的问题，跟使用 Google 搜索差不多，比如：Taco Bell 还有双层塔可吗？高手的做法是，直接上传一堆文档，几份车的配置单、报价、保险方案，然后说：帮我分析这几辆车的优劣，把所有材料都读完再回答，不要着急。AI 可能会花好几分钟思考，最后给你一份详细的对比报告。![image](https://mmbiz.qpic.cn/sz_mmbiz_png/LlSQOKIxJ1GOu9mgAkI6r8vIFt3IwKnRhnFO3D0vQyqftOVE9cW5EibWMMfeibMJVXcGLicXEsVl8XQYZsMTS68kjhBTghF4Uibd4iawtXF5N0C8/640?wx_fmt=png&from=appmsg#imgIndex=1)接下来他讲了第 2 个差距：新手写一句话提示词，高手给 AI 充足的上下文。吴恩达老师举了个特别好的例子，你跟 AI 说：帮我写一份给老板的工作总结。结果 AI 压根不知道你这一年干了啥，只能输出一堆正确但毫无营养的废话。高手的做法是，上传项目追踪截图、最近的文档、甚至语音备忘录，让 AI 充分了解你的情况再动笔。![image](https://mmbiz.qpic.cn/mmbiz_png/LlSQOKIxJ1HrvicrqJicAz4RzaWy3ZczVENkv7mP61sxySOZ81XCicth5oBeAPmnDAiaueGvRYzJG7Nib5LTiamq6ibb8pWgM5OG3FibfHkficQqYgFo/640?wx_fmt=png&from=appmsg#imgIndex=2)把 AI 想象成一个聪明但刚入职的大学毕业生，能力很强，但对你一无所知。你不给足信息，它就只能瞎编。还有一个我之前没想过的观点：新手让 AI 拍马屁，高手让 AI 说真话。这个是整门课最让我印象深刻的部分。吴恩达老师专门讲了「Sycophancy」，也就是 AI 的谄媚问题。比如你问 AI：我有个很棒的创业点子，移动扎染服务，帮我评估一下？你都说了「很棒」了，AI 当然顺着你夸。但高手会怎么问呢？请客观分析以下创业想法：移动扎染，评估是否有需求？市场多大？有没有竞争优势？这样 AI 才会老老实实告诉你，这个想法大概只有 8 分（满分 100）。![image](https://mmbiz.qpic.cn/sz_mmbiz_png/LlSQOKIxJ1EFJG8z2C5V1ZbU06SsPIqDrXGDVZrLJIbHq5qnibBnUjgQGUOj5HjiahDD5vvDzTflyCLZDSx7qNydHknvmqRjx4KSMlvLNZOiaM/640?wx_fmt=png&from=appmsg#imgIndex=3)华盛顿邮报做过一项研究，ChatGPT 说 that's correct、good point 这类认同表达的概率，是说 not quite right、that's not the case 的10 倍。有的模型甚至会说：老哥，你刚才说的太深刻了，我 1000% 同意你！吴恩达老师觉得 AI 一味附和你，对做决策毫无帮助。你可能会质疑，这些大家不是都知道么？还用教学？但其实存在幸存者偏差。你平时看到那些 AI 博主、程序员把 AI 玩得飞起，但他们只是少数。绝大部分人用了一两年 AI，还停留在「问一句答一句」的阶段，压根儿没发挥出 AI 的真正能力。下面我会按课程的 3 个模块，把最值得学的内容整理出来。这门课到底教了什么？整门课分 3 个模块，共 21 节课，信息量还是很大的。看看别人的课程目录，也能帮咱们快速了解「用好 AI」到底要学哪些内容。![image](https://mmbiz.qpic.cn/sz_mmbiz_png/LlSQOKIxJ1HN7bbHcMmiazjnNthRCYwHicIllk1kEOxuG79HDq9fwooMXugGqn3qzADLD16rJjwDKeX6JiaCdBVlJvOpWV3QFd3wjVpufumoks/640?wx_fmt=png&from=appmsg#imgIndex=4)模块 1、怎么用 AI 找信息这部分一共 5 节课，把 AI 获取知识的 3 个层次讲清楚了：预训练知识 → 联网搜索 → 深度调研。预训练知识，简单来说就是 AI 在训练阶段从互联网海量文本中学到的知识，相当于 AI 的「底子」。吴恩达老师举了个有趣的例子，NASA 1970 年代发射的旅行者 1 号上有一张金唱片，AI 居然知道上面录了 55 种语言的问候语。![image](https://mmbiz.qpic.cn/mmbiz_png/LlSQOKIxJ1HzcebCuphJdv42Wkc4R09gk4MVTJeyPicPSl9CrX8ic8CWQvTtzVqAK8bJaGF3qTzzmZPNUX6yoQezlTl6RfR0Bzh59ibWBVXawY/640?wx_fmt=png&from=appmsg#imgIndex=5)但是要注意，AI 的知识是有偏差的。互联网上关于做饭、明星的文章远多于关于类星体的，所以 AI 对热门话题回答得更准，冷门的就不靠谱。![image](https://mmbiz.qpic.cn/sz_mmbiz_png/LlSQOKIxJ1FS8yMMriaMIa99sPLjCboDtfXcHc1tuw6kcgG3nmZXGY5G32iajZWiafgyia6ibGmFFT180gCeuEia8A4lZvKyc0hEHdpmzpcIdQET0/640?wx_fmt=png&from=appmsg#imgIndex=6)而且训练数据有截止日期，比如 GPT-5.4 的知识截止到 2025 年 8 月，之后出现的「6 7 梗」它就不知道了。那如果需要最新的信息怎么办？这就要用到联网搜索了。联网搜索这节课中，我觉得值得关注的是：AI 搜索到的结果也有质量问题。吴恩达老师讲了一个朋友的真实案例，让 AI 推荐内华达州亨德森市的跑步地点，结果 AI 搜到了一个 20 多年前的网页，推荐了一个早已不对公众开放的学校。![image](https://mmbiz.qpic.cn/mmbiz_png/LlSQOKIxJ1HvulOGrcJWrcwMwJrUWcsyE4heicicvRVUzvgbHEMCgVmvd9AffXn9FTradiajSSQaicTLs1hZ1hibS86XqZFplSAlg1BeiaPOgzZjg/640?wx_fmt=png&from=appmsg#imgIndex=7)所以他建议我们在问健康、安全之类的问题时，主动要求 AI 使用官方机构的来源，比如世卫组织、FDA 这些。如果你不主动指定来源，AI 很可能就从 Reddit 这些地方抓信息，质量参差不齐。![image](https://mmbiz.qpic.cn/mmbiz_png/LlSQOKIxJ1HibA9sg4K7uicMp5nia4NKPI9lHCkgYO4aXXyBftr1foOHwKBRtxGz54mSjEbC45avz4tqmgECodeBwerCxrHBvdIyWqUdqZZzrY/640?wx_fmt=png&from=appmsg#imgIndex=8)虽然联网搜索能获取最新信息，但有时候你面对的问题更复杂，需要综合大量来源深入分析，这时候就该用深度调研（Deep Research）了。我觉得这是一个被严重低估的功能。吴恩达老师演示了用 Deep Research 帮自己策划万圣节鬼屋。AI 自己制定调研计划，同时搜索几十个网页，评估哪些有用，迭代几轮之后输出一份详细报告，还带有预算饼图和检查清单。![image](https://mmbiz.qpic.cn/sz_mmbiz_png/LlSQOKIxJ1HkVaUK2BHvic6pJoapicY3ia6QmdoA9upX5pj5HKlWDdU9KObs9HjyUAyIbgTG7IXJmuibVIMEr3icF31WqPW8jzcBibAcib3FWsEwk8/640?wx_fmt=png&from=appmsg#imgIndex=9)Deep Research 的成本会更高，所以要在合适的场景运用合适的方法。简单的事实查询用联网搜索就够了，需要综合几十个来源做深度分析时，才用 Deep Research。模块 2、让 AI 当你的思维搭档这是内容最充实的模块，一共 7 节课，从头脑风暴、上下文管理、桌面应用、推理能力、谄媚问题、到 AI 写作和 AI 批评，覆盖了日常使用 AI 最高频的场景。这部分的第一课是「用 AI 头脑风暴」（Brainstorming with AI）。这节课讲了一个有意思的创造力测试：给你一块砖头，你能想出 200 种用途吗？大部分人想几个就卡住了，但 AI 能给你列一大堆。不过 AI 给的默认答案往往是最常规的。为什么呢？因为 AI 是从互联网上学的，而互联网上关于「砖头能砌墙、能铺路」之类常规用途的文章数量，远比「用砖头当猫的跳台触发健身」这种奇思妙想多得多。所以 AI 默认会倾向于给你最大众的答案。![image](https://mmbiz.qpic.cn/mmbiz_png/LlSQOKIxJ1HO5fGSld2Kbj7uxtGgxGTjI3T8ibm0Rcko35pEibffk0vXC7eS8juUYxohnkAc1VcUUGxbtic62FC9Cic9hnnnRZEXQ3sow7YZbLs/640?wx_fmt=png&from=appmsg#imgIndex=10)想要更有创意的答案，关键是给更多上下文 + 多轮迭代反馈。他用制定健身计划做了演示，告诉 AI 你有蹦床和一只猫，AI 就可能给出「蹦床间歇训练」或「猫触发微型锻炼」这种有创意的方案。![image](https://mmbiz.qpic.cn/mmbiz_png/LlSQOKIxJ1F6nqftoOKEqj3pWIwickvA88JrGqLM8LZTfjNFicBtPZ0O2KrunTf2EABqcJ4Hicib9LOHqIMyrpdyIP3aHbuTmSR1MAIwjkWckZ8/640?wx_fmt=png&from=appmsg#imgIndex=11)头脑风暴解决的是怎么让 AI 给你好点子，但不管什么任务，AI 能给出多好的回答，很大程度取决于你喂给它多少信息。上下文管理（Context）这节课就在讲这件事。课里提到一个数据，现在主流 AI 模型的上下文窗口大概能装75 万个单词，差不多相当于 4 ~ 5 本《哈利波特》。![image](https://mmbiz.qpic.cn/sz_mmbiz_png/LlSQOKIxJ1EB7kxT8FG2ONuUWRj6t3PQ3ZCDheSkDQQ1Q2tDFsI3Iwat0PBZW9iadTvjyJNWL1aC4fCruB6TAnYiafRF2NwMTfHdDUdyma0A0/640?wx_fmt=png&from=appmsg#imgIndex=12)很多人严重低估了可以给 AI 提供多少信息，结果就是只给一句话提示词，得到一个泛泛而谈的回答，然后抱怨 AI 不好用。如果你在一个对话里突然换了完全不相关的话题，之前的上下文反而会干扰 AI 的判断，这时候应该开一个新对话。![image](https://mmbiz.qpic.cn/sz_mmbiz_png/LlSQOKIxJ1EwXAVxQQFbPUtxNVP0yQBWIibQGYZEdsgLgwGvb0dKccfT2dcxC30LXcaicBmhdfbYpibAdTicAnaH4Z2xrGNm4y2XSHc6kP0e3pU/640?wx_fmt=png&from=appmsg#imgIndex=13)接下来是「AI 桌面应用」这节课，讲的是 Claude、Microsoft Copilot 这类桌面端应用，它们能直接读取你电脑上的文件来干活。老师演示了让 AI 整理一个乱七八糟的文件夹。AI 自动扫描文件内容，提出整理方案，人工确认后执行。操作很简单，但是一定要注意安全！AI 删除的文件不会进回收站，编辑文件也没有撤销历史，所以建议只给它你需要处理的那个文件夹的权限。![image](https://mmbiz.qpic.cn/mmbiz_png/LlSQOKIxJ1H0msvSibZlSRzBY4L8as3GFgfEpVhsJSsqw1nkzYpRxM9xwzuQ2BCv9ibKNEVtLCQc6llLV8xbH3ekVjib3zicRgicjw50ywQuKdEk/640?wx_fmt=png&from=appmsg#imgIndex=14)到这里，课程已经把「怎么给 AI 足够的信息」讲透了。接下来的问题是：有了充足的上下文，AI 能思考到什么程度？AI 推理能力（Reasoning with AI）这节课就在回答这个问题。老师提到，现在的 AI 模型能处理需要人类花好几个小时才能完成的任务，还引用了 METR 组织的一项研究数据。![image](https://mmbiz.qpic.cn/sz_mmbiz_png/LlSQOKIxJ1F8rPnfEDNHbcOrt4QVfsB0KXGAxANvyQYpxUgdyVHHtJatjJYDQeicKYt8eHN6nc3Azs96ob3uoZfHVGcQFQbI9GbFicLiaa6Bkk/640?wx_fmt=png&from=appmsg#imgIndex=15)他说以前大家让 AI「think step-by-step」逐步思考，这个技巧已经过时了；现在直接告诉 AI「think hard」认真想，甚至「ultrathink」使劲想，AI 知道该怎么做。![image](https://mmbiz.qpic.cn/mmbiz_png/LlSQOKIxJ1FXsLm1kPibENeQicgd3QR0U7G8XdI5qlGCclIMHywlSyiaMBCWr4RG5Qtwju8QBcb74EkpxpMHRWPotfNydsvm9PibCdKDoc5hwxg/640?wx_fmt=png&from=appmsg#imgIndex=16)下一节课是「AI 写作」，吴恩达老师讲了一个概念叫Progressive Outlining 渐进式大纲法，不要一上来就让 AI 写全文，而是先列大纲，反复讨论修改大纲，展开成要点，再反复打磨，最后才写正文。这个跟我之前分享过的 Vibe Writing 套路一致。![image](https://mmbiz.qpic.cn/mmbiz_png/LlSQOKIxJ1G5Raw8mq7l1Ihic4d2X99d0XZoyOs4kEJ7XVbfz25PN4ZpIyKmerOtEOIfGXe5GyiaUBiaAawVdZibCy1JLpFJIkCvthwpEQJxud4/640?wx_fmt=png&from=appmsg#imgIndex=17)他还专门分析了什么是「AI slop」，就是 AI 生成的看起来每句话都挺通顺，但合在一起就是没什么内容的废话。AI 还特别爱用长破折号、爱用 nuanced（细致入微）、delve（深入探讨）这些看起来高级，但其实没什么营养的词。![image](https://mmbiz.qpic.cn/mmbiz_png/LlSQOKIxJ1FROGhmooX5VU5hmcWSRKhx4SZ1EvvYOKIhZLDY0ZscmgszraY8IeemsOmvJesHWuIhCNG879B3fsUGIgEeDBdqHhNkdkA9bFM/640?wx_fmt=png&from=appmsg#imgIndex=18)有意思的是，人类自从跟 AI 聊天多了以后，自己说话也开始像 AI 了。播客和演讲中使用 delve 这个词的频率明显上升。。。光会用 AI 写作还不够，怎么判断写出来的东西好不好呢？「AI 批评与评估」这节课教了个实用技巧，给 AI 一个评分标准（Rubric）来评估内容。比如评价一篇科幻小说，你定义角色 25 分、情节 25 分、世界观 25 分、写作技巧 25 分，每项再细化成客观可判断的标准（比如每个主角是否有明确目标，是或否，10 分）。![image](https://mmbiz.qpic.cn/mmbiz_png/LlSQOKIxJ1HslXiavtXXYnnX9Ummc2ibADzKo7mywl6Inj41MHAR7ZDBia9ZY78lGYmGwqQiagVhvvbzMsLghAWdicdAJ4JF2oNqN5jSibpfrk4G4/640?wx_fmt=png&from=appmsg#imgIndex=19)这样 AI 就会被迫客观评价，而不是无脑夸你。他还提到一个跨模型评审的技巧，让 ChatGPT 写，让 Gemini 评，效果会比自己评自己稍微好一点。这也是我 AI 编程时一直在用的技巧，多模型交叉验证。![image](https://mmbiz.qpic.cn/sz_mmbiz_png/LlSQOKIxJ1E15LnoRicY01IeKW7AaNDY5oHvdm2mdcusiataHSO69IJT66Lp98B5mfLQ5pKus2oJsoHCAUbIib9zpAtCvTw8YVmHCHic7PIEibWM/640?wx_fmt=png&from=appmsg#imgIndex=20)模块 3、用 AI 玩多媒体和编程前面两个模块主要围绕 AI 生成文本展开，第三个模块的花样就更多了，5 节课覆盖了图片理解、图片生成、零代码做应用、和数据分析。吴恩达老师分享了一个自己的故事：他女儿 Nova 7 岁生日，他用 AI 生成了很多猫咪蛋糕的设计方案，女儿选了一个最喜欢的，然后拿去给面包师照着做成了真实的 3D 蛋糕。![image](https://mmbiz.qpic.cn/mmbiz_png/LlSQOKIxJ1GGxMI36cFFTjqn4tInvok0hCEQR0GnzSysyrSKGRviccyPS4YFAZ9FaYKsATxYshwT7Z4ePR7NcvW4roxzbgUrlia7bQxSC1d08/640?wx_fmt=png&from=appmsg#imgIndex=21)他还展示了 AI 生成的语音克隆，用自己的声音克隆读了一篇 DeepLearning 的新闻。然后把这段录音放给父母听，一个听出来是假的，一个没听出来。AI 不仅能生成图片和声音，还能「看」图。图片理解（Image Understanding）这节课讲了 AI 读图的能力和局限。吴恩达老师上传了自己在白板前讲课的照片，AI 不仅认出了他在讲卷积神经网络，甚至他的头挡住了「convolutional」这个单词，AI 也能根据白板上的图形推断出来。![image](https://mmbiz.qpic.cn/sz_mmbiz_png/LlSQOKIxJ1F1fzFWjPq5q59Ax5vBwLIOAbZsFOOfcRtoSR0hpfdB8hzZFTHgwtJ8onZNxD3U7ye8oS584NrESjGOqCC4A389doCRB7qm8Qk/640?wx_fmt=png&from=appmsg#imgIndex=22)但让 AI 识别健身房器械就不太行了，很多器械隔着一层模糊的镜头看长得都差不多。![image](https://mmbiz.qpic.cn/sz_mmbiz_png/LlSQOKIxJ1Gwjzo1p6kjJtgFHYRdnmEJEfmhJCGec2xeU46cG2QtIx1jQw6sPkqGtwJ24haC9MRv1aULdII2ZWnVv2mIgpK1iagh8j1nesvM/640?wx_fmt=png&from=appmsg#imgIndex=23)能看图、能生图、能生视频和语音，那能不能再进一步，直接帮你做一个 AI 应用出来？零代码做应用（Building Apps）这节课就演示了这件事。用一句话提示词让 Claude 生成了一个障碍物放置游戏，还做了一个烟花模拟器。他建议初学者从简单的应用入手，比如番茄钟、AA 制计算器、天气穿衣推荐这些功能明确的小工具。![image](https://mmbiz.qpic.cn/mmbiz_png/LlSQOKIxJ1GqtSEQ6CYheJTOa4QPrRwbMpZSXDsxkUh31amB7NYAz5ALws6Cg4UwWWglgLZibgS2ia6vaPshHVuEKAOicXkrJHC40tb8R3COIA/640?wx_fmt=png&from=appmsg#imgIndex=24)最后一节是数据分析，讲的是把数据扔给 AI，让它自动写代码分析并生成可视化图表。他用一个奶茶店的销售数据做了演示。AI 自动识别出草莓抹茶在春季促销时卖得特别好、椰奶茶在秋季有增长趋势，还生成了一张带奶茶配色的年度回顾图。![image](https://mmbiz.qpic.cn/mmbiz_png/LlSQOKIxJ1HicyKWml2zXUu8tgUxZ45ib6NUR1POXFfaibqs4OdeibT6Do7tGdptMVIepGG8WicrU5gNgiaNyhL9PkVO83FtLW47XTpGOqfHZUd1U/640?wx_fmt=png&from=appmsg#imgIndex=25)整套课看下来，包含了非常多吴恩达老师自己使用 AI 的经验和事例，就像一个人在跟你聊天讲故事一样，很有温度。这门课值不值得学？这门课适合没有任何编程基础的普通人，作为全面了解 AI 用法和原理的科普课来看，非常合适。它不太侧重实战，但能帮你建立起「AI 到底能干什么、怎么用才对」的完整认知。之前我给大家分享过斯坦福的 AI 编程课和微软的 AI Agent 课，那两门课都偏开发者向，有一定的编程门槛。而吴恩达老师这门课完全没有门槛，甚至可以推荐给不懂技术的朋友和家人。不过缺点是，课程是全英文的，有英文字幕但没有中文翻译，不过你可以让 AI 帮你翻译字幕来看。另外课程整体偏基础，如果你已经是 AI 深度用户了，可能会觉得部分内容不够硬核。如果你对 AI 有一定的了解，想进一步用 AI 编程做点实际的东西。可以看看我免费开源的《Vibe Coding 零基础入门教程》，上千张图、几十万字，结合了我两年半的 AI 编程经验。帮你从 0 开始快速学会 AI 编程，再到做出自己的产品、跑通变现全流程，一次拿捏。开源指路：github.com/liyupi/ai-guide![image](https://mmbiz.qpic.cn/mmbiz_png/LlSQOKIxJ1HtjNgULsoqkdq7q2YXE3aThb5AmJdfRoAeibjb0iaq4yqmCLLGlD231KNwsJbBCWG23lOJGDdN1dDtFQcf0icBIxic5wT4FAMm5icI/640?wx_fmt=png&from=appmsg#imgIndex=26)吴恩达老师的课教你怎么跟 AI 高效对话，我的教程教你怎么用 AI 把东西做出来，两者正好互补。2026 年，AI 已经不是什么遥远的概念了。它就在你手边，每天都能用上。学会用好 AI，不是为了追风口，而是让自己的时间更值钱一点，让重复的事情少做一点，让生活多一点余裕。OK 以上就是本期分享，我是鱼皮，持续分享 AI 编程干货。学会的话记得点赞收藏和关注，也欢迎在评论区聊聊：你都用 AI 做了些什么？有什么使用 AI 的小技巧？往期推荐跌爆了！又完结一个 AI 智能体项目！后端 & AI 全栈开发特训营，明天涨价 1k！时隔六年，曝光一下鱼皮的最新简历！春招最能打的 AI 项目！SSP Offer 拿下面试官都开始用这个网站出题了。。我的 AI 网站，突然起飞了！

大家好，我是程序员鱼皮。

如果你自学过 AI，那你大概率听过吴恩达老师（Andrew Ng）的名字。他是斯坦福大学的教授，Coursera 联合创始人，全球最知名的 AI 教育者之一。从最早的《Machine Learning》到后来的深度学习系列课程，全世界几百万人通过他的课入了 AI 的门。

最近，吴恩达老师又出新课了，课程名叫《AI Prompting for Everyone》，一共 21 节视频课，总时长 3 小时出头，零门槛、免费学。

> 课程指路：https://www.deeplearning.ai/courses/ai-prompting-for-everyone/

课程指路：https://www.deeplearning.ai/courses/ai-prompting-for-everyone/

刚看到「Prompting」这个词的时候，我第一反应是：都 2026 年了还讲提示词？这不是 23 年就卷烂了吗？

但点进去看了几节课之后，我发现自己想错了。。。

这门课真正在讲的，不是怎么写好一个提示词模板，而是怎么从一个 AI 新手变成 AI 高手。

下面我帮大家拆解一下这门课到底在教什么，哪些内容最值得学，能帮你节省至少一个小时。

建议收藏，我们开始~

## AI 新手和高手有啥区别？

课程第一节就直接对比了 AI 新手和高手在使用 AI 方式上的差别。

简单来说：新手把 AI 当搜索引擎，高手让 AI 当分析师。

新手问 AI 的问题，跟使用 Google 搜索差不多，比如：Taco Bell 还有双层塔可吗？

高手的做法是，直接上传一堆文档，几份车的配置单、报价、保险方案，然后说：帮我分析这几辆车的优劣，把所有材料都读完再回答，不要着急。

AI 可能会花好几分钟思考，最后给你一份详细的对比报告。

接下来他讲了第 2 个差距：新手写一句话提示词，高手给 AI 充足的上下文。

吴恩达老师举了个特别好的例子，你跟 AI 说：帮我写一份给老板的工作总结。

结果 AI 压根不知道你这一年干了啥，只能输出一堆正确但毫无营养的废话。

高手的做法是，上传项目追踪截图、最近的文档、甚至语音备忘录，让 AI 充分了解你的情况再动笔。

把 AI 想象成一个聪明但刚入职的大学毕业生，能力很强，但对你一无所知。你不给足信息，它就只能瞎编。

还有一个我之前没想过的观点：新手让 AI 拍马屁，高手让 AI 说真话。

这个是整门课最让我印象深刻的部分。吴恩达老师专门讲了「Sycophancy」，也就是 AI 的谄媚问题。

比如你问 AI：我有个很棒的创业点子，移动扎染服务，帮我评估一下？

你都说了「很棒」了，AI 当然顺着你夸。

但高手会怎么问呢？

请客观分析以下创业想法：移动扎染，评估是否有需求？市场多大？有没有竞争优势？

这样 AI 才会老老实实告诉你，这个想法大概只有 8 分（满分 100）。

华盛顿邮报做过一项研究，ChatGPT 说 that's correct、good point 这类认同表达的概率，是说 not quite right、that's not the case 的10 倍。

有的模型甚至会说：老哥，你刚才说的太深刻了，我 1000% 同意你！

吴恩达老师觉得 AI 一味附和你，对做决策毫无帮助。

你可能会质疑，这些大家不是都知道么？还用教学？

但其实存在幸存者偏差。你平时看到那些 AI 博主、程序员把 AI 玩得飞起，但他们只是少数。绝大部分人用了一两年 AI，还停留在「问一句答一句」的阶段，压根儿没发挥出 AI 的真正能力。

下面我会按课程的 3 个模块，把最值得学的内容整理出来。

## 这门课到底教了什么？

整门课分 3 个模块，共 21 节课，信息量还是很大的。

看看别人的课程目录，也能帮咱们快速了解「用好 AI」到底要学哪些内容。

### 模块 1、怎么用 AI 找信息

这部分一共 5 节课，把 AI 获取知识的 3 个层次讲清楚了：预训练知识 → 联网搜索 → 深度调研。

预训练知识，简单来说就是 AI 在训练阶段从互联网海量文本中学到的知识，相当于 AI 的「底子」。

吴恩达老师举了个有趣的例子，NASA 1970 年代发射的旅行者 1 号上有一张金唱片，AI 居然知道上面录了 55 种语言的问候语。

但是要注意，AI 的知识是有偏差的。

互联网上关于做饭、明星的文章远多于关于类星体的，所以 AI 对热门话题回答得更准，冷门的就不靠谱。

而且训练数据有截止日期，比如 GPT-5.4 的知识截止到 2025 年 8 月，之后出现的「6 7 梗」它就不知道了。

那如果需要最新的信息怎么办？

这就要用到联网搜索了。

联网搜索这节课中，我觉得值得关注的是：AI 搜索到的结果也有质量问题。

吴恩达老师讲了一个朋友的真实案例，让 AI 推荐内华达州亨德森市的跑步地点，结果 AI 搜到了一个 20 多年前的网页，推荐了一个早已不对公众开放的学校。

所以他建议我们在问健康、安全之类的问题时，主动要求 AI 使用官方机构的来源，比如世卫组织、FDA 这些。

如果你不主动指定来源，AI 很可能就从 Reddit 这些地方抓信息，质量参差不齐。

虽然联网搜索能获取最新信息，但有时候你面对的问题更复杂，需要综合大量来源深入分析，这时候就该用深度调研（Deep Research）了。我觉得这是一个被严重低估的功能。

吴恩达老师演示了用 Deep Research 帮自己策划万圣节鬼屋。AI 自己制定调研计划，同时搜索几十个网页，评估哪些有用，迭代几轮之后输出一份详细报告，还带有预算饼图和检查清单。

Deep Research 的成本会更高，所以要在合适的场景运用合适的方法。简单的事实查询用联网搜索就够了，需要综合几十个来源做深度分析时，才用 Deep Research。

### 模块 2、让 AI 当你的思维搭档

这是内容最充实的模块，一共 7 节课，从头脑风暴、上下文管理、桌面应用、推理能力、谄媚问题、到 AI 写作和 AI 批评，覆盖了日常使用 AI 最高频的场景。

这部分的第一课是「用 AI 头脑风暴」（Brainstorming with AI）。

这节课讲了一个有意思的创造力测试：给你一块砖头，你能想出 200 种用途吗？

大部分人想几个就卡住了，但 AI 能给你列一大堆。

不过 AI 给的默认答案往往是最常规的。

为什么呢？

因为 AI 是从互联网上学的，而互联网上关于「砖头能砌墙、能铺路」之类常规用途的文章数量，远比「用砖头当猫的跳台触发健身」这种奇思妙想多得多。所以 AI 默认会倾向于给你最大众的答案。

想要更有创意的答案，关键是给更多上下文 + 多轮迭代反馈。

他用制定健身计划做了演示，告诉 AI 你有蹦床和一只猫，AI 就可能给出「蹦床间歇训练」或「猫触发微型锻炼」这种有创意的方案。

头脑风暴解决的是怎么让 AI 给你好点子，但不管什么任务，AI 能给出多好的回答，很大程度取决于你喂给它多少信息。上下文管理（Context）这节课就在讲这件事。

课里提到一个数据，现在主流 AI 模型的上下文窗口大概能装75 万个单词，差不多相当于 4 ~ 5 本《哈利波特》。

很多人严重低估了可以给 AI 提供多少信息，结果就是只给一句话提示词，得到一个泛泛而谈的回答，然后抱怨 AI 不好用。

如果你在一个对话里突然换了完全不相关的话题，之前的上下文反而会干扰 AI 的判断，这时候应该开一个新对话。

接下来是「AI 桌面应用」这节课，讲的是 Claude、Microsoft Copilot 这类桌面端应用，它们能直接读取你电脑上的文件来干活。

老师演示了让 AI 整理一个乱七八糟的文件夹。AI 自动扫描文件内容，提出整理方案，人工确认后执行。

操作很简单，但是一定要注意安全！AI 删除的文件不会进回收站，编辑文件也没有撤销历史，所以建议只给它你需要处理的那个文件夹的权限。

到这里，课程已经把「怎么给 AI 足够的信息」讲透了。

接下来的问题是：有了充足的上下文，AI 能思考到什么程度？

AI 推理能力（Reasoning with AI）这节课就在回答这个问题。

老师提到，现在的 AI 模型能处理需要人类花好几个小时才能完成的任务，还引用了 METR 组织的一项研究数据。

他说以前大家让 AI「think step-by-step」逐步思考，这个技巧已经过时了；现在直接告诉 AI「think hard」认真想，甚至「ultrathink」使劲想，AI 知道该怎么做。

下一节课是「AI 写作」，吴恩达老师讲了一个概念叫Progressive Outlining 渐进式大纲法，不要一上来就让 AI 写全文，而是先列大纲，反复讨论修改大纲，展开成要点，再反复打磨，最后才写正文。这个跟我之前分享过的 Vibe Writing 套路一致。

他还专门分析了什么是「AI slop」，就是 AI 生成的看起来每句话都挺通顺，但合在一起就是没什么内容的废话。

AI 还特别爱用长破折号、爱用 nuanced（细致入微）、delve（深入探讨）这些看起来高级，但其实没什么营养的词。

有意思的是，人类自从跟 AI 聊天多了以后，自己说话也开始像 AI 了。播客和演讲中使用 delve 这个词的频率明显上升。。。

光会用 AI 写作还不够，怎么判断写出来的东西好不好呢？

「AI 批评与评估」这节课教了个实用技巧，给 AI 一个评分标准（Rubric）来评估内容。

比如评价一篇科幻小说，你定义角色 25 分、情节 25 分、世界观 25 分、写作技巧 25 分，每项再细化成客观可判断的标准（比如每个主角是否有明确目标，是或否，10 分）。

这样 AI 就会被迫客观评价，而不是无脑夸你。

他还提到一个跨模型评审的技巧，让 ChatGPT 写，让 Gemini 评，效果会比自己评自己稍微好一点。这也是我 AI 编程时一直在用的技巧，多模型交叉验证。

### 模块 3、用 AI 玩多媒体和编程

前面两个模块主要围绕 AI 生成文本展开，第三个模块的花样就更多了，5 节课覆盖了图片理解、图片生成、零代码做应用、和数据分析。

吴恩达老师分享了一个自己的故事：他女儿 Nova 7 岁生日，他用 AI 生成了很多猫咪蛋糕的设计方案，女儿选了一个最喜欢的，然后拿去给面包师照着做成了真实的 3D 蛋糕。

他还展示了 AI 生成的语音克隆，用自己的声音克隆读了一篇 DeepLearning 的新闻。然后把这段录音放给父母听，一个听出来是假的，一个没听出来。

AI 不仅能生成图片和声音，还能「看」图。

图片理解（Image Understanding）这节课讲了 AI 读图的能力和局限。

吴恩达老师上传了自己在白板前讲课的照片，AI 不仅认出了他在讲卷积神经网络，甚至他的头挡住了「convolutional」这个单词，AI 也能根据白板上的图形推断出来。

但让 AI 识别健身房器械就不太行了，很多器械隔着一层模糊的镜头看长得都差不多。

能看图、能生图、能生视频和语音，那能不能再进一步，直接帮你做一个 AI 应用出来？

零代码做应用（Building Apps）这节课就演示了这件事。用一句话提示词让 Claude 生成了一个障碍物放置游戏，还做了一个烟花模拟器。

他建议初学者从简单的应用入手，比如番茄钟、AA 制计算器、天气穿衣推荐这些功能明确的小工具。

最后一节是数据分析，讲的是把数据扔给 AI，让它自动写代码分析并生成可视化图表。

他用一个奶茶店的销售数据做了演示。AI 自动识别出草莓抹茶在春季促销时卖得特别好、椰奶茶在秋季有增长趋势，还生成了一张带奶茶配色的年度回顾图。

整套课看下来，包含了非常多吴恩达老师自己使用 AI 的经验和事例，就像一个人在跟你聊天讲故事一样，很有温度。

## 这门课值不值得学？

这门课适合没有任何编程基础的普通人，作为全面了解 AI 用法和原理的科普课来看，非常合适。

它不太侧重实战，但能帮你建立起「AI 到底能干什么、怎么用才对」的完整认知。

之前我给大家分享过斯坦福的 AI 编程课和微软的 AI Agent 课，那两门课都偏开发者向，有一定的编程门槛。而吴恩达老师这门课完全没有门槛，甚至可以推荐给不懂技术的朋友和家人。

不过缺点是，课程是全英文的，有英文字幕但没有中文翻译，不过你可以让 AI 帮你翻译字幕来看。

另外课程整体偏基础，如果你已经是 AI 深度用户了，可能会觉得部分内容不够硬核。

如果你对 AI 有一定的了解，想进一步用 AI 编程做点实际的东西。可以看看我免费开源的《Vibe Coding 零基础入门教程》，上千张图、几十万字，结合了我两年半的 AI 编程经验。帮你从 0 开始快速学会 AI 编程，再到做出自己的产品、跑通变现全流程，一次拿捏。

> 开源指路：github.com/liyupi/ai-guide

开源指路：github.com/liyupi/ai-guide

吴恩达老师的课教你怎么跟 AI 高效对话，我的教程教你怎么用 AI 把东西做出来，两者正好互补。

2026 年，AI 已经不是什么遥远的概念了。

它就在你手边，每天都能用上。

学会用好 AI，不是为了追风口，而是让自己的时间更值钱一点，让重复的事情少做一点，让生活多一点余裕。

OK 以上就是本期分享，我是鱼皮，持续分享 AI 编程干货。学会的话记得点赞收藏和关注，也欢迎在评论区聊聊：你都用 AI 做了些什么？有什么使用 AI 的小技巧？

往期推荐跌爆了！又完结一个 AI 智能体项目！后端 & AI 全栈开发特训营，明天涨价 1k！时隔六年，曝光一下鱼皮的最新简历！春招最能打的 AI 项目！SSP Offer 拿下面试官都开始用这个网站出题了。。我的 AI 网站，突然起飞了！

往期推荐跌爆了！又完结一个 AI 智能体项目！后端 & AI 全栈开发特训营，明天涨价 1k！时隔六年，曝光一下鱼皮的最新简历！春招最能打的 AI 项目！SSP Offer 拿下面试官都开始用这个网站出题了。。我的 AI 网站，突然起飞了！

往期推荐

往期推荐

往期推荐

跌爆了！又完结一个 AI 智能体项目！后端 & AI 全栈开发特训营，明天涨价 1k！时隔六年，曝光一下鱼皮的最新简历！春招最能打的 AI 项目！SSP Offer 拿下面试官都开始用这个网站出题了。。我的 AI 网站，突然起飞了！

跌爆了！

跌爆了！

跌爆了！

又完结一个 AI 智能体项目！

又完结一个 AI 智能体项目！

又完结一个 AI 智能体项目！

后端 & AI 全栈开发特训营，明天涨价 1k！

后端 & AI 全栈开发特训营，明天涨价 1k！

后端 & AI 全栈开发特训营，明天涨价 1k！

时隔六年，曝光一下鱼皮的最新简历！

时隔六年，曝光一下鱼皮的最新简历！

时隔六年，曝光一下鱼皮的最新简历！

春招最能打的 AI 项目！SSP Offer 拿下

春招最能打的 AI 项目！SSP Offer 拿下

春招最能打的 AI 项目！SSP Offer 拿下

面试官都开始用这个网站出题了。。

面试官都开始用这个网站出题了。。

面试官都开始用这个网站出题了。。

我的 AI 网站，突然起飞了！

我的 AI 网站，突然起飞了！

我的 AI 网站，突然起飞了！