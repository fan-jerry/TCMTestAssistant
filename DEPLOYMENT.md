# 🚀 GitHub部署指南

本文档详细说明如何从GitHub仓库部署中医学习平台到您的服务器。

## 📋 部署方式

我们提供多种部署方式供您选择：

### 方式一：直接从GitHub部署（推荐）

适合有GitHub账户，希望跟踪项目更新的用户。

### 方式二：下载ZIP包部署

适合不使用Git的用户或离线部署环境。

### 方式三：Docker容器化部署

适合熟悉Docker的用户，提供最佳的环境隔离。

## 🛠️ 方式一：GitHub直接部署

### 步骤1：克隆仓库

```bash
# 克隆项目到服务器
git clone https://github.com/yourusername/tcm-learning-platform.git

# 进入项目目录
cd tcm-learning-platform
```

### 步骤2：环境配置

```bash
# 复制环境配置文件
cp .env.example .env

# 编辑配置文件（修改数据库密码、域名等）
vim .env
```

### 步骤3：一键部署

```bash
# 安装环境依赖
npm run deploy:install

# 自动部署
npm run deploy:setup

# 启动服务
npm run deploy:start
```

### 步骤4：配置宝塔面板

1. **添加站点**
   - 宝塔面板 → 网站 → 添加站点
   - 域名：your-domain.com
   - 根目录：`/www/wwwroot/tcm-learning-platform/frontend`

2. **配置SSL证书**
   - 网站设置 → SSL → Let's Encrypt
   - 申请免费SSL证书

3. **导入Nginx配置**
   ```bash
   # 复制配置文件到宝塔
   cp deployment/nginx/tcm-learning.conf /www/server/panel/vhost/nginx/your-domain.com.conf
   
   # 重启Nginx
   systemctl reload nginx
   ```

### 步骤5：验证部署

```bash
# 检查服务状态
npm run deploy:status

# 访问健康检查
curl https://your-domain.com/api/health
```

## 📦 方式二：ZIP包部署

### 下载项目包

```bash
# 下载最新版本
wget https://github.com/yourusername/tcm-learning-platform/archive/main.zip

# 解压
unzip main.zip
mv tcm-learning-platform-main tcm-learning-platform
cd tcm-learning-platform
```

后续步骤与方式一相同。

## 🐳 方式三：Docker部署

### 前置要求

```bash
# 安装Docker和Docker Compose
curl -fsSL https://get.docker.com | sh
sudo systemctl start docker
sudo systemctl enable docker

# 安装Docker Compose
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

### Docker部署步骤

```bash
# 克隆项目
git clone https://github.com/yourusername/tcm-learning-platform.git
cd tcm-learning-platform

# 配置环境变量
cp .env.example .env
vim .env

# Docker部署
npm run docker:build
npm run docker:up

# 查看服务状态
npm run docker:logs
```

### Docker服务管理

```bash
# 启动服务
docker-compose -f deployment/docker/docker-compose.yml up -d

# 停止服务
docker-compose -f deployment/docker/docker-compose.yml down

# 查看日志
docker-compose -f deployment/docker/docker-compose.yml logs -f

# 重启服务
docker-compose -f deployment/docker/docker-compose.yml restart
```

## ⚙️ 高级配置

### 自定义配置

编辑后端配置文件：
```bash
cp backend/config.example.py backend/config.py
vim backend/config.py
```

### 数据库配置

```bash
# 创建数据库
mysql -u root -p << EOF
CREATE DATABASE tcm_learning CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
CREATE USER 'tcm_user'@'localhost' IDENTIFIED BY 'your_password';
GRANT ALL PRIVILEGES ON tcm_learning.* TO 'tcm_user'@'localhost';
FLUSH PRIVILEGES;
EOF

# 导入数据
mysql -u tcm_user -p tcm_learning < database/schema.sql
mysql -u tcm_user -p tcm_learning < database/init_data.sql
```

### 前端构建

```bash
cd frontend
npm install
npm run build
```

### 反向代理配置

如果不使用宝塔面板，可以手动配置Nginx：

```bash
# 复制配置文件
sudo cp deployment/nginx/tcm-learning.conf /etc/nginx/sites-available/
sudo ln -s /etc/nginx/sites-available/tcm-learning.conf /etc/nginx/sites-enabled/

# 测试配置
sudo nginx -t

# 重启Nginx
sudo systemctl restart nginx
```

## 🔄 更新部署

### 从GitHub更新

```bash
# 拉取最新代码
git pull origin main

# 更新依赖
npm run setup

# 重新构建前端
npm run build

# 重启服务
npm run deploy:restart
```

### 数据库迁移

```bash
# 备份数据库
mysqldump -u tcm_user -p tcm_learning > backup_$(date +%Y%m%d).sql

# 执行迁移
mysql -u tcm_user -p tcm_learning < database/migrations/xxx.sql
```

## 📊 监控和维护

### 服务监控

```bash
# 实时监控
npm run deploy:status

# 查看日志
tail -f /www/wwwroot/tcm-learning-platform/logs/app.log

# PM2监控
pm2 monit
```

### 性能优化

```bash
# 数据库优化
mysql -u root -p << EOF
SET GLOBAL innodb_buffer_pool_size = 1073741824;
SET GLOBAL max_connections = 200;
EOF

# 清理日志
find /www/wwwroot/tcm-learning-platform/logs -name "*.log" -mtime +7 -delete
```

### 自动备份

添加定时备份任务：
```bash
# 编辑crontab
crontab -e

# 添加以下行（每天凌晨2点备份）
0 2 * * * /www/wwwroot/tcm-learning-platform/deployment/scripts/backup.sh
```

## 🐛 故障排除

### 常见问题

**1. 端口冲突**
```bash
# 查看端口占用
netstat -tulnp | grep :5000

# 修改端口配置
vim .env  # 修改PORT=5001
```

**2. 权限问题**
```bash
# 设置正确权限
sudo chown -R www:www /www/wwwroot/tcm-learning-platform
sudo chmod -R 755 /www/wwwroot/tcm-learning-platform
```

**3. 数据库连接失败**
```bash
# 检查数据库状态
systemctl status mysqld

# 测试连接
mysql -u tcm_user -p -h localhost tcm_learning
```

### 日志分析

```bash
# API错误日志
tail -f logs/error.log

# 访问日志
tail -f logs/access.log

# 系统日志
journalctl -u nginx -f
```

## 📞 获取帮助

### 技术支持

- **文档**: [在线文档](https://docs.tcm-learning.com)
- **Issues**: [GitHub Issues](https://github.com/yourusername/tcm-learning-platform/issues)
- **讨论**: [GitHub Discussions](https://github.com/yourusername/tcm-learning-platform/discussions)

### 社区

- **QQ群**: 123456789
- **微信群**: 扫码加入
- **邮箱**: support@tcm-learning.com

---

🎉 **部署完成后，您的中医学习平台就可以正常使用了！**

记得及时更新系统和依赖包，保持平台的安全性和稳定性。
