# Claude Code fuera de VS Code: tabla comparativa

Situación a 1-nov-2026, con Claude Code 2.1.316. Solo datos oficiales: cada fila enlaza a la página que la respalda. No se instaló nada para hacerla; Xcode y Visual Studio no se pueden probar en Linux.

| Editor | Quién mantiene la integración | Cómo se instala | Cuenta y facturación | Funciones de Claude Code | Fuente |
| --- | --- | --- | --- | --- | --- |
| VS Code | Anthropic | Extensión `anthropic.claude-code` (Visual Studio Marketplace u Open VSX) | Tu plan de Claude o Console | Extensión con revisión visual; algunas funciones cambian respecto a la CLI | [Anthropic](https://code.claude.com/docs/en/vs-code) |
| Cursor y otros forks de VS Code (Devin Desktop) | Anthropic | La misma extensión, desde Open VSX; comprueba publicador y versión | Tu plan de Claude o Console | Como en VS Code | [Anthropic](https://code.claude.com/docs/en/vs-code) |
| IntelliJ, PyCharm, WebStorm, Android Studio, GoLand, PhpStorm | Anthropic | Plugin «Claude Code [Beta]» del Marketplace + la CLI en el PATH | Cualquier plan de pago de Claude o Console, sin clave de API | Todas: el plugin ejecuta la CLI | [Anthropic](https://code.claude.com/docs/es/jetbrains), [Marketplace](https://plugins.jetbrains.com/plugin/27310-claude-code-beta-) |
| JetBrains AI Assistant 2026.2 (Claude Agent) | JetBrains (por ACP) | Dentro del chat de AI Assistant | Suscripción JetBrains AI, tu clave de API (BYOK) o Anthropic Console; no menciona Pro ni Max | Pierdes la terminal de Claude Code | [JetBrains](https://www.jetbrains.com/help/ai-assistant/activate-agents.html) |
| Xcode 26.3 (Claude Agent) | Apple, con el Claude Agent SDK | Settings → Intelligence → Agents → «Get» e «Install» | Fila Account del agente | Subagentes, tareas en segundo plano y plugins; `/skill` puede fallar | [Apple](https://developer.apple.com/documentation/xcode/setting-up-coding-intelligence), [Anthropic](https://www.anthropic.com/news/apple-xcode-claude-agent-sdk) |
| Xcode 26.3 (CLI por MCP) | Apple expone Xcode; tú usas la CLI | `claude mcp add --transport stdio xcode -- xcrun mcpbridge` | La de tu CLI | Todas (es la CLI) más las herramientas de Xcode | [Apple](https://developer.apple.com/documentation/xcode/giving-external-agents-access-to-xcode) |
| Zed | Zed (External Agent por ACP) | Claude Agent desde el ACP Registry | Autenticación propia, se elige con `/login` | Lee CLAUDE.md; los MCP de Zed pueden reenviarse | [Zed](https://zed.dev/docs/ai/external-agents) |
| Visual Studio 2022/2026 | Nadie: no hay extensión oficial | La CLI en Ver → Terminal | La de tu CLI | Todas (es la CLI) | [Microsoft](https://learn.microsoft.com/en-us/visualstudio/releases/2026/release-notes) |
| Neovim | Nadie: solo plugins de la comunidad | `:terminal claude` o un plugin revisado | La de tu CLI | Todas (es la CLI); modo vim en `/config` | [Anthropic](https://code.claude.com/docs/en/interactive-mode) |

## Comandos útiles

```bash
# JetBrains: el plugin necesita la CLI en el PATH
claude --version
which claude                 # ruta para «Claude command» si el IDE no la encuentra
/ide                         # desde una terminal externa, ya dentro de Claude Code

# Xcode 26.3: activa antes «Allow external agents to use Xcode tools» (Settings → Intelligence → Model Context Protocol)
claude mcp add --transport stdio xcode -- xcrun mcpbridge
claude mcp list

# Visual Studio: Ver → Terminal, en la carpeta de la solución
claude

# Neovim
:terminal claude

# Qué ha cargado Claude Code (memoria, skills, cuenta, modelo, MCP)
/context
/status
/mcp
```

## Seguridad

- No hay extensión oficial para Visual Studio ni plugin oficial para Neovim: si instalas uno de la comunidad, revisa el código, quién lo publica y qué permisos pide.
- En Cursor y otros forks, comprueba que el publicador es Anthropic y la versión: el 29-30 de octubre de 2026 Open VSX sirvió copias manipuladas (2.1.312 y 2.1.313, ya retiradas).

## Fuentes oficiales

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
