---
name: overview
description: 分析项目结构并提供概览。
disable-model-invocation: true
---

## 执行步骤

1. **识别项目类型**：读取 package.json、Cargo.toml、go.mod、pom.xml 等文件确定技术栈
2. **扫描目录结构**：使用 `find` 或 `ls` 获取主要目录树（限制深度为 3 层）
3. **识别核心文件**：
   - 配置文件：`*.config.*`、`.*rc`、`*.json`
   - 入口文件：`main.*`、`index.*`、`app.*`
   - 文档文件：`README.*`、`CLAUDE.md`、`CHANGELOG.*`
4. **输出项目概览**：
   - 项目名称和描述
   - 技术栈和依赖
   - 目录结构树（精简版）
   - 核心文件列表及其用途
   - 开发命令（如有）

## 输出格式

# 项目结构

[项目名称] - [简短描述]

## 技术栈
- [技术1]: [版本]
- [技术2]: [版本]

## 目录结构
```
[精简的目录树]
```

## 核心文件
- `path/to/file` - [用途说明]
- `path/to/file` - [用途说明]

## 常用命令
- `command` - [说明]

只输出概览信息，不要执行任何修改操作。
