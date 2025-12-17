# WebAR 互动系统

这是一个基于 Three.js 和 MediaPipe Hands 的 WebAR 互动系统项目，包含两个应用：粒子互动系统和手势控制圣诞树。

## 项目概览

### 1. 粒子互动系统 (WebARParticleSystem.html)
基于物理引擎的 3D 粒子系统，通过手势控制粒子形态变化。

**功能特点：**
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

### 2. 手势控制圣诞树 (WebARChristmasTree.html)
电影级视觉效果的 3D 圣诞树，通过手势控制状态切换和照片展示。

**功能特点：**
- **精美视觉设计**：
  - 配色：哑光绿 + 金属金 + 圣诞红
  - 电影感辉光与光晕效果
  - 金属质感材质 + 发光效果
- **圣诞树构成元素**：
  - 30个装饰球（红/金金属球）
  - 20个宝石立方体（绿色金属）
  - 15个糖果棍（红白相间）
  - 10个照片位置（可上传用户照片）
- **三种交互状态**：
  - **合拢态**：握拳手势，元素收拢成圆锥形圣诞树
  - **散开态**：五指张开，元素在空间中漂浮
  - **照片放大态**：抓取手势，选中照片放大展示
- **相机控制**：在散开态下，手部移动控制相机旋转
- **照片上传**：支持批量上传照片，自动分配到圣诞树元素

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

### 访问应用

启动后访问对应地址：

- **粒子系统**：http://localhost:8000/WebARParticleSystem.html
- **圣诞树**：http://localhost:8000/WebARChristmasTree.html

### 在线体验

GitHub Pages 部署版本：
- **粒子系统**：[https://JasonWuyaocheng.github.io/web-ar-particle-system/WebARParticleSystem.html](https://JasonWuyaocheng.github.io/web-ar-particle-system/WebARParticleSystem.html)
- **圣诞树**：[https://JasonWuyaocheng.github.io/web-ar-particle-system/WebARChristmasTree.html](https://JasonWuyaocheng.github.io/web-ar-particle-system/WebARChristmasTree.html)

## 使用说明

### 粒子系统
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

### 圣诞树系统
1. 允许浏览器访问摄像头
2. 上传照片（可选）：点击"上传照片"按钮，选择多张图片
3. 使用手势控制：
   - **握拳**：圣诞树合拢成形
   - **五指张开**：元素散开漂浮
   - **手部移动**：在散开态下旋转相机视角
   - **抓取**：选中并放大最近的照片
4. 无摄像头时会自动演示循环

## 性能优化

- **共同优化**：
  - BufferGeometry 提高渲染性能
  - 实时 FPS 监控
  - unpkg CDN 确保依赖加载稳定性

- **粒子系统**：
  - Fibonacci 球面算法确保粒子均匀分布
  - 限制最大时间步长保证物理稳定性

- **圣诞树系统**：
  - 后期处理辉光效果（UnrealBloomPass）
  - 缓动函数实现平滑动画
  - 状态管理防止动画冲突

## 兼容性

- 现代浏览器（Chrome、Firefox、Edge等）
- 需要摄像头支持（可选，无摄像头时启用自动模式）
- 需要 WebGL 支持
- HTTPS 环境（摄像头权限要求）

## 项目结构

```
web-ar-particle-system/
├── README.md                    # 项目说明文档
├── WebARParticleSystem.html     # 粒子互动系统
└── WebARChristmasTree.html      # 手势控制圣诞树
```

## 开发者信息

- **单文件实现**：两个应用均为单 HTML 文件，便于部署和分享
- **响应式设计**：适配不同屏幕尺寸
- **自动降级**：无摄像头时启用自动演示模式
- **错误处理**：完善的异常捕获和用户提示
- **调试支持**：键盘快捷键（1/2/3/空格）快速切换状态

## 许可证

MIT License

## 贡献

欢迎提交 Issue 和 Pull Request！

## 作者

Created with ❤️ by WebAR Developer
