---
name: save
description: 保存内容到 .claude/CLAUDE.md。
disable-model-invocation: true
arguments: [content]
---

## 参数

用户输入的内容: $ARGUMENTS

## 执行步骤

1. 如果 `.claude/CLAUDE.md` 不存在，先创建 `.claude/` 目录（如不存在）和空文件
2. 读取当前项目 `.claude/CLAUDE.md` 文件
3. 分析用户提供的内容，判断它属于 CLAUDE.md 的哪个章节：
   - 构建/运行命令 → `## Build & Run Commands`
   - 技术栈/依赖 → `## Tech Stack`
   - 项目结构/模块 → `## Architecture`
   - 编码规范/约定 → `## Conventions`
   - Docker/部署相关 → `## Docker 依赖管理`
   - 以上都不匹配 → 在文件末尾追加，创建合适的新章节
4. 将内容以合适格式（列表项、代码块等）添加到对应章节
5. 输出修改摘要

## 注意事项

- 保持 `.claude/CLAUDE.md` 现有的 markdown 格式和风格
- 不要重复添加已存在的内容
