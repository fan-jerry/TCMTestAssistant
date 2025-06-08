# 贡献指南 / Contributing Guide

感谢您对中医学习平台项目的关注！我们欢迎各种形式的贡献。

## 🤝 如何贡献

### 报告Bug

如果您发现了Bug，请：

1. 查看 [Issues](https://github.com/yourusername/tcm-learning-platform/issues) 确认问题未被报告
2. 创建新Issue，包含：
   - 详细的问题描述
   - 重现步骤
   - 期望行为
   - 实际行为
   - 环境信息（浏览器、操作系统等）
   - 截图（如果有帮助）

### 功能请求

提出新功能建议：

1. 检查现有Issues避免重复
2. 创建Feature Request，包含：
   - 功能描述
   - 使用场景
   - 期望的用户体验
   - 可能的实现方案

### 提交代码

#### 开发环境设置

```bash
# 1. Fork并克隆仓库
git clone https://github.com/yourusername/tcm-learning-platform.git
cd tcm-learning-platform

# 2. 安装依赖
cd frontend && npm install
cd ../backend && pip install -r requirements.txt

# 3. 配置数据库
mysql -u root -p < database/schema.sql

# 4. 启动开发服务器
cd frontend && npm run dev  # 前端
cd backend && python app.py  # 后端
```

#### 代码规范

**前端代码规范：**
- 使用TypeScript
- 遵循ESLint配置
- 组件使用PascalCase命名
- Hook使用use开头
- 样式使用TailwindCSS

**后端代码规范：**
- 遵循PEP 8
- 使用类型注解
- 函数和变量使用snake_case
- 类名使用PascalCase

#### 提交流程

1. **创建分支**
   ```bash
   git checkout -b feature/your-feature-name
   # 或
   git checkout -b fix/bug-description
   ```

2. **编写代码**
   - 保持提交原子性
   - 写清晰的提交信息
   - 添加必要的测试

3. **测试**
   ```bash
   # 前端测试
   cd frontend && npm run test
   
   # 后端测试
   cd backend && pytest
   ```

4. **提交**
   ```bash
   git add .
   git commit -m "feat: add new feature description"
   ```

5. **推送并创建PR**
   ```bash
   git push origin feature/your-feature-name
   ```

#### Pull Request要求

- PR标题简洁明确
- 详细描述变更内容
- 关联相关Issue
- 确保所有测试通过
- 添加截图（UI变更）
- 更新相关文档

## 📝 提交信息规范

使用 [Conventional Commits](https://conventionalcommits.org/) 规范：

```
<类型>[可选作用域]: <描述>

[可选正文]

[可选脚注]
```

**类型说明：**
- `feat`: 新功能
- `fix`: Bug修复
- `docs`: 文档更新
- `style`: 代码格式（不影响功能）
- `refactor`: 重构
- `test`: 测试相关
- `chore`: 构建过程或辅助工具变动

**示例：**
```
feat(auth): add user registration validation

- Add email format validation
- Add password strength check
- Add username uniqueness check

Closes #123
```

## 🔍 代码审查

### 审查标准

- **功能性**: 代码实现是否正确
- **可读性**: 代码是否易于理解
- **性能**: 是否有性能问题
- **安全性**: 是否存在安全隐患
- **测试**: 是否有足够的测试覆盖

### 审查流程

1. 自动化检查（CI/CD）
2. 同行代码审查
3. 维护者最终审查
4. 合并到主分支

## 🎨 设计贡献

### UI/UX设计

- 遵循中医文化元素
- 保持简洁现代的设计
- 确保响应式设计
- 注意可访问性

### 设计文件

- 使用Figma或Sketch
- 提供多种屏幕尺寸设计
- 包含交互说明
- 导出必要的图标和素材

## 📖 文档贡献

### 文档类型

- API文档
- 用户手册
- 开发指南
- 部署文档

### 文档规范

- 使用Markdown格式
- 包含代码示例
- 提供截图说明
- 支持多语言

## 🌐 翻译贡献

### 支持语言

- 中文（简体）
- 英文
- 其他语言欢迎贡献

### 翻译指南

1. 翻译文件位于 `frontend/src/i18n/`
2. 保持键名一致
3. 注意中医术语的准确性
4. 考虑文化差异

## 👥 社区参与

### 交流方式

- GitHub Discussions
- QQ群：123456789
- 微信群：扫码加入
- 邮件：community@tcm-learning.com

### 行为准则

- 尊重他人意见
- 建设性的讨论
- 包容多样性
- 专业友善的交流

## 🏆 贡献者认可

### 贡献者名单

所有贡献者都会在README.md中得到认可。

### 贡献统计

- 代码贡献
- 文档贡献
- Bug报告
- 功能建议
- 社区帮助

## 📞 联系方式

如有任何问题，欢迎联系：

- **项目维护者**: maintainer@tcm-learning.com
- **技术问题**: tech@tcm-learning.com
- **其他问题**: hello@tcm-learning.com

---

再次感谢您的贡献！🙏
