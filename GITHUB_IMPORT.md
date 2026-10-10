# 发布到私有 GitHub 仓库（文档导入操作说明）

期望仓库：`guog/ai-native-mes-framework`，**private**。如果目前 GitHub 连接没有创建仓库权限，请先在 GitHub 网站选择 **New repository**：

1. Owner：`guog`；Repository name：`ai-native-mes-framework`。
2. Visibility：**Private**；不要选择公开。
3. 创建空仓库（建议不要预生成 README / LICENSE，以免首次推送分支冲突）。
4. 在本目录执行下面的命令；请自行使用已经认证的 GitHub 凭据，不要将 Token 粘贴到 ChatGPT 对话中。

```bash
git init -b main
git add .
git commit -m "docs: establish AI Native MES architecture specification v0.2"
git remote add origin https://github.com/guog/ai-native-mes-framework.git
git push -u origin main
```

建议先检查 `git status` 和 `git diff --cached --stat`，确认只包含公开允许提交的架构文档，无密钥和客户数据。

**注意：** 此文件只是未完成仓库创建时的可重复操作说明，不能证明 GitHub 已创建或提交成功。
