# Shell 环境配置文档

## 一、Shell 环境

| 组件 | 说明 |
|------|------|
| **zsh** | 已安装 |
| **oh-my-zsh** | 已安装 |
| **Powerlevel10k** | 已安装（`~/.oh-my-zsh/custom/themes/powerlevel10k`） |
| **Meslo Nerd Font** | 已安装 Regular / Bold / Italic / Bold Italic |

## 二、已配置插件

| 插件 | 来源 | 功能 |
|------|------|------|
| `git` | oh-my-zsh 内置 | Git 别名与补全 |
| `tmux` | oh-my-zsh 内置 | Tmux 集成 |
| `sudo` | oh-my-zsh 内置 | 双击 Esc 自动添加 sudo |
| `autojump` | 系统包 | 目录智能跳转 |
| `fzf` | 系统包 | 模糊搜索 |
| `zsh-autosuggestions` | 自定义插件 | 命令历史自动建议 |
| `zsh-syntax-highlighting` | 自定义插件 | 命令语法高亮 |

## 三、Node.js 环境

| 组件 | 说明 |
|------|------|
| **nvm** | 已安装，管理 Node 版本 |
| **Node.js LTS** | 已安装 |
| **npm** | 随 Node.js 安装 |

## 四、.zshrc 配置

```bash
# 主题
ZSH_THEME="powerlevel10k/powerlevel10k"

# 禁用 oh-my-zsh 自动更新提示
zstyle ':omz:update' mode disabled

# 插件列表
plugins=(git autojump fzf tmux sudo)

# NVM
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"

# 插件加载（zsh-syntax-highlighting 必须放最后）
source ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions/zsh-autosuggestions.zsh
source ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh

# FZF 默认选项
export FZF_DEFAULT_OPTS="--height 40% --layout=reverse --border"

# Autojump
[ -s /usr/share/autojump/autojump.zsh ] && source /usr/share/autojump/autojump.zsh
```

## 五、常用 Alias

```bash
# 重载配置
alias src='source ~/.zshrc'

# 代理开关
alias proxy='export http_proxy="http://localhost:7890" https_proxy="https://localhost:7890" all_proxy="socks5://localhost:7890"'
alias unproxy='unset http_proxy https_proxy all_proxy'

# 文件列表
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# 目录跳转
alias ..='cd ..'
alias ...='cd ../..'

# Claude
alias c-d='claude --dangerously-skip-permissions'

# Git
alias gs='git status'
alias gc='git commit'
alias gp='git push'
alias gl='git log --oneline --graph --decorate'
```

## 六、使用说明

| 操作 | 命令 |
|------|------|
| 重载配置 | `src` |
| 开启代理 | `proxy` |
| 关闭代理 | `unproxy` |
| 目录跳转 | `j <目录名>` (autojump) |
| 模糊搜索文件 | `Ctrl+R` (fzf) |
| 添加 sudo | 双击 `Esc` (sudo 插件) |
