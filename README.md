# Course Simulator · 静态托管版（GitHub Pages 等）

本目录内容为**纯静态文件**（单文件 HTML，数据已内联 2026 秋 2079 门 + 三学期结构），
无需服务器即可在任意静态托管上线。

| 文件 | 说明 |
|---|---|
| `index.html`   | 完整版（含生物气溶胶推荐+智能生成方案） |
| `generic.html` | 通用版（无研究方向推荐） |
| `README.md`    | 本说明 |

## 部署（任选其一）

### GitHub Pages（推荐）
1. 新建仓库（如 `course-simulator`），把本目录 3 个文件推送上去（`index.html` 放根目录即可）。
2. 仓库 Settings → **Pages** → Source 选 `Deploy from a branch` → 分支 `main` + 目录 `/ (root)` → Save。
3. 等 1~2 分钟，访问 `https://<你的用户名>.github.io/<仓库名>/` 即上线。
   （子路径：`/generic.html` 打开通用版。）

### Netlify / Vercel（拖拽即用）
- Netlify：把本目录（或 index.html 单文件）**拖进** https://app.netlify.com/drop  → 立即获得 https URL。
- Vercel：`vercel deploy` 或拖拽导入同样可行。

### Gitee Pages / 其它静态空间
- 将 `index.html` 放到任意静态目录（如 七牛/OSS/服务器 web 根），直接访问即可。

## 托管版行为说明（与本地 exe 版差异）
- **一切数据仍只在浏览器本地**：选课单/设置存浏览器 localStorage，不动服务器、不上传（符合免责声明）。
- **协议同意**走 cookie（https 下正常），清除站点数据会重新弹出。
- **无后端接口**：页面里的“退出/心跳”请求会 404（浏览器 console 可见一次报错，无碍）。
- **退出关闭标签的行为差异（浏览器安全限制）**：从本页点开的标签可被程序自动关闭并回到“新建标签页”；**地址栏直接输入网址/书签进入**的标签，浏览器禁止程序关闭，且**禁止网页跳转 edge://newtab / chrome://newtab 等内部地址**（会报 `Not allowed to load local resource`）——此时“退出”会切换到**深色整屏“已退出 · 请手动关闭本标签页”**状态（无空白页、无控制台报错），手动关掉标签即可。
- **多学期数据更新**：重新生成单文件后覆盖 `index.html` 推送即可（无需改代码）。
- **跨设备不共享**：localStorage 按域名隔离，换设备需用“导出选课单(txt)→导入”迁移。

## 更新频率
构建脚本：`node build_single_file.js`（完整版）、`node build_single_file.js --generic`（通用版）→ 覆盖本目录后推送。
