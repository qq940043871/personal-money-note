# 行业追踪 (industry/overview.html)

## 页面概述
行业追踪模块的标签容器页：顶部标签栏在同目录子页面间切换，内容通过内部 iframe 加载。

## 功能需求
1. 标签切换
   - 行业追踪 → `industry_tracking.html`（默认）
   - 工业软件 → `industrial_software.html`
   - 产业链 → `industrial_software_chain.html`
2. 子页面透传导航
   - 提供 `loadPage(page, title, evt)` 转发到 `parent.loadPage`

## 页面结构
- 顶部标签栏（高 42px，激活态底部靛蓝色下划线）
- 全高标签内容 iframe（`tab-frame`）

## 技术实现
- `switchTab(btn, page)` 切换激活样式并更新 iframe `src`
- 路径相对当前目录（非项目根）
- 侧边栏入口：`loadPage('industry/overview.html','行业追踪',event)`
