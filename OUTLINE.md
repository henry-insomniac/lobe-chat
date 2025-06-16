## 📚 项目概览

**Lobe Chat** 是一个开源、高性能、现代化的 AI 对话 UI 与框架，基于 TypeScript 与 Next.js 构建，支持多模型、多模态、插件扩展与知识库功能 ([github.com][1])。

### 核心特性

1. **Chain of Thought（思维链可视化）**：展示 AI 推理过程，方便调试与理解&#x20;
2. **Branching Conversations（分支对话）**：支持在任意节点创建多个对话分支，形成树结构 ([github.com][2])
3. **Artifacts（多模态输出）**：支持图像、SVG、HTML 等在对话中以特殊格式展示&#x20;
4. **文件上传与知识库**：用户可上传文档、媒体，构建知识库，并在对话中引用 ([github.com][2])
5. **多模型支持 & 函数调用**：适配 OpenAI、Claude、Gemini、Ollama 等服务，同时具备插件机制 ([github.com][2])
6. **TTS/STT 与图像生成**：支持语音合成、识别及文本生成图像&#x20;
7. **PWA 与多端适配**：适配网页版、桌面端（Electron）、移动端，多端一致性体验 ([github.com][2])

---

## 📂 项目结构

```text
/
├─ apps/desktop        # 桌面客户端（Electron+React）
├─ packages/           # 核心模块：UI、图标、语音等组件
├─ src/                # Web 端源码（Next.js 主体）
├─ public/             # 静态资源
├─ docs/, README.md    # 文档与使用指南
├─ docker-compose.yml  # Docker 容器部署
└─ ...                 # CI、配置、测试等文件
```

---

## 🚀 入门指南

### 1. 克隆与安装（Web 端）

```bash
git clone https://github.com/lobehub/lobe-chat.git
cd lobe-chat
pnpm install
pnpm dev
```

运行后访问 `http://localhost:3000` 即可体验界面 。

### 2. 环境变量配置

| 变量名                 | 是否必需 | 描述                                                 |
| ------------------- | ---- | -------------------------------------------------- |
| OPENAI\_API\_KEY    | 是    | 用于 OpenAI 接口访问                                     |
| OPENAI\_PROXY\_URL  | 否    | 自定义代理地址                                            |
| ACCESS\_CODE        | 否    | 设置访问密码                                             |
| OPENAI\_MODEL\_LIST | 否    | 控制展示模型，例如 `qwen-7b-chat,+glm-6b` ([github.com][2]) |

完整变量可查看官方文档。

### 3. Docker 部署

```sh
mkdir lobe-chat-db && cd lobe-chat-db
bash <(curl -fsSL https://lobe.li/setup.sh)
docker compose up -d
```

通过 `docker-compose.yml` 文件一键部署后端与前端 。

---

## 🧩 插件与 Agent 架构

* **插件机制**：支持函数调用扩展，官方提供 `chat-plugin-template` 和 `@lobehub/chat-plugin-sdk` ([github.com][2])。
* **Agent 市场**：通过独立仓库 `lobe‑chat‑agents` 管理多种“智能代理”，如学术导师、营养顾问、旅行助手等 ([github.com][3])。

---

## 🛠 开发流程推荐

1. **设置开发环境**：推荐使用 Codespaces 或本地 `pnpm dev`
2. **添加新功能**：

   * UI：位于 `packages/ui` 中
   * 语音：在 `packages/tts`
   * 插件：参考 `chat-plugin-template` 和 SDK
3. **调试对话分支**：更新 `src/components/chat` 下的分支逻辑
4. **测试**：框架使用 Vitest，测试位于 `tests/`
5. **发布流程**：提交 PR → CI 验证 → 合并即可发布，仓库采用 semantic-release

---

## 🧭 快速功能总览

| 功能          | 快速路径或文件区域                                   |
| ----------- | ------------------------------------------- |
| 思维链渲染 (CoT) | `src/components/chain-of-thought`           |
| 对话分支逻辑      | `src/components/conversation-tree`          |
| 插件 & 函数调用   | `src/plugins/` + `@lobehub/chat-plugin-sdk` |
| 文件处理/知识库    | `src/components/knowledge-base`             |
| 多模型适配       | `src/lib/providers` 内不同 API 集成              |
| 桌面客户端       | `apps/desktop/`（Electron + React）           |

---

## ✔️ 小结

* **定位**：高可扩展、多模型、多端的 AI 聊天框架
* **适合对象**：前端开发者 / AI 应用构建者
* **快速上手**：Git + pnpm，几分钟即能本地运行并体验全部核心功能
* **扩展方式**：通过插件、模型适配和 Agent 市场，支持自定义功能和多角色交互

---

如果你是初学者，可以按以下路径学习：

1. **先运行 demo**，熟悉界面与聊天流程
2. 阅读 **核心组件代码**（CoT、分支对话、知识库）
3. **尝试添加简单插件**，理解函数调用机制
4. 进一步定制界面、添加新模型或 Desktop 端支持

有任何具体问题或想做的功能扩展，随时欢迎提问！

[1]: https://github.com/henry-insomniac?utm_source=chatgpt.com "HenryHou henry-insomniac - GitHub"
[2]: https://github.com/lobehub/lobe-chat?utm_source=chatgpt.com "Lobe Chat - an open-source, modern-design AI chat ... - GitHub"
[3]: https://github.com/lobehub/lobe-chat-agents?utm_source=chatgpt.com "lobehub/lobe-chat-agents: / Agent Index - GitHub"
