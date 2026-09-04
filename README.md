# Codex Markdown Preview

A [Codex CLI hook](https://learn.chatgpt.com/docs/hooks) that opens completed responses in a browser with better Markdown rendering, including LaTeX math via MathML. It keeps each session's prompts and responses on one page with a turn index.

Requires Python 3.9+ and [Pandoc](https://pandoc.org/) on `PATH`.

Add `hooks = true` to your existing `[features]` table in `~/.codex/config.toml`, then add the hooks below and replace `/absolute/path`:

```toml
[features]
hooks = true

[[hooks.UserPromptSubmit]]
[[hooks.UserPromptSubmit.hooks]]
type = "command"
command = 'python3 /absolute/path/codex-markdown-preview/markdown-preview.py'
timeout = 3

[[hooks.Stop]]
[[hooks.Stop.hooks]]
type = "command"
command = 'python3 /absolute/path/codex-markdown-preview/markdown-preview.py'
async = true
timeout = 30

[[hooks.SessionEnd]]
[[hooks.SessionEnd.hooks]]
type = "command"
command = 'python3 /absolute/path/codex-markdown-preview/markdown-preview.py'
timeout = 3
```

Restart Codex and approve the hooks when prompted. Run `python3 markdown-preview.py --check` to verify the installation.
