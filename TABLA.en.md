# Claude Code outside VS Code: comparison table

As of Nov 1, 2026, with Claude Code 2.1.316. Official data only: every row links to the page that backs it. Nothing was installed to build it; Xcode and Visual Studio cannot be tested on Linux.

| Editor | Who maintains the integration | How to install it | Account and billing | Claude Code features | Source |
| --- | --- | --- | --- | --- | --- |
| VS Code | Anthropic | Extension `anthropic.claude-code` (Visual Studio Marketplace or Open VSX) | Your Claude plan or Console | Extension with visual review; some features differ from the CLI | [Anthropic](https://code.claude.com/docs/en/vs-code) |
| Cursor and other VS Code forks (Devin Desktop) | Anthropic | The same extension, from Open VSX; check publisher and version | Your Claude plan or Console | Same as VS Code | [Anthropic](https://code.claude.com/docs/en/vs-code) |
| IntelliJ, PyCharm, WebStorm, Android Studio, GoLand, PhpStorm | Anthropic | "Claude Code [Beta]" plugin from the Marketplace + the CLI on the PATH | Any paid Claude plan or Console, no API key | All of them: the plugin runs the CLI | [Anthropic](https://code.claude.com/docs/en/jetbrains), [Marketplace](https://plugins.jetbrains.com/plugin/27310-claude-code-beta-) |
| JetBrains AI Assistant 2026.2 (Claude Agent) | JetBrains (over ACP) | Inside the AI Assistant chat | JetBrains AI subscription, your API key (BYOK) or Anthropic Console; Pro and Max are not mentioned | You lose the Claude Code terminal | [JetBrains](https://www.jetbrains.com/help/ai-assistant/activate-agents.html) |
| Xcode 26.3 (Claude Agent) | Apple, with the Claude Agent SDK | Settings → Intelligence → Agents → "Get" and "Install" | The agent's Account row | Subagents, background tasks and plugins; `/skill` may fail | [Apple](https://developer.apple.com/documentation/xcode/setting-up-coding-intelligence), [Anthropic](https://www.anthropic.com/news/apple-xcode-claude-agent-sdk) |
| Xcode 26.3 (CLI over MCP) | Apple exposes Xcode; you use the CLI | `claude mcp add --transport stdio xcode -- xcrun mcpbridge` | Your CLI's | All of them (it is the CLI) plus the Xcode tools | [Apple](https://developer.apple.com/documentation/xcode/giving-external-agents-access-to-xcode) |
| Zed | Zed (External Agent over ACP) | Claude Agent from the ACP Registry | Its own authentication, chosen with `/login` | Reads CLAUDE.md; Zed's MCP servers can be forwarded | [Zed](https://zed.dev/docs/ai/external-agents) |
| Visual Studio 2022/2026 | Nobody: there is no official extension | The CLI in View → Terminal | Your CLI's | All of them (it is the CLI) | [Microsoft](https://learn.microsoft.com/en-us/visualstudio/releases/2026/release-notes) |
| Neovim | Nobody: community plugins only | `:terminal claude` or a reviewed plugin | Your CLI's | All of them (it is the CLI); vim mode in `/config` | [Anthropic](https://code.claude.com/docs/en/interactive-mode) |

## Useful commands

```bash
# JetBrains: the plugin needs the CLI on the PATH
claude --version
which claude                 # path for "Claude command" if the IDE cannot find it
/ide                         # from an external terminal, already inside Claude Code

# Xcode 26.3: first enable "Allow external agents to use Xcode tools" (Settings → Intelligence → Model Context Protocol)
claude mcp add --transport stdio xcode -- xcrun mcpbridge
claude mcp list

# Visual Studio: View → Terminal, in the solution folder
claude

# Neovim
:terminal claude

# What Claude Code loaded (memory, skills, account, model, MCP)
/context
/status
/mcp
```

## Security

- There is no official extension for Visual Studio and no official plugin for Neovim: if you install a community one, review the code, who publishes it and which permissions it asks for.
- In Cursor and other forks, check that the publisher is Anthropic and the version: on October 29-30, 2026 Open VSX served tampered copies (2.1.312 and 2.1.313, now removed).

## Official sources

- https://code.claude.com/docs/en/jetbrains
- https://code.claude.com/docs/es/jetbrains
- https://code.claude.com/docs/en/vs-code
- https://code.claude.com/docs/en/platforms
- https://code.claude.com/docs/en/interactive-mode
- https://plugins.jetbrains.com/plugin/27310-claude-code-beta-
- https://www.jetbrains.com/help/ai-assistant/activate-agents.html
- https://developer.apple.com/documentation/xcode-release-notes/xcode-26_3-release-notes
- https://developer.apple.com/documentation/xcode/setting-up-coding-intelligence
- https://developer.apple.com/documentation/xcode/giving-external-agents-access-to-xcode
- https://www.anthropic.com/news/apple-xcode-claude-agent-sdk
- https://zed.dev/docs/ai/external-agents
- https://learn.microsoft.com/en-us/visualstudio/releases/2026/release-notes
