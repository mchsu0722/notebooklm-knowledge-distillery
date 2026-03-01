# NotebookLM Knowledge Distillery 🎓

> 🇹🇼 **知識蒸餾器** — 你只要把 YouTube 影片連結或網路文章丟進來，它會自動打開 Google NotebookLM，讓 Gemini AI 幫你分析所有內容，然後產出一份結構完整的 Word 研究報告。不用自己花兩小時看影片、做筆記，4 支影片大概 3-5 分鐘就能搞定。適合做投資研究、技術學習、市場調查，任何需要快速消化大量影片內容的場景都能用。
>
> 🇺🇸 **Knowledge Distillery** — Just drop in YouTube links or article URLs, and it automatically opens Google NotebookLM, lets Gemini AI analyze all the content, and generates a well-structured Word research report. No need to spend hours watching videos and taking notes — 4 videos take about 3-5 minutes. Perfect for investment research, technical learning, market analysis, or any scenario where you need to quickly digest large amounts of video content.

---

---

## 🚀 Quick Start

```bash
uv run scripts/kd.py research \
  --topic "Financial Research" \
  --urls "https://youtube.com/watch?v=xxx,https://youtube.com/watch?v=yyy" \
  --format briefing
```

## 📋 Command Reference

```bash
uv run scripts/kd.py research [OPTIONS]
```

**Required:**
- `--topic TOPIC`: Topic name (used as folder name)
- `--urls URLS`: Comma-separated YouTube/article URLs

**Optional:**
- `--format {briefing|study-guide|blog}`: Report format (default: briefing)
- `--output OUTPUT`: Output directory (default: workspace/{topic}_knowledge_distillery/)
- `--profile PROFILE`: Browser profile (default: openclaw)

## 📂 Output Structure

```
{topic}_knowledge_distillery/
├── README.md                          # Index with NotebookLM link
└── YYYY-MM-DD_{topic}_knowledge_distillery報告.md        # Full structured report
```

## ⚙️ How It Works

1. Opens NotebookLM in browser (automated via OpenClaw)
2. Creates new notebook & batch imports URLs
3. Waits for Gemini AI analysis (~45 seconds)
4. Generates report in selected format
5. Copies and saves report to local folder

## 🔧 Requirements

- [OpenClaw](https://github.com/openclaw/openclaw) with browser automation
- [uv](https://github.com/astral-sh/uv) (Python package runner)
- macOS (uses `pbpaste` for clipboard)
- Google account with NotebookLM access

## 📝 Notes

- Only works with **public** YouTube videos (with transcripts)
- Articles must be publicly accessible (no paywalls)
- NotebookLM has a **50-source limit** per notebook
- 3-4 URLs per research session recommended
- Reports default to Traditional Chinese (customizable via NotebookLM settings)

## 🐛 Troubleshooting

| Issue | Solution |
|-------|----------|
| Import failed | Verify URLs are public and have transcripts |
| Report timeout | Wait longer; check NotebookLM UI manually |
| Clipboard empty | Ensure `pbpaste` works; check if copy button was clicked |

## 📄 License

MIT

---

Built with [OpenClaw](https://github.com/openclaw/openclaw) 🦀
