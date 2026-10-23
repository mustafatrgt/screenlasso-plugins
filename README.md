# ScreenLasso plugins

Plugins that let Claude and Codex convert and optimize images with ScreenLasso, a Mac app from the Mac App Store. Everything runs on your Mac.

Before you install, open ScreenLasso and turn on **Settings › AI Agents › Let AI agents use ScreenLasso**. The key shown there is what the plugin asks for.

## Claude Code

```bash
claude plugin marketplace add mustafatrgt/screenlasso-plugins
claude plugin install screenlasso@screenlasso
```

Claude Code asks for the key when the plugin is enabled.

## Claude Desktop

In ScreenLasso › Settings › AI Agents, choose **Install in Claude Desktop**. Claude Desktop opens the ScreenLasso extension and asks for the key, which ScreenLasso has copied for you.

## Codex

```bash
codex plugin marketplace add mustafatrgt/screenlasso-plugins
```

Then install ScreenLasso from the plugins list (`/plugins` in Codex) and enter the key when Codex asks. You can also skip the plugin: ScreenLasso › Settings › AI Agents › Codex › **Copy Configuration** gives the lines for `~/.codex/config.toml`.

## Privacy

The plugins talk only to ScreenLasso on 127.0.0.1. Images never leave your Mac.
