# 随机人格生成器 GitHub Pages 版本

这个目录是纯静态页面，可以直接发布到 GitHub Pages / Cloudflare Pages。

页面本身不保存人格缓存，不包含 QQ 机器人控制功能，也不包含任何 API Key。它只通过浏览器请求机器人服务器公开的随机人格 API：

- `GET /api/health`
- `POST /api/random`

## 必要条件

GitHub Pages 默认使用 HTTPS，所以服务器 API 也必须是 HTTPS。不能直接使用 `http://a.mcstory.cc:8791`，否则浏览器通常会按混合内容拦截。

推荐二选一：

- 用 Cloudflare Tunnel 给 `http://127.0.0.1:8791` 暴露一个 HTTPS 域名。
- 让已有 nginx / 面板添加 HTTPS 反代，把某个路径或子域名转发到机器人服务器的 `8791` 服务。

## 配置 API 地址

编辑 `config.js`：

```js
window.RANDOM_IDENTITY_API_BASE = "https://你的公网API域名";
```

不要在末尾加 `/api`。页面会自动请求：

```text
https://你的公网API域名/api/health
https://你的公网API域名/api/random
```

## 发布到 GitHub Pages

1. 新建一个公开仓库，例如 `random-limbus-identity`。
2. 把本目录里的 `index.html`、`config.js`、`.nojekyll` 上传到仓库根目录。
3. 在仓库 `Settings -> Pages` 中选择从 `main` 分支根目录发布。
4. 等待 GitHub Pages 给出 `https://用户名.github.io/random-limbus-identity/` 地址。

如果不想公开仓库，也可以改用 Cloudflare Pages、Vercel 或 Netlify，文件内容不需要变化。
