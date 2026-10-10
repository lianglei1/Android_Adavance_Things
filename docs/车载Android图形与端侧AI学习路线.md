# 车载 Android 图形与端侧 AI 技术学习路线

## 1. 个人定位

### 目标岗位

- 车载 Android 图形渲染专家
- 智能座舱 3D HMI / 渲染引擎专家
- AVM / APA / SR / AR-HUD 图形开发专家
- 智能座舱 Android Native 架构师
- 舱驾融合可视化研发专家
- 端侧 AI 与车载图形融合研发专家

### 核心竞争力定位

```text
Android / Framework
        +
C++ / NDK / Native
        +
OpenGL ES / Vulkan / GPU
        +
ADAS / 摄像头 / 车辆信号
        +
端侧 AI / 多模态 / Agent
```

不转成普通 Prompt、RAG 或 Agent 应用开发工程师，而是在已有 Android、车载和图形能力上增加端侧 AI，形成“车载实时图形与端侧智能融合”的技术壁垒。

## 2. 能力现状与主要缺口

### 已有优势

- 12 年 Android 开发经验
- Kotlin、Java、C/C++、JNI、NDK
- OpenGL ES、自研 2D/3D 渲染引擎
- PBR、Shader、模型、材质、骨骼动画和粒子特效
- 360 环视、APA、SR 地图、AR-HUD
- CAN、DDS、CarService、ADAS 与地图数据接入
- Unity、Unreal Engine 及车载量产项目经验
- 端侧模型、RAG、Agent、MCP 和多模态落地经验

### 需要重点加强

1. Vulkan 工程化和量产能力
2. GPU 性能分析及数据化优化
3. Android 底层图形系统
4. 高通车载平台图形性能调优
5. ADAS / SR / AR-HUD 数据可视化体系
6. Unity / 团结引擎车机版量产能力
7. QNX、多屏与跨系统渲染
8. 车规软件稳定性、功能安全和量产流程
9. AI 与 3D HMI 的融合应用
10. 可公开演示的作品与量化技术材料

## 3. 学习优先级

### P0：直接决定求职竞争力

- Vulkan
- RenderDoc、AGI、Snapdragon Profiler、Perfetto
- Android Surface / EGL / BufferQueue / SurfaceFlinger
- ADAS / SR / AR-HUD 实时可视化
- 帧率、延迟、内存、启动速度及长稳优化

### P1：扩大岗位覆盖范围

- Unity / 团结引擎车机版
- QNX Screen、多屏和虚拟化架构
- SOME/IP、DDS、共享内存及低延迟数据链路
- 高通 8155 / 8295 等平台特性
- ASPICE、ISO 26262 及车载软件交付流程

### P2：形成长期差异化

- 多模态感知结果可视化
- 端侧 AI 与 3D HMI 联动
- A2UI / 生成式 UI
- Agent 驱动车辆功能和 3D 场景
- AI 辅助资源生产、Shader开发及性能分析

## 4. 阶段一：Vulkan 核心能力

### 学习目标

能够在 Android 上独立开发、调试和优化 Vulkan 实时渲染应用，并能解释与 OpenGL ES 的架构差异。

### 学习内容

- Instance、Physical Device、Logical Device
- Queue Family、Graphics Queue、Transfer Queue
- Surface、SwapChain、Present
- Render Pass、Framebuffer
- Graphics Pipeline、Pipeline Layout
- Command Pool、Command Buffer
- Vertex Buffer、Index Buffer
- Uniform Buffer、Storage Buffer
- Descriptor Set、Descriptor Pool
- Texture、Sampler、Mipmap
- Fence、Semaphore、Event
- Pipeline Barrier、Image Layout
- Staging Buffer 与异步资源上传
- GPU 内存管理
- 多线程 Command Buffer 录制
- Pipeline Cache
- Android Surface 生命周期与 SwapChain 重建
- Vulkan Validation Layer

### 实践任务

将现有 OpenGL ES 车模渲染项目迁移为 Vulkan：

- glTF 车模加载
- PBR 材质
- IBL 环境光照
- 阴影
- 车门和车轮动画
- 触摸旋转、缩放
- OpenGL ES / Vulkan 双渲染后端

### 验收标准

- 无 Validation Layer 错误
- 正确处理前后台切换、旋转及 Surface 重建
- 输出 OpenGL ES 与 Vulkan 的 CPU/GPU 帧耗时对比
- 能定位同步错误、资源泄漏和花屏问题
- 能说明 Vulkan 是否真正带来性能收益及原因

### 推荐资料

- Khronos Vulkan Tutorial
- Khronos Vulkan Samples
- Sascha Willems Vulkan Samples
- Android Developers Vulkan 文档
- 《Vulkan Programming Guide》

## 5. 阶段二：GPU 性能分析

### 学习目标

从“凭经验优化”升级为“通过指标和工具定位瓶颈”。

### 必备工具

- RenderDoc
- Android GPU Inspector
- Snapdragon Profiler
- Perfetto
- Android Studio CPU / Memory Profiler
- Unity Profiler
- Unreal Insights

### 重点问题

- CPU Bound 与 GPU Bound 判断
- Draw Call与状态切换
- Overdraw
- Shader 指令数、分支和精度
- 纹理带宽、格式及显存
- GPU Stall
- Pipeline Bubble
- Buffer 上传和同步阻塞
- Frame Pacing
- Jank及长尾帧
- 内存抖动和资源泄漏
- Thermal Throttling

### 优化技术

- Instancing
- Batching
- Frustum Culling
- Occlusion Culling
- LOD
- ASTC / ETC2 / KTX2 纹理压缩
- Shader Variant 控制
- UBO / SSBO 数据组织
- 异步资源加载
- Pipeline Cache
- Render Target复用
- 降低透明与后处理开销

### 性能报告模板

```text
目标平台：
系统版本：
分辨率：
目标帧率：

优化前：
- CPU帧耗时：
- GPU帧耗时：
- P95 / P99帧耗时：
- Draw Call：
- 三角形数量：
- 峰值内存：
- GPU占用：

问题定位：
- 使用工具：
- 瓶颈位置：
- 根本原因：

优化措施：
- 方案：
- 画质影响：
- 兼容性影响：

优化后：
- CPU帧耗时：
- GPU帧耗时：
- P95 / P99帧耗时：
- Draw Call：
- 峰值内存：
```

## 6. 阶段三：Android 底层图形系统

### 学习目标

理解应用提交一帧画面后，从 Buffer 生产到屏幕合成显示的完整链路。

### 学习内容

- Surface、SurfaceView、TextureView
- ANativeWindow
- BufferQueue
- Gralloc
- SurfaceFlinger
- Hardware Composer
- VSync、Choreographer、FrameTimeline
- EGLDisplay、EGLSurface、EGLContext
- EGLContext 共享
- AHardwareBuffer
- ImageReader、SurfaceTexture
- Camera 到 GPU 的低拷贝路径
- 多 Display 管理
- Android 图层合成和 Z-Order
- 黑屏、花屏、Context Lost及Fence问题

### 实践任务

- Camera / 视频纹理直接进入 GPU
- Java UI 与 Native 渲染层混合
- 双屏输出不同内容
- 两个 EGLContext 共享纹理
- AHardwareBuffer 跨模块共享图像
- 使用 Perfetto 分析一帧从应用到显示的链路

## 7. 阶段四：车载功能型 3D

### 7.1 SR / ADAS 可视化

#### 学习内容

- 车辆、世界、传感器和屏幕坐标系
- 车辆姿态与矩阵转换
- 自车、旁车、行人、锥桶和两轮车
- 车道线、停止线、道路边界
- 车位、搜索区域和泊车规划线
- 目标生命周期管理
- 数据插值、外推和平滑
- 数据线程与渲染线程解耦
- 感知数据延迟和乱序处理
- ProtoBuf / DDS / SOME-IP数据接入

#### 实践任务

建立一个可回放的 ADAS 数据系统：

```text
离线数据 / 模拟车辆数据
          ↓
协议解析与时间戳对齐
          ↓
目标缓存、插值与生命周期
          ↓
场景图
          ↓
OpenGL ES / Vulkan 渲染
```

### 7.2 AVM / APA

#### 学习内容

- Camera2 / Camera HAL 基础
- 多路摄像头纹理
- 鱼眼畸变校正
- 鸟瞰投影
- 图像拼接与融合
- 亮度和颜色一致性
- 轨迹线生成
- 方向盘转角与车辆运动模型
- 车轮动画
- 摄像头数据低拷贝

### 7.3 AR-HUD

#### 学习内容

- 相机标定
- 世界到屏幕坐标转换
- 导航元素空间锚定
- 车辆姿态补偿
- 延迟补偿
- 抖动过滤
- 畸变校正
- 遮挡关系
- 强光与低对比度环境可读性
- 驾驶员注意力和安全显示规则

## 8. 阶段五：主流车载 3D 引擎

### 学习策略

不同时深入学习所有引擎，优先顺序：

1. Unity / 团结引擎车机版
2. Kanzi 或 Qt/QML
3. Unreal Engine 保持现有能力

### Unity / 团结引擎

- URP
- Native Plugin
- Android Activity / View 嵌入
- C#与C++数据通信
- Shader Graph与手写Shader
- Addressables
- 资源裁剪
- 启动优化
- 多屏渲染
- Android、QNX、Embedded Linux部署
- 原生Android应用与3D界面融合

### Kanzi

- Kanzi Studio
- Engine API
- Plugin开发
- Data Source与车辆数据绑定
- QNX部署
- Shader和特效优化
- 仪表与多屏HMI

### 验收标准

能够回答并实现：

> 如何将CAN、DDS或ADAS数据稳定绑定到3D场景，并在目标车载平台上长期稳定运行。

## 9. 阶段六：QNX、多屏与跨系统

### 学习内容

- QNX基础开发环境
- QNX Screen
- QNX进程和线程模型
- Android + QNX Hypervisor
- 仪表域与娱乐域隔离
- 跨系统共享内存
- 跨系统纹理传输
- 多屏与多Surface管理
- 仪表、中控、副驾屏和HUD协同
- 系统启动顺序与电源状态管理

### 实践任务

- 设计Android娱乐域与QNX仪表域的交互架构
- 实现车辆数据同时驱动中控3D车模和HUD元素
- 编写异常降级方案：Android重启时仪表安全信息不受影响

## 10. 阶段七：车规稳定性与量产能力

### 学习内容

- ASPICE基础流程
- ISO 26262基础
- ASIL与QM概念
- 功能降级
- Watchdog
- Crash与ANR监控
- GPU Hang与Context Lost恢复
- 黑屏和花屏诊断
- 内存泄漏及碎片
- OTA兼容
- 版本回滚
- 日志、Trace与故障码
- 长稳测试
- 不同配置车型兼容

### 必须形成的能力

- 不只实现效果，还能定义异常策略
- 不只优化平均帧率，还关注P95/P99长尾帧
- 不只在开发机运行，还考虑量产硬件限制
- 不只解决当前问题，还能建设诊断工具和规范

## 11. 阶段八：AI与车载3D融合

### 学习目标

让AI成为图形能力的增量，而不是离开原有优势重新进入通用Agent竞争。

### 值得投入的方向

- 多模态模型理解车内外图像
- 感知结果驱动3D场景提示
- Agent控制车模、车辆功能和HMI
- A2UI / 生成式UI
- 用户意图生成个性化座舱界面
- AI辅助生成Shader、材质和动画
- AI辅助分析RenderDoc和性能日志
- 端侧模型与图形任务的CPU/GPU/NPU资源调度

### 实践任务

在智能座舱演示项目中增加Agent：

1. 用户输入“打开360环视并显示右侧障碍物”。
2. Agent解析意图并调用车辆工具。
3. 3D场景切换至环视模式。
4. 多模态模型或模拟感知数据返回障碍物。
5. 渲染系统高亮对应目标。
6. 系统反馈执行状态和异常。

### AI适合辅助的工作

- Vulkan样板代码
- Shader初稿
- 模型转换脚本
- 单元测试
- 技术文档
- 日志归类
- 性能报告初步分析

### 必须由工程师判断的工作

- 同步和内存正确性
- GPU性能瓶颈
- 车辆数据准确性
- 安全显示逻辑
- 异常恢复
- 量产稳定性

## 12. 综合作品项目

### 项目名称

智能座舱实时图形与端侧AI系统

### 功能范围

- Android应用及Native渲染服务
- OpenGL ES / Vulkan双后端
- glTF PBR车模
- 车门、车窗、车灯和车轮动画
- 自车、旁车、行人、锥桶及车道线
- APA车位和泊车规划线
- SR环境重构
- 360环视模拟数据
- AR-HUD独立视口
- 模拟CAN / DDS / ADAS数据
- Agent语音或文本控制
- 多模态图像识别结果可视化
- RenderDoc / AGI性能报告

### 工程架构

```text
Android UI / 语音入口
          ↓
Agent / Function Calling
          ↓
车辆工具与数据服务
          ↓
DDS / ProtoBuf / 模拟CAN
          ↓
场景状态与时间戳同步
          ↓
OpenGL ES / Vulkan Renderer
          ↓
中控屏 / HUD / 第二Display
```

### 最终交付物

1. Git代码仓库
2. Android APK
3. 系统架构图
4. 模块设计文档
5. 演示视频
6. OpenGL ES与Vulkan对比报告
7. GPU性能优化报告
8. 异常恢复和长稳测试报告
9. 面试用技术PPT

## 13. 面试知识检查表

### 图形基础

- MVP矩阵和坐标系
- 渲染管线
- 深度、模板和混合
- PBR和IBL
- Shader优化
- 纹理格式与压缩

### Vulkan

- Vulkan与OpenGL ES的差异
- Command Buffer
- Descriptor Set
- Pipeline Barrier
- Fence与Semaphore
- GPU内存管理
- SwapChain重建

### Android图形

- BufferQueue
- SurfaceFlinger
- HWC
- EGLContext
- VSync与卡顿
- AHardwareBuffer
- Camera低拷贝

### 车载业务

- AVM拼接与轨迹线
- APA规划线
- SR目标管理
- AR-HUD坐标转换
- CAN / DDS / SOME-IP
- 多屏与跨系统

### 性能与稳定性

- CPU/GPU瓶颈判断
- 掉帧分析
- 内存泄漏
- GPU Hang
- Context Lost
- 长稳和异常恢复

## 14. 不建议过度投入

- 重新从基础矩阵开始系统学习
- Blender高级美术建模
- 纯影视离线渲染
- 桌面级光线追踪算法研究
- 同时深入Unity、Unreal、Kanzi和Qt
- 只做炫酷动效而不接车辆数据
- 只学习Prompt和通用RAG
- 追逐频繁变化但无法形成工程壁垒的Agent框架

## 15. 学习成果与简历映射

每完成一个阶段，都转换为可证明的简历成果：

```text
错误写法：
熟悉Vulkan和GPU性能优化。

正确写法：
完成Android车载渲染模块从OpenGL ES到Vulkan的迁移；
通过实例化、LOD、ASTC纹理压缩和Pipeline Cache，
将目标平台GPU帧耗时由Xms降至Xms，峰值内存降低X%。
```

```text
错误写法：
熟悉ADAS可视化。

正确写法：
设计ADAS目标缓存与场景图系统，支持车辆、行人、车道线和车位的
时间戳对齐、插值及生命周期管理，在乱序和短时丢帧场景下保持稳定显示。
```

## 16. 最终技术路线

```text
Vulkan
  ↓
GPU性能分析
  ↓
Android底层图形系统
  ↓
ADAS / SR / AVM / AR-HUD
  ↓
Unity / 团结引擎
  ↓
QNX / 多屏 / 跨系统
  ↓
车规稳定性与量产
  ↓
端侧AI与3D HMI融合
```

最终目标不是成为单纯的3D动效开发工程师，而是成为：

> 能够将车辆、摄像头、ADAS和AI数据稳定转化为量产级实时图形体验的智能座舱技术专家。
