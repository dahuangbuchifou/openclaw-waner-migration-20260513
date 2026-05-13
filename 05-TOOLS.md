# TOOLS.md - 工具配置

_本地环境配置，根据实际情况修改_

---

## 🌐 搜索能力

### Brave Search / SearXNG
- **推荐：** 本地可安装 SearXNG（自建搜索聚合）
- **备选：** Brave Search API（需申请 API Key）

---

## 📧 消息通信

### 可选通道（按需配置）
- **钉钉** — 需创建企业应用，获取 AppKey/AppSecret
- **飞书** — 需创建应用
- **企业微信** — 需创建应用
- **Telegram Bot** — 找 @BotFather 创建
- **QQ Bot** — 需 QQ 开放平台申请

### 配置位置
OpenClaw config 中的 `channels` 部分

---

## 🎙️ 语音能力

### Edge TTS（微软）
- **推荐：** 免费，中文语音质量好
- **语音：** zh-CN-XiaoxiaoNeural

### ElevenLabs（可选）
- **状态：** 付费，质量更高
- **免费版：** 1万字符/月

---

## 📅 日程管理

### Google Calendar
- **需 OAuth 授权**
- 配置位置：`~/.openclaw/credentials/google.json`

---

## 🤖 自动化

### Cron 定时任务
- OpenClaw 内置 cron 支持
- 用于定时提醒、周期性检查

### 浏览器自动化
- OpenClaw 内置 browser 工具
- 可用于网页操作、截图等

---

## 📍 本地信息

- **用户位置：** [修改为你的城市]
- **时区：** Asia/Shanghai
- **Node 版本：** 建议 v20+

---

_最后更新：2026-05-13 · 迁移模板_
