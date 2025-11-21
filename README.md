# 📘 闲云附魔书查询系统 (Xianyun Enchant Search)

> 一个现代化的、无服务端的 Minecraft 附魔书查询与价格计算工具，包含炫酷的前端展示与基于 GitHub API 的管理后台。

![Version](https://img.shields.io/badge/Version-2.3-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Tech](https://img.shields.io/badge/Tech-HTML5%20%7C%20JS%20%7C%20GitHub_API-orange)

## 📖 项目简介

本项目是一个**纯静态**的 Web 应用，旨在帮助服务器玩家快速查询附魔书属性、价格、冲突关系，并提供预算计算功能。

项目包含两个核心部分：
1.  **用户端 (`index.html`)**：提供列表视图和**星图视图**，支持昼夜主题切换、购物车计算、多语言架构。
2.  **管理端 (`admin.html`)**：通过 GitHub API 直接对 `data.json` 进行增删改查，无需后端服务器，支持批量更新发布。

---

## ✨ 功能特性

### 🖥️ 用户端 (Client)
*   **双重视图**：
    *   📁 **列表视图**：卡片式布局，支持 3D 悬停效果，清晰展示价格与属性。
    *   🌌 **星图视图**：基于 HTML5 Canvas 的互动星系图，节点闪烁，支持拖拽与缩放。
*   **价格计算器**：内置购物车功能，支持数量增减，自动计算总金币预算。
*   **多维筛选**：支持按名称、用途、装备部位搜索，以及按品质（颜色）筛选。
*   **昼夜主题**：
    *   自动根据时间（6:00-18:00）切换白昼/黑夜模式。
    *   带有沉浸式的“命运之门”转场动画。
*   **响应式设计**：完美适配桌面端与移动端设备。

### 🛡️ 管理后台 (Admin)
*   **无后端架构**：直接利用 GitHub REST API 读取和写入仓库数据。
*   **安全验证**：通过 GitHub Personal Access Token (PAT) 登录。
*   **可视化编辑**：
    *   提供颜色（品质）、等级的可视化选择器。
    *   支持冲突附魔与适用物品的标签云选择。
*   **批量发布**：支持增、删、改操作的暂存（Pending），一键推送到 GitHub 仓库。

---

## 🚀 快速开始

### 1. 部署 (Deployment)
由于是纯静态文件，您可以将项目部署到任何静态托管服务：
*   **GitHub Pages** (推荐)
*   Vercel
*   Netlify
*   或直接在本地浏览器打开 `index.html`。

### 2. 文件结构
```
.
├── index.html      # 用户查询主页
├── admin.html      # 管理员后台
├── data.json       # 数据存储文件
└── README.md       # 项目文档
```

⚙️ 管理后台配置 (Admin Setup)
要使用 admin.html 管理数据，您需要进行以下配置：<br>
1.获取 GitHub Token:
访问 GitHub Settings -> Developer settings -> Personal access tokens.
生成一个新的 Token (Classic)，勾选 repo 权限（用于读写仓库文件）。<br>
2.配置仓库信息:
打开 admin.html。
在代码中找到以下隐藏的 input 区域（约第 150 行），修改 value 为您的实际信息：

```
<div style="display:none">
    <!-- 修改为你的 GitHub 用户名 -->
    <input type="text" id="ghOwner" value="Your-GitHub-Username">
    <!-- 修改为你的仓库名称 -->
    <input type="text" id="ghRepo" value="Your-Repo-Name">
    <!-- 数据文件路径，通常无需修改 -->
    <input type="text" id="ghPath" value="data.json">
</div>
```

3.登录使用:
在浏览器打开 admin.html。
输入您的 GitHub Token 即可进入管理面板。

📊 数据结构 (Data Structure)
data.json 存储了所有附魔书信息，格式如下：

```
[
  {
    "id": "附魔名称",
    "name_zh": "附魔名称",
    "level_zh": "七级",
    "price": "3000",
    "desc_zh": "附魔描述...",
    "color": "红",        // 品质颜色：白/绿/蓝/紫/金/红
    "target_zh": "剑, 斧", // 适用物品
    "conflicts_zh": "冲突附魔1, 冲突附魔2"
  }
]
```

品质颜色对照
```
颜色	品质	代表含义
白	普通	Common
绿	优秀	Uncommon
蓝	稀有	Rare
紫	史诗	Epic
金	传说	Legend
红	神话	Mythic
```

🛠️ 技术栈 (Tech Stack)<br>
HTML5 / CSS3:使用了 CSS Variables, Flexbox, Grid, Glassmorphism (毛玻璃效果), Keyframe Animations.<br>
JavaScript (ES6+): 原生 JS 实现，无第三方重型框架依赖。<br>
Canvas: 用于星图视图的绘制与交互。<br>
FontAwesome: 用于界面图标。<br>
GitHub REST API: 用于数据的云端同步。<br>

🤝 贡献 欢迎提交 Issue 或 Pull Request 来改进代码！<br>
❤️ by CCCC4444
