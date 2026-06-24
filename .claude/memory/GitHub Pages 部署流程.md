---
name: github-pages
description: 将作品集网站部署到 GitHub Pages 的完整步骤
metadata: 
  node_type: memory
  type: feedback
  originSessionId: b4bbb150-9dd0-468b-8695-aaf6323f76c1
---

## 标准部署步骤

1. **准备工作**
   - 确保当前目录已 `git init`
   - 确保文件名是 `index.html`（GitHub Pages 只识别这个文件名）
   - 只推送 `index.html` + `style.css` 两个文件，不推原始数据/方案文档

2. **提交代码**
   - `git add index.html style.css`
   - `git commit -m "init: 个人作品集网站"`

3. **创建远程仓库**
   - 通过 GitHub API 创建：`curl -x http://127.0.0.1:7890 -H "Authorization: token <TOKEN>" -d '{"name":"portfolio","private":false}' ...`
   - 注意：梯子走 `127.0.0.1:7890` 代理

4. **配置远程并推送**
   - `git branch -m master main`（如果默认分支是 master）
   - `git remote add origin https://github.com/xiaolu-fzu/portfolio.git`
   - `git -c http.proxy=http://127.0.0.1:7890 push -u origin main`

5. **启用 GitHub Pages**
   - 通过 API 设置 Pages：`POST /repos/xiaolu-fzu/portfolio/pages`，指定 `source.branch=main`
   - 等待约 30-60 秒构建完成
   - 访问 `https://xiaolu-fzu.github.io/portfolio/` 验证
