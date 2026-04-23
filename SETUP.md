# Dev Digest — 一次性部署指南

你只需要跟着这份文档走一遍，之后就全自动了。总共大概 15 分钟。

---

## 第 1 步：在 GitHub 上创建仓库

1. 浏览器打开 https://github.com/new
2. 填写：
   - **Owner**: `jerryni`
   - **Repository name**: `dev-digest`
   - **Visibility**: Public（必须公开，GitHub Pages 免费版只支持公开仓库）
   - **Initialize**: 三个选项都**不要勾**（README/license/gitignore 都已经在本地准备好了）
3. 点 **Create repository**

## 第 2 步：创建 Personal Access Token (PAT)

1. 打开 https://github.com/settings/tokens?type=beta
2. **Generate new token → Fine-grained token**
3. 填写：
   - **Token name**: `dev-digest-daily-push`
   - **Expiration**: 90 days（到期前我会提醒你换）
   - **Repository access**: "Only select repositories" → 选 `dev-digest`
   - **Permissions → Repository permissions**：
     - **Contents**: `Read and write`
     - **Metadata**: `Read-only`（默认）
     - 其他保持 No access
4. 点 **Generate token**，把 token 复制下来（只会显示一次）
5. **把 token 临时粘到一个安全的地方**，下一步要用

## 第 3 步：把本地项目 push 到 GitHub

打开终端（Terminal.app），依次执行：

```bash
# 1. 把项目从 demos 下挪到你想要的位置
mv "/Users/ni/Github/demos/dev-digest" "/Users/ni/Github/dev-digest"

# 2. 进入项目目录
cd /Users/ni/Github/dev-digest

# 3. 初始化 git（如果还没有）
git init -b main

# 4. 配置 commit 身份（用你 GitHub 账户的邮箱）
git config user.name "Jerry Ni"
git config user.email "jerryni2014@gmail.com"

# 5. 把 PaperMod 主题作为子模块拉下来
git submodule add -b master https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod

# 6. 配置 remote，用 HTTPS + PAT 格式
#    把 <YOUR_PAT_HERE> 换成第 2 步复制的 token
git remote add origin https://jerryni:<YOUR_PAT_HERE>@github.com/jerryni/dev-digest.git

# 7. 首次 commit + push
git add -A
git commit -m "init: Dev Digest trilingual blog"
git push -u origin main
```

> ⚠️ 安全提示：token 嵌在 remote URL 里虽然方便，但会被 macOS 钥匙串缓存，后续 push 就不需要再输了。如果你想更规范，可以用 `git credential-osxkeychain` 存储，但对个人项目这样够用。

## 第 4 步：启用 GitHub Pages

1. 打开 https://github.com/jerryni/dev-digest/settings/pages
2. **Source** 选：`GitHub Actions`（**不要**选 "Deploy from a branch"）
3. 保存

几秒后，Actions tab 会自动触发第一次构建。你可以在 https://github.com/jerryni/dev-digest/actions 看进度。

## 第 5 步：验证站点上线

构建成功后（大约 2-3 分钟），打开：

- 中文版：https://jerryni.github.io/dev-digest/zh/
- 日文版：https://jerryni.github.io/dev-digest/ja/
- English: https://jerryni.github.io/dev-digest/en/

如果看到今日示例文章，说明整条流水线已经跑通了 🎉

## 第 6 步：设置每日定时任务

**这步让我来做**——回到 Claude 对话，告诉我"设置每日定时任务"，我会用 Cowork 的 schedule 功能帮你建一个东京时间每天早上 7:00 触发的任务，自动执行 `scripts/daily-digest.md` 里定义的流程。

---

## 日常维护

### 手动触发一次（比如某天 Claude 漏掉了）

```bash
cd /Users/ni/Github/dev-digest
# 打开 Claude，说："帮我生成今天的 dev-digest"
```

### 查看最近部署状态

https://github.com/jerryni/dev-digest/actions

### PAT 到期前更换

90 天后会收到 GitHub 提醒邮件。到时候：
1. 重新生成一个 PAT（重复第 2 步）
2. 更新 remote URL：
   ```bash
   cd /Users/ni/Github/dev-digest
   git remote set-url origin https://jerryni:<NEW_PAT>@github.com/jerryni/dev-digest.git
   ```

### 想要修改首页介绍/主题配色/菜单

改 `hugo.toml` 里对应的 `[languages.xx.params]` 或 `[params]` 段落，push 后自动生效。

### 新增第 4 种语言

1. 在 `hugo.toml` 加 `[languages.xx]` 区块
2. 复制 `content/_index.*.md` 和 `content/archives.*.md` 并改语言后缀
3. 更新 `scripts/daily-digest.md` 里的生成流程

---

## 故障排查

**Actions 构建失败 · "submodule not found"**
→ PaperMod 子模块没正确添加。重新执行：
```bash
git submodule update --init --recursive
git add .gitmodules themes/
git commit -m "fix: add PaperMod submodule"
git push
```

**Pages 404**
→ 第 4 步 Source 没选 "GitHub Actions"。回去改一下。

**Push 报 403 / "Permission denied"**
→ PAT 权限不对，或者仓库 owner/name 写错了。去 https://github.com/settings/tokens 检查 token 对 `dev-digest` 有没有 `Contents: Read and write` 权限。

**三语 URL 有一个 404**
→ 检查 `content/posts/YYYY-MM-DD/index.xx.md` 是否三个都创建了。只创建了两个的话，那个语言会 404。
