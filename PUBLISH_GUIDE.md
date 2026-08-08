# ACCA F9 电子书发布指南

## 背景

这本电子书基于 [Quarto](https://quarto.org/) 制作，源代码存放在本地，通过 Git 推送到 GitHub，再利用 GitHub Pages 发布为公开网站。

---

## 关键网址

| 用途 | 网址 |
|------|------|
| 📖 **电子书网站** | https://yehuiapple.github.io/ACCA-/ |
| 🔧 **GitHub 仓库**（源代码） | https://github.com/yehuiapple/ACCA- |
| ⚙️ **GitHub Pages 设置**（启用网站） | https://github.com/yehuiapple/ACCA-/settings/pages |
| 🔑 **SSH 密钥管理**（添加电脑公钥） | https://github.com/settings/ssh/new |
| 💻 **本地项目文件夹** | `/Users/yehui/坚果云/2_Area/quarto_book` |

---

## 发布流程总结

### 第一步：修改内容（本地）

在本地项目文件夹中编辑 `.qmd` 或 `.md` 文件（位于 `body/` 目录下），修改电子书章节内容。

### 第二步：重新渲染

在终端中运行以下命令，将修改后的内容生成 HTML 网页文件（输出到 `docs/` 目录）：

```bash
cd /Users/yehui/坚果云/2_Area/quarto_book
quarto render
```

### 第三步：提交并推送

将渲染好的文件推送到 GitHub：

```bash
cd /Users/yehui/坚果云/2_Area/quarto_book
git add -A
git commit -m "更新内容描述"
git push origin main
```

### 第四步：等待自动发布

推送成功后，GitHub Pages 会自动更新网站（通常 1-2 分钟内生效）。访问 https://yehuiapple.github.io/ACCA-/ 即可查看最新内容。

---

## 首次配置备忘（已完成，仅供参考）

以下步骤是首次发布时完成的，**以后无需重复操作**：

1. **SSH 密钥配置**：在 `/Users/yehui/.ssh/id_ed25519.pub` 生成了公钥，已添加到 GitHub 账号（https://github.com/settings/ssh/new），实现了免密码推送。
2. **远程仓库绑定**：本地仓库的远程地址已设为 `git@github.com:yehuiapple/ACCA-.git`（SSH 方式）。
3. **站点 URL 配置**：`_quarto.yml` 中 `site-url` 设为 `https://yehuiapple.github.io/ACCA-/`。
4. **GitHub Pages 启用**：需要在仓库设置中，将 Pages 来源设为 `main` 分支的 `/docs` 文件夹。

---

## 常见问题

### 推送时提示权限错误？
说明 SSH 密钥失效或未配置，检查 `~/.ssh/id_ed25519.pub` 是否已添加到 GitHub。

### 网站显示 404？
检查 GitHub Pages 是否已启用：进入 https://github.com/yehuiapple/ACCA-/settings/pages，确认 Source 为 `Deploy from a branch`，Branch 为 `main`，文件夹为 `/docs`。

### 本地如何预览？
在终端运行：
```bash
cd /Users/yehui/坚果云/2_Area/quarto_book
quarto preview
```
或直接打开 `docs/index.html` 文件。

---

> 📅 最后更新：2026-08-08
