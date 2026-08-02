# 阿瓦隆地图 · 部署指南

## 仓库结构

```
avalon-map/
├── avalon-map.html          # 地图 H5 页面
├── images/
│   └── locations/
│       ├── 正1_101.png      # 正面插图
│       ├── 反1_101.png      # 反面插图
│       └── ... (共 63 个地点，126 张图)
└── README.md
```

## 部署步骤

### 1. 创建 GitHub 仓库

打开 https://github.com/jalaka12?tab=repositories ，点击「New」创建新仓库：
- Repository name: `avalon-map`
- Public
- 不要勾选「Add a README file」

### 2. 上传文件

在终端中执行（或在 GitHub 网页端拖拽上传）：

```bash
cd deploy-package/
git init
git add .
git commit -m "Add avalon map with 63 location cards"
git remote add origin https://github.com/jalaka12/avalon-map.git
git branch -M main
git push -u origin main
```

如果 344MB 的文件太大无法推送，可以使用 GitHub 网页端分批上传 `images/locations/` 文件夹。

### 3. 验证 CDN

推送后等待 1-2 分钟，访问：
```
https://cdn.jsdelivr.net/gh/jalaka12/avalon-map@main/images/locations/正1_101.png
```

如果能加载图片，说明部署成功。

### 4. 在酒馆中使用地图

地图 HTML 已集成到角色卡 `card.json` 中，通过世界书条目触发。玩家输入「打开地图」即可看到完整地图界面。

## 地图功能

- 63 个地点卡片，带正反面插图
- 双击翻面查看背面信息
- 拖拽平移 + 滚轮缩放
- 单击地点查看大图和详情
- 当前位置脉动动画
- MVU 变量集成（自动读取当前地点和已揭示地点）
- 「全部揭示」按钮用于测试
