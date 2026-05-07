# Content Fetch Tools

这里放的是被 GitHub Actions 直接调用的抓取脚本，不是 Codex skill。

## 文件

- `fetch_weixin.py`：抓取微信公众号文章并输出 Markdown
- `fetch_feishu.py`：抓取飞书文档并输出 Markdown

## 当前用途

`Fetch WeChat Article` workflow 会直接调用：

```bash
python tools/content-fetch/fetch_weixin.py "<weixin_url>" --output-dir articles
```

## 依赖

### WeChat 抓取

- Python 3.8+
- `playwright`
- `beautifulsoup4`
- `lxml`

安装示例：

```bash
pip install playwright beautifulsoup4 lxml
playwright install chromium
```

### Feishu 抓取

- Python 3.8+
- `requests`
- 环境变量：`FEISHU_APP_ID`、`FEISHU_APP_SECRET`

## 输出

脚本默认输出 Markdown，可带 YAML frontmatter。

`fetch_weixin.py` 额外支持：

- `--json`
- `--output-dir <DIR>`
