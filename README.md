# Dev Digest

每日精选 10 条全球技术资讯，由 Claude 自动生成，中 / 日 / 英三语独立编辑。每天东京时间 07:00 更新。

- 🌐 **Live**: https://jerryni.github.io/dev-digest/
- 📡 **Sources**: Hacker News · GitHub Trending · Simon Willison · V2EX · Zenn · Publickey · Anthropic / OpenAI / DeepMind 官方博客
- 🤖 **Generation**: Claude (via Cowork scheduled task, daily at 07:00 JST)
- 🎨 **Tech stack**: Hugo + PaperMod + GitHub Pages + GitHub Actions

## Structure

```
dev-digest/
├── content/
│   ├── posts/
│   │   └── YYYY-MM-DD/
│   │       ├── index.zh.md      # 中文版
│   │       ├── index.ja.md      # 日本語版
│   │       └── index.en.md      # English
│   ├── _index.*.md              # home pages
│   ├── archives.*.md            # archive pages
│   └── search.*.md              # search pages
├── scripts/
│   └── daily-digest.md          # generation playbook (read by the scheduled task)
├── .github/workflows/deploy.yml # Hugo build & Pages deploy
├── hugo.toml                    # Hugo config with trilingual setup
└── SETUP.md                     # one-time setup guide
```

## First-time setup

See [SETUP.md](./SETUP.md).

## Philosophy

The three language versions are **independently written**, not translated. Same news items, but framed for each culture's context:

- **中文版** speaks to Chinese developers globally (包括北美/日本华人)
- **日本語版** speaks to Japanese engineers in the context of 日本企業 realities
- **English** speaks to the global dev audience

This makes the blog useful as a daily habit and as a signal of cross-cultural perspective.

## License

Content: CC BY 4.0. Code: MIT.
