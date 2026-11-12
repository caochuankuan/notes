# 命令行终端快捷键指南：Windows 与 macOS

> 适用范围：Windows Terminal、PowerShell、Git Bash、WSL，以及 macOS Terminal、Zsh、Bash。  
> 基线：Windows Terminal 常见默认设置、PSReadLine 2.x 的 Windows 编辑模式、macOS Terminal 默认配置、Zsh 5.9 与 Bash 3.2 的常见 Readline 设置。

快捷键分为两层：

- **终端应用层**：新建标签、分屏、复制粘贴、搜索输出、调整字号。
- **Shell 编辑层**：移动光标、删除单词、搜索历史、补全、进程控制。

先确认这两层，再查对应平台的快捷键，能避免大多数混用问题。

## 目录

- [1. 双平台高频快捷键总表](#1-双平台高频快捷键总表)
- [2. Windows](#2-windows)
- [3. macOS](#3-macos)
- [4. 最容易混淆的按键](#4-最容易混淆的按键)
- [5. 日常编辑组合](#5-日常编辑组合)
- [6. 历史命令](#6-历史命令)
- [7. 一页速记](#7-一页速记)
- [8. 检查和自定义键位](#8-检查和自定义键位)

## 1. 双平台高频快捷键总表

| 操作 | macOS Zsh / Bash | Windows PowerShell | Windows Git Bash / WSL |
|---|---|---|---|
| 行首 | `Ctrl+A` | `Home` | `Ctrl+A` |
| 行尾 | `Ctrl+E` | `End` | `Ctrl+E` |
| 左移 / 右移一个字符 | `Ctrl+B` / `Ctrl+F` | `←` / `→` | `Ctrl+B` / `Ctrl+F` |
| 左移 / 右移一个单词 | `Option+B` / `Option+F` | `Ctrl+←` / `Ctrl+→` | `Alt+B` / `Alt+F` |
| 删除左侧单词 | `Ctrl+W` | `Ctrl+Backspace` | `Ctrl+W` |
| 删除右侧单词 | `Option+D` | `Ctrl+Delete` | `Alt+D` |
| 撤销行编辑 | `Ctrl+_` | `Ctrl+Z` | `Ctrl+_` |
| 清屏 | `Ctrl+L` | `Ctrl+L` | `Ctrl+L` |
| 反向搜索历史 | `Ctrl+R` | `Ctrl+R` | `Ctrl+R` |
| 上一条 / 下一条历史 | `Ctrl+P` / `Ctrl+N` | `↑` / `↓` | `Ctrl+P` / `Ctrl+N` |
| 插入上一条命令的参数 | `Option+.` | `Alt+.` | `Alt+.` |
| 补全 | `Tab` | `Tab` / `Shift+Tab` | `Tab` |
| 中断当前进程 | `Ctrl+C` | `Ctrl+C` | `Ctrl+C` |
| 结束输入 / 退出 Shell | `Ctrl+D` | `exit` | `Ctrl+D` |
| 暂停前台进程 | `Ctrl+Z` | 无 Unix 式对应 | `Ctrl+Z` |
| 复制 / 粘贴 | `Cmd+C` / `Cmd+V` | `Ctrl+Shift+C` / `Ctrl+Shift+V` | `Ctrl+Shift+C` / `Ctrl+Shift+V` |
| 搜索终端缓冲区 | `Cmd+F` | `Ctrl+Shift+F` | `Ctrl+Shift+F` |
| 新建标签页 | `Cmd+T` | `Ctrl+Shift+T` | `Ctrl+Shift+T` |

> PowerShell 的 `Ctrl+Z` 在提示符下通常是撤销行编辑，不是挂起进程。正在运行的任务使用 `Ctrl+C` 中断。

## 2. Windows

### 2.1 PowerShell 与 PSReadLine

Windows 10/11 的 PowerShell 命令行编辑由 PSReadLine 负责。默认 Windows 编辑模式更接近 Windows 文本编辑习惯，因此 `Home`、`End`、`Ctrl+←`、`Ctrl+→` 比 `Ctrl+A`、`Ctrl+E` 更可靠。

| 操作 | 默认快捷键 | 说明 |
|---|---|---|
| 左右移动字符 | `←` / `→` | 按字符移动 |
| 左右移动单词 | `Ctrl+←` / `Ctrl+→` | 跨过一个命令行单词 |
| 行首 / 行尾 | `Home` / `End` | 当前逻辑行 |
| 输入缓冲区首尾 | `Ctrl+Home` / `Ctrl+End` | 多行命令时有用 |
| 删除左侧 / 右侧单词 | `Ctrl+Backspace` / `Ctrl+Delete` | 比逐字符删除更快 |
| 历史记录 | `↑` / `↓` | 按时间顺序查找 |
| 反向搜索历史 | `Ctrl+R` | 再按一次继续向前查找 |
| 补全 | `Tab` / `Shift+Tab` | 向前或向后循环候选 |
| 补全候选菜单 | `Ctrl+Space` | 显示可选补全项 |
| 清屏 | `Ctrl+L` | 保留当前命令行 |
| 清空当前输入 | `Esc` | 不执行命令 |
| 撤销 / 重做行编辑 | `Ctrl+Z` / `Ctrl+Y` | 只作用于命令行输入 |
| 插入上一条命令参数 | `Alt+.` | 重复按可继续向前查找 |
| 中断当前命令 | `Ctrl+C` | 有文本选择时可能优先复制选择内容 |

#### 切换到 Emacs 模式

如果经常在 Windows 与 macOS 之间切换，可以临时把 PSReadLine 切到 Emacs 模式：

```powershell
Set-PSReadLineOption -EditMode Emacs
```

该设置只在当前 PowerShell 会话生效。若要持久化，把同一行加入 `$PROFILE`。

查看当前实际绑定：

```powershell
Get-PSReadLineKeyHandler
```

### 2.2 Windows Terminal 应用快捷键

下表是较常见的默认绑定。版本升级或自定义 actions 后可能变化，可通过 `Ctrl+Shift+P` 打开命令面板，或进入 `Ctrl+,` 设置页查看当前绑定。

| 操作 | 默认快捷键 | 备注 |
|---|---|---|
| 新建标签页 | `Ctrl+Shift+T` | 打开新的终端标签 |
| 关闭窗格 / 标签 | `Ctrl+Shift+W` | 关闭对象取决于当前焦点 |
| 切换标签页 | `Ctrl+Tab` / `Ctrl+Shift+Tab` | 下一个 / 上一个 |
| 命令面板 | `Ctrl+Shift+P` | 查找所有终端动作 |
| 搜索缓冲区 | `Ctrl+Shift+F` | 搜索当前终端输出 |
| 复制 / 粘贴 | `Ctrl+Shift+C` / `Ctrl+Shift+V` | 不要与 `Ctrl+C` 中断混淆 |
| 打开设置 | `Ctrl+,` | 修改 profiles 与 keybindings |
| 全屏 | `F11` | 切换全屏显示 |
| 字号调整 | `Ctrl++` / `Ctrl+-` / `Ctrl+0` | 放大 / 缩小 / 恢复 |

> 分屏等动作可能因 Windows Terminal 版本和自定义键位不同。以 `Ctrl+Shift+P` 命令面板显示的当前绑定为准。

### 2.3 Git Bash 与 WSL

Git Bash 和 WSL 中运行的 Bash 使用 Readline 风格的命令行编辑：

- 行首、删除单词、历史搜索：按 **Windows Git Bash / WSL** 一栏。
- 标签页、分屏、复制粘贴、搜索缓冲区：按 **Windows Terminal** 一栏。
- `Ctrl+C` 仍然是中断进程，复制通常使用 `Ctrl+Shift+C`。

## 3. macOS

### 3.1 Zsh 与 Bash 的命令行编辑

macOS 默认使用 Zsh，命令行编辑由 ZLE 负责；切换回 Bash 时由 Readline 负责。两者的默认 Emacs 风格键位高度相似。

| 操作 | 快捷键 | 说明 |
|---|---|---|
| 行首 / 行尾 | `Ctrl+A` / `Ctrl+E` | 比 `Home` / `End` 更稳定 |
| 左右移动字符 | `Ctrl+B` / `Ctrl+F` | Emacs 风格移动 |
| 左右移动单词 | `Option+B` / `Option+F` | 未启用 Meta 时使用 `Esc, B` / `Esc, F` |
| 删除左侧单词 | `Ctrl+W` 或 `Option+Delete` | 取决于终端如何发送 Option 键序列 |
| 删除右侧单词 | `Option+D` | 未启用 Meta 时使用 `Esc, D` |
| 删除到行首 / 行尾 | `Ctrl+U` / `Ctrl+K` | 快速重写命令 |
| 粘贴最近删除的文本 | `Ctrl+Y` | 与 `Ctrl+U`、`Ctrl+K`、`Ctrl+W` 配合 |
| 撤销行编辑 | `Ctrl+_` | Zsh 与 Bash 常见默认绑定 |
| 反向搜索历史 | `Ctrl+R` | 再按一次继续向前；`Ctrl+G` 取消 |
| 上一条 / 下一条历史 | `Ctrl+P` / `Ctrl+N` | 与方向键等效 |
| 插入上一条命令参数 | `Option+.` | 连续按可继续向前查找 |
| 插入按键字面值 | `Ctrl+V` | 例如 `Ctrl+V` 后按 `Tab` |
| 用编辑器编辑当前命令 | `Ctrl+X`，然后 `Ctrl+E` | 调用 `$VISUAL` 或 `$EDITOR` |
| 中断当前命令 | `Ctrl+C` | 不是复制 |
| 结束输入 / 退出 Shell | `Ctrl+D` | 空提示符下退出 |
| 暂停前台进程 | `Ctrl+Z` | 之后用 `jobs`、`bg`、`fg` 恢复 |

在部分终端配置中，`Cmd+←` 与 `Cmd+→` 也会移动到行首或行尾，但这属于终端应用的按键映射。跨环境时优先使用 `Ctrl+A` / `Ctrl+E`。

### 3.2 macOS Terminal 应用快捷键

| 操作 | 常见快捷键 | 备注 |
|---|---|---|
| 复制 / 粘贴 | `Cmd+C` / `Cmd+V` | `Ctrl+C` 仍是中断进程 |
| 清空屏幕与回滚缓冲区 | `Cmd+K` | 与 Shell 的 `Ctrl+L` 不同 |
| 新建标签页 | `Cmd+T` | 在当前窗口打开新标签 |
| 新建窗口 | `Cmd+N` | 打开独立终端窗口 |
| 关闭当前标签 / 窗口 | `Cmd+W` | 关闭前确认是否有运行中的任务 |
| 搜索终端输出 | `Cmd+F` | 搜索当前缓冲区 |
| 放大 / 缩小 / 恢复字号 | `Cmd++` / `Cmd+-` / `Cmd+0` | 应用层快捷键 |
| 切换全屏 | `Ctrl+Cmd+F` | macOS 常见全屏组合 |

> iTerm2 等终端可能使用不同的分屏、标签页和搜索快捷键，以应用设置中的 Key Bindings 为准。

### 3.3 启用 Option 作为 Meta 键

如果 `Option+B` 输入的是 `ƒ`，而不是向左移动单词，说明终端尚未把 Option 作为 Meta 发送。

#### Apple Terminal

进入：

```text
Settings → Profiles → 当前配置 → Keyboard
```

勾选：

```text
Use Option as Meta key
```

#### iTerm2

进入：

```text
Settings → Profiles → Keys
```

将 Left Option key 设置为：

```text
Esc+
```

未启用 Meta 时，可以把 `Option+B` 改写为先后按 `Esc`、`B`。

## 4. 最容易混淆的按键

| 按键 | macOS Zsh / Bash | Windows PowerShell | 结论 |
|---|---|---|---|
| `Ctrl+C` | 中断当前命令 | 中断当前命令；有选择文本时可能优先复制 | 不要当作复制键 |
| `Cmd+C` | 复制选中文本 | 不适用 | macOS 的应用层复制键 |
| `Ctrl+Shift+C` | 通常不用于复制 | Windows Terminal 复制 | Windows 的复制键 |
| `Ctrl+A` | 移动到行首 | Windows 编辑模式常见为全选，取决于 PSReadLine 模式 | 不要默认相同 |
| `Ctrl+Z` | 挂起前台进程 | 提示符下通常是撤销行编辑 | 不要用它挂起 Windows 任务 |
| `Ctrl+Y` | 粘贴最近删除的文本 | 通常是重做行编辑 | 含义不同 |
| `Ctrl+U` | 删除光标左侧内容 | 绑定可能不同，不应假设相同 | 先用绑定检查命令确认 |
| `Home` / `End` | 部分外接键盘需要 `Fn+←` / `Fn+→` | 移动到行首 / 行尾 | macOS 可优先使用 `Ctrl+A` / `Ctrl+E` |

### 统一策略

- 在 macOS 上固定使用 `Ctrl+A` 与 `Ctrl+E`，不依赖 `Cmd+←` / `Cmd+→`。
- 在 Windows PowerShell 中保留 `Home` / `End` 与 `Ctrl+方向键`。
- 始终区分复制粘贴和 Shell 编辑：复制是终端应用动作，中断是进程动作。
- 在 Windows 上使用 Git Bash 或 WSL 时，行编辑按 Bash 表，窗口与复制按 Windows Terminal 表。

## 5. 日常编辑组合

### 只保留命令前半段

```text
Ctrl+U  删除光标左侧内容
输入新前缀
Ctrl+Y  粘回刚删除的文本
```

### 复用上一条命令的参数

```text
Option+.  # macOS
Alt+.     # Windows Bash / PowerShell
```

插入上一条命令的最后一个参数；重复按可继续向前查找。

### 修改写错的长命令

```text
Option+B / Option+F  按单词移动
Ctrl+W              删除左侧单词
Option+D            删除右侧单词
Ctrl+_              撤销行编辑
```

### 从历史中找回长命令

```text
Ctrl+R
输入命令片段
再按 Ctrl+R 继续向前查找
Enter 执行
```

取消搜索使用 `Ctrl+G`。

## 6. 历史命令

### Bash / Zsh

```bash
!!          # 重复上一条命令
sudo !!     # 用 sudo 重跑上一条命令
!$          # 上一条命令的最后一个参数
!abc        # 执行最近一条以 abc 开头的命令
!abc:p      # 只显示，不执行
^old^new    # 替换上一条命令中的 old，再执行
history     # 查看历史记录
```

### PowerShell

PowerShell 默认不支持与 Bash 相同的 `!!`、`!$` 和 `^old^new` 历史展开语法。

| 目标 | PowerShell 写法 |
|---|---|
| 重复上一条命令 | 按 `↑`，再按 `Enter` |
| 引用上一条命令的参数 | `Alt+.` |
| 按片段搜索历史 | `Ctrl+R` |
| 列出历史记录 | `Get-History` |
| 执行指定编号的历史命令 | `Invoke-History -Id 123` |
| 替换上一条命令中的文本 | 用 `↑` / `Ctrl+R` 找回后手动编辑 |

## 7. 一页速记

### macOS 必记

| 快捷键 | 作用 |
|---|---|
| `Ctrl+R` | 搜索历史 |
| `Ctrl+A` / `Ctrl+E` | 行首 / 行尾 |
| `Ctrl+W` / `Option+D` | 删除左侧 / 右侧单词 |
| `Option+B` / `Option+F` | 按单词移动 |
| `Option+.` | 插入上一条命令的参数 |
| `Ctrl+_` | 撤销行编辑 |
| `Ctrl+C` | 中断进程 |
| `Ctrl+D` | 退出 Shell |
| `Cmd+C` / `Cmd+V` | 复制 / 粘贴 |
| `Cmd+K` | 清空终端缓冲区 |

### Windows 必记

| 快捷键 | 作用 |
|---|---|
| `Ctrl+R` | 搜索历史 |
| `Home` / `End` | 行首 / 行尾 |
| `Ctrl+←` / `Ctrl+→` | 按单词移动 |
| `Ctrl+Backspace` / `Ctrl+Delete` | 删除左侧 / 右侧单词 |
| `Alt+.` | 插入上一条命令的参数 |
| `Ctrl+Z` / `Ctrl+Y` | 命令行撤销 / 重做 |
| `Ctrl+C` | 中断进程 |
| `Ctrl+Shift+C` / `Ctrl+Shift+V` | 复制 / 粘贴 |
| `Ctrl+Shift+T` | 新建标签 |
| `Ctrl+Shift+P` | 命令面板 |

## 8. 检查和自定义键位

### macOS

查看当前 Shell：

```bash
echo "$SHELL"
```

查看 Zsh 键位绑定：

```bash
bindkey -L
```

查看 Bash 键位绑定：

```bash
bind -P
```

如果终端支持，按 `Ctrl+V` 后再按某个组合，通常可以查看它发送的转义序列，便于定位 Option 键行为。

### Windows PowerShell

查看 PowerShell 版本：

```powershell
$PSVersionTable.PSVersion
```

查看 PSReadLine 配置：

```powershell
Get-PSReadLineOption
```

查看当前键位绑定：

```powershell
Get-PSReadLineKeyHandler
```

Windows Terminal 的设置页在 `Ctrl+,`；命令面板在 `Ctrl+Shift+P`。

## 说明

本文以常见默认配置为基线：

| 环境 | 参考的默认层 |
|---|---|
| Windows Terminal | Windows 10/11 常见默认 keybindings；复制粘贴使用 `Ctrl+Shift+C` / `Ctrl+Shift+V` |
| PowerShell | PSReadLine 2.x；默认 Windows 编辑模式的常用绑定 |
| Git Bash / WSL | Bash + Readline 的常见 Emacs 风格键位 |
| macOS Terminal | 系统 Terminal.app 常见应用快捷键 |
| macOS Shell | Zsh 5.9 默认键位；Bash 3.2 Readline 常见键位 |

终端版本、Shell 版本、PSReadLine 编辑模式和用户配置都会改变快捷键。某个组合不符合预期时，先确认当前环境，再检查应用设置。
