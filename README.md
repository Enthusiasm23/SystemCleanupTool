# System Cleanup Tool

System Cleanup Tool 是一个专为 Windows 用户设计的系统清理工具集合。这些工具旨在简化系统优化过程，通过移除冗余文件，释放磁盘空间，进而提升系统性能和用户效率。

## 工具列表

目前，该仓库提供以下工具：

- `ClearSystemJunk.bat`：用于移除 Windows 系统中的临时文件、日志和缓存文件。

更多工具将会添加至该系列，以覆盖更全面的系统维护任务，例如磁盘碎片整理、注册表清理和启动项管理。

## 使用说明

### ClearSystemJunk

`ClearSystemJunk` 是一个高效的批处理脚本，专门用于清除系统垃圾文件，以优化 Windows 运行效率。

#### 功能

- 删除 `.tmp`, `.log`, `.old` 等临时文件
- 清空回收站
- 清理 Windows 更新缓存
- 清除系统日志
- 清理个人临时文件和互联网缓存

#### 如何使用

- [`ClearSystemJunk.bat`](ClearSystemJunk.bat)：可直接下载并以管理员权限运行的脚本。
- [`ClearSystemJunk.txt`](ClearSystemJunk.txt)：以文本形式查看的脚本版本。下载后需将后缀名改为 `.bat`。

运行任何脚本前，请确保关闭可能干扰执行的系统保护软件，如杀毒程序或系统优化工具。

## 注意事项

在运行脚本前，请确保您已备份所有重要数据。虽然我们尽可能确保工具安全可靠，但系统清理工具的使用可能带来风险。

## 贡献

我们欢迎并鼓励社区贡献，无论是功能建议、代码优化还是问题报告。请通过 GitHub Issues 或 Pull Requests 与我们分享您的想法。

## 许可证

本项目采用 [MIT 许可证](LICENSE)。更多详情请查阅许可证文件。
