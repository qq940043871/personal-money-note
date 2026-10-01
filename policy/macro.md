# 宏观经济 (policy/macro.html)

## 页面概述
宏观政策模块下的宏观经济标签容器页，聚合利率、财政、中外经济与周期内容。

## 功能需求
1. 标签切换（默认：美联储利率）
   - 美联储利率 → `fed.html`
   - 政府财政 → `government_finance.html`
   - 中国经济 → `economic_development.html`
   - 世界经济 → `global_economic_development.html`
   - 经济周期 → `economic_conditions.html`
2. 子页面透传导航

## 页面结构
- 顶部标签栏
- 全高标签内容 iframe

## 技术实现
- 标准 `switchTab` 容器模板
- 侧边栏入口：`loadPage('policy/macro.html','宏观经济',event)`（badge 5）
