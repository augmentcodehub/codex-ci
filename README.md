# Codex CI - 微信公众号文章抓取

通过 GitHub Actions + Codex CLI + Skills 抓取微信公众号文章并转为 Markdown。

## 项目结构

```
markdown-proxy/
├── SKILL.md                    # Codex skill 定义
└── scripts/
    ├── fetch_weixin.py         # 公众号抓取（Playwright）
    └── fetch_feishu.py         # 飞书文档抓取
.github/
└── workflows/
    └── fetch-weixin.yml        # GitHub Actions 工作流
```

## 使用方法

1. 推送到 GitHub
2. 配置 Secrets：
   - `CODEX_API_KEY` — 中转站 API key
   - `CODEX_BASE_URL` — 中转站地址（如 `https://your-proxy.com/v1`）
3. Actions → "Fetch WeChat Article" → Run workflow → 输入公众号 URL
4. 完成后在 Artifacts 下载 Markdown 文件
