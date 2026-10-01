# 应用外壳 (index.html)

## 页面概述
投资交易工作站的主外壳：顶栏 + 可折叠侧边导航 + 主内容 iframe + 底部状态栏。浏览器直接打开本文件即可运行整个原型。

## 功能需求
1. 顶栏（48px）
   - 当前页面标题（`#pageTitle`，随导航更新）
   - 行情 ticker（上证 / 深证 / 创业板 / 沪深300，静态示意）
   - 时钟与用户标识
2. 侧边栏（`w-52`，深色渐变）
   - 6 个分组：工作台、行情市场、交易体系、宏观政策、学习成长、系统
   - 分组可折叠；初始仅展开「工作台」「行情市场」
   - 导航项高亮 `.active-nav`，部分项带子页数量 badge
3. 主内容区
   - `<iframe id="mainFrame">` 默认加载 `portal/home.html`
4. 底部状态栏（28px）
   - 盘中状态、时间、风险提示

## 导航 API
- `loadPage(page, title, evt)`：设置 iframe `src`、更新标题、高亮侧栏项
  - 有 `evt` 时直接高亮点击项；否则按 `onclick` 中的路径字符串匹配
  - 自动展开被折叠的分组
- 子页面调用：`parent.loadPage('module/page.html')`（路径相对项目根）

## 页面结构
- `#topbar` → `.workspace`（`#sidebar` + `main#mainFrame`）→ `#statusbar`

## 技术实现
- Tailwind 扩展色：`brand`（靛蓝系）、`up`/`down`（涨红跌绿）、`sidebar` 深色
- 纯静态，无构建；`start.bat` 可用 `npx http-server -p 3004` 本地起服
