# OpenAI Secure Proxy (For China Environment)

这是一个专门为国内环境与 App/Web/小程序调用设计的
**OpenAI 安全代理后端**。

✔ 保护你的 OPENAI_API_KEY  
✔ 国内用户无需 VPN  
✔ 隐藏 Key，不会暴露在前端  
✔ 适用于图像识别、你画我猜、涂鸦识别、GPT 对话等  
✔ 支持 Cursor / Swift / Next.js / React / Flutter 等客户端调用

---

## 🚀 一键部署到 Vercel（推荐）

点击按钮即可 10 秒部署：

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/openai-proxy-template/example&env=OPENAI_API_KEY&project-name=openai-proxy&repository-name=openai-proxy)

---

## 📡 使用方式（你的前端这样调用即可）

```ts
fetch("https://your-app.vercel.app/api/openai", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({
    model: "gpt-4.1",
    messages: [{ role: "user", content: "Hello" }]
  })
});
```

---

## 🔑 配置环境变量

在 Vercel → Settings → Environment Variables 添加：

```
OPENAI_API_KEY = sk-xxxx
```

你的 key 永远不会暴露。

---

## 📂 项目结构（Cursor 会自动生成）

```
/app
  /api
    /openai
      route.ts
package.json
README.md
```

---

