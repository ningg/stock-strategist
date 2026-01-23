# Docsify 项目使用说明

## 快速开始

### 1. 安装 docsify-cli（如果还没有安装）

```bash
npm i docsify-cli -g
```

### 2. 启动本地服务器（支持热重载）

在项目根目录运行：

```bash
docsify serve .
```

或者使用 npm 脚本：

```bash
npm run serve
# 或
npm run dev
```

**重要提示**：`docsify serve` 默认支持**热重载（Hot Reload）**功能！
- ✅ 自动监听文件变化
- ✅ 保存文件后自动刷新浏览器
- ✅ 无需手动刷新页面

### 3. 访问文档

启动后会自动打开浏览器，或手动访问：http://localhost:3000

**实时编辑**：
1. 启动服务器后，直接编辑任何 `.md` 文件
2. 保存文件后，浏览器会自动刷新显示最新内容
3. 无需重启服务器，无需手动刷新

## 项目结构

```
stock-strategist/
├── index.html          # Docsify 主入口文件
├── README.md           # 首页内容
├── _sidebar.md         # 侧边栏导航配置
├── 404.md              # 404 错误页面
├── .nojekyll           # GitHub Pages 配置
├── .gitignore          # Git 忽略文件
├── package.json        # 项目配置
├── plan.md             # 项目规划
├── analysis/           # 历史分析报告
└── analysis_2026/      # 2026年分析报告
```

## 功能特性

- ✅ 侧边栏导航
- ✅ 全文搜索
- ✅ 代码高亮
- ✅ 响应式设计
- ✅ 自动目录生成
- ✅ 404 页面处理
- ✅ **热重载（Hot Reload）** - 自动监听文件变化并刷新

## 部署到 GitHub Pages

1. 在 GitHub 仓库设置中启用 GitHub Pages
2. 选择 `main` 分支的 `/ (root)` 目录
3. 访问 `https://yourusername.github.io/stock-strategist`

## 自定义配置

编辑 `index.html` 中的 `window.$docsify` 配置对象来自定义文档行为。

主要配置项：
- `name`: 文档名称
- `loadSidebar`: 是否加载侧边栏
- `subMaxLevel`: 侧边栏最大层级
- `search`: 搜索配置
- `homepage`: 首页文件

## 添加新文档

1. 在相应目录创建 `.md` 文件
2. 在 `_sidebar.md` 中添加链接
3. **保存文件后，浏览器会自动刷新显示新文档**（如果服务器正在运行）

## 热重载说明

`docsify serve` 命令内置了文件监听功能，会自动检测以下变化：
- ✅ Markdown 文件（`.md`）的修改
- ✅ 侧边栏配置（`_sidebar.md`）的修改
- ✅ 首页（`README.md`）的修改
- ✅ 配置文件（`index.html`）的修改

**工作原理**：
- 服务器会监听项目目录下的所有文件变化
- 当检测到文件修改并保存后，会自动向浏览器发送刷新信号
- 浏览器会自动重新加载当前页面，显示最新内容

**注意事项**：
- 如果修改了 `index.html`，可能需要手动刷新浏览器
- 某些浏览器可能需要允许自动刷新功能
- 确保服务器进程正在运行，才能享受热重载功能
