# ZCF - Zero-Config Claude-Code Flow

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code](https://img.shields.io/badge/Claude-Code-blue)](https://claude.ai/code)
[![Version](https://img.shields.io/npm/v/zcf)](https://www.npmjs.com/package/zcf)
[![codecov](https://codecov.io/gh/UfoMiao/zcf/graph/badge.svg?token=HZI6K4Y7D7)](https://codecov.io/gh/UfoMiao/zcf)
[![Ask DeepWiki](https://deepwiki.com/badge.svg)](https://deepwiki.com/UfoMiao/zcf)

[中文](README_zh-CN.md) | **English** | [Changelog](CHANGELOG.md) | [📖 **Complete Documentation**](https://zcf.ufomiao.top)

> Zero-config, one-click setup for Claude Code with bilingual support, intelligent agent system and personalized AI assistant

![Rendering](./src/assets/screenshot-en.webp)

## 📖 Documentation

For comprehensive guides, tutorials, and best practices, visit our **[GitBook Documentation](https://zcf.ufomiao.top)**:

- **[Getting Started](https://zcf.ufomiao.top/getting-started)** - Installation and setup guide
- **[Advanced Guide](https://zcf.ufomiao.top/advanced-guide)** - Configuration and customization
- **[Claude Code Tips](https://zcf.ufomiao.top/claude-tips)** - Best practices and usage tips
- **[Development](https://zcf.ufomiao.top/development)** - Contributing and architecture guide

## 🚀 Quick Start

### 🎯 Recommended: Use Interactive Menu (v2.0 New)

```bash
npx zcf          # Open interactive menu and choose operations based on your needs
```

Menu options include:

- `1` Full initialization (equivalent to `zcf i`)
- `2` Import workflows (equivalent to `zcf u`)
- `3-7` Configuration management (API/CCR, MCP, Model settings, AI personality, etc.)
- `R` Claude Code Router management (enhanced in v2.8.1)
- `U` ccusage - Claude Code usage analysis
- `L` CCometixLine - High-performance statusline tool with Git integration and real-time usage tracking (v2.9.9+ new)
- `+` Check updates - Check and update Claude Code, CCR and CCometixLine versions (v2.9.9+ enhanced)
- More features...

### Or, use direct commands:

#### 🆕 First time using Claude Code

```bash
npx zcf i        # Execute full initialization directly: Install Claude Code + Import workflows + Configure API + Set up MCP services
# or
npx zcf → select 1  # Execute full initialization via menu
```

#### 🔄 Already have Claude Code installed

```bash
npx zcf u        # Update workflows only: Quick add AI workflows and command system
# or
npx zcf → select 2  # Execute workflow update via menu
```

> **Note**:
>
> - Since v2.0, `zcf` opens the interactive menu by default, providing a visual operation interface
> - You can choose operations through the menu or use commands directly for quick execution
> - `zcf i` = full initialization, `zcf u` = update workflows only

#### 🤖 Non-interactive Mode

For CI/CD and automated setups, use `--skip-prompt` with parameters:

```bash
# Shorthand version
npx zcf i -s -g zh-CN -t api_key -k "sk-xxx" -u "https://xxx.xxx"

# Complete version
npx zcf i --skip-prompt --all-lang zh-CN --api-type api_key --api-key "sk-xxx" --api-url "https://xxx.xxx"
```

#### Non-interactive Mode Parameters

When using `--skip-prompt`, the following parameters are available:

| Parameter                    | Description                                             | Values                                                                                             | Required                               | Default                                                                                                                          |
| ---------------------------- | ------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `--skip-prompt, -s`          | Skip all interactive prompts                            | -                                                                                                  | Yes (for non-interactive mode)         | -                                                                                                                                |
| `--lang, -l`                 | ZCF display language                                    | `zh-CN`, `en`                                                                                      | No                                     | `en`                                                                                                                             |
| `--config-lang, -c`          | Configuration language                                  | `zh-CN`, `en`                                                                                      | No                                     | `en`                                                                                                                             |
| `--ai-output-lang, -a`       | AI output language                                      | `zh-CN`, `en`, custom string                                                                       | No                                     | `en`                                                                                                                             |
| `--all-lang, -g`             | Set all language parameters to this value               | `zh-CN`, `en`, custom string                                                                       | No                                     | - (overrides above 3 params. Custom string sets AI output language to custom while interaction and config languages remain 'en') |
| `--config-action, -o`        | Config handling                                         | `new`, `backup`, `merge`, `docs-only`, `skip`                                                      | No                                     | `backup`                                                                                                                         |
| `--api-type, -t`             | API configuration type                                  | `auth_token`, `api_key`, `ccr_proxy`, `skip`                                                       | No                                     | `skip`                                                                                                                           |
| `--api-key, -k`              | API key (for both API key and auth token types)         | string                                                                                             | Required when `api-type` is not `skip` | -                                                                                                                                |
| `--api-url, -u`              | Custom API URL                                          | URL string                                                                                         | No                                     | official API                                                                                                                     |
| `--mcp-services, -m`         | MCP services to install (multi-select, comma-separated) | `context7`, `mcp-deepwiki`, `Playwright`, `exa`, or `skip` for none                                | No                                     | `all`                                                                                                                            |
| `--workflows, -w`            | Workflows to install (multi-select, comma-separated)    | `commonTools`, `sixStepsWorkflow`, `featPlanUx`, `gitWorkflow`, `bmadWorkflow`, or `skip` for none | No                                     | `all`                                                                                                                            |
| `--ai-personality, -p`       | AI personality type                                     | `professional`, `catgirl`, `friendly`, `mentor`, `custom`                                          | No                                     | `professional`                                                                                                                   |
| `--install-cometix-line, -x` | Install CCometixLine statusline tool                    | `true`, `false`                                                                                    | No                                     | `true`                                                                                                                           |

#### 🎯 BMad Workflow (v2.7 New Feature)

[BMad](https://github.com/bmad-code-org/BMAD-METHOD) (BMad-Method: Universal AI Agent Framework) is an enterprise-grade workflow system that provides:

- Complete team of specialized AI agents (PO, PM, Architect, Dev, QA, etc.)
- Structured development process with quality gates
- Automatic documentation generation
- Support for both greenfield and brownfield projects

After installation, use `/bmad-init` to initialize the BMad workflow in your project.

#### 🚀 CCR (Claude Code Router) Support (v2.8+ Enhanced)

[CCR](https://github.com/musistudio/claude-code-router/blob/main/README.md) is a powerful proxy router that enables:

- **Free Model Access**: Use free AI models (like Gemini, DeepSeek) through Claude Code interface
- **Custom Routing**: Route different types of requests to different models based on your rules
- **Cost Optimization**: Significantly reduce API costs by using appropriate models for different tasks
- **Easy Management**: Interactive menu for CCR configuration and service control
- **Auto Updates**: Automatic version checking and updates for CCR and Claude Code (v2.8.1+)

To access CCR features:

```bash
npx zcf ccr      # Open CCR management menu
# or
npx zcf → select R
```

CCR menu options:

- Initialize CCR - Install and configure CCR with preset providers
- Start UI - Launch CCR web interface for advanced configuration
- Service Control - Start/stop/restart CCR service
- Check Status - View current CCR service status

After CCR setup, ZCF automatically configures Claude Code to use CCR as the API proxy.

**Important Notice for v2.9.9 Users**: If you previously installed CCometixLine using ZCF v2.9.9, please rerun the installation process to ensure that the CCometixLine configuration is correctly added. Run `npx zcf` -> `Select L` -> `Select 1` to add the CCometixLine configuration.

#### 📊 CCometixLine Support (Status Bar Tool) (v2.9.9+ New)

[CCometixLine](https://github.com/Haleclipse/CCometixLine) is a high-performance Rust-based statusline tool that provides:

- **Real-time Usage Tracking**: Monitor Claude Code API usage in real-time
- **Git Integration**: Display Git status and branch information
- **Status Line Display**: Native integration with your terminal statusline
- **Performance Optimized**: Built with Rust for minimal resource usage
- **TUI Configuration**: Interactive terminal UI for customizing themes, segments, and display options
- **Auto Updates**: Included in ZCF's update checking system

CCometixLine menu options (accessible via `npx zcf` → `L`):

- `1` Install or Update - Install or update CCometixLine using npm
- `2` Print Default Configuration - Display current CCometixLine configuration
- `3` Custom Config - TUI Configuration Mode - Interactive terminal UI for customizing settings

> **Important Note for v2.9.9 Users**: If you have previously used ZCF v2.9.9 to set up your environment, please re-run the initialization process to ensure CCometixLine configuration is properly added. Run `npx zcf` and select the appropriate setup option to update your configuration with CCometixLine support.

#### 🚀 Check for updates (v2.8.1+, CCometixLine support v2.9.9+):

```bash
npx zcf check-updates  # Check and update Claude Code, CCR and CCometixLine to latest versions
# or
npx zcf → select +
```

### Setup Process

Full initialization (`npx zcf`) will automatically:

- ✅ Detect and install Claude Code
- ✅ Select AI output language (new feature)
- ✅ Configure API keys or CCR proxy
- ✅ Select and configure MCP services
- ✅ Set up all necessary configuration files

### Usage

After configuration:

- **For first-time project use, strongly recommend running `/init-project` to generate CLAUDE.md for better AI understanding of project architecture**
- `<task description>` - Execute directly without workflow, following SOLID, KISS, DRY, and YAGNI principles, suitable for small tasks like bug fixes
- `/feat <task description>` - Start new feature development, divided into plan and UI phases
- `/workflow <task description>` - Execute complete development workflow, not automated, starts with multiple solution options, asks for user feedback at each step, allows plan modifications, maximum control

> **PS**:
>
> - Both feat and workflow have their advantages, try both to compare
> - Generated documents are located by default at `.claude/xxx.md` in project root, you can add `.claude/` to your project's `.gitignore`

## ✨ ZCF Tool Features

### 🌏 Multi-language Support

- Script interaction language: Controls installation prompts language
- Configuration file language: Determines which configuration set to install (zh-CN/en)
- AI output language: Choose the language for AI responses (supports Chinese, English, and custom languages)
- AI personality: Support multiple preset personalities (Professional, Catgirl, Friendly, Mentor) or custom

### 🔧 Smart Installation

- Auto-detects Claude Code installation status
- Uses npm for automatic installation (ensures compatibility)
- Cross-platform support (Windows/macOS/Linux/Termux)
- Automatic MCP service configuration
- Smart configuration merging and partial modification support (v2.0 new)
- Enhanced command detection mechanism (v2.1 new)
- Dangerous operation confirmation mechanism (v2.3 new)

### 📦 Complete Configuration

- CLAUDE.md system instructions
- settings.json configuration file
- commands custom commands
- agents AI agent configurations

### 🔐 API Configuration

- Supports two authentication methods:
  - **Auth Token**: For tokens obtained via OAuth or browser login
  - **API Key**: For API keys from Anthropic Console
- Custom API URL support
- Support for manual configuration later
- Partial modification: Update only needed configuration items (v2.0 new)

### 💾 Configuration Management

- Smart backup of existing configurations (all backups saved in ~/.claude/backup/)
- Configuration merge option (v2.0 enhanced: supports deep merge)
- Safe overwrite mechanism
- Automatic backup before MCP configuration changes
- Default model configuration (v2.0 new)
- AI memory management (v2.0 new)
- ZCF cache cleanup (v2.0 new)

## 📖 Usage Instructions

### Interactive Menu (v2.0)

```bash
$ npx zcf

 ZCF - Zero-Config Claude-Code Flow

? Select ZCF display language / 选择ZCF显示语言:
  ❯ 简体中文
    English

Select function:
  -------- Claude Code --------
  1. Full initialization - Install Claude Code + Import workflow + Configure API or CCR proxy + Configure MCP services
  2. Import workflow - Import/update workflow-related files only
  3. Configure API - Configure API URL and authentication (supports CCR proxy)
  4. Configure MCP - Configure MCP services (includes Windows fix)
  5. Configure default model - Set default model (opus/sonnet)
  6. Configure Claude global memory - Configure AI output language and personality
  7. Import recommended environment variables and permissions - Import privacy protection environment variables and system permissions

  --------- Other Tools ----------
  R. CCR - Claude Code Router management
  U. ccusage - Claude Code usage analysis
  L. CCometixLine - High-performance statusline tool with Git integration and real-time usage tracking

  ------------ ZCF ------------
  0. Select display language / 更改显示语言 - Change ZCF interface language
  -. Clear preference cache - Clear preference language and other caches
  +. Check updates - Check and update Claude Code, CCR and CCometixLine versions
  Q. Exit

Enter your choice: _
```

### Full Initialization Flow (Select 1 or use `zcf i`)

```bash
? Select Claude Code configuration language:
  ❯ 简体中文 (zh-CN) - Chinese (easier for Chinese users to customize)
    English (en) - English (recommended, lower token consumption)

? Select AI output language:
  AI will respond to you in this language
  ❯ 简体中文
    English
    Custom
    (Supports Japanese, French, German, and more)

? Select AI personality:
  ❯ Professional Assistant(Default)
    Catgirl Assistant
    Friendly Assistant
    Mentor Mode
    Custom

? Claude Code not found. Install automatically? (Y/n)

✔ Claude Code installed successfully

? Select API authentication method
  ❯ Use Auth Token (OAuth authentication)
    For tokens obtained via OAuth or browser login
    Use API Key (Key authentication)
    For API keys from Anthropic Console
    Configure CCR Proxy (Claude Code Router)
    Use free models and custom routing to reduce costs and explore the possibilities of Claude Code
    Skip (configure manually later)

? Enter API URL: https://api.anthropic.com
? Enter Auth Token or API Key: xxx

? Existing config detected. How to proceed?
  ❯ Backup and overwrite all
    Update workflow-related md files only with backup
    Merge config
    Skip

✔ All config files backed up to ~/.claude/backup/xxx
✔ Config files copied to ~/.claude

? Select workflows to install (space to select, enter to confirm)
  ❯ ◉ Common Tools (init-project + init-architect + get-current-datetime) - Essential project initialization and utility commands
    ◉ Six Steps Workflow (workflow) - Complete 6-phase development process
    ◉ Feature Planning and UX Design (feat + planner + ui-ux-designer) - Structured feature development
    ◉ Git Commands (commit + rollback + cleanBranches + worktree) - Streamlined Git operations
    ◉ BMAD-Method Extension Installer - Enterprise agile development workflow

✔ Installing workflows...
  ✔ Installed command: zcf/workflow.md
  ✔ Installed command: zcf/feat.md
  ✔ Installed agent: zcf/plan/planner.md
  ✔ Installed agent: zcf/plan/ui-ux-designer.md
  ✔ Installed command: zcf/git/git-commit.md
  ✔ Installed command: zcf/git/git-rollback.md
  ✔ Installed command: zcf/git/git-cleanBranches.md
  ✔ Installed command: zcf/git/git-worktree.md
  ✔ Installed command: zcf/bmad-init.md
✔ Workflow installation successful

✔ API configured

? Configure MCP services? (Y/n)

? Select MCP services to install (space to select, enter to confirm)
  ❯ ◯ Install all
    ◯ Context7 Documentation Query - Query latest library docs and code examples
    ◯ DeepWiki - Query GitHub repository docs and examples
    ◯ Playwright Browser Control - Direct browser automation control
    ◯ Exa AI Search - Web search using Exa AI

? Enter Exa API Key (get from https://dashboard.exa.ai/api-keys)

✔ MCP services configured

🎉 Setup complete! Use 'claude' command to start.
```

### Command Line Options

#### Commands Quick Reference

| Command             | Alias   | Description                                                                           |
| ------------------- | ------- | ------------------------------------------------------------------------------------- |
| `zcf`               | -       | Show interactive menu (v2.0 default command)                                          |
| `zcf init`          | `zcf i` | Initialize Claude Code configuration                                                  |
| `zcf update`        | `zcf u` | Update workflow-related md files with backup                                          |
| `zcf ccu`           | -       | Run Claude Code usage analysis tool - [ccusage](https://github.com/ryoppippi/ccusage) |
| `zcf ccr`           | -       | Open CCR (Claude Code Router) management menu                                         |
| `zcf check-updates` | -       | Check and update Claude Code, CCR and CCometixLine versions                           |

#### Common Options

```bash
# Specify configuration language
npx zcf --config-lang zh-CN
npx zcf -c zh-CN            # Using short option

# Force overwrite existing configuration
npx zcf --force
npx zcf -f                 # Using short option

# Update workflow-related md files with backup (preserve API and MCP configs)
npx zcf u                  # Using update command
npx zcf update             # Full command

# Show help information
npx zcf --help
npx zcf -h

# Show version
npx zcf --version
npx zcf -v
```

#### Usage Examples

```bash
# Show interactive menu (default)
npx zcf

# First-time installation, complete initialization
npx zcf i
npx zcf init              # Full command

# Update workflow-related md files with backup, keep API and MCP configs
npx zcf u
npx zcf update            # Full command

# Force reinitialize with Chinese config
npx zcf i --config-lang zh-CN --force
npx zcf i -c zh-CN -f      # Using short options

# Update to English prompts (lower token consumption)
npx zcf u --config-lang en
npx zcf u -c en            # Using short option

# Run Claude Code usage analysis tool (powered by ccusage)
npx zcf ccu               # Daily usage (default), or use: monthly, session, blocks
```

## 📁 Project Structure

For detailed architecture and development information, see our [Development Documentation](https://zcf.ufomiao.top/development).

```
zcf/
├── README.md              # Basic usage
├── src/                  # Source code
├── templates/            # Configuration templates
├── gitbook/             # Complete documentation
└── dist/                # Build output
```

## ✨ Core Features (v2.0 Enhanced)

### 🤖 Professional Agents

- **Task Planner**: Breaks down complex tasks into executable steps
- **UI/UX Designer**: Provides professional interface design guidance
- **AI Personality**: Support multiple preset personalities and custom (v2.0 new)
- **BMad Team** (New): Complete agile development team including:
  - Product Owner (PO): Requirements elicitation and prioritization
  - Project Manager (PM): Planning and coordination
  - System Architect: Technical design and architecture
  - Developer: Implementation and coding
  - QA Engineer: Testing and quality assurance
  - Scrum Master (SM): Process facilitation
  - Business Analyst: Requirements analysis
  - UX Expert: User experience design

### ⚡ Command System

- **Feature Development** (`/feat`): Structured new feature development
- **Workflow** (`/workflow`): Complete six-phase development workflow
- **Git Commands**: Streamlined Git operations
  - `/git-commit`: Smart commit with automatic staging and message generation
  - `/git-rollback`: Safely rollback to previous commits with backup
  - `/git-cleanBranches`: Clean up merged branches and maintain repository hygiene
  - `/git-worktree`: Manage Git worktrees with IDE integration and content migration
- **BMad Workflow** (`/bmad-init`): Initialize BMad workflow for enterprise development
  - Supports both greenfield (new projects) and brownfield (existing projects)
  - Provides comprehensive templates for PRDs, architecture docs, and user stories
  - Integrated quality gates and checklist system

### 🔧 Smart Configuration

- API key management (supports partial modification)
- Fine-grained permission control
- Multiple Claude model support (configurable default model)
- Interactive menu system (v2.0 new)
- AI memory management (v2.0 new)

## 🎯 Development Workflow

### Six-Phase Workflow

1. [Mode: Research] - Understand requirements
2. [Mode: Ideate] - Design solutions
3. [Mode: Plan] - Create detailed plan
4. [Mode: Execute] - Implement development
5. [Mode: Optimize] - Improve quality
6. [Mode: Review] - Final assessment

## 🛠️ Development

For detailed development setup and contribution guidelines, see our [Development Documentation](https://zcf.ufomiao.top/development).

```bash
# Quick setup
git clone https://github.com/UfoMiao/zcf.git
cd zcf && pnpm install && pnpm build
```

## 💡 Best Practices

For comprehensive usage tips and best practices, see our [Claude Code Tips](https://zcf.ufomiao.top/claude-tips) section.

1. **Task Breakdown**: Keep tasks independent and testable
2. **Code Quality**: Follow SOLID, KISS, DRY, and YAGNI principles  
3. **Documentation Management**: Plans are stored in `.claude/plan/` directory

## 🔧 Troubleshooting

If you encounter issues:

1. Re-run `npx zcf` to reconfigure
2. Check configuration files in `~/.claude/` directory  
3. Ensure Claude Code is properly installed

For detailed troubleshooting guides, visit our [Advanced Guide](https://zcf.ufomiao.top/advanced-guide/troubleshooting).

## 🙏 Acknowledgments

This project is inspired by and incorporates the following open source projects:

- [LINUX DO - The New Ideal Community](https://linux.do)
- [CCR](https://github.com/musistudio/claude-code-router)
- [CCometixLine](https://github.com/Haleclipse/CCometixLine)
- [ccusage](https://github.com/ryoppippi/ccusage)
- [BMad Method](https://github.com/bmad-code-org/BMAD-METHOD)

Thanks to these community contributors for sharing!

## ❤️ Support & Sponsorship

If you find this project helpful, please consider sponsoring its development. Your support is greatly appreciated!

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/UfoMiao)

<table>
  <tr>
    <td><img src="/src/assets/alipay.webp" width="200" alt="Alipay" /></td>
    <td><img src="/src/assets/wechat.webp" width="200" alt="WeChat Pay" /></td>
  </tr>
</table>

### Our Sponsors

A huge thank you to all our sponsors for their generous support!

- Tc (first sponsor)
- Argolinhas (first ko-fi sponsor ٩(•̤̀ᵕ•̤́๑))
- r\*r (first anonymous sponsor🤣)
- 16°C coffee (My best friend🤪, offered Claude Code max $200 package)

## 📄 License

MIT License

---

If this project helps you, please give me a ⭐️ Star!

[![Star History Chart](https://api.star-history.com/svg?repos=UfoMiao/zcf&type=Date)](https://star-history.com/#UfoMiao/zcf&Date)
