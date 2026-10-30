# dsh-sag

dsh-sag 是 DeepSeek Harness 的 SAG 本地个人知识库插件，让 dsh 可以检索和阅读知识、上传文件、写入笔记并管理文档。

## 维护位置

本插件在 SAG 原项目仓库中统一维护，源码、issue 和使用文档都以原项目为准：

| 用途 | 地址 |
| --- | --- |
| 源码目录 | [Zleap-AI/SAG · integrations/dsh-sag](https://github.com/Zleap-AI/SAG/tree/main/integrations/dsh-sag) |
| 使用文档 | [dsh-sag 使用文档（中文）](https://github.com/Zleap-AI/SAG/blob/main/integrations/dsh-sag/docs/usage.zh.md) |
| 问题反馈 | [Zleap-AI/SAG issues](https://github.com/Zleap-AI/SAG/issues) |

本仓库不再作为独立主线开发。插件随 SAG 一起发版，版本号和兼容性由 SAG 仓库统一维护；克隆、提交和发布请在 SAG 仓库的 `integrations/dsh-sag` 目录进行。

## 兼容版本

- DeepSeek Harness：`0.1.1-rc.2`（当前 npm `latest`）
- SAG：需要包含“连接 dsh”设置和本地连接器 API

## 快速开始

确认 dsh 和 SAG 已启动，再安装并检查插件：

```sh
dsh --version
dsh plugin --profile web add @zleap-ai/dsh-sag
dsh plugin --profile web exec dsh-sag doctor
```

`doctor` 显示“SAG 已连接”即可开始使用。插件会自动发现常见本机地址，正常使用不需要准备 Python 环境或手工填写密钥。

如果没有自动发现 SAG，运行 `setup`：

```sh
# 自动发现已经启动的 SAG
dsh plugin --profile web exec dsh-sag setup

# 使用 SAG 导出的连接文件
dsh plugin --profile web exec dsh-sag setup ./sag-dsh.json

# 显式指定 SAG 地址
dsh plugin --profile web exec dsh-sag setup --url http://127.0.0.1:8000

# 检查保存后的连接
dsh plugin --profile web exec dsh-sag doctor
```

## 使用方式

- 检查 SAG 状态
- 创建和查询知识源
- 检索知识并读取原文
- 上传本地文件或写入文本笔记
- 查询、重新处理和删除文档

SAG 会通过能力清单告诉插件当前可用的操作；插件不会调用 SAG 未启用的能力。

安装完成后，直接在 dsh 中提出知识库任务，例如：

- “在我的 SAG 知识库里查找 DW-2412P30 的上传限制，并给出原文依据。”
- “把 `/Users/me/Documents/产品手册.pdf` 上传到 SAG，处理完成后总结主要内容。”
- “把下面这段会议结论作为一篇笔记写入 SAG：……”

更细的参数、命令和排错说明见 [使用文档](https://github.com/Zleap-AI/SAG/blob/main/integrations/dsh-sag/docs/usage.zh.md)。

## 更新或卸载

```sh
dsh plugin --profile web update @zleap-ai/dsh-sag
dsh plugin --profile web remove @zleap-ai/dsh-sag
```

连接失败时，请确认 SAG 正在运行，然后重新执行 `setup` 和 `doctor`。普通用户不需要配置 Python 环境。

## 参与开发

开发相关提交（代码、打包脚本、发布说明）请提到 SAG 仓库的 `integrations/dsh-sag` 目录，并在那里提交 PR 和 issue。本仓库保留历史记录，便于对照旧版本行为。
