# 学习心得 (learning/notes.html)

## 页面概述
学习成长模块的标签容器页，聚合学习系统、学习心得、评分体系、政策解读与名人传记。

## 功能需求
1. 标签切换（默认：学习系统）
   - 学习系统 → `learning_system.html`
   - 学习心得 → `learning.html`
   - 评分体系 → `scoring_system.html`
   - 政策解读 → `learning_news.html`
   - 名人传记 → `biography.html`
2. 子页面透传导航到外层 shell

## 页面结构
- 顶部标签栏
- 全高标签内容 iframe

## 技术实现
- 与其它 `*container*` 标签页同一套 `switchTab` 模式
- 侧边栏入口：`loadPage('learning/notes.html','学习心得',event)`
