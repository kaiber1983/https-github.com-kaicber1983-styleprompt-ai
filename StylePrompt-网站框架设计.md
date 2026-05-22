# StylePrompt 网站框架设计文档
## AI 视觉风格平台 - 完整技术架构

---

## 一、网站架构总览

### 1.1 架构理念
- **移动优先**：响应式设计，移动端体验优先
- **性能优先**：快速加载，图片懒加载，CDN 加速
- **SEO 优先**：每个风格卡独立页面，结构化数据
- **用户留存**：从浏览到收藏到创作的完整闭环

### 1.2 技术栈选型

**前端**：
- Next.js 14 (App Router)
- React 18
- TypeScript
- Tailwind CSS
- shadcn/ui
- Framer Motion (动画)
- React Query (数据获取)

**后端**：
- Node.js + Express / Next.js API Routes
- PostgreSQL (用户、订阅、资产)
- MongoDB (风格卡内容)
- Redis (缓存、会话)
- Prisma ORM

**基础设施**：
- Vercel (部署)
- AWS S3 / Cloudflare R2 (图片存储)
- Cloudflare CDN
- Stripe (支付)
- Resend (邮件)

**AI 集成**：
- OpenAI API (提示词优化)
- Replicate (Flux, SD)
- Google Vertex AI (Gemini, Imagen)

---

## 二、网站地图 (Sitemap)

### 2.1 公开页面

```
/                           首页 - 风格探索
├── /styles                 风格库主页
│   ├── /styles/[id]        单个风格详情页
│   ├── /styles/category/[name]  分类页
│   └── /styles/search      搜索结果页
│
├── /collections            精选合集
│   ├── /collections/trending    热门风格
│   ├── /collections/new         最新风格
│   └── /collections/[id]        主题合集详情
│
├── /use-cases              使用场景
│   ├── /use-cases/ecommerce     电商产品图
│   ├── /use-cases/social-media  社交媒体
│   ├── /use-cases/character     角色设计
│   ├── /use-cases/game-asset    游戏资产
│   └── /use-cases/video-cover   视频封面
│
├── /pricing                定价页面
├── /about                  关于我们
├── /blog                   博客/教程
└── /docs                   文档中心
```

### 2.2 用户页面（需登录）

```
/dashboard                  用户仪表盘
├── /dashboard/favorites    我的收藏
├── /dashboard/moodboards   我的情绪板
├── /dashboard/projects     我的项目
├── /dashboard/characters   我的角色库
├── /dashboard/assets       我的资产库
├── /dashboard/history      生成历史
└── /dashboard/settings     账户设置
```

### 2.3 工具页面

```
/tools                      工具集
├── /tools/converter        提示词转换器
├── /tools/optimizer        提示词优化器
├── /tools/generator        批量生成器
└── /tools/analyzer         风格分析器
```

### 2.4 认证页面

```
/auth
├── /auth/login            登录
├── /auth/signup           注册
├── /auth/forgot-password  忘记密码
└── /auth/verify-email     邮箱验证
```

---

## 三、核心页面设计

### 3.1 首页 (/)

**设计目标**：
- 3 秒内让用户理解产品价值
- 引导用户浏览风格库
- 展示平台核心能力

**页面结构**：

```
┌─────────────────────────────────────┐
│ Header (固定顶部)                      │
│ Logo | 风格库 | 使用场景 | 定价 | 登录   │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ Hero Section                         │
│                                      │
│ [大标题] 3 分钟找到你的 AI 视觉风格      │
│ [副标题] 1000+ 风格 × 多模型提示词       │
│                                      │
│ [搜索框] 搜索风格、情绪、场景...         │
│ [热门标签] #赛博朋克 #电商产品图 #国风    │
│                                      │
│ [风格预览网格 - 6 个精选风格卡]          │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ 热门风格分类                           │
│ [Tab] 全部 | 电商 | 角色 | 游戏 | 视频  │
│                                      │
│ [瀑布流网格 - 12 个风格卡]              │
│ [加载更多]                            │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ 功能亮点                              │
│ [图标+文字]                           │
│ • 多模型支持                          │
│ • 一键转换                            │
│ • 风格资产库                          │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ 使用场景展示                           │
│ [4 个场景卡片]                         │
│ 电商 | 社交媒体 | 游戏 | IP 角色        │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ 用户案例 / 社区作品                     │
│ [作品展示网格]                         │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ CTA Section                          │
│ 开始探索你的风格                        │
│ [免费开始] [查看定价]                   │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ Footer                               │
│ 产品 | 资源 | 社区 | 关于 | 法律        │
└─────────────────────────────────────┘
```

**关键交互**：
- 搜索框支持自动补全
- 风格卡 hover 显示快速预览
- 无限滚动加载
- 标签点击筛选

---

### 3.2 风格详情页 (/styles/[id])

**设计目标**：
- 完整展示风格的所有信息
- 提供多模型提示词
- 引导用户收藏或生成

**页面结构**：

```
┌─────────────────────────────────────┐
│ Header (固定)                         │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ 面包屑导航                             │
│ 首页 > 风格库 > 赛博朋克 > 赛博东方禅意   │
└─────────────────────────────────────┘

┌──────────────────┬──────────────────┐
│                  │                  │
│  [主图展示区]      │  [风格信息卡]      │
│  大图 + 缩略图网格  │                  │
│                  │  风格名称          │
│  [图片灯箱]        │  情绪标签          │
│                  │  适用场景          │
│                  │  热度/收藏数        │
│                  │                  │
│                  │  [收藏按钮]        │
│                  │  [分享按钮]        │
│                  │                  │
└──────────────────┴──────────────────┘

┌─────────────────────────────────────┐
│ 提示词区域 (Tab 切换)                   │
│                                      │
│ [Tab] Midjourney | Gemini | Imagen | Flux │
│                                      │
│ ┌─────────────────────────────────┐ │
│ │ Midjourney Prompt               │ │
│ │                                 │ │
│ │ [提示词内容]                      │ │
│ │                                 │ │
│ │ sref: 1234567890                │ │
│ │                                 │ │
│ │ [复制] [优化] [生成]              │ │
│ └─────────────────────────────────┘ │
│                                      │
│ ┌─────────────────────────────────┐ │
│ │ 反向提示词                        │ │
│ │ [内容]                           │ │
│ │ [复制]                           │ │
│ └─────────────────────────────────┘ │
│                                      │
│ ┌─────────────────────────────────┐ │
│ │ 参数建议                          │ │
│ │ 尺寸: 16:9                       │ │
│ │ 步数: 30-50                      │ │
│ │ 权重: --stylize 500              │ │
│ └─────────────────────────────────┘ │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ 场景变体                              │
│ [Tab] 产品图 | 角色 | 场景 | 3D参考    │
│                                      │
│ [对应场景的提示词变体]                  │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ 使用案例                              │
│ [用户生成的作品展示]                    │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ 相似风格推荐                           │
│ [6-8 个相似风格卡]                     │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ Footer                               │
└─────────────────────────────────────┘
```

**关键功能**：
- 一键复制提示词
- 提示词优化（AI 改写）
- 直接生成（Pro 用户）
- 添加到情绪板
- 导出为 PDF/JSON

**权限控制**：
- 免费用户：查看基础提示词
- Pro 用户：查看全部模型提示词 + 场景变体
- Studio 用户：批量导出 + 自定义修改

### 3.3 风格库页面 (/styles)

**设计目标**：
- 高效浏览大量风格
- 强大的筛选和搜索
- 引导用户深入探索

**页面结构**：

```
┌─────────────────────────────────────┐
│ Header                               │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ 搜索 + 筛选栏                          │
│                                      │
│ [搜索框] 搜索风格、情绪、场景...         │
│                                      │
│ [筛选器]                              │
│ 情绪: [全部 ▼] 场景: [全部 ▼]         │
│ 模型: [全部 ▼] 排序: [热门 ▼]         │
└─────────────────────────────────────┘

┌──────────┬──────────────────────────┐
│          │                          │
│ [侧边栏]  │  [风格卡网格 - 瀑布流]      │
│          │                          │
│ 情绪      │  ┌────┐ ┌────┐ ┌────┐   │
│ □ 孤独    │  │卡片│ │卡片│ │卡片│   │
│ □ 温暖    │  └────┘ └────┘ └────┘   │
│ □ 神秘    │                          │
│          │  ┌────┐ ┌────┐ ┌────┐   │
│ 光影      │  │卡片│ │卡片│ │卡片│   │
│ □ 霓虹    │  └────┘ └────┘ └────┘   │
│ □ 柔光    │                          │
│          │  [无限滚动加载]            │
│ 场景      │                          │
│ □ 电商    │                          │
│ □ 游戏    │                          │
│          │                          │
│ [清除]    │                          │
│          │                          │
└──────────┴──────────────────────────┘

┌─────────────────────────────────────┐
│ Footer                               │
└─────────────────────────────────────┘
```

**风格卡组件设计**：

```
┌─────────────────────┐
│                     │
│   [预览图]           │
│                     │
├─────────────────────┤
│ 风格名称             │
│ [情绪标签] [场景标签] │
│                     │
│ 👁 1.2k  ❤️ 234     │
│                     │
│ [收藏] [查看详情]     │
└─────────────────────┘
```

**交互特性**：
- Hover 显示快速预览
- 点击卡片进入详情页
- 快速收藏（无需跳转）
- 筛选器实时更新
- URL 参数同步（可分享筛选结果）

---

### 3.4 用户仪表盘 (/dashboard)

**设计目标**：
- 清晰展示用户资产
- 快速访问常用功能
- 引导用户深度使用

**页面结构**：

```
┌─────────────────────────────────────┐
│ Header                               │
└─────────────────────────────────────┘

┌──────────┬──────────────────────────┐
│          │                          │
│ [侧边栏]  │  [主内容区]               │
│          │                          │
│ 📊 概览   │  ┌────────────────────┐ │
│ ❤️ 收藏   │  │ 欢迎回来，用户名    │ │
│ 📋 情绪板  │  │                    │ │
│ 📁 项目   │  │ 统计卡片            │ │
│ 👤 角色库  │  │ 收藏: 45  项目: 3   │ │
│ 🖼️ 资产库  │  │ 生成: 128         │ │
│ 📜 历史   │  └────────────────────┘ │
│ ⚙️ 设置   │                          │
│          │  ┌────────────────────┐ │
│ [升级]    │  │ 最近收藏            │ │
│          │  │ [风格卡网格]        │ │
│          │  └────────────────────┘ │
│          │                          │
│          │  ┌────────────────────┐ │
│          │  │ 我的项目            │ │
│          │  │ [项目卡片列表]      │ │
│          │  └────────────────────┘ │
│          │                          │
└──────────┴──────────────────────────┘
```

**子页面设计**：

#### 我的收藏 (/dashboard/favorites)
```
┌─────────────────────────────────────┐
│ 我的收藏 (45)                         │
│                                      │
│ [搜索] [筛选: 全部 ▼] [排序: 最新 ▼]  │
│                                      │
│ [风格卡网格]                          │
│                                      │
│ [分页]                               │
└─────────────────────────────────────┘
```

#### 我的情绪板 (/dashboard/moodboards)
```
┌─────────────────────────────────────┐
│ 我的情绪板                            │
│                                      │
│ [+ 新建情绪板]                        │
│                                      │
│ ┌──────────────┐ ┌──────────────┐  │
│ │ 情绪板 1      │ │ 情绪板 2      │  │
│ │ [预览网格]    │ │ [预览网格]    │  │
│ │ 12 个风格     │ │ 8 个风格      │  │
│ │ [编辑][分享]  │ │ [编辑][分享]  │  │
│ └──────────────┘ └──────────────┘  │
└─────────────────────────────────────┘
```

#### 我的项目 (/dashboard/projects)
```
┌─────────────────────────────────────┐
│ 我的项目                              │
│                                      │
│ [+ 新建项目]                          │
│                                      │
│ ┌─────────────────────────────────┐ │
│ │ 项目名称: 电商春季大促              │ │
│ │ 创建时间: 2026-05-15               │ │
│ │                                  │ │
│ │ 风格: 3  角色: 2  资产: 45        │ │
│ │                                  │ │
│ │ [打开项目] [设置]                  │ │
│ └─────────────────────────────────┘ │
└─────────────────────────────────────┘
```

---

### 3.5 提示词转换器 (/tools/converter)

**设计目标**：
- 快速转换不同模型提示词
- 提供场景化变体
- 引导用户升级

**页面结构**：

```
┌─────────────────────────────────────┐
│ Header                               │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ 提示词转换器                           │
│                                      │
│ 将你的提示词转换为不同 AI 模型格式       │
└─────────────────────────────────────┘

┌──────────────────┬──────────────────┐
│                  │                  │
│ [输入区]          │  [输出区]         │
│                  │                  │
│ 源模型:           │  目标模型:        │
│ [Midjourney ▼]   │  [Gemini ▼]      │
│                  │                  │
│ ┌──────────────┐ │  ┌─────────────┐ │
│ │              │ │  │             │ │
│ │ [输入提示词]  │ │  │ [转换结果]   │ │
│ │              │ │  │             │ │
│ │              │ │  │             │ │
│ └──────────────┘ │  └─────────────┘ │
│                  │                  │
│ 或选择风格:       │  [复制] [优化]    │
│ [从风格库选择]    │                  │
│                  │                  │
│ [转换]           │                  │
│                  │                  │
└──────────────────┴──────────────────┘

┌─────────────────────────────────────┐
│ 场景变体 (Pro 功能)                    │
│                                      │
│ [Tab] 产品图 | 角色 | 场景 | 视频封面  │
│                                      │
│ [对应场景的提示词]                     │
│                                      │
│ [升级解锁]                            │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│ 批量转换 (Studio 功能)                 │
│                                      │
│ [上传 CSV] [批量处理] [导出结果]       │
│                                      │
│ [升级解锁]                            │
└─────────────────────────────────────┘
```

## 四、组件库设计

### 4.1 核心组件

#### StyleCard（风格卡片）
```typescript
interface StyleCardProps {
  id: string;
  name: string;
  nameEn: string;
  previewImage: string;
  tags: {
    mood: string[];
    scene: string[];
  };
  views: number;
  favorites: number;
  isFavorited: boolean;
  onFavorite: () => void;
  onClick: () => void;
}
```

**视觉设计**：
- 卡片尺寸：自适应（瀑布流）
- 圆角：8px
- 阴影：hover 时提升
- 图片比例：4:3 或 16:9
- 标签：最多显示 3 个，其余折叠

#### PromptDisplay（提示词展示）
```typescript
interface PromptDisplayProps {
  model: 'midjourney' | 'gemini' | 'imagen' | 'flux';
  prompt: string;
  negativePrompt?: string;
  sref?: string;
  parameters?: Record<string, any>;
  onCopy: () => void;
  onOptimize?: () => void;
  onGenerate?: () => void;
}
```

**功能**：
- 语法高亮
- 一键复制
- AI 优化（Pro）
- 直接生成（Pro）

#### FilterSidebar（筛选侧边栏）
```typescript
interface FilterSidebarProps {
  filters: {
    mood: string[];
    lighting: string[];
    material: string[];
    scene: string[];
  };
  selectedFilters: Record<string, string[]>;
  onFilterChange: (category: string, values: string[]) => void;
  onClear: () => void;
}
```

#### MoodboardGrid（情绪板网格）
```typescript
interface MoodboardGridProps {
  styles: Style[];
  layout: 'grid' | 'masonry';
  editable: boolean;
  onReorder?: (newOrder: string[]) => void;
  onRemove?: (id: string) => void;
}
```

---

### 4.2 布局组件

#### AppLayout（应用布局）
```typescript
interface AppLayoutProps {
  children: React.ReactNode;
  showSidebar?: boolean;
  sidebarContent?: React.ReactNode;
}
```

#### DashboardLayout（仪表盘布局）
```typescript
interface DashboardLayoutProps {
  children: React.ReactNode;
  activeTab: string;
}
```

---

### 4.3 交互组件

#### SearchBar（搜索栏）
- 自动补全
- 搜索历史
- 热门搜索建议
- 支持标签搜索

#### TagFilter（标签筛选器）
- 多选支持
- 快速清除
- 标签计数显示

#### ImageGallery（图片画廊）
- 灯箱效果
- 缩放/平移
- 键盘导航
- 分享功能

---

## 五、数据库设计

### 5.1 核心表结构

#### users（用户表）
```sql
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  email VARCHAR(255) UNIQUE NOT NULL,
  username VARCHAR(50) UNIQUE,
  password_hash VARCHAR(255) NOT NULL,
  full_name VARCHAR(100),
  avatar_url TEXT,
  subscription_tier VARCHAR(20) DEFAULT 'free',
  subscription_status VARCHAR(20),
  subscription_expires_at TIMESTAMP,
  credits INT DEFAULT 0,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);
```

#### styles（风格表 - MongoDB）
```javascript
{
  _id: ObjectId,
  id: "style_001",
  name: {
    cn: "赛博东方禅意",
    en: "Cyber Oriental Zen"
  },
  description: {
    cn: "...",
    en: "..."
  },
  tags: {
    mood: ["孤独", "神秘", "克制"],
    lighting: ["霓虹", "柔光"],
    material: ["金属", "玻璃"],
    composition: ["中心构图", "广角"],
    scene: ["头像", "海报", "游戏"],
    style: ["赛博朋克", "东方"]
  },
  prompts: {
    midjourney: {
      sref: "1234567890",
      prompt: "...",
      negative: "...",
      parameters: {
        aspect: "16:9",
        stylize: 500
      }
    },
    gemini: {
      prompt: "...",
      negative: "..."
    },
    imagen: {
      prompt: "...",
      negative: "..."
    },
    flux: {
      prompt: "...",
      negative: "..."
    }
  },
  variants: {
    product: { /* 产品图变体 */ },
    character: { /* 角色变体 */ },
    scene: { /* 场景变体 */ },
    video: { /* 视频封面变体 */ }
  },
  preview_images: [
    {
      url: "https://...",
      width: 1024,
      height: 768,
      thumbnail: "https://..."
    }
  ],
  use_cases: ["电商", "IP", "游戏"],
  stats: {
    views: 8500,
    favorites: 234,
    generations: 1200
  },
  seo: {
    slug: "cyber-oriental-zen",
    meta_title: "...",
    meta_description: "...",
    keywords: ["..."]
  },
  status: "published",
  featured: false,
  created_at: ISODate,
  updated_at: ISODate
}
```

#### favorites（收藏表）
```sql
CREATE TABLE favorites (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  style_id VARCHAR(50) NOT NULL,
  created_at TIMESTAMP DEFAULT NOW(),
  UNIQUE(user_id, style_id)
);

CREATE INDEX idx_favorites_user ON favorites(user_id);
CREATE INDEX idx_favorites_style ON favorites(style_id);
```

#### moodboards（情绪板表）
```sql
CREATE TABLE moodboards (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  name VARCHAR(100) NOT NULL,
  description TEXT,
  is_public BOOLEAN DEFAULT false,
  style_ids TEXT[], -- Array of style IDs
  cover_image TEXT,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_moodboards_user ON moodboards(user_id);
```

#### projects（项目表）
```sql
CREATE TABLE projects (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  name VARCHAR(100) NOT NULL,
  description TEXT,
  brand_colors JSONB, -- 品牌色
  style_preferences JSONB, -- 风格偏好
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);
```

#### generations（生成历史表）
```sql
CREATE TABLE generations (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  style_id VARCHAR(50),
  model VARCHAR(50) NOT NULL,
  prompt TEXT NOT NULL,
  negative_prompt TEXT,
  parameters JSONB,
  result_url TEXT,
  status VARCHAR(20) DEFAULT 'pending',
  error_message TEXT,
  credits_used INT DEFAULT 1,
  created_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_generations_user ON generations(user_id);
CREATE INDEX idx_generations_style ON generations(style_id);
```

---

### 5.2 关系图

```
users (1) ─────< (N) favorites
  │
  ├─────< (N) moodboards
  │
  ├─────< (N) projects
  │
  └─────< (N) generations

styles (MongoDB) ←──── favorites.style_id
                 ←──── generations.style_id
```

---

## 六、API 设计

### 6.1 RESTful API 端点

#### 风格相关
```
GET    /api/styles              获取风格列表
GET    /api/styles/:id          获取风格详情
GET    /api/styles/search       搜索风格
GET    /api/styles/trending     热门风格
GET    /api/styles/similar/:id  相似风格推荐
```

#### 用户相关
```
POST   /api/auth/signup         注册
POST   /api/auth/login          登录
POST   /api/auth/logout         登出
GET    /api/user/profile        获取用户信息
PATCH  /api/user/profile        更新用户信息
```

#### 收藏相关
```
GET    /api/favorites           获取收藏列表
POST   /api/favorites           添加收藏
DELETE /api/favorites/:styleId  取消收藏
```

#### 情绪板相关
```
GET    /api/moodboards          获取情绪板列表
POST   /api/moodboards          创建情绪板
GET    /api/moodboards/:id      获取情绪板详情
PATCH  /api/moodboards/:id      更新情绪板
DELETE /api/moodboards/:id      删除情绪板
POST   /api/moodboards/:id/styles  添加风格到情绪板
DELETE /api/moodboards/:id/styles/:styleId  移除风格
```

#### 工具相关
```
POST   /api/tools/convert       提示词转换
POST   /api/tools/optimize      提示词优化
POST   /api/tools/generate      生成图片
GET    /api/tools/generations   获取生成历史
```

---

### 6.2 API 响应格式

**成功响应**：
```json
{
  "success": true,
  "data": { /* 数据 */ },
  "meta": {
    "page": 1,
    "limit": 20,
    "total": 100
  }
}
```

**错误响应**：
```json
{
  "success": false,
  "error": {
    "code": "UNAUTHORIZED",
    "message": "请先登录",
    "details": {}
  }
}
```

## 七、用户流程设计

### 7.1 新用户首次访问流程

```
1. 访问首页
   ↓
2. 浏览风格卡（无需登录）
   ↓
3. 点击风格卡查看详情
   ↓
4. 尝试复制提示词 → 提示登录
   ↓
5. 注册/登录
   ↓
6. 复制提示词成功
   ↓
7. 引导收藏风格
   ↓
8. 引导创建情绪板
   ↓
9. 引导升级 Pro（如果使用频繁）
```

### 7.2 付费用户典型工作流

**场景 1：电商卖家准备产品图**
```
1. 登录 → 进入仪表盘
   ↓
2. 创建新项目："春季新品发布"
   ↓
3. 在风格库搜索"产品摄影"
   ↓
4. 收藏 5-10 个适合的风格
   ↓
5. 创建情绪板："春季产品风格"
   ↓
6. 使用提示词转换器，转换为 Gemini 格式
   ↓
7. 批量生成产品图
   ↓
8. 保存到资产库
   ↓
9. 导出提示词包给团队
```

**场景 2：游戏美术寻找角色风格**
```
1. 搜索"角色设计 + 赛博朋克"
   ↓
2. 筛选：情绪=神秘，场景=游戏
   ↓
3. 查看 20+ 个风格详情
   ↓
4. 收藏 3 个最符合的风格
   ↓
5. 使用"角色一致性模板"
   ↓
6. 生成角色多角度参考图
   ↓
7. 保存到角色库
   ↓
8. 分享给团队评审
```

**场景 3：自媒体创作者制作封面**
```
1. 进入"使用场景 > 视频封面"
   ↓
2. 浏览推荐风格
   ↓
3. 选择"电影感 + 高对比"风格
   ↓
4. 查看 YouTube 封面变体
   ↓
5. 复制提示词到 Midjourney
   ↓
6. 生成 3-5 个版本
   ↓
7. 保存最佳版本到资产库
   ↓
8. 下次直接从历史记录复用
```

---

## 八、权限与订阅系统

### 8.1 功能权限矩阵

| 功能 | 免费版 | Pro | Studio | Enterprise |
|------|--------|-----|--------|------------|
| 浏览风格库 | 30% | 100% | 100% | 100% |
| 查看基础提示词 | ✓ | ✓ | ✓ | ✓ |
| 查看多模型提示词 | ✗ | ✓ | ✓ | ✓ |
| 复制提示词 | 3次/天 | 无限 | 无限 | 无限 |
| 收藏风格 | 10个 | 无限 | 无限 | 无限 |
| 创建情绪板 | 1个 | 10个 | 无限 | 无限 |
| 提示词转换 | 5次/天 | 无限 | 无限 | 无限 |
| 提示词优化 | ✗ | ✓ | ✓ | ✓ |
| 场景变体 | ✗ | ✓ | ✓ | ✓ |
| 平台内生成 | ✗ | 50次/月 | 200次/月 | 无限 |
| 批量导出 | ✗ | ✓ | ✓ | ✓ |
| 项目管理 | ✗ | 3个 | 无限 | 无限 |
| 角色库 | ✗ | ✓ | ✓ | ✓ |
| 资产库 | ✗ | 1GB | 10GB | 无限 |
| 团队协作 | ✗ | ✗ | 5人 | 无限 |
| 品牌风格库 | ✗ | ✗ | ✓ | ✓ |
| API 访问 | ✗ | ✗ | ✗ | ✓ |
| 优先支持 | ✗ | ✗ | ✓ | ✓ |

### 8.2 订阅管理流程

```
用户点击"升级" 
   ↓
选择套餐（月付/年付）
   ↓
Stripe 支付页面
   ↓
支付成功 → Webhook 回调
   ↓
更新用户订阅状态
   ↓
发送欢迎邮件
   ↓
解锁 Pro 功能
```

### 8.3 使用限制实现

**前端检查**：
```typescript
// 检查用户权限
const canAccessFeature = (feature: string) => {
  const tier = user.subscriptionTier;
  return FEATURE_MATRIX[tier][feature];
};

// 使用示例
if (!canAccessFeature('multiModelPrompts')) {
  showUpgradeModal();
  return;
}
```

**后端验证**：
```typescript
// API 中间件
const requirePro = (req, res, next) => {
  if (!['pro', 'studio', 'enterprise'].includes(req.user.tier)) {
    return res.status(403).json({
      error: 'PRO_REQUIRED',
      message: '此功能需要 Pro 订阅'
    });
  }
  next();
};
```

---

## 九、SEO 优化策略

### 9.1 页面 SEO 结构

**风格详情页 SEO**：
```html
<head>
  <title>赛博东方禅意 AI 风格 | Midjourney Prompt | StylePrompt</title>
  <meta name="description" content="赛博东方禅意 AI 艺术风格，包含 Midjourney、Gemini、Imagen 提示词。适用于游戏、海报、IP 角色设计。" />
  <meta name="keywords" content="赛博朋克,东方风格,AI提示词,Midjourney sref,游戏美术" />
  
  <!-- Open Graph -->
  <meta property="og:title" content="赛博东方禅意 AI 风格" />
  <meta property="og:description" content="..." />
  <meta property="og:image" content="https://..." />
  <meta property="og:type" content="article" />
  
  <!-- Twitter Card -->
  <meta name="twitter:card" content="summary_large_image" />
  <meta name="twitter:title" content="..." />
  <meta name="twitter:description" content="..." />
  <meta name="twitter:image" content="..." />
  
  <!-- Structured Data -->
  <script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "CreativeWork",
    "name": "赛博东方禅意",
    "description": "...",
    "image": "...",
    "keywords": "...",
    "author": {
      "@type": "Organization",
      "name": "StylePrompt"
    }
  }
  </script>
</head>
```

### 9.2 URL 结构

```
https://styleprompt.ai/
https://styleprompt.ai/styles
https://styleprompt.ai/styles/cyber-oriental-zen
https://styleprompt.ai/styles/category/cyberpunk
https://styleprompt.ai/use-cases/ecommerce
https://styleprompt.ai/blog/how-to-create-product-photos-with-ai
```

### 9.3 内容策略

**博客主题**：
- "如何用 AI 生成电商产品图"
- "Midjourney sref 代码完全指南"
- "10 个最适合游戏角色的 AI 风格"
- "从 Midjourney 到 Gemini：提示词转换技巧"

**长尾关键词**：
- "midjourney sref code for product photography"
- "ai prompt for anime character design"
- "how to create consistent character in midjourney"
- "best ai style for ecommerce"

---

## 十、性能优化

### 10.1 图片优化

**策略**：
- 使用 WebP 格式（降级到 JPEG）
- 响应式图片（srcset）
- 懒加载（Intersection Observer）
- CDN 加速
- 缩略图预加载

**实现**：
```typescript
<Image
  src={style.previewImage}
  alt={style.name}
  width={400}
  height={300}
  loading="lazy"
  placeholder="blur"
  blurDataURL={style.thumbnail}
  sizes="(max-width: 768px) 100vw, (max-width: 1200px) 50vw, 33vw"
/>
```

### 10.2 数据加载优化

**无限滚动**：
```typescript
const { data, fetchNextPage, hasNextPage } = useInfiniteQuery({
  queryKey: ['styles', filters],
  queryFn: ({ pageParam = 1 }) => fetchStyles(pageParam, filters),
  getNextPageParam: (lastPage) => lastPage.nextPage,
});

// Intersection Observer 触发加载
useEffect(() => {
  if (inView && hasNextPage) {
    fetchNextPage();
  }
}, [inView, hasNextPage]);
```

**缓存策略**：
- 风格列表：缓存 5 分钟
- 风格详情：缓存 1 小时
- 用户数据：实时
- 静态内容：缓存 1 天

### 10.3 代码分割

```typescript
// 路由级别代码分割
const Dashboard = lazy(() => import('./pages/Dashboard'));
const StyleDetail = lazy(() => import('./pages/StyleDetail'));

// 组件级别代码分割
const ImageGallery = lazy(() => import('./components/ImageGallery'));
```

---

## 十一、安全性设计

### 11.1 认证与授权

**JWT Token 策略**：
```typescript
// Access Token: 15 分钟
// Refresh Token: 7 天

const generateTokens = (userId: string) => {
  const accessToken = jwt.sign(
    { userId, type: 'access' },
    ACCESS_SECRET,
    { expiresIn: '15m' }
  );
  
  const refreshToken = jwt.sign(
    { userId, type: 'refresh' },
    REFRESH_SECRET,
    { expiresIn: '7d' }
  );
  
  return { accessToken, refreshToken };
};
```

### 11.2 API 安全

**速率限制**：
```typescript
// 免费用户：100 请求/小时
// Pro 用户：1000 请求/小时
// Studio 用户：5000 请求/小时

const rateLimiter = rateLimit({
  windowMs: 60 * 60 * 1000, // 1 小时
  max: (req) => {
    const tier = req.user?.tier || 'free';
    return RATE_LIMITS[tier];
  }
});
```

**输入验证**：
```typescript
// 使用 Zod 验证
const createMoodboardSchema = z.object({
  name: z.string().min(1).max(100),
  description: z.string().max(500).optional(),
  styleIds: z.array(z.string()).max(50)
});
```

### 11.3 数据安全

- 密码使用 bcrypt 加密（10 轮）
- 敏感数据加密存储
- HTTPS 强制
- CORS 配置
- XSS 防护
- CSRF Token

---

## 十二、监控与分析

### 12.1 用户行为分析

**关键指标**：
- 页面浏览量（PV）
- 独立访客（UV）
- 跳出率
- 平均停留时间
- 转化漏斗

**事件追踪**：
```typescript
// 风格卡点击
trackEvent('style_card_click', {
  styleId: style.id,
  styleName: style.name,
  source: 'homepage'
});

// 提示词复制
trackEvent('prompt_copy', {
  styleId: style.id,
  model: 'midjourney',
  userTier: user.tier
});

// 升级按钮点击
trackEvent('upgrade_click', {
  source: 'feature_gate',
  targetTier: 'pro'
});
```

### 12.2 性能监控

**Core Web Vitals**：
- LCP (Largest Contentful Paint) < 2.5s
- FID (First Input Delay) < 100ms
- CLS (Cumulative Layout Shift) < 0.1

**工具**：
- Vercel Analytics
- Google Analytics 4
- Sentry (错误追踪)
- LogRocket (会话回放)

---

## 十三、移动端设计

### 13.1 响应式断点

```css
/* Tailwind 断点 */
sm: 640px   /* 手机横屏 */
md: 768px   /* 平板 */
lg: 1024px  /* 小笔记本 */
xl: 1280px  /* 桌面 */
2xl: 1536px /* 大屏 */
```

### 13.2 移动端优化

**导航**：
- 汉堡菜单
- 底部导航栏（主要功能）
- 手势支持（滑动返回）

**风格卡**：
- 单列布局
- 更大的点击区域
- 简化信息展示

**提示词展示**：
- 折叠/展开
- 快速复制按钮
- 分享功能

---

## 十四、国际化 (i18n)

### 14.1 支持语言

**第一阶段**：
- 简体中文（zh-CN）
- 英文（en-US）

**第二阶段**：
- 繁体中文（zh-TW）
- 日文（ja-JP）
- 韩文（ko-KR）

### 14.2 实现方案

```typescript
// next-intl 配置
import { useTranslations } from 'next-intl';

const t = useTranslations('StyleCard');

<h3>{t('title')}</h3>
<p>{t('description')}</p>
```

**翻译文件结构**：
```
locales/
├── en/
│   ├── common.json
│   ├── style.json
│   └── dashboard.json
└── zh/
    ├── common.json
    ├── style.json
    └── dashboard.json
```

---

## 十五、开发路线图

### 15.1 Phase 1: MVP (2 个月)

**Week 1-2: 基础架构**
- [ ] 项目初始化（Next.js + TypeScript）
- [ ] 数据库设计与搭建
- [ ] 认证系统（注册/登录）
- [ ] 基础 UI 组件库

**Week 3-4: 风格库核心**
- [ ] 风格卡组件
- [ ] 风格列表页
- [ ] 风格详情页
- [ ] 搜索与筛选

**Week 5-6: 用户功能**
- [ ] 收藏功能
- [ ] 用户仪表盘
- [ ] 提示词复制
- [ ] 基础权限控制

**Week 7-8: 内容与优化**
- [ ] 导入 300+ 风格数据
- [ ] SEO 优化
- [ ] 性能优化
- [ ] 测试与修复

### 15.2 Phase 2: 付费功能 (2-3 个月)

- [ ] Stripe 支付集成
- [ ] 订阅管理系统
- [ ] 提示词转换器
- [ ] 情绪板功能
- [ ] 多模型提示词
- [ ] 场景变体
- [ ] 营销页面

### 15.3 Phase 3: 高级功能 (3-6 个月)

- [ ] AI 模型集成（生成功能）
- [ ] 项目管理
- [ ] 角色库
- [ ] 资产库
- [ ] 团队协作
- [ ] 批量生成
- [ ] API 开放

---

## 十六、技术栈总结

### 16.1 前端技术栈
```json
{
  "framework": "Next.js 14",
  "language": "TypeScript",
  "styling": "Tailwind CSS",
  "ui": "shadcn/ui",
  "state": "Zustand",
  "data-fetching": "React Query",
  "forms": "React Hook Form + Zod",
  "animation": "Framer Motion",
  "i18n": "next-intl"
}
```

### 16.2 后端技术栈
```json
{
  "runtime": "Node.js",
  "framework": "Next.js API Routes",
  "database": {
    "sql": "PostgreSQL + Prisma",
    "nosql": "MongoDB"
  },
  "cache": "Redis",
  "storage": "Cloudflare R2",
  "auth": "JWT + bcrypt",
  "payment": "Stripe",
  "email": "Resend"
}
```

### 16.3 DevOps
```json
{
  "hosting": "Vercel",
  "cdn": "Cloudflare",
  "monitoring": "Sentry + Vercel Analytics",
  "ci-cd": "GitHub Actions",
  "version-control": "Git + GitHub"
}
```

---

## 十七、预算估算

### 17.1 开发成本

| 项目 | 时间 | 成本 |
|------|------|------|
| 全栈开发（2人） | 3个月 | $30,000 |
| UI/UX 设计 | 1个月 | $5,000 |
| 内容制作（风格卡） | 持续 | $8,000 |
| **总计** | | **$43,000** |

### 17.2 运营成本（月度）

| 项目 | 成本 |
|------|------|
| Vercel Pro | $20 |
| Database (Supabase/Railway) | $25 |
| Redis (Upstash) | $10 |
| Storage (Cloudflare R2) | $15 |
| CDN | $20 |
| Monitoring | $30 |
| Email (Resend) | $20 |
| AI API Credits | $200 |
| **总计** | **$340/月** |

---

## 十八、成功指标

### 18.1 MVP 阶段（前 3 个月）

- [ ] 月访问量：10,000+
- [ ] 注册用户：1,000+
- [ ] 风格卡点击率：>15%
- [ ] 提示词复制率：>20%
- [ ] 收藏率：>8%

### 18.2 增长阶段（3-6 个月）

- [ ] 月访问量：50,000+
- [ ] 付费用户：100+
- [ ] 转化率：3-5%
- [ ] MRR：$1,200+
- [ ] 月留存率：>30%

### 18.3 规模化阶段（6-12 个月）

- [ ] 月访问量：200,000+
- [ ] 付费用户：1,000+
- [ ] MRR：$12,000+
- [ ] 月留存率：>40%
- [ ] NPS 分数：>50

---

## 结语

这份网站框架设计文档涵盖了从信息架构、页面设计、组件库、数据库、API、用户流程到技术实现的完整方案。

**核心设计原则**：
1. **用户体验优先**：快速、直观、愉悦
2. **SEO 友好**：每个风格独立页面，结构化数据
3. **性能优化**：图片懒加载、代码分割、CDN
4. **可扩展性**：模块化设计，易于添加新功能
5. **商业化导向**：清晰的付费转化路径

**下一步行动**：
1. 确认技术栈选型
2. 搭建开发环境
3. 设计数据库 Schema
4. 开发核心组件
5. 导入初始风格数据
6. 内测与迭代

祝项目成功！

---

**文档版本**：v1.0  
**创建日期**：2026-05-22  
**维护者**：开发团队

