---
name: git-push-init
description: 初始化 Git 仓库并推送到 GitHub。
disable-model-invocation: true
allowed-tools: Bash(git *) Bash(gh *)
arguments: [repo, visibility]
---

## 参数

仓库名: $repo（如果未提供，使用当前目录名）
可见性: $visibility（`public` 或 `private`，如果未提供默认 `private`）

## 执行步骤

1. 检查当前目录是否已是 git 仓库，如果是则停止并告知用户
2. 如果项目根目录没有 .gitignore，根据项目类型（Java/Node/Python 等）自动创建一个合适的 .gitignore
3. 运行 `git init`
4. 运行 `git add -A`
5. 运行 `git status` 确认暂存内容合理
6. 创建初始提交，commit message 为 "Initial commit"
7. 使用 `gh repo create <仓库名> --<public|private> --source=. --push` 创建远程仓库并推送
8. 输出仓库地址

## 注意事项

- 使用 `gh auth status` 先确认 GitHub CLI 已认证
- 不要提交 .env、credentials 等敏感文件，如果发现要提醒用户
- commit message 末尾不要加 Co-Authored-By
