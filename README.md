# Codex CI - 抓取与改写工作流

通过 GitHub Actions 抓取微信公众号文章为 Markdown，并可选用 Codex + writer skills 将素材改写为不同风格的文章。

## 项目结构

```
markdown-proxy/
├── SKILL.md                    # URL 转 Markdown skill
└── scripts/
    ├── fetch_weixin.py         # 公众号抓取（Playwright）
    └── fetch_feishu.py         # 飞书文档抓取
lu-xun-writer/                  # 鲁迅风格改写 skill
ma-sanli-writer/                # 马三立风格改写 skill
xu-zhimo-writer/                # 徐志摩风格改写 skill
.github/
└── workflows/
    ├── fetch-weixin.yml        # 抓取公众号文章
    └── rewrite-article.yml     # 用 Codex 改写已有 Markdown
```

## 使用方法

1. 推送到 GitHub
2. 配置 Secrets：
   - `CODEX_API_KEY` — 中转站 API key
   - `CODEX_BASE_URL` — 中转站地址（如 `https://your-proxy.com/v1`）
3. 抓取原文：
   - Actions → `Fetch WeChat Article`
   - 输入公众号 URL
   - 运行后文章会提交到仓库 `articles/` 目录
4. 改写文章：
   - Actions → `Rewrite Article`
   - 输入 `source_file`，例如 `articles/你的文章.md`
   - 选择 `style`：`lu-xun` / `ma-sanli` / `xu-zhimo`
   - 运行后改写结果会提交到 `rewritten/` 目录
