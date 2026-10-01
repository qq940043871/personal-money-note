# 政策会议 (policy/meetings_policy.html)

## 页面概述
政策会议标签容器页，在重要会议与经济政策两页间切换。

## 功能需求
1. 标签切换（默认：重要会议）
   - 重要会议 → `meetings.html`
   - 经济政策 → `policy.html`
2. 子页面透传导航

## 页面结构
- 顶部标签栏（双标签）
- 全高标签内容 iframe

## 技术实现
- 标准 `switchTab` 容器模板
- 侧边栏入口：`loadPage('policy/meetings_policy.html','政策会议',event)`（badge 2）
