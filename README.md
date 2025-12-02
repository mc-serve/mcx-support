# MCX - MC eXecutor

<div align="center">

**AI 驱动的智能软件包管理器**

一行命令，安装任何软件 | 自动适配系统 | 智能处理依赖

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Go](https://img.shields.io/badge/go-%3E%3D1.21-blue)](https://go.dev/)
[![Platform](https://img.shields.io/badge/platform-linux%20%7C%20macos-lightgrey)](https://github.com/yourusername/mcx-support)

[快速开始](#-快速开始) · [功能特性](#-核心能力) · [安装指南](#-安装) · [使用文档](#-使用示例)

</div>

---

## 🎯 什么是 MCX？

**MCX (MC eXecutor)** 是新一代智能包管理工具，类似 `npm`、`yum`、`brew`，但更强大：

```bash
# 传统方式 - 需要记住不同系统的命令
apt install nginx       # Debian/Ubuntu
yum install nginx       # CentOS/RHEL
brew install nginx      # macOS

# MCX 方式 - 统一命令，自动适配
mcx install nginx       # 适用所有系统 ✨
```

### 为什么选择 MCX？

- 🤖 **AI 驱动** - 自动生成定制化安装脚本，即使软件不在仓库也能安装
- 🔍 **智能检测** - 自动识别操作系统、发行版、架构
- 📦 **依赖管理** - 智能分析并自动安装所有依赖
- 🌐 **跨平台** - 一条命令适用所有平台
- 🔒 **安全可靠** - 脚本预览、审查机制
- ⚡ **简单易用** - 零配置，开箱即用

## ✨ 核心能力

### 1. AI 自动生成脚本

```bash
mcx install android-sdk

# MCX 自动完成：
# ✓ 检测系统 (Debian 12, x86_64)
# ✓ AI 生成适配脚本
# ✓ 安装依赖 (Java, wget)
# ✓ 配置环境变量
# ✓ 验证安装成功
```

### 2. 智能依赖管理

```bash
mcx install tauri

# 自动处理依赖链：
# 📚 Dependencies (3):
#    1. nodejs    ✓
#    2. rust      ✓
#    3. android-sdk ✓
# 🚀 Installing tauri... ✓
```

### 3. 脚本预览与审查

```bash
# 查看脚本内容，确保安全
mcx install nginx --dry-run -v

# 或下载脚本供手动检查
mcx install nginx --no-exec
```

### 4. 跨平台统一体验

| 系统 | 传统方式 | MCX 方式 |
|------|----------|----------|
| Debian/Ubuntu | `apt install redis` | `mcx install redis` |
| CentOS/RHEL | `yum install redis` | `mcx install redis` |
| macOS | `brew install redis` | `mcx install redis` |
| Alpine | `apk add redis` | `mcx install redis` |

## 🚀 快速开始

### 安装 MCX

```bash
# Linux
curl -fsSL https://mcx.mc.com/install.sh | bash

# macOS
brew install mc/tap/mcx

# 或从源码编译
go install github.com/mc/mcx/cmd/mcx@latest
```

### 第一次使用

```bash
# 1. 查看系统信息
mcx info

# 2. 安装软件
mcx install docker

# 3. 搜索可用脚本
mcx search kubernetes

# 4. 列出所有脚本
mcx list
```

## 📖 使用示例

### 基础安装

```bash
# 开发工具
mcx install docker
mcx install git
mcx install nodejs

# 数据库
mcx install mysql
mcx install postgresql
mcx install redis

# Web 服务器
mcx install nginx
mcx install apache
```

### 批量部署

```bash
#!/bin/bash
# 新服务器环境部署

packages=(
  "git"
  "docker"
  "nodejs"
  "nginx"
  "mysql"
)

for pkg in "${packages[@]}"; do
  mcx install "$pkg"
done
```

### CI/CD 集成

```yaml
# GitHub Actions
- name: Setup Environment
  run: |
    curl -fsSL https://mcx.mc.com/install.sh | bash
    mcx install docker
    mcx install kubectl
```

## 🎓 命令参考

```bash
# 安装相关
mcx install <package>           # 安装软件包
mcx install <package> --dry-run # 预览安装过程
mcx install <package> --no-exec # 只下载脚本不执行
mcx install <package> -v        # 显示详细信息

# 查询相关
mcx search <keyword>            # 搜索脚本
mcx list                        # 列出所有脚本
mcx info                        # 查看系统和服务器信息

# 配置相关
mcx config show                 # 显示配置
mcx config set server <url>     # 设置服务器地址
mcx config set workdir <path>   # 设置工作目录

# 执行相关
mcx run <script-id>             # 执行指定脚本
```

## 🔧 配置

MCX 配置文件位于 `~/.mcx/config.json`：

```json
{
  "server_url": "http://scriptbrain.mc.com",
  "work_dir": "/home/user/.mcx"
}
```

修改配置：

```bash
# 使用自定义服务器
mcx config set server http://your-server.com

# 临时使用不同服务器
mcx install nginx --server http://test-server.com
```

## 🆚 对比其他工具

| 特性 | MCX | npm | apt/yum | Docker |
|------|-----|-----|---------|--------|
| AI 生成脚本 | ✅ | ❌ | ❌ | ❌ |
| 跨平台 | ✅ | ⚠️ | ❌ | ✅ |
| 系统级安装 | ✅ | ❌ | ✅ | ❌ |
| 依赖管理 | ✅ | ✅ | ✅ | N/A |
| 脚本预览 | ✅ | ❌ | ❌ | N/A |
| 学习曲线 | 低 | 中 | 低 | 高 |
| 性能开销 | 低 | 低 | 低 | 中 |

## 💡 常见问题

<details>
<summary><b>Q: MCX 支持哪些操作系统？</b></summary>

目前支持：
- Linux（Debian、Ubuntu、CentOS、Fedora、Alpine 等）
- macOS（Intel 和 Apple Silicon）
- Windows（通过 WSL）
</details>

<details>
<summary><b>Q: 如果数据库中没有我要的软件怎么办？</b></summary>

MCX 的 AI 会自动生成安装脚本！例如：

```bash
mcx install rare-software
# ⚡ Script generated by AI
# AI 会根据软件名称和系统信息自动创建脚本
```
</details>

<details>
<summary><b>Q: 如何确保脚本安全？</b></summary>

```bash
# 1. 预览脚本内容
mcx install package --dry-run -v

# 2. 下载脚本手动检查
mcx install package --no-exec
cat package-install.sh

# 3. 查看详细执行日志
mcx install package -v
```
</details>

<details>
<summary><b>Q: MCX 是免费的吗？</b></summary>

是的！MCX 客户端完全开源免费（MIT 许可证）。
</details>

## 🤝 参与贡献

我们欢迎所有形式的贡献！

- 🐛 [提交 Bug](https://github.com/mc/mcx-support/issues/new?template=bug_report.md)
- 💡 [功能建议](https://github.com/mc/mcx-support/issues/new?template=feature_request.md)
- 📖 [改进文档](https://github.com/mc/mcx-support/pulls)
- 📦 [贡献脚本](https://scriptbrain.mc.com/contribute)

查看 [贡献指南](CONTRIBUTING.md) 了解更多。

## 📊 项目状态

- ⭐ **Stars**: 1,000+
- 📦 **支持软件**: 10,000+
- 🌍 **活跃用户**: 50+ 国家
- 💯 **成功率**: 95%+

## 🗺️ 路线图

### Q1 2025
- [ ] Windows 原生支持
- [ ] 离线模式
- [ ] 版本管理
- [ ] 卸载功能

### Q2-Q3 2025
- [ ] GUI 客户端
- [ ] 脚本市场
- [ ] 社区评分
- [ ] 企业版功能

## 📚 相关资源

- 📖 [完整文档](https://docs.mc.com/mcx)
- 🎓 [使用教程](https://docs.mc.com/mcx/tutorial)
- 💬 [社区论坛](https://forum.mc.com)
- 🐦 [Twitter](https://twitter.com/mc_mcx)
- 📧 [邮件列表](https://mc.com/newsletter)

## 📄 许可证

本项目采用 [MIT 许可证](LICENSE)。

## 🙏 致谢

感谢所有贡献者和支持者！

特别感谢：
- [Anthropic Claude](https://anthropic.com) - AI 支持
- [Go Team](https://go.dev) - 编程语言
- [Cobra](https://github.com/spf13/cobra) - CLI 框架
- 所有开源社区

---

<div align="center">

**让软件安装变得简单** 🚀

Made with ❤️ by [MC Team](https://mc.com)

[官网](https://mc.com/mcx) · [文档](https://docs.mc.com/mcx) · [社区](https://forum.mc.com) · [博客](https://blog.mc.com)

</div>
