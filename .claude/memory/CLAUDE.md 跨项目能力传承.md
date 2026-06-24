---
name: claude-md
description: 通过 CLAUDE.md + 记忆系统实现跨 AI 工具的能力继承
metadata: 
  node_type: memory
  type: feedback
  originSessionId: b4bbb150-9dd0-468b-8695-aaf6323f76c1
---

## 方案：CLAUDE.md + 记忆系统 + 初始化提示词

要让不同 AI 工具（Claude Code、Cursor、Copilot 等）在项目中"记住怎么做"，不需要靠工具自身的记忆功能，而是靠项目内文件：

### 三层结构

1. **`CLAUDE.md`**（项目根目录）
   - 任何 AI 工具打开项目最先读取的文件
   - 记录：项目简介、目录结构、关键路径、部署命令、编码规范
   - Claude Code 原生支持，其他 AI 工具也普遍支持

2. **`.claude/memory/` 记忆系统**
   - 存放详细的步骤文档（如部署流程、数据源说明）
   - MEMORY.md 作为索引

3. **初始化提示词**
   - 一段标准提示词，贴到新项目的首次会话
   - 自动创建上述两套文件结构

### 跨工具使用

这套方案不依赖特定 AI 工具的记忆功能，而是把知识写在项目文件里。
任何能读文件的 AI 工具都能继承。

新建项目时贴初始化提示词即可。
