# 🎬 123AV Android Application

<div align="center">

![Kotlin](https://img.shields.io/badge/Kotlin-2.0.21-7F52FF?logo=kotlin)
![Jetpack Compose](https://img.shields.io/badge/Jetpack%20Compose-2024.09.00-FF6B6B?logo=jetpackcompose)
![Android SDK](https://img.shields.io/badge/Android%20SDK-36-3DDC84?logo=android)
![License](https://img.shields.io/badge/License-MIT-FFFFFF)

</div>

<div align="center">

### ✨ 123AV 的非官方 Android 视频聚合平台

基于 **Kotlin** 与 **Jetpack Compose** 构建的现代化视频应用，集视频浏览、高清播放、智能搜索与个性化管理于一体

[🚀 快速开始](#快速开始) • [📱 功能特性](#功能特性) • [🏗️ 技术架构](#技术架构) • [📁 项目结构](#项目结构)

</div>

---

## 📋 目录

```
├── 功能特性
├── 技术架构
├── 项目结构
├── 环境配置
├── 快速开始
├── 数据来源
└── 许可证
```

---

## ✨ 功能特性

### 🎯 核心功能模块

| 模块 | 功能描述 | 技术实现 |
|------|----------|----------|
| **🏠 首页** | 推荐视频智能展示，支持多分类切换与下拉刷新 | Compose LazyColumn + SwipeRefresh |
| **🔍 搜索** | 关键词智能检索视频内容 | Retrofit + Jsoup 解析 |
| **❤️ 收藏** | 用户登录后管理个人收藏视频，支持无限滚动加载 | StateFlow + Pagination |
| **👤 个人中心** | 用户信息展示、登录状态安全管理 | Secure State Persistence |

### 🚀 技术亮点

- **🎬 专业视频播放**：独立播放器界面，支持多种视频格式
- **📄 智能分页加载**：无限滚动分页，优雅处理大数据量场景
- **💾 状态持久化**：用户登录状态安全本地管理
- **🎨 响应式 UI**：严格遵循 Material Design 3 设计规范
- **🌐 网络优化**：OkHttp + Retrofit 高性能网络请求
- **🔄 异步处理**：Kotlin Coroutines 协程异步编程
- **🔧 代码优化**：统一的异常处理、数据库索引优化、消除魔法数字

---

## 🏗️ 技术架构

### 📦 核心技术栈

| 类别 | 技术选型 | 版本要求 |
|------|----------|----------|
| **开发语言** | Kotlin | 2.0.21 |
| **UI 框架** | Jetpack Compose | 2024.09.00 |
| **状态管理** | MutableState + StateFlow | - |
| **网络请求** | OkHttp | 4.12.0 |
| **HTML 解析** | Jsoup | 1.17.2 |
| **JSON 解析** | Gson | 2.10.1 |
| **视频播放** | AndroidX Media3 (ExoPlayer) | 1.3.1 |
| **本地存储** | Room Database | 2.8.4 |
| **图片加载** | Coil | 2.7.0 |
| **异步处理** | Kotlin Coroutines | - |
| **最低 SDK** | Android | 11 (API 30) |
| **目标 SDK** | Android | 14 (API 36) |

### 🏛️ 分层架构设计

```
┌─────────────────────────────────────────────────────────┐
│                      UI Layer                           │
│  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐      │
│  │  Home   │ │ Search  │ │Favorites│ │ Profile │      │
│  │ Screen  │ │ Screen  │ │ Screen  │ │ Screen  │      │
│  └────┬────┘ └────┬────┘ └────┬────┘ └────┬────┘      │
│       └───────────┴───────────┴───────────┘           │
│                      Navigation                        │
├─────────────────────────────────────────────────────────┤
│                   State Management                      │
│              UserStateManager + StateFlow               │
├─────────────────────────────────────────────────────────┤
│                   Data Layer                           │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐      │
│  │   Network   │ │    Models   │ │   Download  │      │
│  │   Service   │ │             │ │   Manager   │      │
│  └─────────────┘ └─────────────┘ └─────────────┘      │
├─────────────────────────────────────────────────────────┤
│                   Network Layer                        │
│              OkHttp + Jsoup + Gson + Media3            │
└─────────────────────────────────────────────────────────┘
```

---

## 📁 项目结构

```
app/src/main/java/com/android123av/app/
├── 📂 components/              # 🎨 可复用 UI 组件库
│   ├── CategoryTabs.kt        # 📑 分类标签组件
│   ├── NavigationComponent.kt # 🧭 导航组件
│   ├── PaginationComponent.kt # 📄 智能分页组件
│   └── VideoItem.kt          # 📹 视频列表项组件
├── 📂 constants/              # ⚙️ 常量定义
│   ├── AppConstants.kt       # 📱 应用常量
│   └── PlayerConstants.kt    # 🎬 播放器常量
├── 📂 download/                # ⬇️ 下载管理层
│   ├── CachedVideoDetails.kt  # 💾 缓存视频详情
│   ├── DownloadDatabase.kt    # 🗄️ 下载数据库
│   ├── DownloadModels.kt      # 📊 下载任务模型
│   ├── M3U8DownloadManager.kt # 🎥 M3U8 下载管理
│   └── VideoDetailsCacheManager.kt # 📋 视频详情缓存管理
├── 📂 models/                  # 📊 数据模型层
│   ├── Models.kt              # 🎬 视频数据模型
│   ├── PlayerState.kt         # 🎮 播放器状态
│   └── VideoDetails.kt        # 📋 视频详情模型
├── 📂 network/                 # 🌐 网络请求层
│   ├── HtmlParser.kt          # 🔍 HTML 解析器
│   ├── HtmlParserUtils.kt     # 🔧 HTML 解析工具
│   ├── NetworkConfig.kt       # ⚙️ 网络配置
│   ├── NetworkService.kt      # 🔗 网络请求服务
│   ├── PersistentCookieJar.kt  # 🍪 Cookie 持久化
│   └── SiteManager.kt         # 🌍 站点管理
├── 📂 player/                  # 🎬 播放器层
│   └── ExoPlayerManager.kt    # 🎥 ExoPlayer 管理器
├── 📂 repository/              # 📦 数据仓库层
│   └── VideoRepository.kt     # 🎬 视频数据仓库
├── 📂 screens/                 # 📱 页面组件层
│   ├── AllVideo.kt            # 🔍 全部视频页面
│   ├── DownloadsScreen.kt     # ⬇️ 下载页面
│   ├── FavoritesScreen.kt     # ❤️ 收藏页面
│   ├── HelpScreen.kt          # ❓ 帮助页面
│   ├── HomeScreen.kt          # 🏠 首页
│   ├── NetworkTestScreen.kt   # 🌐 网络测试页面
│   ├── ProfileScreen.kt       # 👤 个人中心
│   ├── SettingsScreen.kt      # ⚙️ 设置页面
│   ├── VideoPlayerScreen.kt   # 🎬 视频播放页面
│   └── VideoPlayerScreenRefactored.kt # 🎬 播放器重构版本
├── 📂 state/                   # 💾 状态管理层
│   ├── AppState.kt            # 📱 应用状态
│   ├── DownloadPathManager.kt # 📁 下载路径管理
│   ├── SearchHistoryManager.kt # 🔍 搜索历史管理
│   ├── ThemeStateManager.kt   # 🎨 主题状态管理
│   ├── UserState.kt           # 👤 用户状态
│   └── UserStateManager.kt    # 👤 用户状态管理
├── 📂 ui/                      # 🎨 UI 组件层
│   ├── components/            # 🧩 UI 子组件
│   │   ├── LoadingState.kt    # ⏳ 加载状态
│   │   ├── PlayerControls.kt  # 🎮 播放器控件
│   │   ├── VideoErrorState.kt # ❌ 视频错误状态
│   │   └── VideoInfoPanel.kt  # 📋 视频信息面板
│   └── theme/                 # 🎨 主题配置
│       ├── Color.kt           # 🌈 颜色定义
│       ├── Theme.kt           # 🎯 应用主题
│       └── Type.kt            # 🔤 字体排版
├── 📂 utils/                   # 🔧 工具类层
│   ├── ActivityUtils.kt       # 📱 Activity 工具
│   └── ExceptionHandler.kt   # ⚠️ 异常处理工具
├── 📂 viewmodel/               # 🧠 ViewModel 层
│   ├── VideoPlayerViewModel.kt # 🎬 播放器 ViewModel
│   └── VideoPlayerViewModelFactory.kt # 🏭 ViewModel 工厂
├── MainActivity.kt            # 🚀 应用入口
├── Navigation.kt              # 🧭 导航配置
├── DownloadsActivity.kt       # ⬇️ 下载 Activity
├── HelpActivity.kt            # ❓ 帮助 Activity
├── LoginActivity.kt           # 🔐 登录 Activity
├── NetworkTestActivity.kt     # 🌐 网络测试 Activity
├── SettingsActivity.kt       # ⚙️ 设置 Activity
└── VideoPlayerActivity.kt    # 🎬 播放器 Activity
```

---

## ⚙️ 环境配置

### 🔧 开发环境要求

| 工具 | 版本要求 | 说明 |
|------|----------|------|
| **Android Studio** | Ladybug (2024.2.1)+ | 官方 IDE |
| **JDK** | 11 | Java 开发套件 |
| **Gradle** | 8.13.2+ | 构建工具 |
| **Android SDK** | 36 | 编译目标 SDK |
| **Kotlin** | 2.0.21 | 编程语言 |
| **KSP** | - | Kotlin 符号处理器 |

### 📦 核心依赖配置

项目采用 Gradle Kotlin DSL 与版本目录（`libs.versions.toml`）进行现代化构建配置：

```kotlin
// 🚀 Core
implementation("androidx.core:core-ktx:1.17.0")
implementation("androidx.lifecycle:lifecycle-runtime-ktx:2.9.4")
implementation("androidx.lifecycle:lifecycle-viewmodel-compose:2.9.4")
implementation("androidx.activity:activity-compose:1.11.0")

// 🎨 Compose BOM
implementation(platform("androidx.compose:compose-bom:2024.09.00"))
implementation("androidx.compose.ui:ui")
implementation("androidx.compose.ui:ui-graphics")
implementation("androidx.compose.ui:ui-tooling-preview")
implementation("androidx.compose.material3:material3")
implementation("androidx.compose.material3:material3-adaptive-navigation-suite")
implementation("androidx.compose.material3:material3-pullrefresh")
implementation("androidx.compose.material:material")
implementation("androidx.compose.material:material-icons-extended")
implementation("androidx.compose.foundation:foundation:1.10.0")
implementation("androidx.compose.animation:animation:1.10.0")

// 🧭 Navigation
implementation("androidx.navigation:navigation-compose:2.7.7")

// 🌐 Network
implementation("com.squareup.okhttp3:okhttp:4.12.0")
implementation("org.jsoup:jsoup:1.17.2")
implementation("com.google.code.gson:gson:2.10.1")

// 🖼️ Image Loading
implementation("io.coil-kt:coil-compose:2.7.0")

// 🎬 Media3 Video Player
implementation("androidx.media3:media3-exoplayer:1.3.1")
implementation("androidx.media3:media3-exoplayer-hls:1.3.1")
implementation("androidx.media3:media3-exoplayer-dash:1.3.1")
implementation("androidx.media3:media3-datasource-okhttp:1.3.1")
implementation("androidx.media3:media3-ui:1.9.0")

// 💾 Room Database
implementation("androidx.room:room-runtime:2.8.4")
implementation("androidx.room:room-ktx:2.8.4")
ksp("androidx.room:room-compiler:2.8.4")

// 🎮 Cast
implementation("com.google.android.gms:play-services-cast:22.2.0")

// 📐 Layout
implementation("androidx.constraintlayout:constraintlayout:2.2.1")
```

---

## 🚀 快速开始

### 📦 编译构建

```bash
# 🔄 同步并构建项目
./gradlew assembleDebug

# ✅ 运行 lint 代码检查
./gradlew lint

# 🧪 运行单元测试
./gradlew test

# 🧹 清理构建产物
./gradlew clean

# 📱 调试构建并安装到设备
./gradlew installDebug
```

### 📱 运行应用

1. 📂 使用 Android Studio 打开项目
2. ⏳ 等待 Gradle 同步完成
3. 📱 选择目标设备（真机或模拟器）
4. ▶️ 点击 `Run` 按钮或使用快捷键 `Shift + F10`


---

<div align="center">

## ⚠️ 免责声明

<div align="left" style="background-color: #1a1a2e; padding: 20px; border-radius: 12px; border: 1px solid #16213e;">

### 📌 法律声明

**1. 数据来源声明**
- 本应用程序所展示的全部数据均来源于公开的第三方平台 [123AV.org](https://123av.org)
- 本应用仅作为技术演示与学习研究之用，不拥有任何原始数据内容

**2. 无关联关系声明**
- 本项目与 **123av.org** 及其关联方不存在任何形式的隶属、合作、授权或代言关系
- 本应用未获得 123AV 官方的任何形式认可或背书

**3. 使用限制声明**
- 本软件仅供个人学习研究和技术交流使用
- **严禁将本软件用于任何商业用途**
- 用户应自行承担使用本软件的一切法律责任

**4. 知识产权声明**
- 本软件涉及的知识产权归原始权利人所有
- 如您认为本软件侵犯了您的权益，请立即联系我们进行删除处理

**5. 风险提示声明**
- 本软件按"原样"提供，不提供任何明示或暗示的保证
- 对于因使用本软件而产生的任何直接或间接损失，我们不承担任何责任
- 使用本软件即表示您已充分理解并同意上述全部声明

</div>

<div align="center">

---

**如对本仓库有任何异议，请通过 GitHub Issues 联系处理。**

</div>

</div>

