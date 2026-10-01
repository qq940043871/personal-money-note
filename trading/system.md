# 交易系统 (trading/system.html)

## 页面概述
交易体系入口标签容器页：交易系统方法论、股海导航与投资规划。

## 功能需求
1. 标签切换（默认：交易系统）
   - 交易系统 → `trading_system.html`
   - 股海导航 → `stock_navigation.html`
   - 投资规划 → `investment_plan.html`
2. 子页面透传导航

## 页面结构
- 顶部标签栏（3 个标签）
- 全高标签内容 iframe

## 技术实现
- 标准 `switchTab` 容器模板
- 侧边栏入口：`loadPage('trading/system.html','交易系统',event)`（badge 3）
- 注意与同名内容页 `trading_system.html` 区分：容器页是 `system.html`
