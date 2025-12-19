# Muti-userOnlineEditing 多人在线协作编辑软件

一个基于React和Node.js的多人在线协作编辑平台，支持实时文档编辑、协作、评论和任务管理。

## 功能特性

### 核心功能

1. **用户管理模块**
   - 用户注册与登录（支持邮箱/手机号）
   - 密码找回与重置
   - 个人资料编辑
   - 头像上传与设置
   - 用户权限管理（管理员、编辑者、查看者）

2. **文档管理模块**
   - 富文本编辑器
   - 模板库
   - 自动保存与恢复
   - 文档分类与搜索
   - 全文搜索
   - 高级搜索（按作者、日期、关键词等）

3. **实时协作模块**
   - 多用户同时编辑
   - 实时光标位置显示
   - 评论与批注
   - 行内评论
   - 回复与@提及
   - 评论通知
   - 任务分配与跟踪
   - 任务状态跟踪
   - 截止日期设置

4. **通知与通讯模块**
   - 实时通知（编辑、评论、任务等）
   - 通知分类与过滤
   - 通知设置
   - 通知历史记录
   - 内置聊天功能

5. **系统管理模块**
   - 用户管理
   - 用户权限调整
   - 用户行为分析

## 技术栈

### 后端
- Node.js
- Express
- Socket.IO
- MongoDB (支持openGauss)
- JWT认证
- Multer文件上传

### 前端
- React
- Material-UI
- React Quill
- Socket.IO客户端
- Axios
- React Router

## 项目结构

```
多人在线编辑软件/
├── package.json                 # 项目依赖配置
├── server/                      # 后端代码
│   ├── index.js                 # 服务器入口
│   ├── .env.example             # 环境变量示例
│   ├── models/                  # 数据模型
│   │   ├── User.js              # 用户模型
│   │   ├── Document.js          # 文档模型
│   │   ├── Folder.js            # 文件夹模型
│   │   └── Notification.js      # 通知模型
│   ├── routes/                  # API路由
│   │   ├── auth.js              # 认证路由
│   │   ├── users.js             # 用户路由
│   │   ├── documents.js         # 文档路由
│   │   └── notifications.js     # 通知路由
│   ├── middleware/              # 中间件
│   │   └── auth.js              # 认证中间件
│   ├── socket/                  # Socket.IO处理
│   │   └── socketHandler.js     # Socket事件处理
│   └── uploads/                 # 上传文件目录
│       └── avatars/             # 用户头像
└── client/                      # 前端代码
    ├── package.json             # 前端依赖
    ├── public/                  # 公共资源
    │   └── index.html           # HTML模板
    └── src/                     # 源代码
        ├── index.js             # 应用入口
        ├── App.js                # 主应用组件
        ├── contexts/             # React上下文
        │   ├── AuthContext.js    # 认证上下文
        │   └── SocketContext.js  # Socket上下文
        ├── services/             # API服务
        │   ├── authService.js    # 认证服务
        │   ├── documentService.js # 文档服务
        │   ├── userService.js    # 用户服务
        │   └── notificationService.js # 通知服务
        ├── components/           # 通用组件
        │   ├── common/           # 通用组件
        │   │   └── PrivateRoute.js
        │   ├── layout/           # 布局组件
        │   │   └── Navbar.js
        │   ├── documents/        # 文档相关组件
        │   │   ├── DocumentCreateDialog.js
        │   │   └── CollaboratorDialog.js
        │   └── editor/           # 编辑器相关组件
        │       ├── CommentDialog.js
        │       └── TaskDialog.js
        └── pages/                 # 页面组件
            ├── auth/              # 认证页面
            │   ├── Login.js
            │   ├── Register.js
            │   └── ForgotPassword.js
            ├── dashboard/         # 仪表板
            │   └── Dashboard.js
            ├── documents/         # 文档管理
            │   └── Documents.js
            ├── editor/            # 文档编辑器
            │   └── DocumentEditor.js
            ├── user/              # 用户页面
            │   └── Profile.js
            └── notifications/     # 通知页面
                └── Notifications.js
```

## 安装与运行

### 环境要求
- Node.js 14.0+
- MongoDB 或 openGauss 数据库
- npm 或 yarn

### 安装步骤

1. 克隆项目
```bash
git clone <repository-url>
cd 多人在线编辑软件
```

2. 安装依赖
```bash
npm run install:all
```

或者分别安装
```bash
npm install
cd client && npm install
```

3. 配置环境变量
```bash
cd server
cp .env.example .env
# 编辑 .env 文件，配置数据库连接等信息
```

4. 启动数据库（确保MongoDB或openGauss已运行）

5. 启动应用
```bash
npm run dev
```

或者分别启动
```bash
# 启动后端
npm run server:dev

# 在另一个终端启动前端
npm run client:dev
```

6. 打开浏览器访问 http://localhost:3000

## 配置说明

### 后端环境变量 (.env)

```bash
# 服务器配置
PORT=5000
NODE_ENV=development

# 数据库配置
MONGODB_URI=mongodb://localhost:27017/collaborative_editor

# JWT 配置
JWT_SECRET=your_jwt_secret_key_here
JWT_EXPIRES_IN=7d

# 客户端 URL
CLIENT_URL=http://localhost:3000

# 文件上传配置
UPLOAD_PATH=./uploads
MAX_FILE_SIZE=5242880

# 邮件配置 (用于密码重置等)
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USER=your_email@gmail.com
EMAIL_PASS=your_email_password
```

### 前端环境变量

创建 `client/.env` 文件：

```bash
REACT_APP_API_URL=http://localhost:5000/api
REACT_APP_SERVER_URL=http://localhost:5000
```

## 开发指南

### 添加新功能

1. 在 `server/routes/` 中添加新的API路由
2. 在 `server/models/` 中添加数据模型
3. 在 `client/services/` 中添加API服务
4. 在 `client/components/` 中添加组件
5. 在 `client/pages/` 中添加页面

### 数据库模型

项目使用MongoDB作为默认数据库，但代码结构支持切换到openGauss。如需使用openGauss，需要：

1. 安装相应的Node.js驱动
2. 修改 `server/models/` 中的模型定义
3. 更新 `server/index.js` 中的数据库连接代码

### 实时协作

实时协作功能基于Socket.IO实现，主要逻辑在 `server/socket/socketHandler.js` 中。

- 文档编辑同步
- 用户光标位置显示
- 实时聊天
- 通知推送

## 部署

### 生产环境构建

1. 构建前端
```bash
cd client
npm run build
```

2. 启动后端
```bash
cd server
npm start
```

### Docker部署

（可选）创建Dockerfile和docker-compose.yml文件进行容器化部署。

## 许可证

MIT
