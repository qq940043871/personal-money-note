# 股市认知 (market/cognition.html)

## 页面概述
行情市场下的认知类标签容器页，承载股市本质、底层逻辑等长文子页。

## 功能需求
1. 标签切换（默认：股市本质）
   - 股市本质 → `market_essence.html`
   - 底层逻辑 → `fundamental_logic.html`
   - 技术与想象 → `technology_imagination.html`
   - 中国未来 → `china_future.html`
   - 先发优势 → `first_mover_advantage.html`
2. 子页面 `parent.loadPage` 透传

## 页面结构
- 顶部标签栏
- 全高标签内容 iframe

## 技术实现
- 标准 `switchTab` 容器模板
- 侧边栏入口：`loadPage('market/cognition.html','股市认知',event)`（badge 5）
