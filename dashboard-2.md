---
dashboard: true
layout: side
banner:
  quote: "The mind is everything. What you think you become."
  author: "Buddha"
  image: "https://images.pexels.com/photos/2307638/pexels-photo-2307638.jpeg"
  quoteFont: "Didot,\"Bodoni MT\",Georgia,serif"
  images:
    - "https://images.pexels.com/photos/2307638/pexels-photo-2307638.jpeg"
    - "https://images.pexels.com/photos/10664504/pexels-photo-10664504.jpeg"
  imagePos:
    "https://images.pexels.com/photos/2307638/pexels-photo-2307638.jpeg": "72,49"
immersiveBackground: "https://images.pexels.com/photos/2307638/pexels-photo-2307638.jpeg"
columns:
  - name: 便利贴
    color: "#f59e0b"
    type: sticky
  - name: Projects
    color: "#10b981"
    type: projects
  - name: Library
    color: "#8b5cf6"
    type: projects
  - name: 项目管理
    color: "#6366f1"
    type: pm
    pm:
      viewMode: gantt
      ganttScale: week
      ganttFilter: todos
      rootFolder: "1455-国家电投"
  - name: 网页
    color: "#6366f1"
    type: web
    web:
      url: "https://github.com/"
---

## 便利贴

### 2026-11-01 备忘
id: demo-memo-1
type: generic
欢迎使用 Apex Dashboard！点击此处编辑你的第一条备忘。
**小贴士**
- 在 **设置 → Apex Dashboard** 中可修改 dashboard 文件路径
- 双击分区标题即可**重命名分区**

### 快速上手
id: demo-todo-1
type: task
- [ ] 游泳
- [ ] 同步obsidian到GITHUB

### 界面操作指南
id: demo-todo-2
type: task
- [ ] 在设置中切换布局（侧栏 / 堆叠 / 沉浸式）

## Projects

### 我的第一个项目
id: demo-project-1
type: project
- [[Joule.md]]
- [[11.md]]

## Library

### Reading
id: demo-lib-reading
type: project
- [[全球视野下的投资机会（时寒冰）.md]]

### To Read
id: demo-lib-toread
type: project
- [[configuration of financial]]

### Done
id: demo-lib-done
type: project

## 项目管理

## 网页
