# 随机人格生成器 GitHub Pages 版本

这个目录是纯静态页面，可以直接发布到 GitHub Pages / Cloudflare Pages。

当前 Pages 地址：

https://xy177.github.io/limbuscompany-any/

页面不包含 QQ 机器人控制功能，也不包含任何 API Key。它直接读取仓库内的静态缓存文件：

- `data/random-identity-cache.json`
- `assets/random-identity.js`

所有随机生成逻辑都在访问者浏览器本地执行，不需要机器人服务器公开端口，也不需要额外 HTTPS API。

## 发布到 GitHub Pages

1. 新建一个公开仓库，例如 `random-limbus-identity`。
2. 把本目录里的 `index.html`、`assets/`、`data/`、`.nojekyll` 上传到仓库根目录。
3. 在仓库 `Settings -> Pages` 中选择从 `main` 分支根目录发布。
4. 等待 GitHub Pages 给出 `https://用户名.github.io/random-limbus-identity/` 地址。

如果不想公开仓库，也可以改用 Cloudflare Pages、Vercel 或 Netlify，文件内容不需要变化。

## 更新缓存

在机器人项目根目录执行：

```bash
npm run build:github-random
```

然后提交并推送本目录变化即可。
