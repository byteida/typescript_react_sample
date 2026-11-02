# React + TypeScript + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Oxc](https://oxc.rs)
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/)

## React Compiler

The React Compiler is not enabled on this template because of its impact on dev & build performances. To add it, see [this documentation](https://react.dev/learn/react-compiler/installation).

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type-aware lint rules:

```js
export default defineConfig([
  globalIgnores(["dist"]),
  {
    files: ["**/*.{ts,tsx}"],
    extends: [
      // Other configs...

      // Remove tseslint.configs.recommended and replace with this
      tseslint.configs.recommendedTypeChecked,
      // Alternatively, use this for stricter rules
      tseslint.configs.strictTypeChecked,
      // Optionally, add this for stylistic rules
      tseslint.configs.stylisticTypeChecked,

      // Other configs...
    ],
    languageOptions: {
      parserOptions: {
        project: ["./tsconfig.node.json", "./tsconfig.app.json"],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
]);
```

You can also install [eslint-plugin-react-x](https://npmx.dev/package/eslint-plugin-react-x) and [eslint-plugin-react-dom](https://npmx.dev/package/eslint-plugin-react-dom) for React-specific lint rules:

```js
// eslint.config.js
import reactX from "eslint-plugin-react-x";
import reactDom from "eslint-plugin-react-dom";

export default defineConfig([
  globalIgnores(["dist"]),
  {
    files: ["**/*.{ts,tsx}"],
    extends: [
      // Other configs...
      // Enable lint rules for React
      reactX.configs["recommended-typescript"],
      // Enable lint rules for React DOM
      reactDom.configs.recommended,
    ],
    languageOptions: {
      parserOptions: {
        project: ["./tsconfig.node.json", "./tsconfig.app.json"],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
]);
```

# Windows + VS Code + React + pnpm 开发环境搭建

这次采用一套现代化的前端开发环境，从零开始搭建，适合 React、Next.js、TypeScript 等项目。

最终技术栈

Logo Windows 11 – Logos PNG

Windows 10/11

操作系统

File:Visual Studio Code 1.35 icon.svg - Wikimedia Commons

VS Code

代码编辑器

Node.js Logo PNG, AI, EPS, CDR, PDF, SVG - iconLogoVector

Node.js LTS

运行环境

Pnpm Logo PNG Vectors Free Download

pnpm

包管理器

File:React.svg - Wikimedia Commons

React

前端框架

TypeScript Logo Icons for Web and App Development

TypeScript

开发语言

整体安装顺序：

1. 安装 Node.js
2. 安装 VS Code
3. 安装 pnpm
4. 配置 VS Code 插件
5. 安装 Git
6. 创建 React 项目
7. 启动项目并验证

## 一、安装 Node.js

LF开源软件学园 - 专区 - OSCHINA - 中文开源技术交流社区

Node.js

React 开发工具链运行所需环境。

[Node.js 官网](https://nodejs.org/?utm_source=chatgpt.com)

建议下载 LTS 版本，不建议初学者使用实验性版本。

安装完成后，打开 PowerShell：

powershell

```powershell
node -v
npm -v
```

确认 Node.js 和 npm 均能正常输出版本号。

Next.js 当前最低要求 Node.js 20.9。建议使用较新的 LTS 版本。

Next.js

+1

## 二、安装 VS Code

precis0x (@precisox) on X

Visual Studio Code

前端代码编辑器。

[VS Code 官网](https://code.visualstudio.com/?utm_source=chatgpt.com)

安装时建议勾选：

- 添加到 PATH 环境变量
- 添加到文件右键菜单
- 添加到目录右键菜单
- 注册为支持的文件编辑器

安装后执行：

powershell

```powershell
code --version
```

如果能显示版本号，说明安装成功。

## 三、安装 pnpm

pnpm Logo PNG Vector (SVG) Free Download

pnpm

高效的 Node.js 包管理器。

[pnpm 官方安装文档](https://pnpm.io/installation?utm_source=chatgpt.com)

pnpm 相比 npm，具有依赖存储复用、安装效率高、依赖管理严格等优点。

推荐安装方式：通过 npm 安装 pnpm。

在 PowerShell 中执行：

powershell

```powershell
npm install -g pnpm@latest
```

安装完成后检查：

powershell

```powershell
pnpm -v
```

如果能够显示版本号，说明安装成功。

当前 pnpm 官方文档提供 Windows 安装方式，并建议 Windows 用户优先考虑通过 npm 安装，以避免独立安装程序被 Defender 拦截的问题。

pnpm

### 配置 pnpm

查看 pnpm 全局安装目录：

powershell

```powershell
pnpm config get global-bin-dir
```

查看 pnpm 缓存存储目录：

powershell

```powershell
pnpm store path
```

如果需要使用国内 npm 镜像：

powershell

```powershell
pnpm config set registry https://registry.npmmirror.com
```

检查：

powershell

```powershell
pnpm config get registry
```

恢复官方源：

powershell

```powershell
pnpm config set registry https://registry.npmjs.org/
```

## 四、安装 VS Code 开发插件

打开 VS Code，按：

`Ctrl + Shift + X`

搜索并安装以下插件：

| 插件                      | 作用               | 推荐程度 |
| ------------------------- | ------------------ | -------- |
| ESLint                    | 代码规范检查       | 必装     |
| Prettier                  | 代码自动格式化     | 必装     |
| ES7+ React Snippets       | React 代码片段     | 推荐     |
| Tailwind CSS IntelliSense | CSS 智能提示       | 推荐     |
| Error Lens                | 错误提示           | 推荐     |
| GitLens                   | Git 代码管理       | 推荐     |
| Auto Rename Tag           | 自动修改 HTML 标签 | 推荐     |
| Chinese Language Pack     | 中文界面           | 可选     |

### 配置 VS Code 自动格式化

打开 VS Code 设置 JSON：

`Ctrl + Shift + P`

搜索：

`Preferences: Open User Settings (JSON)`

添加：

json

```json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.tabSize": 2,
  "editor.wordWrap": "on",
  "files.autoSave": "afterDelay",
  "files.autoSaveDelay": 1000
}
```

保存文件后，Prettier 就可以自动格式化代码。

## 五、安装 Git

Git アイコン、ロゴ、シンボル – 無料ダウンロード PNG、SVG

Git

代码版本管理工具。

[Git for Windows 下载](https://git-scm.com/downloads/win?utm_source=chatgpt.com)

安装完成后执行：

powershell

```powershell
git --version
```

配置 Git 用户信息：

powershell

```powershell
git config --global user.name "Your Name"

git config --global user.email "your@email.com"
```

检查配置：

powershell

```powershell
git config --list
```

## 六、创建 React 项目

这里推荐使用 Vite + React + TypeScript。

Vite 是现代化前端构建工具，适合独立 React 项目。

File:Vitejs-logo.svg - Wikimedia Commons

Vite

React 项目开发与构建工具。

[Vite 官方网站](https://vite.dev/?utm_source=chatgpt.com)

### 1. 创建项目目录

powershell

```powershell
D:
mkdir frontend-projects
cd frontend-projects
```

### 2. 使用 pnpm 创建 React 项目

powershell

```powershell
pnpm create vite my-react-app --template react-ts
```

这里选择的是：

- React
- TypeScript
- Vite

### 3. 进入项目目录

powershell

```powershell
cd my-react-app
```

### 4. 安装项目依赖

powershell

```powershell
pnpm install
```

### 5. 启动项目

powershell

```powershell
pnpm dev
```

正常情况下会看到类似：

text

```text
VITE ready

Local: http://localhost:5173/
```

打开浏览器：

[http://localhost:5173/](http://localhost:5173/?utm_source=chatgpt.com)

Vite + React

[blog.systemi.co.jp](https://blog.systemi.co.jp/vite-storybook/?utm_source=chatgpt.com)

看到 Vite + React 页面，说明 React 开发环境搭建成功。

## 七、使用 VS Code 打开项目

在项目根目录执行：

powershell

```powershell
code .
```

推荐项目结构：

text

```text
my-react-app/
│
├── public/                 # 静态资源
│
├── src/
│   ├── assets/             # 图片资源
│   │
│   ├── components/         # 公共组件
│   │
│   ├── hooks/              # 自定义 Hooks
│   │
│   ├── pages/              # 页面组件
│   │
│   ├── App.tsx             # 根组件
│   │
│   ├── main.tsx            # 项目入口
│   │
│   └── index.css           # 全局样式
│
├── index.html
├── package.json
├── pnpm-lock.yaml
├── tsconfig.json
└── vite.config.ts
```

`components`、`hooks` 和 `pages` 可以根据项目需要自行创建。

## 八、编写第一个 React 组件

打开：

`src/App.tsx`

替换成下面代码：

tsx

```tsx
import { useState } from "react";
import "./App.css";

function App() {
  const [count, setCount] = useState(0);

  return (
    <div className="app">
      <h1>React + TypeScript</h1>

      <p>Windows + VS Code + pnpm</p>

      <h2>当前计数：{count}</h2>

      <button onClick={() => setCount(count + 1)}>点击 +1</button>
    </div>
  );
}

export default App;
```

打开 `src/App.css`：

css

```css
.app {
  text-align: center;
  padding: 80px 20px;
  font-family: Arial, sans-serif;
}

h1 {
  color: #646cff;
}

button {
  padding: 10px 24px;
  border: none;
  border-radius: 8px;
  background: #646cff;
  color: white;
  cursor: pointer;
}
```

保存后，浏览器会自动刷新。

到这里，你已经完成了第一个 React + TypeScript 交互页面。

## 九、pnpm 常用命令

日常 React 开发中，建议熟悉以下命令：

| 命令                 | 作用           |
| -------------------- | -------------- |
| `pnpm install`       | 安装项目依赖   |
| `pnpm add axios`     | 安装生产依赖   |
| `pnpm add -D eslint` | 安装开发依赖   |
| `pnpm remove axios`  | 删除依赖       |
| `pnpm dev`           | 启动开发服务器 |
| `pnpm build`         | 构建生产版本   |
| `pnpm preview`       | 预览构建结果   |
| `pnpm list`          | 查看依赖       |
| `pnpm update`        | 更新依赖       |
| `pnpm store path`    | 查看缓存目录   |

### 常见依赖安装示例

React 项目中常用的第三方库：

powershell

```powershell
# 路由
pnpm add react-router-dom

# HTTP 请求
pnpm add axios

# 状态管理
pnpm add zustand

# 图标
pnpm add lucide-react

# UI 组件库
pnpm add antd

# 日期处理
pnpm add dayjs
```

## 十、如果还需要 Next.js

如果后续要开发服务端渲染、全栈应用，可以直接使用 pnpm 创建 Next.js 项目。

powershell

```powershell
cd D:\frontend-projects

pnpm create next-app@latest my-next-app --yes

cd my-next-app

pnpm dev
```

浏览器访问：

[http://localhost:3000](http://localhost:3000?utm_source=chatgpt.com)

官方脚手架默认配置包含 TypeScript、ESLint、Tailwind CSS、App Router 和 Turbopack。

Next.js

注意：Vite React 项目和 Next.js 项目是两种不同的项目创建方式，不需要把它们安装在同一个项目中。

## 十一、常见问题

1. pnpm 不是内部或外部命令

检查：

powershell

```powershell
where.exe pnpm
```

如果找不到命令：

- 关闭并重新打开 PowerShell。
- 检查 npm 全局安装目录是否在 PATH 中。
- 尝试重新安装：

powershell

```powershell
npm install -g pnpm@latest
```

2. pnpm install 下载速度慢

切换镜像：

powershell

```powershell
pnpm config set registry https://registry.npmmirror.com
```

3. 端口 5173 被占用

powershell

```powershell
pnpm dev -- --port 5174
```

4. 删除依赖重新安装

powershell

```powershell
Remove-Item -Recurse -Force node_modules

pnpm install
```

如果有 `pnpm-lock.yaml`，建议保留它，确保依赖版本一致。

## 十二、最终环境检查清单

开发环境完成情况

# 0/11

[ ]Node.js 安装成功

[ ]npm 安装成功

[ ]pnpm 安装成功

[ ]VS Code 安装成功

[ ]React 开发插件安装成功

[ ]Prettier 自动格式化配置完成

[ ]Git 安装及配置完成

[ ]Vite + React + TypeScript 项目创建成功

[ ]pnpm dev 启动成功

[ ]React 计数器运行成功

[ ]pnpm build 构建成功

## 十三、官方学习资源

| 技术       | 官方文档                                                                  |
| ---------- | ------------------------------------------------------------------------- |
| Node.js    | [Node.js](https://nodejs.org/?utm_source=chatgpt.com)                     |
| VS Code    | [VS Code](https://code.visualstudio.com/docs?utm_source=chatgpt.com)      |
| pnpm       | [pnpm](https://pnpm.io/?utm_source=chatgpt.com)                           |
| React      | [React](https://react.dev/learn?utm_source=chatgpt.com)                   |
| TypeScript | [TypeScript](https://www.typescriptlang.org/docs/?utm_source=chatgpt.com) |
| Vite       | [Vite](https://vite.dev/guide/?utm_source=chatgpt.com)                    |
| Next.js    | [Next.js](https://nextjs.org/docs?utm_source=chatgpt.com)                 |

## 十四、推荐的前端技术学习路线

1. 基础环境
   Windows、VS Code、Node.js、pnpm、Git
2. 前端基础
   HTML、CSS、JavaScript、ES6+
3. React 核心
   JSX、组件、Props、State、Hooks
4. TypeScript
   类型、接口、泛型、类型推导
5. React 生态
   React Router、Axios、Zustand、Ant Design
6. Next.js
   App Router、Server Components、API、数据库
7. 实战项目
   后台管理系统、博客系统、电商网站

建议： 如果你主要学习 React，先使用 Vite + React + TypeScript；等掌握 React 后，再学习 Next.js。

这样可以更清晰地理解 React 本身和 Next.js 框架之间的区别。
