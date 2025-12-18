# 🚀 WebAR 粒子星球 - 完整部署清单

## ✅ 已完成的工作

### 下载的本地文件（存放在 `local-libs/` 目录）
```
local-libs/
├── three.min.js                    (669KB) - Three.js 160
├── mediapipe-hands.js              (39KB) - MediaPipe Hands
├── mediapipe-camera-utils.js       (7KB) - MediaPipe Camera
├── mediapipe-drawing-utils.js      (3KB) - MediaPipe Drawing
├── mediapipe-control-utils.js      (24KB) - MediaPipe Control
```

### 创建的 HTML 文件
1. **WebARPlanetParticles_GitHub.html** - GitHub Pages 优化版
2. **WebARPlanetParticles_Offline.html** - 完全离线版（推荐）
3. **WebARPlanetParticles_FullLocal.html** - 本地资源优先版

## 🎯 推荐方案：完全离线版

### 为什么选择离线版？
- ✅ **无需网络**：所有资源都在本地
- ✅ **避免 CDN 问题**：不受广告拦截器影响
- ✅ **最快加载**：无需下载外部资源
- ✅ **最稳定**：不受 GitHub Pages 缓存影响

### 部署步骤

#### 1. 准备文件结构
```
your-project/
├── WebARPlanetParticles_Offline.html  (重命名为 index.html)
├── local-libs/
│   ├── three.min.js
│   ├── mediapipe-hands.js
│   ├── mediapipe-camera-utils.js
│   ├── mediapipe-drawing-utils.js
│   └── mediapipe-control-utils.js
├── README.md
└── DEPLOYMENT_CHECKLIST.md
```

#### 2. 本地测试
```bash
# 方法 1: Python
cd your-project
python -m http.server 8080
# 访问 http://localhost:8080

# 方法 2: Node.js
cd your-project
npx http-server -p 8080
# 访问 http://localhost:8080
```

#### 3. GitHub Pages 部署
```bash
# 1. 创建仓库
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/你的用户名/仓库名.git
git push -u origin main

# 2. 启用 Pages
# Settings → Pages → Source: Deploy from branch
# Branch: main, Folder: /(root)

# 3. 访问
# https://你的用户名.github.io/仓库名/
# 或设置自定义域名
```

## 🔍 故障排除

### 问题 1：页面显示 "需要安全连接"
**原因**：浏览器要求 HTTPS 才能访问摄像头

**解决方案**：
- 本地测试使用 `localhost` 而非 `127.0.0.1`
- GitHub Pages 自动提供 HTTPS
- 如果使用自定义域名，必须配置 SSL

### 问题 2：摄像头权限被拒绝
**原因**：浏览器阻止了摄像头访问

**解决方案**：
1. 检查浏览器地址栏左侧的锁图标
2. 点击"网站设置"或"权限"
3. 将摄像头设置为"允许"
4. 刷新页面

### 问题 3：MediaPipe 加载失败
**原因**：模型文件下载失败（约 10MB）

**解决方案**：
1. 检查网络连接
2. 检查浏览器控制台（F12）查看具体错误
3. 如果是 GitHub Pages，等待几分钟让缓存更新
4. 尝试清除浏览器缓存后刷新

### 问题 4：页面空白/白屏
**原因**：JavaScript 错误或资源加载失败

**解决方案**：
1. 按 F12 打开开发者工具
2. 查看 Console 标签页的红色错误信息
3. 查看 Network 标签页的资源加载状态
4. 将错误信息截图或复制给我

### 问题 5：手势识别不灵敏
**原因**：摄像头分辨率或环境光线问题

**解决方案**：
1. 确保环境光线充足
2. 保持手部在摄像头视野内
3. 尝试调整手势幅度（更大、更慢）
4. 使用调试按钮查看摄像头画面

## 📋 完整文件清单（GitHub Pages）

### 必需文件（最小化部署）
```
repository/
├── index.html                      (复制 WebARPlanetParticles_Offline.html)
└── local-libs/
    ├── three.min.js
    ├── mediapipe-hands.js
    ├── mediapipe-camera-utils.js
    ├── mediapipe-drawing-utils.js
    └── mediapipe-control-utils.js
```

### 可选文件（便于管理）
```
repository/
├── index.html
├── local-libs/
│   └── (所有 .js 文件)
├── README.md                       (项目说明)
├── DEPLOYMENT_CHECKLIST.md         (本文件)
└── screenshots/                    (截图展示)
    ├── demo-1.jpg
    └── demo-2.jpg
```

## 🎨 用户体验优化

### 首次访问流程
1. 页面加载 → 显示系统状态栏
2. 自动检查依赖 → 显示加载进度
3. 请求摄像头 → 浏览器权限弹窗
4. 用户授权 → 显示成功提示
5. 用户点击 → 启动手势识别
6. 开始交互 → 正常使用

### 状态指示器说明
- 🔴 灰色：未加载
- 🟢 绿色：已加载/正常
- 🟡 黄色：加载中
- 🔴 红色：错误

### 错误处理
- 友好错误提示
- 显示具体原因
- 提供重试按钮
- 记录错误日志（控制台）

## 📞 获取帮助

如果遇到问题，请提供：

1. **错误截图**（F12 控制台）
2. **浏览器信息**（Chrome 120.0 等）
3. **访问地址**（本地还是 GitHub Pages）
4. **具体症状**（白屏、卡住、报错等）
5. **已尝试的解决方案**

## 🎉 成功标准

当你的应用正常工作时，应该看到：

✅ 页面显示"正在初始化系统..."  
✅ 自动切换到"请点击屏幕开始"  
✅ 点击后显示摄像头权限请求  
✅ 允许权限后显示"系统就绪"  
✅ 3D 粒子星球正常渲染并缓慢旋转  
✅ 调试按钮可以正常显示/隐藏摄像头  
✅ 手势可以控制星球旋转和镜头距离  

## 📝 部署后检查清单

- [ ] 页面可以正常访问
- [ ] 所有状态指示器变为绿色
- [ ] 摄像头权限请求正常弹出
- [ ] 用户允许后，系统正常启动
- [ ] 3D 粒子星球渲染正常
- [ ] 手势识别工作正常
- [ ] 调试功能可以正常开关
- [ ] 在不同浏览器测试（Chrome/Edge/Firefox）
- [ ] 在移动设备测试（如果支持）
- [ ] 清除缓存后仍能正常工作

## 🚀 性能优化建议

### 如果遇到性能问题：
1. 减少粒子数量（planetCount: 2000）
2. 降低渲染质量（renderer.setPixelRatio(1)）
3. 使用更低的 MediaPipe 复杂度（modelComplexity: 0）
4. 启用浏览器硬件加速

### 代码优化位置：
```javascript
// 降低粒子数量
const planetCount = 2000; // 原来 4000

// 降低渲染质量
renderer.setPixelRatio(1); // 原来 Math.min(window.devicePixelRatio, 2)

// 使用轻量模型
hands.setOptions({
    modelComplexity: 0, // 原来 1
    minDetectionConfidence: 0.3, // 更宽松
    minTrackingConfidence: 0.3
});
```

---

**祝部署成功！** 🎊

如果按照此清单操作仍有问题，请随时联系我。
