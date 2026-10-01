# 交易方法 (trading/methods.html)

## 页面概述
交易方法标签容器页，聚合策略总览、量价关系、股价周期与大盘共振。

## 功能需求
1. 标签切换（默认：策略总览）
   - 策略总览 → `strategies.html`
   - 量价关系 → `volume_price.html`
   - 股价周期 → `stock_cycle.html`
   - 大盘共振 → `market_resonance.html`
2. 子页面透传导航

## 页面结构
- 顶部标签栏（4 个标签）
- 全高标签内容 iframe

## 技术实现
- 标准 `switchTab` 容器模板
- 侧边栏入口：`loadPage('trading/methods.html','交易方法',event)`（badge 4）
