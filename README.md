# WebAR 粒子互动系统

这是一个基于 Three.js 和 MediaPipe Hands 的 WebAR 粒子互动系统，可实现手势控制的 3D 粒子效果。

## 功能特点

- **16,000个青色流体粒子**：高性能渲染流畅的粒子动画
- **物理引擎**：基于速度+加速度的真实物理模型，拒绝生硬插值
- **五态手势识别**：
  - 张手 → 球形变换
  - 剪刀手 → "我是 Mok" 文字展示
  - 握拳 → 圆环形态
  - 食指 → 星形图案
  - 竖大拇指 → 爱心形状
- **交互特效**：
  - 手势切换爆炸过渡效果
  - 挥手风暴（快速挥动手掌可吹散粒子）
  - 深度推拉反馈（根据手掌大小实时缩放粒子系统）

## 技术栈

- [Three.js](https://threejs.org/) - 3D 图形渲染库
- [MediaPipe Hands](https://google.github.io/mediapipe/solutions/hands.html) - 手势识别
- WebGL - GPU 加速图形渲染
- unpkg CDN - 依赖库加载

## 运行方式

### 本地运行

由于浏览器安全策略限制，需要通过本地服务器运行：

#### 方法一：Python（推荐）
```bash
# Python 3.x
python -m http.server 8000

# Python 2.x
python -m SimpleHTTPServer 8000
```

#### 方法二：Node.js
```bash
# 安装 http-server
npm install -g http-server

# 启动服务器
http-server
```

启动后访问：http://localhost:8000/WebARParticleSystem.html

### 在线体验

GitHub Pages 部署版本：[https://JasonWuyaocheng.github.io/web-ar-particle-system/WebARParticleSystem.html](https://JasonWuyaocheng.github.io/web-ar-particle-system/WebARParticleSystem.html)

## 使用说明

1. 允许浏览器访问摄像头
2. 将手掌放置在摄像头前
3. 尝试不同手势查看粒子变换效果：
   - 张开手掌显示球形
   - 做剪刀手显示文字
   - 握拳显示圆环
   - 伸出食指显示星形
   - 竖起大拇指显示爱心
4. 快速挥动手掌可触发风暴效果
5. 改变手掌与摄像头的距离可缩放粒子系统

## 性能优化

- 使用 BufferGeometry 提高渲染性能
- 粒子更新采用高效算法
- 实时 FPS 监控确保流畅体验

## 兼容性

- 现代浏览器（Chrome、Firefox、Edge等）
- 需要摄像头支持
- 需要 WebGL 支持

## 开发者信息

- 使用 unpkg CDN 确保依赖加载稳定性
- 单文件 HTML 实现，便于部署和分享

- 响应式设计，适配不同屏幕尺寸
