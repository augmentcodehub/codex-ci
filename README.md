# Codex CI - Content Fetch and Rewrite

这个仓库现在分成两条很清楚的主线：

- `GitHub Actions + Python 脚本` 负责抓取公众号文章并保存为 Markdown
- `GitHub Actions + Codex + writer skills` 负责把已有 Markdown 改写成不同风格的文章

## 目录结构

```text
.github/workflows/
├── fetch-weixin.yml              # 抓取公众号文章到 articles/
└── rewrite-article.yml           # 用 Codex 改写已有 Markdown

articles/                         # 原始抓取文章
rewritten/                        # 改写后的文章

tools/content-fetch/
├── fetch_weixin.py               # 公众号抓取脚本
├── fetch_feishu.py               # 飞书抓取脚本
└── README.md                     # 抓取脚本说明

skills/writers/
├── lu-xun-writer/                # 鲁迅风格改写 skill
├── ma-sanli-writer/              # 马三立风格改写 skill
└── xu-zhimo-writer/              # 徐志摩风格改写 skill
```

## 当前工作方式

### 1. 抓取公众号文章

运行 `Fetch WeChat Article` workflow。

输入：

- `url`: 公众号文章链接

执行方式：

- GitHub Action 直接调用 `tools/content-fetch/fetch_weixin.py`
- 不再通过 `markdown-proxy` skill 抓取
- 成功后文章会提交到 `articles/`

### 2. 改写已有 Markdown

运行 `Rewrite Article` workflow。

输入：

- `source_file`: 待改写的 Markdown 文件，例如 `articles/xxx.md`
- `style`: `lu-xun` / `ma-sanli` / `xu-zhimo`

执行方式：

- GitHub Action 安装 Codex CLI
- 将所选 writer skill 复制到 `~/.codex/skills/`
- 调用 Codex 读取源 Markdown 并输出改写稿
- 成功后文章会提交到 `rewritten/`

## Secrets

需要在 GitHub 仓库里配置：

- `CODEX_API_KEY`
- `CODEX_BASE_URL`

其中：

- 抓取 workflow 本身不依赖 Codex
- 改写 workflow 依赖 Codex provider 配置

## 说明

- `tools/content-fetch/` 是脚本工具目录，不再作为 Codex skill 使用
- `skills/writers/` 才是当前真正参与 Codex 改写的 skills
- 仓库里如果后面继续扩展风格，建议继续放到 `skills/writers/` 下
