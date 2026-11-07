# scterm

![scterm CI](https://github.com/OrangeArtc0915/test/actions/workflows/scterm-ci.yml/badge.svg)

为 **Windows Server Core** 打造的终端多路复用工具：在原生 conhost 上提供标签页、窗格分屏、布局模板、会话恢复、回看搜索、Quake 热键、键盘标记模式与矩形选择；零第三方依赖，编译为单文件 `scterm.exe`。

默认 profile 直接托管真实 PowerShell（优先 `pwsh.exe`，缺失时回退 Windows PowerShell 5.1），也可在设置面板切回自研 cmd 风格 shell 或 `cmd.exe`。

## 功能

- 标签页 / 任意嵌套窗格 / 拖拽分隔线 / 窗格放大
- `scterm --layout "h(powershell,v(cmd,scterm))"` 布局模板
- 正常退出保存 `session.toml`，下次启动恢复标签与布局
- 64 套配色、渐变背景、每 profile 字体/渐变/标签色覆盖
- 回看搜索、OSC 8 链接、OSC 7 目录、OSC 133 提示符跳转
- `Ctrl+Shift+M` 标记模式、`Alt+左键` 矩形选择
- `[quake]` 全局呼出热键、底部状态栏
- 外部 shell 集成（PowerShell / cmd）

## 构建与运行

```bash
cd tools/scterm
cargo build --release
./target/release/scterm.exe
```

要求：Windows 10 1809 / Server 2019 及以上（ConPTY），Rust stable。

## 这个目录的"独立仓库"入口

- 源码：https://github.com/OrangeArtc0915/test/tree/main/tools/scterm
- 提交历史：https://github.com/OrangeArtc0915/test/commits/main/tools/scterm
- 标签：https://github.com/OrangeArtc0915/test/tags?q=scterm-
- 发布：https://github.com/OrangeArtc0915/test/releases/tag/scterm-v0.1.0
- Issue：https://github.com/OrangeArtc0915/test/issues?q=label%3Atool%2Fscterm

## 许可证

MIT，见 [LICENSE](LICENSE)。

<!-- CI trigger: 2026-11-07T22:08:53 -->
