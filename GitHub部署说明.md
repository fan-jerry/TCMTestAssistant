# 📦 中医学习平台 GitHub 部署包使用说明

## 🎯 部署包概述

您现在获得的是一个完整的GitHub项目包，包含了部署中医学习平台所需的全部文件和配置。

### 📁 包含内容

- ✅ **完整的源代码** - 前端React应用 + 后端Flask API
- ✅ **数据库设计** - MySQL表结构和初始数据
- ✅ **自动化脚本** - 一键部署和服务管理脚本
- ✅ **Docker配置** - 容器化部署支持
- ✅ **CI/CD配置** - GitHub Actions自动化部署
- ✅ **完整文档** - 部署指南、API文档、使用手册
- ✅ **开源配置** - MIT协议、贡献指南等

## 🚀 三种部署方式

### 方式一：上传到您的GitHub仓库（推荐）

**优势：** 
- 版本控制管理
- 自动化CI/CD
- 团队协作开发
- 持续更新维护

**步骤：**

1. **创建GitHub仓库**
   ```bash
   # 在GitHub上创建新仓库：tcm-learning-platform
   ```

2. **上传项目文件**
   ```bash
   # 解压项目包
   unzip tcm-learning-platform-github.zip
   cd tcm-learning-platform
   
   # 初始化Git仓库
   git init
   git add .
   git commit -m "Initial commit: TCM Learning Platform"
   
   # 添加远程仓库
   git remote add origin https://github.com/yourusername/tcm-learning-platform.git
   git branch -M main
   git push -u origin main
   ```

3. **配置部署密钥**
   
   在GitHub仓库设置中添加以下Secrets：
   - `HOST`: 服务器IP地址
   - `USERNAME`: 服务器用户名
   - `PRIVATE_KEY`: SSH私钥
   - `PORT`: SSH端口（默认22）

4. **服务器部署**
   ```bash
   # 在服务器上克隆项目
   git clone https://github.com/yourusername/tcm-learning-platform.git
   cd tcm-learning-platform
   
   # 一键部署
   chmod +x deployment/scripts/*.sh
   sudo ./deployment/scripts/install_requirements.sh
   sudo ./deployment/scripts/deploy.sh
   sudo ./deployment/scripts/start.sh
   ```

### 方式二：直接服务器部署

**优势：**
- 快速部署
- 无需GitHub账户
- 适合私有项目

**步骤：**

1. **上传项目包到服务器**
   ```bash
   # 使用SCP上传
   scp tcm-learning-platform-github.zip root@your-server:/root/
   
   # 登录服务器并解压
   ssh root@your-server
   cd /root
   unzip tcm-learning-platform-github.zip
   mv tcm-learning-platform /www/wwwroot/
   ```

2. **执行部署**
   ```bash
   cd /www/wwwroot/tcm-learning-platform
   chmod +x deployment/scripts/*.sh
   ./deployment/scripts/install_requirements.sh
   ./deployment/scripts/deploy.sh
   ./deployment/scripts/start.sh
   ```

### 方式三：Docker容器化部署

**优势：**
- 环境隔离
- 一致性部署
- 易于扩展

**步骤：**

1. **安装Docker环境**
   ```bash
   curl -fsSL https://get.docker.com | sh
   sudo systemctl start docker
   sudo systemctl enable docker
   ```

2. **Docker部署**
   ```bash
   cd tcm-learning-platform
   cp .env.example .env
   vim .env  # 编辑配置
   
   # 启动所有服务
   docker-compose -f deployment/docker/docker-compose.yml up -d
   ```

## ⚙️ 配置说明

### 环境配置

1. **复制配置文件**
   ```bash
   cp .env.example .env
   ```

2. **修改关键配置**
   ```bash
   # 数据库配置
   MYSQL_PASSWORD=your_strong_password
   
   # 域名配置
   APP_URL=https://your-domain.com
   
   # JWT密钥
   JWT_SECRET_KEY=your_jwt_secret
   ```

### 宝塔面板配置

1. **添加站点**
   - 域名：your-domain.com
   - 根目录：`/www/wwwroot/tcm-learning-platform/frontend`

2. **SSL证书**
   - 申请Let's Encrypt免费证书
   - 强制HTTPS

3. **Nginx配置**
   ```bash
   # 导入配置文件
   cp deployment/nginx/tcm-learning.conf /www/server/panel/vhost/nginx/
   ```

## 🔧 服务管理

### 服务控制命令

```bash
# 查看状态
npm run deploy:status

# 启动服务
npm run deploy:start

# 停止服务
npm run deploy:stop

# 重启服务
npm run deploy:restart
```

### 日志查看

```bash
# 查看API日志
pm2 logs tcm-learning-api

# 查看访问日志
tail -f logs/access.log

# 查看错误日志
tail -f logs/error.log
```

## 📱 访问系统

部署完成后，您可以访问：

- **🌐 前端网站**: https://your-domain.com
- **🔌 API接口**: https://your-domain.com/api
- **❤️ 健康检查**: https://your-domain.com/api/health
- **👤 管理后台**: https://your-domain.com/admin

### 默认账户

- **管理员**: admin / admin123
- **编辑员**: editor / admin123

> ⚠️ **首次登录后请立即修改默认密码！**

## 🔍 故障排除

### 常见问题

1. **API服务无法启动**
   ```bash
   # 检查Python环境
   which python3
   pip3 list
   
   # 手动启动测试
   cd backend && python app.py
   ```

2. **数据库连接失败**
   ```bash
   # 测试数据库连接
   mysql -u tcm_user -p tcm_learning
   
   # 检查配置文件
   cat backend/config.py
   ```

3. **前端页面404**
   ```bash
   # 检查文件权限
   ls -la frontend/
   
   # 检查Nginx配置
   nginx -t
   ```

### 获取帮助

- 📖 **详细文档**: [DEPLOYMENT.md](DEPLOYMENT.md)
- 🐛 **问题反馈**: GitHub Issues
- 💬 **技术讨论**: GitHub Discussions

## 📞 技术支持

- **邮箱**: support@tcm-learning.com
- **QQ群**: 123456789
- **微信群**: 扫码加入

## 🎉 部署成功

恭喜！您已经成功获得了完整的中医学习平台部署包。

### 下一步

1. **选择合适的部署方式**
2. **配置服务器环境**
3. **执行部署脚本**
4. **访问系统验证**
5. **修改默认密码**

### 重要提醒

- 🔐 **安全第一**: 及时修改默认密码和密钥
- 🔄 **定期更新**: 保持系统和依赖包最新
- 💾 **备份数据**: 设置自动备份策略
- 📊 **监控系统**: 关注系统运行状态

---

**🚀 开始您的中医学习平台之旅吧！**

如有任何问题，随时联系我们获取技术支持。
