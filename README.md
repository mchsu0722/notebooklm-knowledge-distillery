# NotebookLM Knowledge Distillery 🎓

> 🇹🇼 **知識蒸餾器** — 把 YouTube 影片和網路文章丟進去，自動幫你整理成結構化的研究報告。用 NotebookLM + Gemini AI，4 支影片只要 3-5 分鐘就搞定，不用自己看完兩小時的內容。
>
> 🇺🇸 **Knowledge Distillery** — Feed YouTube videos and articles in, get structured research reports out. Powered by NotebookLM + Gemini AI. Turn 2+ hours of video into a concise report in just 3-5 minutes.

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
