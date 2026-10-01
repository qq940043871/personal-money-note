# 市场规则 (policy/rules.html)

## 页面概述
市场规则标签容器页，聚合财报披露与退市规则两份监管内容。

## 功能需求
1. 标签切换（默认：财报披露）
   - 财报披露 → `financial_disclosure_rules.html`
   - 退市规则 → `delisting_rules.html`
2. 子页面透传导航

## 页面结构
- 顶部标签栏（双标签）
- 全高标签内容 iframe

## 技术实现
- 标准 `switchTab` 容器模板
- 侧边栏入口：`loadPage('policy/rules.html','市场规则',event)`（badge 2）
