# GitHub Pages 部署说明 (WebAR 粒子星球)

## 🚀 快速部署

### 方法 1：直接上传（推荐）
1. 将以下文件上传到你的 GitHub 仓库根目录：
   - `WebARPlanetParticles_GitHub.html`
   - `local-libs/three.min.js`

2. 在仓库设置中启用 GitHub Pages：
   - Settings → Pages → Source: Deploy from a branch
   - Branch: main (或 master), Folder: / (root)

3. 访问：`https://你的用户名.github.io/仓库名/WebARPlanetParticles_GitHub.html`

### 方法 2：完全本地化（最稳定）
1. 上传整个项目结构：
```
your-repo/
├── index.html (复制 WebARPlanetParticles_GitHub.html 内容)
├── local-libs/
│   └── three.min.js
└── README.md
```

2. 访问：`https://你的用户名.github.io/仓库名/`

## 🔧 问题解决

### 如果遇到 ERR_BLOCKED_BY_CLIENT
**原因**：浏览器广告拦截器阻止了 MediaPipe 的 CDN 资源

**解决方案**：
1. 使用浏览器**无痕模式**访问
2. 在广告拦截器中将你的 GitHub Pages 网址加入白名单
3. 或者使用本地部署版本

### 如果摄像头权限失败
**原因**：GitHub Pages 的 HTTPS 有时会限制摄像头访问

**解决方案**：
1. 点击地址栏左侧的锁形图标
2. 允许摄像头和麦克风访问
3. 刷新页面

### 如果页面空白/无法加载
**可能原因**：网络连接问题或 CDN 被阻止

**解决方案**：
1. 检查浏览器控制台（F12）查看具体错误
2. 尝试在本地运行：`python -m http.server 8080`
3. 使用 VPN 或更换网络环境

## 📋 文件说明

### WebARPlanetParticles_GitHub.html
- 优化版本，包含错误处理和用户提示
- 自动检测 GitHub Pages 环境
- 提供友好的用户界面

### local-libs/three.min.js
- Three.js 160 版本，已下载到本地
- 避免 CDN 加载失败问题

### 依赖的 CDN（MediaPipe）
以下资源仍需从 CDN 加载（被广告拦截器阻止的可能性较大）：
- `https://cdn.jsdelivr.net/npm/@mediapipe/camera_utils/camera_utils.js`
- `https://cdn.jsdelivr.net/npm/@mediapipe/hands/hands.js`
- `https://cdn.jsdelivr.net/npm/@mediapipe/drawing_utils/drawing_utils.js`
- `https://cdn.jsdelivr.net/npm/@mediapipe/control_utils/control_utils.js`

## 🎯 推荐测试流程

1. **本地测试**（确保功能正常）
   ```bash
   python -m http.server 8080
   # 访问 http://localhost:8080/WebARPlanetParticles_GitHub.html
   ```

2. **GitHub Pages 测试**
   - 上传文件
   - 等待 1-2 分钟让 Pages 部署完成
   - 使用无痕模式访问

3. **验证功能**
   - 看到加载提示 ✅
   - 点击屏幕后显示权限请求 ✅
   - 允许权限后看到粒子星球 ✅
   - 调试按钮可以正常工作 ✅

## 📝 注意事项

1. **HTTPS 必需**：摄像头权限需要安全连接
2. **用户交互**：必须点击页面才能启动摄像头
3. **网络连接**：需要下载 MediaPipe 模型文件（约 10MB）
4. **浏览器兼容**：推荐 Chrome、Edge、Firefox 最新版
5. **设备要求**：需要摄像头和麦克风权限

## 🔍 调试信息

如果出现问题，请按以下步骤检查：

1. 打开浏览器控制台 (F12)
2. 查看 Console 标签页的错误信息
3. 查看 Network 标签页的资源加载状态
4. 将错误信息截图或复制给我

## 📞 支持

如果按照以上步骤操作仍然无法运行，请提供：
1. 具体的错误信息
2. 使用的浏览器和版本
3. 是否在本地可以运行
4. GitHub Pages 的完整网址
