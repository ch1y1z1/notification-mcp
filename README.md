# 消息推送服务 (MCP)

[![PyPI](https://img.shields.io/pypi/v/notification-mcp.svg)](https://pypi.org/project/notification-mcp/)

这是一个使用 [FastMCP](https://github.com/ch1y1z1/fastmcp) 框架构建的消息推送服务集合。它支持 Bark 和 PushDeer。

![show](image.png)

## 使用

这个包提供了两个主要命令：`mcp-bark` 和 `mcp-pushdeer`。你可以使用像 `uvx` 或 `pipx` 这样的工具来运行它们。

**使用 `uvx` 的例子：**

```bash
# 运行 Bark 服务
# 这将启动 Bark 通知的 MCP 服务器
uvx --from notification_mcp mcp-bark

# 运行 PushDeer 服务
# 这将启动 PushDeer 通知的 MCP 服务器
uvx --from notification_mcp mcp-pushdeer
```

一旦服务启动，你就可以使用 FastMCP 客户端或其他兼容方法来与工具（如 `send_message`）进行交互。

## 环境变量

在运行命令之前，请配置以下环境变量：

**对于 Bark (`mcp-bark`）：**

*   `BARK_DEVICE_KEYS`: **必需**。逗号分隔的 Bark 设备密钥列表（例如 `key1,key2`）。
*   `BARK_SERVER`: 可选。自建 Bark 服务器 URL，默认为 `https://api.day.app`。

**对于 PushDeer (`mcp-pushdeer`）：**

*   `PUSHDEER_KEYS`: **必需**。逗号分隔的 PushDeer 密钥列表（例如 `keyA,keyB`）。
*   `PUSHDEER_SERVER`: 可选。自建 PushDeer 服务器 URL，默认为 `https://api2.pushdeer.com`。

## 功能

### Bark 服务 (`mcp-bark`)

提供以下工具：

*   **`send_message(title: str, content: str) -> str`**: 向所有配置的 Bark 设备发送带有指定标题和内容的通知。

### PushDeer 服务 (`mcp-pushdeer`)

提供以下工具：

*   **`send_message(text: str, desp: Optional[str] = None, type: str = 'text', pushkey: Optional[str] = None) -> str`**: 发送消息。`type` 可以是 'text'、'markdown' 或 'image'（其中 `text` 是图像 URL）。
*   **`send_markdown(markdown: str, desp: Optional[str] = None, pushkey: Optional[str] = None) -> str`**: 一个发送 Markdown 消息的便捷工具。
*   **`send_image(image_url: str, desp: Optional[str] = None, pushkey: Optional[str] = None) -> str`**: 一个通过 URL 发送图像消息的便捷工具。

## 许可

MIT