# Optional Codex Cloud

Codex Cloud is supported as a separate workflow where tasks run in isolated cloud environments connected to GitHub.

It is not the same as the ChatGPT mobile Remote workflow:

```text
Mobile Remote
  -> controls Codex running on your laptop, devbox, or remote machine

Codex Cloud
  -> delegates a task to an OpenAI-managed cloud sandbox
```

Do not require a Codex Cloud environment when the selected execution mode is `codex-local-remote` or `codex-vscode`.

Use cloud only when the user explicitly chooses background cloud delegation or cannot keep a development host available.
