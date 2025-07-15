# FDX实验室管理系统

一个基于Next.js和Supabase构建的现代化实验室管理系统，集成腾讯云COS文件存储。

## 🌟 主要功能

### 🖼️ 头像管理系统
- **预设头像**: 使用DiceBear API生成的多样化头像
- **自定义头像**: 集成腾讯云COS的文件上传和存储
- **智能缓存**: 多层缓存机制，优先从数据库获取最新数据
- **拖拽上传**: 支持点击选择和拖拽上传两种方式

### 📊 数据可视化
- **生产数据图表**: 使用Recharts展示生产趋势和分析
- **实时数据**: 连接Supabase实时数据更新
- **多维度分析**: 支持时间范围筛选和数据对比

### 👥 用户认证与管理
- **安全登录**: 基于Supabase Auth的用户认证
- **权限控制**: 行级安全(RLS)策略保护数据
- **用户资料**: 完整的用户信息管理

### 🧪 实验室功能
- **化验数据管理**: 样品检测数据录入和查询
- **设备监控**: 实验室设备运行状态监控
- **数据汇总**: 自动化的数据统计和报告

## 🛠️ 技术栈

- **前端框架**: Next.js 15 + TypeScript
- **UI组件**: Tailwind CSS + shadcn/ui
- **数据库**: Supabase (PostgreSQL)
- **文件存储**: 腾讯云COS
- **状态管理**: Zustand
- **表单处理**: React Hook Form + Zod
- **图表库**: Recharts
- **3D渲染**: Three.js + React Three Fiber

## 🚀 快速开始

### 环境要求
- Node.js 18+
- npm 或 yarn

### 安装依赖
```bash
npm install
# 或
yarn install
```

### 环境配置
创建 `.env.local` 文件并配置以下环境变量：

```env
# Supabase配置
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
SUPABASE_SERVICE_ROLE_KEY=your_service_role_key

# 腾讯云COS配置
NEXT_PUBLIC_COS_SECRET_ID=your_cos_secret_id
NEXT_PUBLIC_COS_SECRET_KEY=your_cos_secret_key
NEXT_PUBLIC_COS_BUCKET=your_cos_bucket
NEXT_PUBLIC_COS_REGION=your_cos_region
```

### 启动开发服务器
```bash
npm run dev
# 或
yarn dev
```

访问 [http://localhost:3000](http://localhost:3000) 查看应用。

## 📁 项目结构

```
src/
├── app/                    # Next.js App Router页面
│   ├── api/               # API路由
│   ├── avatar-selector/   # 头像选择页面
│   ├── profile/           # 用户资料页面
│   └── ...
├── components/            # 可复用组件
│   ├── ui/               # shadcn/ui组件
│   └── ...
├── contexts/             # React上下文
├── hooks/                # 自定义Hooks
├── lib/                  # 工具库
└── types/                # TypeScript类型定义
```

## 🔧 核心功能说明

### 头像管理系统

系统支持三种头像类型：
1. **预设头像**: 基于DiceBear API的生成头像
2. **字母头像**: 基于用户姓名首字母的头像
3. **自定义头像**: 用户上传的图片，存储在腾讯云COS

头像读取优先级：
```
数据库API查询 → 有效缓存降级 → 过期缓存降级 → 默认头像
```

### 数据库设计

主要数据表：
- `用户资料`: 用户基本信息和头像URL
- `生产班报`: 生产数据记录
- `化验数据`: 实验室检测结果
- `设备运行`: 设备状态监控

### API接口

- `/api/users` - 用户信息管理
- `/api/cos/upload-simple` - COS文件上传
- `/api/current-user` - 当前用户信息
- `/api/test-avatar-update` - 头像更新测试

## 🧪 测试工具

系统包含多个测试和调试页面：

- `/avatar-database-check` - 数据库状态检查
- `/avatar-debug` - 数据一致性调试
- `/avatar-timing-test` - 时序问题测试
- `/clear-cache-test` - 缓存清理测试

## 📝 开发说明

### 代码规范
- 使用TypeScript进行类型安全
- 遵循ESLint配置的代码规范
- 组件使用函数式组件和Hooks
- 样式使用Tailwind CSS类名

### 提交规范
使用语义化提交信息：
- `feat:` 新功能
- `fix:` 修复问题
- `docs:` 文档更新
- `style:` 代码格式调整
- `refactor:` 代码重构
- `test:` 测试相关

## 🤝 贡献指南

1. Fork本仓库
2. 创建功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 创建Pull Request

## 📄 许可证

本项目采用MIT许可证 - 查看 [LICENSE](LICENSE) 文件了解详情。

## 🙏 致谢

- [Next.js](https://nextjs.org/) - React框架
- [Supabase](https://supabase.com/) - 后端即服务
- [Tailwind CSS](https://tailwindcss.com/) - CSS框架
- [shadcn/ui](https://ui.shadcn.com/) - UI组件库
- [腾讯云COS](https://cloud.tencent.com/product/cos) - 对象存储服务

---

**FDX实验室管理系统** - 让实验室管理更智能、更高效！ 🚀