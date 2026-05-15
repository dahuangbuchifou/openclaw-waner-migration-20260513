# 🖥️ OpenClaw 本地部署指南（Windows）

> 适用于 RTX 3070 8G + 32G 内存 + E盘安装
> 创建时间：2026-05-15

---

## 1. 环境要求

| 项目 | 要求 | 你的配置 |
|------|------|----------|
| 操作系统 | Windows 10/11 | ✅ |
| Node.js | v20+ | 需确认 |
| Ollama | 最新稳定版 | 需安装 |
| 内存 | 16G+ | ✅ 32G |
| 显卡 | RTX 3070 8G | ✅ |
| 磁盘空间 | 20G+（E盘） | 需确认 |

---

## 2. 安装步骤

### Step 1：安装 Ollama
1. 下载安装：https://ollama.com/download/windows
2. 默认安装即可（会自动设置环境变量）
3. 验证：打开 PowerShell，运行 `ollama --version`

### Step 2：拉取本地模型
```powershell
# 主力模型（约 4.9GB，占显存 ~5GB）
ollama pull qwen3:8b

# 备用/兜底模型（约 2.8GB，占显存 ~3GB）
ollama pull qwen3:4b
```

### Step 3：安装 OpenClaw
```powershell
npm install -g openclaw
```

### Step 4：创建目录结构
```
E:/OpenClaw/
├── workspace/          ← 工作区（放 SOUL.md、AGENTS.md 等）
├── logs/               ← 日志
└── config/             ← 配置文件
```

### Step 5：配置环境变量
在 PowerShell 中设置（或写入系统环境变量）：
```powershell
$env:OPENCLAW_GATEWAY_TOKEN = "你的随机token"
$env:BAILIAN_API_KEY = "你的百炼API Key"
$env:DEEPSEEK_API_KEY = "你的DeepSeek API Key"
```

### Step 6：复制配置文件
将 `openclaw.json` 放到 OpenClaw 配置目录：
```
%USERPROFILE%\.openclaw\openclaw.json
```

### Step 7：复制 workspace 文件
将 migration/ 目录下的文件复制到：
```
E:/OpenClaw/workspace/
```

### Step 8：启动
```powershell
openclaw start
```

---

## 3. 模型选择建议

| 场景 | 推荐模型 | 原因 |
|------|---------|------|
| 日常对话 | ollama/qwen3:8b | 本地优先，隐私好 |
| 复杂任务 | dashscope/qwen3.6-plus | 1M 上下文，能力强 |
| 长文档 | dashscope/qwen-plus-2025-07-28 | 128K 上下文 |
| 离线兜底 | ollama/qwen3:4b | 轻量，速度快 |
| 代码 | dashscope/qwen3.6-plus | 或本地 8b |

---

## 4. RTX 3070 8G 显存参考

| 模型 | Q4_K_M 大小 | KV Cache (8K ctx) | 总计 | 能否跑 |
|------|------------|-------------------|------|--------|
| qwen3:0.6b | ~0.4GB | ~0.2GB | ~0.6GB | ✅ 秒回 |
| qwen3:1.7b | ~1.1GB | ~0.4GB | ~1.5GB | ✅ 快 |
| **qwen3:4b** | ~2.8GB | ~0.8GB | ~3.6GB | ✅ 推荐兜底 |
| **qwen3:8b** | ~4.9GB | ~1.2GB | ~6.1GB | ✅ 推荐主力 |
| qwen3:14b | ~9GB | ~2GB | ~11GB | ❌ 爆显存 |

> 💡 上下文越长，KV Cache 越大。8b 模型建议 ctx ≤ 8192。

---

## 5. 与服务器配置对比

| 项目 | 服务器 | 本地 |
|------|--------|------|
| 主模型 | dashscope/qwen3.6-plus | ollama/qwen3:8b |
| 备选 | dashscope/qwen-max | dashscope/qwen3.6-plus |
| 兜底 | dashscope/qwen3.5-plus | ollama/qwen3:4b |
| 部署方式 | 云端 | 本地 Ollama |
| 隐私 | 数据出网 | 本地优先 |
| 成本 | API 费用 | 电费而已 |

---

_婉儿 整理 · 2026-05-15_ 🎋
