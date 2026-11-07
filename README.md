# SCM 单仓库 · 多项目体验模拟

这个仓库用来验证一件事：**只维护一个 git 仓库，但每个附属工具看起来、用起来都像独立仓库。**

主程序（Server Core Manager）与附属工具共用同一个仓库，但通过「目录 + 标签前缀 + 过滤链接 + 按目录的 CI/归属」拆出独立感。

## 工具索引

| 工具 | 源码目录 | 提交历史 | Issue | 发布 |
|---|---|---|---|---|
| **scterm**（终端多路复用） | [tools/scterm](https://github.com/OrangeArtc0915/test/tree/main/tools/scterm) | [commits](https://github.com/OrangeArtc0915/test/commits/main/tools/scterm) | [tool/scterm](https://github.com/OrangeArtc0915/test/issues?q=label%3Atool%2Fscterm) | [scterm-v*](https://github.com/OrangeArtc0915/test/tags?q=scterm-) |
| **CraftDock**（Minecraft 服务端管理器） | [tools/craftdock](https://github.com/OrangeArtc0915/test/tree/main/tools/craftdock) | [commits](https://github.com/OrangeArtc0915/test/commits/main/tools/craftdock) | [tool/craftdock](https://github.com/OrangeArtc0915/test/issues?q=label%3Atool%2Fcraftdock) | [craftdock-v*](https://github.com/OrangeArtc0915/test/tags?q=craftdock-) |
| **TuiMonitor** | [tools/tuimonitor](https://github.com/OrangeArtc0915/test/tree/main/tools/tuimonitor) | [commits](https://github.com/OrangeArtc0915/test/commits/main/tools/tuimonitor) | [tool/tuimonitor](https://github.com/OrangeArtc0915/test/issues?q=label%3Atool%2Ftuimonitor) | [tuimonitor-v*](https://github.com/OrangeArtc0915/test/tags?q=tuimonitor-) |
| **SCM 主程序** | [gui](https://github.com/OrangeArtc0915/test/tree/main/gui) | [commits](https://github.com/OrangeArtc0915/test/commits/main/gui) | [tool/scm](https://github.com/OrangeArtc0915/test/issues?q=label%3Atool%2Fscm) | [scm-v*](https://github.com/OrangeArtc0915/test/tags?q=scm-) |

## 约定

- **源码**：每个工具一个目录，目录内自带 `README.md` / `LICENSE` / `CHANGELOG.md` / 独立版本文件。
- **标签**：`scm-v2.1.0`、`scterm-v0.1.0`、`craftdock-v1.4.0`；每个工具的「发布页」= 自己的 tag 页面。
- **Issue/PR**：统一用 `tool/<名称>` 标签，配合上面的过滤链接，看起来就是各自的 issue 列表。
- **CI**：按 `paths` 过滤，只跑被改动工具的测试；打 `scterm-v*` 标签只触发 scterm 的构建与发布。
- **归属**：`.github/CODEOWNERS` 按目录指定 owner。
- **清单**：根目录 [plugins.json](plugins.json) 给主程序做插件版本/下载检查。

## 只检出某个工具

```bash
git clone --filter=blob:none --sparse https://github.com/OrangeArtc0915/test.git
cd test
git sparse-checkout set tools/scterm
```

## 限制

Star / Watch / Fork / Insights / 权限 / Webhook / Ruleset 仍是仓库级，无法按目录拆；Releases 列表也共用，只能靠 tag 页面制造独立感。真需要这些时，把 `tools/<名称>` 拆成独立仓库即可。
