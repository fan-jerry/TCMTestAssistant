# 中医学习平台 / Traditional Chinese Medicine Learning Platform

<div align="center">

![TCM Learning Platform](https://img.shields.io/badge/TCM-Learning%20Platform-green)
![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Platform](https://img.shields.io/badge/platform-CentOS%207.9-red)

**专业的中医药在线学习平台**

[演示地址](https://your-demo.com) · [部署文档](docs/deployment.md) · [API文档](docs/api.md) · [问题反馈](issues)

</div>

## 📋 项目简介

中医学习平台是一个集中医药知识学习、在线测试、资源管理于一体的综合性学习平台。平台提供丰富的中医药内容，支持多语言（中文/英文），具备完善的用户管理和会员系统。

### 🌟 核心功能

- **🌿 中药材数据库** - 详细的中药材信息查询和学习
- **📚 方剂大全** - 经典方剂的组成、功效、应用
- **🎯 穴位定位** - 精确的穴位位置和针灸方法
- **📖 经典阅读** - 中医古籍在线阅读，支持竖排显示
- **✅ 在线测试** - 智能组卷、实时答题、成绩分析
- **📹 学习资源** - 视频、音频、PDF等多媒体资源
- **👥 用户系统** - 注册登录、会员管理、学习进度跟踪
- **🛠️ 后台管理** - CMS内容管理、用户管理、数据统计

### 🔧 技术架构

```
前端技术栈:
├── React 18 + TypeScript
├── TailwindCSS + 响应式设计
├── Vite + 热重载开发
├── React Router + 状态管理
└── PWA支持

后端技术栈:
├── Python Flask + RESTful API
├── JWT认证 + 权限控制
├── MySQL 8.0 + Redis缓存
├── PM2进程管理
└── Docker容器化支持

部署环境:
├── CentOS 7.9 服务器
├── 宝塔面板管理
├── Nginx反向代理
├── SSL证书支持
└── 自动化部署脚本
```

## 🚀 快速开始

### 环境要求

- **服务器**: CentOS 7.9 或更高版本
- **内存**: 至少 2GB RAM
- **硬盘**: 至少 20GB 可用空间
- **面板**: 宝塔Linux面板 7.x+
- **域名**: 已备案域名（可选）

### 一键部署

```bash
# 1. 克隆项目
git clone https://github.com/yourusername/tcm-learning-platform.git
cd tcm-learning-platform

# 2. 安装环境依赖
chmod +x deployment/scripts/*.sh
./deployment/scripts/install_requirements.sh

# 3. 自动部署
./deployment/scripts/deploy.sh

# 4. 启动服务
./deployment/scripts/start.sh
```

### 手动部署

详细的手动部署步骤请参考：[部署文档](docs/deployment.md)

## 📖 文档导航

| 文档 | 描述 |
|------|------|
| [快速开始](docs/quick-start.md) | 快速部署和使用指南 |
| [部署文档](docs/deployment.md) | 详细的部署操作文档 |
| [API文档](docs/api.md) | 后端API接口说明 |
| [开发指南](docs/development.md) | 本地开发环境搭建 |
| [用户手册](docs/user-guide.md) | 平台使用说明 |
| [故障排除](docs/troubleshooting.md) | 常见问题解决方案 |

## 🎯 功能特性

### 用户端功能

- ✅ **多语言支持** - 中文/英文自动切换
- ✅ **响应式设计** - 适配PC、平板、手机
- ✅ **PWA支持** - 可添加到桌面，离线访问
- ✅ **智能搜索** - 全文搜索，智能推荐
- ✅ **学习进度** - 自动记录，云端同步
- ✅ **收藏功能** - 收藏夹管理，个性化推荐
- ✅ **在线笔记** - 学习笔记，批注分享
- ✅ **社交互动** - 评论点赞，经验分享

### 管理端功能

- ✅ **内容管理** - 富文本编辑，批量操作
- ✅ **用户管理** - 用户权限，会员管理
- ✅ **数据统计** - 访问统计，学习分析
- ✅ **系统配置** - 灵活配置，主题设置
- ✅ **备份恢复** - 自动备份，一键恢复
- ✅ **安全监控** - 访问日志，异常告警

## 📊 项目结构

```
tcm-learning-platform/
├── frontend/                 # 前端React应用
│   ├── src/
│   │   ├── components/       # React组件
│   │   ├── pages/           # 页面组件
│   │   ├── hooks/           # 自定义Hooks
│   │   ├── utils/           # 工具函数
│   │   ├── types/           # TypeScript类型
│   │   ├── i18n/            # 多语言文件
│   │   └── styles/          # 样式文件
│   ├── public/              # 静态资源
│   └── package.json         # 前端依赖
├── backend/                  # 后端Flask API
│   ├── app.py              # 主应用文件
│   ├── config.py           # 配置文件
│   ├── models/             # 数据模型
│   ├── routes/             # API路由
│   ├── utils/              # 工具函数
│   └── requirements.txt    # Python依赖
├── database/                # 数据库相关
│   ├── schema.sql          # 数据库结构
│   ├── init_data.sql       # 初始数据
│   └── migrations/         # 数据库迁移
├── deployment/              # 部署相关
│   ├── scripts/            # 部署脚本
│   ├── nginx/              # Nginx配置
│   ├── docker/             # Docker配置
│   └── systemd/            # 系统服务
├── docs/                    # 项目文档
└── .github/                 # GitHub配置
    └── workflows/           # CI/CD工作流
```

## 🔧 本地开发

### 前端开发

```bash
cd frontend
npm install
npm run dev
```

### 后端开发

```bash
cd backend
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python app.py
```

### 数据库设置

```bash
mysql -u root -p < database/schema.sql
mysql -u root -p < database/init_data.sql
```

## 🤝 贡献指南

我们欢迎所有形式的贡献！请阅读 [贡献指南](CONTRIBUTING.md) 了解详情。

### 贡献方式

- 🐛 报告Bug
- 💡 提出新功能建议
- 📖 改进文档
- 🔧 提交代码修复
- 🌐 翻译文档

## 📄 开源协议

本项目采用 [MIT协议](LICENSE) 开源。

## 🙏 致谢

感谢所有为本项目做出贡献的开发者和中医药专家！

- 中医药数据来源：中国药典、本草纲目等权威资料
- 技术支持：开源社区的优秀项目和工具
- 设计灵感：现代化Web应用最佳实践

## 📞 联系我们

- **项目官网**: https://your-website.com
- **技术支持**: support@your-website.com
- **QQ交流群**: 123456789
- **微信群**: 扫码加入

## 🔖 版本历史

- **v1.0.0** - 初始版本发布
  - ✅ 基础功能完成
  - ✅ 用户系统搭建
  - ✅ 中医药数据库
  - ✅ 部署文档完善

---

<div align="center">

**⭐ 如果这个项目对您有帮助，请不要忘记给个Star ⭐**

Made with ❤️ by TCM Learning Team

</div>

