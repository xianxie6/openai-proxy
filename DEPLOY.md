# 🚀 Vercel 部署指南

## 步骤 1：推送到 GitHub

### 1.1 在 GitHub 上创建新仓库
1. 访问 [GitHub](https://github.com/new)
2. 仓库名称：`openai-proxy`（或你喜欢的名字）
3. 选择 **Public** 或 **Private**
4. **不要**勾选 "Initialize this repository with a README"
5. 点击 "Create repository"

### 1.2 推送代码到 GitHub

在终端执行以下命令（将 `YOUR_USERNAME` 替换为你的 GitHub 用户名）：

```bash
cd /Users/zhangxian/Desktop/Xian-AI/xcode/TuArt/openai-proxy

# 添加远程仓库（替换 YOUR_USERNAME 为你的 GitHub 用户名）
git remote add origin https://github.com/YOUR_USERNAME/openai-proxy.git

# 推送代码
git branch -M main
git push -u origin main
```

如果使用 SSH（推荐）：
```bash
git remote add origin git@github.com:YOUR_USERNAME/openai-proxy.git
git branch -M main
git push -u origin main
```

---

## 步骤 2：部署到 Vercel

### 2.1 访问 Vercel
1. 访问 [vercel.com](https://vercel.com)
2. 使用 GitHub 账号登录

### 2.2 导入项目
1. 点击 **"Add New..."** → **"Project"**
2. 在 "Import Git Repository" 中找到你的 `openai-proxy` 仓库
3. 点击 **"Import"**

### 2.3 配置项目
1. **Framework Preset**: 选择 **Next.js**（应该自动检测）
2. **Root Directory**: 保持默认（`./`）
3. **Build Command**: 保持默认（`npm run build`）
4. **Output Directory**: 保持默认（`.next`）

### 2.4 添加环境变量 ⚠️ 重要！
1. 在 "Environment Variables" 部分点击 **"Add"**
2. 添加以下环境变量：
   - **Name**: `OPENAI_API_KEY`
   - **Value**: `sk-你的实际API密钥`
3. 确保所有环境（Production, Preview, Development）都勾选
4. 点击 **"Add"**

### 2.5 部署
1. 点击 **"Deploy"** 按钮
2. 等待部署完成（通常 1-2 分钟）

---

## 步骤 3：获取你的 API 地址

部署完成后，你会看到：
- **Production URL**: `https://your-project.vercel.app`
- **API 端点**: `https://your-project.vercel.app/api/openai`

**保存这个 URL**，你将在 Swift App 中使用它！

---

## 步骤 4：测试 API

使用以下命令测试你的代理是否工作：

```bash
curl -X POST https://your-project.vercel.app/api/openai \
  -H "Content-Type: application/json" \
  -d '{
    "model": "gpt-3.5-turbo",
    "messages": [{"role": "user", "content": "Hello"}]
  }'
```

如果返回 JSON 响应，说明部署成功！🎉

---

## 常见问题

### Q: 部署失败怎么办？
A: 检查：
- 环境变量 `OPENAI_API_KEY` 是否正确设置
- API Key 是否有效
- 查看 Vercel 的部署日志

### Q: 如何更新代码？
A: 推送新代码到 GitHub，Vercel 会自动重新部署

### Q: 如何查看日志？
A: 在 Vercel 项目页面 → "Deployments" → 点击部署 → "Functions" → 查看日志

---

## ✅ 完成！

现在你可以在 Swift App 中使用这个代理 URL 了！

