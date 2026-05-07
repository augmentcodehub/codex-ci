---
title: "Sage Wiki：把 Karpathy 的 LLM Wiki 理念变成了一个真正能用的产品"
author: "Joneyao"
date: "2026年5月6日 10:54"
url: "https://mp.weixin.qq.com/s/oe6ydtP8DCvRSPmBheNi_Q"
---

# Sage Wiki：把 Karpathy 的 LLM Wiki 理念变成了一个真正能用的产品

2026 年 4 月 4 日，Andrej Karpathy 在 X 上发了一条帖子，说他不再主要用 LLM 写代码了——而是用它来构建个人知识库。帖子获得了 1600 万次浏览，随后发布的 GitHub Gist 在几天内拿到 5000+ star。这条帖子戳中了一个痛点：每个知识工作者都有一堆废弃的知识管理系统。Notion 数据库三个月没更新，Obsidian 图谱长满了灰，浏览器书签夹里 500 个链接没有一个写了摘要。问题不在工具，在维护成本。Karpathy 的洞察很简单：LLM 天生擅长这种"苦力活"——阅读文档、提取概念、生成摘要、建立交叉引用、更新索引。人类负责策展输入，LLM 负责其余一切。但 Karpathy 发布的只是一个"模式"（pattern），不是产品。你需要自己搭目录结构，自己写 CLAUDE.md schema，自己处理各种边界情况。对于想直接用起来的人，这个门槛不低。Sage Wiki 就是把这个模式工程化的产物。一个 Go 编写的单二进制文件，零 CGO 依赖，支持 12+ 种源文件格式，能扩展到 10 万+ 文档，内置混合搜索、本体图谱、MCP 集成和 Web UI。![image](https://mmbiz.qpic.cn/mmbiz_png/dLBesCqkPI1CsoZAP6ox9Ha2PhNdZibEDGSYbQw7c1UWJ3nz91paKADia4mO3vBDubpwmyibiaEqL0F6JAY1xTwiboVCsmFnAV3OWqGFyIv5QHiaI/640?from=appmsg&watermark=1#imgIndex=0)raw/ 原始素材什么是 LLM Wiki 模式传统知识管理有三步：收集（容易）、组织（困难）、维护（规模化后几乎不可能）。每加入一篇新文章，你需要阅读它、写摘要、链接到已有概念、更新相关页面、检查与现有知识的矛盾。没人能持续做到这些。LLM Wiki 模式用一个编译器类比来解决这个问题：源代码= 你收集的原始素材（论文、文章、笔记、代码）编译器= LLM（读取源文件，生成结构化输出）可执行文件= Wiki（结构化的、可搜索的、互相链接的知识库）和 RAG 的区别在哪？RAG 是"每次查询时实时检索原始文档"，LLM Wiki 是"提前编译好，查询时直接读编译产物"。就像你不会每次运行程序都重新编译源码一样。实际效果：Karpathy 的单主题 Wiki 在没有他直接编写任何内容的情况下，增长到了约 100 篇文章、40 万字——比大多数博士论文还长。为什么比 RAG 更适合个人知识库？维度RAGLLM Wiki查询成本每次查询都要嵌入+检索+生成查询时直接读 Markdown，接近零成本知识质量受限于 chunk 切分质量编译时已做概念提取和交叉验证可维护性向量库漂移、chunk 边界错误纯文本，git 可追踪复合增长每次查询独立，不积累每次编译都丰富已有文章Token 消耗每次查询消耗大量 token编译一次，查询几乎免费有测试表明，对于小型聚焦知识库，LLM Wiki 模式相比朴素 RAG 可以减少高达 95% 的 token 消耗。Sage Wiki 的技术方案Sage Wiki 不是简单地把 Karpathy 的 Gist 包装成 CLI。它在几个关键维度上做了工程化突破。分层编译：10 万文档不是梦这是 sage-wiki 最有意思的设计。不是所有文档都需要完整的 LLM 编译——大部分时候你只需要能搜到它就行。![image](https://mmbiz.qpic.cn/sz_mmbiz_png/dLBesCqkPI11AgQcic8Iwg3mluV1B9VYPrDCvy7pfQJNGaB4icPSzOETbQ15TU8ad42iaicBaUFZTRibaE4VBKvgIse2wuBnqsFsuGmoa4xIcWibE/640?from=appmsg&watermark=1#imgIndex=1)图表关键机制：文件类型默认分层：JSON/YAML/lock 文件自动走 Tier 0，Markdown 走 Tier 1，代码走 Tier 2自动提升：某个源文件被搜索命中 3 次以上，自动提升到 Tier 3 做完整编译自动降级：90 天没被查询的文章降回 Tier 1，下次访问时重新编译按需编译：通过 MCP 的wiki_compile_topic工具，Agent 可以实时触发特定主题的编译实际效果：一个 10 万文档的知识库，全量索引（Tier 1）只需约 5.5 小时。而传统的全量 Tier 3 编译可能需要数周。混合搜索管线sage-wiki 的搜索不是简单的关键词匹配或向量相似度，而是一个多阶段管线：![image](https://mmbiz.qpic.cn/sz_mmbiz_png/dLBesCqkPI3EyOXHWtPhesDWfia2c8Ot2l8D79fmx2fn8W4Ph7nxYvAniaibJvT0THJL9ERRZp1LaQ0yUCO6KGAWmjKRf39ibbN6IuMEZib5ETMM/640?from=appmsg&watermark=1#imgIndex=2)图表四个图谱扩展信号：直接关系（×3.0）：本体图谱中的直接边共享源文档（×4.0）：两个概念来自同一源文件共同邻居（×1.5）：Adamic-Adar 算法计算的结构相似度实体类型亲和（×1.0）：同类型实体的额外加分性能数据（来自 1107 个源文件、2832 个 wiki 文件的真实测试）：FTS5 关键词搜索：411µs（1775 qps）向量搜索：81ms（15 qps）混合 RRF 搜索：80ms（16 qps）图谱遍历：1µs（738K qps）搜索召回率@10：100%搜索召回率@1：91.6%本体图谱sage-wiki 不只是生成独立的文章——它构建了一个类型化的实体-关系图谱。8 种内置关系类型：implements、extends、optimizes、contradicts、cites、prerequisite_of、trades_off、derived_from。关系提取基于段落级关键词共现：一个关键词必须与[[wikilink]]在同一段落或标题块中共现才会建立边。这避免了跨段落的虚假关联。你还可以自定义关系类型，甚至限制关系的源/目标实体类型：ontology:relation_types:-name: curated_bysynonyms: ["curatedby","organizedby"]valid_sources: [exhibition,program]valid_targets: [artist]MCP 集成：17 个工具sage-wiki 作为 MCP 服务器运行，提供 17 个工具（6 读、9 写、2 复合）。这意味着任何支持 MCP 的 AI Agent 都可以直接操作你的知识库：wiki_search/wiki_query：搜索和问答wiki_compile_topic：按需编译特定主题wiki_capture：从对话中提取知识wiki_learn：存储单条知识wiki_add_source：添加源文件配置极简，在.mcp.json中加一行：{"mcpServers": {"sage-wiki": {"command":"sage-wiki","args": ["serve","--project","/path/to/wiki"]}}}横向对比：Sage Wiki vs 同类方案Karpathy 的帖子发出后一周内，社区涌现了大量实现。它们各有侧重，适合不同场景。维度sage-wikiDeepWiki手动 Karpathy 模式传统 RAG定位通用个人知识库代码仓库文档生成DIY 知识库企业级检索源文件支持12+ 格式（PDF/DOCX/代码/图片等）仅代码仓库取决于 Agent 能力通常需要预处理扩展性10 万+ 文档（分层编译）单仓库级别数百文档（受上下文窗口限制）理论无限（但成本线性增长）搜索能力混合搜索 + 图谱扩展 + LLM 重排内置 Chat依赖 Agent 的文件读取向量相似度 + 可选重排知识积累复合增长（新源丰富旧文章）静态快照手动触发更新不积累部署方式单二进制 / DockerSaaS本地文件夹 + Agent需要向量库 + API 服务成本编译时付费，查询几乎免费按仓库付费每次交互消耗 token每次查询消耗 tokenObsidian 集成原生支持（vault overlay）无手动配置无MCP 支持17 个工具无无标准接口取决于实现开源MIT部分开源N/A（模式）取决于实现![image](https://mmbiz.qpic.cn/mmbiz_png/dLBesCqkPI2Fde6zDLjtH2OMibMu9jibwD49wY2DSF1onNtrSwvJAO0j1vbZIuia2KnT7sFzcEjo0lJHVHuvzdBibjfLBkcjjU0Jk9EV1qBeHGc/640?from=appmsg&watermark=1#imgIndex=3)雷达图：五个维度对比四种知识库方案，sage-wiki 在扩展性和搜索质量维度接近满分，手动模式在易用性上最低什么时候选 sage-wiki？你有大量异构源文件（论文 + 笔记 + 代码 + 图片混合）你需要知识库持续增长，而不是一次性生成你想让 AI Agent 直接操作知识库（MCP）你已经在用 Obsidian，想无缝集成什么时候不需要 sage-wiki？只是想快速理解一个 GitHub 仓库 → DeepWiki 更合适知识库规模很小（< 50 篇文档）→ 手动 Karpathy 模式足够需要实时数据（股票、新闻）→ RAG 更合适安装与快速上手sage-wiki 提供三种安装方式，覆盖从"试一下"到"生产部署"的全部场景。![image](https://mmbiz.qpic.cn/mmbiz_png/dLBesCqkPI0MCcAuDm2iawun8iad6VHwj1KfN91ZrQwSu5fwMjCiaZApVP6dW89m0PT2cefHhzUhPCuzfZo90BmHtvgjfKksbnUwor6qlGibGxg/640?from=appmsg&watermark=1#imgIndex=4)图表方式一：Go Install（最快）# 仅 CLI（无 Web UI）goinstallgithub.com/xoai/sage-wiki/cmd/sage-wiki@latest需要 Go 1.21+。这种方式不包含 Web UI，但 CLI、TUI、MCP 功能完整。方式二：Docker（推荐生产环境）# 拉取镜像dockerpullghcr.io/xoai/sage-wiki:latest# 运行dockerrun-d-p3333:3333\-v./my-wiki:/wiki\-eGEMINI_API_KEY=your-key-here\ghcr.io/xoai/sage-wiki支持linux/amd64和linux/arm64。可以跑在 VPS、NAS、树莓派上，从任何设备通过浏览器访问。方式三：源码编译（含 Web UI）gitclonehttps://github.com/xoai/sage-wiki.git&&cdsage-wikicdweb&&npminstall&&npmrunbuild&&cd..gobuild-tagswebui-osage-wiki./cmd/sage-wiki/需要 Node.js（构建前端资源）。Web UI 基于 Preact + Tailwind CSS，通过go:embed嵌入二进制，额外增加约 1.2 MB。第一次编译mkdirmy-wiki&&cdmy-wikisage-wikiinit# 把你的素材丢进 raw/ 目录cp~/papers/*.pdfraw/papers/cp~/notes/*.mdraw/notes/# 编辑 config.yaml，配置 API key 和模型# 然后编译sage-wikicompile# 搜索试试sage-wikisearch"attention mechanism"# 问个问题sage-wikiquery"Flash Attention 如何优化内存？"配置 LLM Providersage-wiki 支持多种 LLM 提供商，配置方式统一：api:provider: gemini# anthropic / openai / gemini / ollama / qwenapi_key: ${GEMINI_API_KEY}models:summarize: gemini-3-flash-preview# 高频任务用便宜模型extract: gemini-3-flash-previewwrite: gemini-3-flash-preview# 写作可以用更好的模型query: gemini-3-flash-preview支持环境变量展开（${VAR_NAME}），也支持 OpenRouter 等兼容接口：api:provider: openai-compatiblebase_url: https://openrouter.ai/api/v1api_key: ${OPENROUTER_API_KEY}国内用户可以直接用阿里云 DashScope（通义千问）：api:provider: qwenapi_key: ${DASHSCOPE_API_KEY}最佳实践大规模知识库的分层策略如果你的知识库超过 1 万文档，不要用默认的default_tier: 3（全量编译）。推荐策略：compiler:default_tier: 1# 默认只索引+嵌入tier_defaults:json: 0# 结构化数据只索引yaml: 0lock: 0md: 1# 文本索引+嵌入go: 1# 代码索引+嵌入auto_promote: true# 被搜索命中时自动提升auto_demote: true# 90 天不活跃自动降级这样 10 万文档可以在几小时内完成初始索引，然后按需编译真正需要的内容。Obsidian Vault 集成如果你已经有一个 Obsidian vault，不需要迁移——sage-wiki 支持"覆盖模式"：cd~/Documents/MyVaultsage-wikiinit--vault# 编辑 config.yaml 设置要忽略的目录# ignore:#   - Daily Notes#   - Personalsage-wikicompile--watch# 监听变化，自动编译编译产物默认输出到_wiki/目录，在 Obsidian 中可以直接浏览，[[wikilinks]]可点击跳转。Agent Skill 文件sage-wiki 有 17 个 MCP 工具，但 Agent 不会主动使用它们——除非有东西告诉它"什么时候该查 wiki"。Skill 文件就是这个桥梁：# 为 Claude Code 生成 skill 文件sage-wikiskillrefresh--targetclaude-code# 支持的 Agent：claude-code, cursor, windsurf, gemini, generic这会在你的CLAUDE.md（或.cursorrules）中追加一段行为指令，包含项目特定的触发条件、捕获指南和查询示例。成本优化三板斧![image](https://mmbiz.qpic.cn/sz_mmbiz_png/dLBesCqkPI0d8csF2u31ufNjNxdicNU6cAAdlcKy7roZ4lgMFiaaF1shYkU3DF7wNIk3IpboUFNw1TINy6jVMaibzIe9KTzK99mm1GAiaRddbPE/640?from=appmsg&watermark=1#imgIndex=5)柱状图：四种优化策略下编译 1000 篇文档的成本对比，从无优化的 $150 逐步降到分层编译的 $151. Prompt 缓存（默认开启）同一编译 pass 内复用系统提示词。Anthropic 和 Gemini 显式缓存，OpenAI 自动缓存。节省 50-90% 输入 token。2. Batch API（50% 折扣）sage-wikicompile--batch# 提交批处理，退出# ... 等待完成 ...sage-wikicompile# 轮询状态，取回结果Anthropic 和 OpenAI 的 Batch API 提供 50% 成本折扣，代价是异步等待。3. 分层编译（最大节省）只对真正需要的文档做完整编译。配合auto_promote，系统会自动识别高价值文档。自托管部署sage-wiki 可以跑在服务器上——VPS、NAS、树莓派、家庭实验室——从任何设备通过浏览器访问。配合 Syncthing 做文件同步，在笔记本上添加源文件，自动同步到服务器编译，然后从手机浏览 wiki。# Docker Compose 示例dockerrun-d\--namesage-wiki\-p3333:3333\-v/data/wiki:/wiki\-eGEMINI_API_KEY=...\--restartunless-stopped\ghcr.io/xoai/sage-wiki:latest结语Sage Wiki 代表了个人知识管理的一个新方向：不是让人去维护知识库，而是让 LLM 来做这件事。它的核心价值在于三点：编译而非检索——知识在写入时就被理解、关联、结构化，而不是在查询时临时拼凑分层而非全量——10 万文档不需要全部经过昂贵的 LLM 处理，按需编译才是正确的扩展策略开放而非封闭——纯 Markdown 输出、MCP 接口、Obsidian 兼容，不锁定任何生态如果你是一个重度知识消费者——每天阅读大量论文、文章、代码——sage-wiki 值得一试。初始设置大约 10 分钟，第一次编译的"啊哈时刻"会让你意识到，之前那些废弃的知识管理系统，问题从来不在你的自律，而在工具没有承担它该承担的工作。项目地址：https://github.com/xoai/sage-wiki参考链接[1] Sage Wiki GitHub 仓库；https://github.com/xoai/sage-wiki[2] Karpathy LLM Wiki Gist；https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f[3] The Complete Guide to AI-Maintained Knowledge Bases；https://blog.starmorph.com/blog/karpathy-llm-wiki-knowledge-base-guide[4] Karpathy's LLM Wiki: 95% Less Token Use Than RAG；https://www.mindstudio.ai/blog/llm-wiki-vs-rag-markdown-knowledge-base-comparison[5] I Built Karpathy's LLM Wiki for My Day Job；https://tomnguyenit.medium.com/i-built-karpathys-llm-wiki-for-my-day-job-here-s-what-actually-works-0d4ec6d1e433[6] From RAG to LLM Wiki: What Karpathy's Idea Means；https://denser.ai/blog/llm-wiki-karpathy-knowledge-base/[7] A Practical Guide to Building an Effective Second Brain with AI；https://open.substack.com/pub/faafospecialist/p/a-practical-guide-to-building-an[8] DeepWiki vs Traditional Documentation；https://codersera.com/blog/deepwiki-vs-traditional-documentation-developer-decision-framework

2026 年 4 月 4 日，Andrej Karpathy 在 X 上发了一条帖子，说他不再主要用 LLM 写代码了——而是用它来构建个人知识库。帖子获得了 1600 万次浏览，随后发布的 GitHub Gist 在几天内拿到 5000+ star。

这条帖子戳中了一个痛点：每个知识工作者都有一堆废弃的知识管理系统。Notion 数据库三个月没更新，Obsidian 图谱长满了灰，浏览器书签夹里 500 个链接没有一个写了摘要。问题不在工具，在维护成本。

Karpathy 的洞察很简单：LLM 天生擅长这种"苦力活"——阅读文档、提取概念、生成摘要、建立交叉引用、更新索引。人类负责策展输入，LLM 负责其余一切。

但 Karpathy 发布的只是一个"模式"（pattern），不是产品。你需要自己搭目录结构，自己写 CLAUDE.md schema，自己处理各种边界情况。对于想直接用起来的人，这个门槛不低。

Sage Wiki 就是把这个模式工程化的产物。一个 Go 编写的单二进制文件，零 CGO 依赖，支持 12+ 种源文件格式，能扩展到 10 万+ 文档，内置混合搜索、本体图谱、MCP 集成和 Web UI。

![image](https://mmbiz.qpic.cn/mmbiz_png/dLBesCqkPI1CsoZAP6ox9Ha2PhNdZibEDGSYbQw7c1UWJ3nz91paKADia4mO3vBDubpwmyibiaEqL0F6JAY1xTwiboVCsmFnAV3OWqGFyIv5QHiaI/640?from=appmsg&watermark=1#imgIndex=0)

raw/ 原始素材

## 什么是 LLM Wiki 模式

传统知识管理有三步：收集（容易）、组织（困难）、维护（规模化后几乎不可能）。每加入一篇新文章，你需要阅读它、写摘要、链接到已有概念、更新相关页面、检查与现有知识的矛盾。没人能持续做到这些。

LLM Wiki 模式用一个编译器类比来解决这个问题：

和 RAG 的区别在哪？RAG 是"每次查询时实时检索原始文档"，LLM Wiki 是"提前编译好，查询时直接读编译产物"。就像你不会每次运行程序都重新编译源码一样。

实际效果：Karpathy 的单主题 Wiki 在没有他直接编写任何内容的情况下，增长到了约 100 篇文章、40 万字——比大多数博士论文还长。

为什么比 RAG 更适合个人知识库？

有测试表明，对于小型聚焦知识库，LLM Wiki 模式相比朴素 RAG 可以减少高达 95% 的 token 消耗。

## Sage Wiki 的技术方案

Sage Wiki 不是简单地把 Karpathy 的 Gist 包装成 CLI。它在几个关键维度上做了工程化突破。

### 分层编译：10 万文档不是梦

这是 sage-wiki 最有意思的设计。不是所有文档都需要完整的 LLM 编译——大部分时候你只需要能搜到它就行。

![image](https://mmbiz.qpic.cn/sz_mmbiz_png/dLBesCqkPI11AgQcic8Iwg3mluV1B9VYPrDCvy7pfQJNGaB4icPSzOETbQ15TU8ad42iaicBaUFZTRibaE4VBKvgIse2wuBnqsFsuGmoa4xIcWibE/640?from=appmsg&watermark=1#imgIndex=1)

图表

关键机制：

实际效果：一个 10 万文档的知识库，全量索引（Tier 1）只需约 5.5 小时。而传统的全量 Tier 3 编译可能需要数周。

### 混合搜索管线

sage-wiki 的搜索不是简单的关键词匹配或向量相似度，而是一个多阶段管线：

![image](https://mmbiz.qpic.cn/sz_mmbiz_png/dLBesCqkPI3EyOXHWtPhesDWfia2c8Ot2l8D79fmx2fn8W4Ph7nxYvAniaibJvT0THJL9ERRZp1LaQ0yUCO6KGAWmjKRf39ibbN6IuMEZib5ETMM/640?from=appmsg&watermark=1#imgIndex=2)

图表

四个图谱扩展信号：

性能数据（来自 1107 个源文件、2832 个 wiki 文件的真实测试）：

### 本体图谱

sage-wiki 不只是生成独立的文章——它构建了一个类型化的实体-关系图谱。8 种内置关系类型：implements、extends、optimizes、contradicts、cites、prerequisite_of、trades_off、derived_from。

关系提取基于段落级关键词共现：一个关键词必须与[[wikilink]]在同一段落或标题块中共现才会建立边。这避免了跨段落的虚假关联。

你还可以自定义关系类型，甚至限制关系的源/目标实体类型：

ontology:relation_types:-name: curated_bysynonyms: ["curatedby","organizedby"]valid_sources: [exhibition,program]valid_targets: [artist]

ontology:relation_types:-name: curated_bysynonyms: ["curatedby","organizedby"]valid_sources: [exhibition,program]valid_targets: [artist]

### MCP 集成：17 个工具

sage-wiki 作为 MCP 服务器运行，提供 17 个工具（6 读、9 写、2 复合）。这意味着任何支持 MCP 的 AI Agent 都可以直接操作你的知识库：

配置极简，在.mcp.json中加一行：

{"mcpServers": {"sage-wiki": {"command":"sage-wiki","args": ["serve","--project","/path/to/wiki"]}}}

{"mcpServers": {"sage-wiki": {"command":"sage-wiki","args": ["serve","--project","/path/to/wiki"]}}}

## 横向对比：Sage Wiki vs 同类方案

Karpathy 的帖子发出后一周内，社区涌现了大量实现。它们各有侧重，适合不同场景。

![image](https://mmbiz.qpic.cn/mmbiz_png/dLBesCqkPI2Fde6zDLjtH2OMibMu9jibwD49wY2DSF1onNtrSwvJAO0j1vbZIuia2KnT7sFzcEjo0lJHVHuvzdBibjfLBkcjjU0Jk9EV1qBeHGc/640?from=appmsg&watermark=1#imgIndex=3)

雷达图：五个维度对比四种知识库方案，sage-wiki 在扩展性和搜索质量维度接近满分，手动模式在易用性上最低

什么时候选 sage-wiki？

什么时候不需要 sage-wiki？

## 安装与快速上手

sage-wiki 提供三种安装方式，覆盖从"试一下"到"生产部署"的全部场景。

![image](https://mmbiz.qpic.cn/mmbiz_png/dLBesCqkPI0MCcAuDm2iawun8iad6VHwj1KfN91ZrQwSu5fwMjCiaZApVP6dW89m0PT2cefHhzUhPCuzfZo90BmHtvgjfKksbnUwor6qlGibGxg/640?from=appmsg&watermark=1#imgIndex=4)

图表

### 方式一：Go Install（最快）

# 仅 CLI（无 Web UI）goinstallgithub.com/xoai/sage-wiki/cmd/sage-wiki@latest

# 仅 CLI（无 Web UI）goinstallgithub.com/xoai/sage-wiki/cmd/sage-wiki@latest

需要 Go 1.21+。这种方式不包含 Web UI，但 CLI、TUI、MCP 功能完整。

### 方式二：Docker（推荐生产环境）

# 拉取镜像dockerpullghcr.io/xoai/sage-wiki:latest# 运行dockerrun-d-p3333:3333\-v./my-wiki:/wiki\-eGEMINI_API_KEY=your-key-here\ghcr.io/xoai/sage-wiki

# 拉取镜像dockerpullghcr.io/xoai/sage-wiki:latest# 运行dockerrun-d-p3333:3333\-v./my-wiki:/wiki\-eGEMINI_API_KEY=your-key-here\ghcr.io/xoai/sage-wiki

支持linux/amd64和linux/arm64。可以跑在 VPS、NAS、树莓派上，从任何设备通过浏览器访问。

### 方式三：源码编译（含 Web UI）

gitclonehttps://github.com/xoai/sage-wiki.git&&cdsage-wikicdweb&&npminstall&&npmrunbuild&&cd..gobuild-tagswebui-osage-wiki./cmd/sage-wiki/

gitclonehttps://github.com/xoai/sage-wiki.git&&cdsage-wikicdweb&&npminstall&&npmrunbuild&&cd..gobuild-tagswebui-osage-wiki./cmd/sage-wiki/

需要 Node.js（构建前端资源）。Web UI 基于 Preact + Tailwind CSS，通过go:embed嵌入二进制，额外增加约 1.2 MB。

### 第一次编译

mkdirmy-wiki&&cdmy-wikisage-wikiinit# 把你的素材丢进 raw/ 目录cp~/papers/*.pdfraw/papers/cp~/notes/*.mdraw/notes/# 编辑 config.yaml，配置 API key 和模型# 然后编译sage-wikicompile# 搜索试试sage-wikisearch"attention mechanism"# 问个问题sage-wikiquery"Flash Attention 如何优化内存？"

mkdirmy-wiki&&cdmy-wikisage-wikiinit# 把你的素材丢进 raw/ 目录cp~/papers/*.pdfraw/papers/cp~/notes/*.mdraw/notes/# 编辑 config.yaml，配置 API key 和模型# 然后编译sage-wikicompile# 搜索试试sage-wikisearch"attention mechanism"# 问个问题sage-wikiquery"Flash Attention 如何优化内存？"

### 配置 LLM Provider

sage-wiki 支持多种 LLM 提供商，配置方式统一：

api:provider: gemini# anthropic / openai / gemini / ollama / qwenapi_key: ${GEMINI_API_KEY}models:summarize: gemini-3-flash-preview# 高频任务用便宜模型extract: gemini-3-flash-previewwrite: gemini-3-flash-preview# 写作可以用更好的模型query: gemini-3-flash-preview

api:provider: gemini# anthropic / openai / gemini / ollama / qwenapi_key: ${GEMINI_API_KEY}models:summarize: gemini-3-flash-preview# 高频任务用便宜模型extract: gemini-3-flash-previewwrite: gemini-3-flash-preview# 写作可以用更好的模型query: gemini-3-flash-preview

支持环境变量展开（${VAR_NAME}），也支持 OpenRouter 等兼容接口：

api:provider: openai-compatiblebase_url: https://openrouter.ai/api/v1api_key: ${OPENROUTER_API_KEY}

api:provider: openai-compatiblebase_url: https://openrouter.ai/api/v1api_key: ${OPENROUTER_API_KEY}

国内用户可以直接用阿里云 DashScope（通义千问）：

api:provider: qwenapi_key: ${DASHSCOPE_API_KEY}

api:provider: qwenapi_key: ${DASHSCOPE_API_KEY}

## 最佳实践

### 大规模知识库的分层策略

如果你的知识库超过 1 万文档，不要用默认的default_tier: 3（全量编译）。推荐策略：

compiler:default_tier: 1# 默认只索引+嵌入tier_defaults:json: 0# 结构化数据只索引yaml: 0lock: 0md: 1# 文本索引+嵌入go: 1# 代码索引+嵌入auto_promote: true# 被搜索命中时自动提升auto_demote: true# 90 天不活跃自动降级

compiler:default_tier: 1# 默认只索引+嵌入tier_defaults:json: 0# 结构化数据只索引yaml: 0lock: 0md: 1# 文本索引+嵌入go: 1# 代码索引+嵌入auto_promote: true# 被搜索命中时自动提升auto_demote: true# 90 天不活跃自动降级

这样 10 万文档可以在几小时内完成初始索引，然后按需编译真正需要的内容。

### Obsidian Vault 集成

如果你已经有一个 Obsidian vault，不需要迁移——sage-wiki 支持"覆盖模式"：

cd~/Documents/MyVaultsage-wikiinit--vault# 编辑 config.yaml 设置要忽略的目录# ignore:#   - Daily Notes#   - Personalsage-wikicompile--watch# 监听变化，自动编译

cd~/Documents/MyVaultsage-wikiinit--vault# 编辑 config.yaml 设置要忽略的目录# ignore:#   - Daily Notes#   - Personalsage-wikicompile--watch# 监听变化，自动编译

编译产物默认输出到_wiki/目录，在 Obsidian 中可以直接浏览，[[wikilinks]]可点击跳转。

### Agent Skill 文件

sage-wiki 有 17 个 MCP 工具，但 Agent 不会主动使用它们——除非有东西告诉它"什么时候该查 wiki"。Skill 文件就是这个桥梁：

# 为 Claude Code 生成 skill 文件sage-wikiskillrefresh--targetclaude-code# 支持的 Agent：claude-code, cursor, windsurf, gemini, generic

# 为 Claude Code 生成 skill 文件sage-wikiskillrefresh--targetclaude-code# 支持的 Agent：claude-code, cursor, windsurf, gemini, generic

这会在你的CLAUDE.md（或.cursorrules）中追加一段行为指令，包含项目特定的触发条件、捕获指南和查询示例。

### 成本优化三板斧

![image](https://mmbiz.qpic.cn/sz_mmbiz_png/dLBesCqkPI0d8csF2u31ufNjNxdicNU6cAAdlcKy7roZ4lgMFiaaF1shYkU3DF7wNIk3IpboUFNw1TINy6jVMaibzIe9KTzK99mm1GAiaRddbPE/640?from=appmsg&watermark=1#imgIndex=5)

柱状图：四种优化策略下编译 1000 篇文档的成本对比，从无优化的 $150 逐步降到分层编译的 $15

1. Prompt 缓存（默认开启）

同一编译 pass 内复用系统提示词。Anthropic 和 Gemini 显式缓存，OpenAI 自动缓存。节省 50-90% 输入 token。

2. Batch API（50% 折扣）

sage-wikicompile--batch# 提交批处理，退出# ... 等待完成 ...sage-wikicompile# 轮询状态，取回结果

sage-wikicompile--batch# 提交批处理，退出# ... 等待完成 ...sage-wikicompile# 轮询状态，取回结果

Anthropic 和 OpenAI 的 Batch API 提供 50% 成本折扣，代价是异步等待。

3. 分层编译（最大节省）

只对真正需要的文档做完整编译。配合auto_promote，系统会自动识别高价值文档。

### 自托管部署

sage-wiki 可以跑在服务器上——VPS、NAS、树莓派、家庭实验室——从任何设备通过浏览器访问。配合 Syncthing 做文件同步，在笔记本上添加源文件，自动同步到服务器编译，然后从手机浏览 wiki。

# Docker Compose 示例dockerrun-d\--namesage-wiki\-p3333:3333\-v/data/wiki:/wiki\-eGEMINI_API_KEY=...\--restartunless-stopped\ghcr.io/xoai/sage-wiki:latest

# Docker Compose 示例dockerrun-d\--namesage-wiki\-p3333:3333\-v/data/wiki:/wiki\-eGEMINI_API_KEY=...\--restartunless-stopped\ghcr.io/xoai/sage-wiki:latest

## 结语

Sage Wiki 代表了个人知识管理的一个新方向：不是让人去维护知识库，而是让 LLM 来做这件事。

它的核心价值在于三点：

如果你是一个重度知识消费者——每天阅读大量论文、文章、代码——sage-wiki 值得一试。初始设置大约 10 分钟，第一次编译的"啊哈时刻"会让你意识到，之前那些废弃的知识管理系统，问题从来不在你的自律，而在工具没有承担它该承担的工作。

项目地址：https://github.com/xoai/sage-wiki

参考链接

[1] Sage Wiki GitHub 仓库；https://github.com/xoai/sage-wiki

[2] Karpathy LLM Wiki Gist；https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f

[3] The Complete Guide to AI-Maintained Knowledge Bases；https://blog.starmorph.com/blog/karpathy-llm-wiki-knowledge-base-guide

[4] Karpathy's LLM Wiki: 95% Less Token Use Than RAG；https://www.mindstudio.ai/blog/llm-wiki-vs-rag-markdown-knowledge-base-comparison

[5] I Built Karpathy's LLM Wiki for My Day Job；https://tomnguyenit.medium.com/i-built-karpathys-llm-wiki-for-my-day-job-here-s-what-actually-works-0d4ec6d1e433

[6] From RAG to LLM Wiki: What Karpathy's Idea Means；https://denser.ai/blog/llm-wiki-karpathy-knowledge-base/

[7] A Practical Guide to Building an Effective Second Brain with AI；https://open.substack.com/pub/faafospecialist/p/a-practical-guide-to-building-an

[8] DeepWiki vs Traditional Documentation；https://codersera.com/blog/deepwiki-vs-traditional-documentation-developer-decision-framework