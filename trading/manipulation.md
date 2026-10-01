# 庄家与散户 (trading/manipulation.html)

## 页面概述
交易体系下的庄家与散户标签容器页：庄家收割过程 + 散户心理相关跨模块子页。

## 功能需求
1. 标签切换（默认：庄家收割）
   - 庄家收割 → `mainipulation_process.html`
   - 散户心理 → `../learning/retail_psychology.html`（跨目录）
   - 心理建设 → `../learning/psychological_construction.html`（跨目录）
2. 子页面透传导航

## 页面结构
- 顶部标签栏（3 个标签）
- 全高标签内容 iframe

## 技术实现
- 标准 `switchTab` 容器模板；跨模块标签用相对路径 `../learning/...`
- 侧边栏入口：`loadPage('trading/manipulation.html','庄家与散户',event)`（badge 3）
- 文件名注意：庄家过程页为 `mainipulation_process.html`（历史拼写，勿改）
