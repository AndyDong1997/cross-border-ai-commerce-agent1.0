# GitHub 部署完整指南

## 🚀 您的跨境AI电商代理应用已准备好部署到 GitHub！

### 项目概述
- **项目名称**: cross-border-ai-commerce-agent
- **技术栈**: React + Vite + TypeScript + Gemini AI
- **部署目标**: GitHub Pages + GitHub Actions 自动化

## 📋 部署前准备

### 1. 创建 GitHub 仓库

#### 方式一：通过 GitHub 网页界面
1. 访问 [GitHub.com](https://github.com)
2. 点击右上角的 **"+"** 按钮
3. 选择 **"New repository"**
4. 仓库设置：
   - **Repository name**: `cross-border-ai-commerce-agent`
   - **Description**: `AI-powered cross-border e-commerce assistant`
   - **Visibility**: 选择 Public 或 Private
   - **Initialize**: 
     - ✅ Add a README file
     - ✅ Add .gitignore: Node
     - ✅ Choose a license: MIT License
5. 点击 **"Create repository"**

#### 方式二：通过 GitHub CLI
```bash
# 登录 GitHub（如果未登录）
gh auth login

# 创建仓库
gh repo create cross-border-ai-commerce-agent --public --source=. --push
```

### 2. 上传代码到 GitHub

#### 使用 Git 命令行
```bash
# 在项目根目录执行
git init
git add .
git commit -m "Initial commit: AI-powered e-commerce agent"

# 添加远程仓库（替换 YOUR_USERNAME 为您的 GitHub 用户名）
git remote add origin https://github.com/YOUR_USERNAME/cross-border-ai-commerce-agent.git

# 推送到 GitHub
git branch -M main
git push -u origin main
```

#### 使用 GitHub Desktop
1. 下载并安装 [GitHub Desktop](https://desktop.github.com/)
2. 登录您的 GitHub 账户
3. 点击 **"Add an Existing Repository from your Hard Drive"**
4. 选择项目目录
5. 点击 **"Publish repository"**

### 3. 配置 GitHub Pages

#### 启用 GitHub Pages
1. 进入您的 GitHub 仓库页面
2. 点击 **"Settings"** 标签
3. 滚动到左侧 **"Pages"** 选项
4. 在 **"Source"** 部分：
   - 选择 **"GitHub Actions"**
5. 保存设置

### 4. 设置环境变量（API 密钥）

由于您的应用需要 Gemini API 密钥，您需要安全地配置它：

#### 方法一：使用 GitHub Secrets（推荐）
1. 进入仓库 **Settings** → **Secrets and variables** → **Actions**
2. 点击 **"New repository secret"**
3. 设置：
   - **Name**: `GEMINI_API_KEY`
   - **Secret**: 您的实际 Gemini API 密钥
4. 点击 **"Add secret"**

#### 方法二：修改构建配置
由于这是客户端应用，API 密钥需要暴露给前端。您可以：

1. **临时方案**：在构建时设置环境变量
2. **生产方案**：考虑使用后端代理服务

### 5. 自动化部署配置

已为您创建了 GitHub Actions 工作流文件：
- `.github/workflows/deploy.yml` - 主要部署工作流
- `.github/workflows/pages.yml` - 备用部署工作流

工作流将自动：
- ✅ 检测代码推送
- ✅ 安装依赖
- ✅ 构建项目
- ✅ 部署到 GitHub Pages
- ✅ 提供部署 URL

### 6. 首次部署

#### 触发部署
1. 推送代码到 `main` 分支：
   ```bash
   git add .
   git commit -m "Configure GitHub deployment"
   git push origin main
   ```

2. 查看部署进度：
   - 进入仓库 **Actions** 标签
   - 查看最新的工作流运行
   - 等待构建和部署完成

#### 获取部署 URL
部署成功后，您将获得类似以下的 URL：
- `https://YOUR_USERNAME.github.io/cross-border-ai-commerce-agent`

### 7. 自定义域名（可选）

如果您有自定义域名：

1. 在仓库根目录创建 `CNAME` 文件：
   ```
   your-domain.com
   ```

2. 在域名提供商处设置 DNS 记录：
   ```
   类型: CNAME
   名称: www
   值: YOUR_USERNAME.github.io
   ```

3. 在 GitHub Pages 设置中配置自定义域名

## 🔧 高级配置

### 性能优化
- ✅ Vite 代码分割
- ✅ Gzip 压缩
- ✅ 浏览器缓存
- ✅ 安全头配置

### 监控和分析
- GitHub Pages 提供基本分析
- 可以集成 Google Analytics
- 错误监控（如 Sentry）

### 持续集成
- 每次推送自动部署
- Pull Request 自动构建测试
- 分支预览部署

## 🛠️ 故障排除

### 构建失败
**检查项目：**
```bash
# 本地测试构建
npm run build
```

**常见问题：**
- 依赖安装失败 → 检查 `package.json`
- TypeScript 错误 → 检查类型定义
- API 密钥问题 → 验证 GitHub Secrets

### 部署失败
**检查工作流日志：**
1. 进入 **Actions** 标签
2. 点击失败的 workflow
3. 查看详细日志

**常见问题：**
- 权限问题 → 检查仓库设置
- 路径问题 → 验证 `publish_dir` 配置
- 缓存问题 → 清除工作流缓存

### 页面显示异常
**检查项目：**
- 浏览器控制台错误
- 网络请求失败
- 资源加载问题

**解决方案：**
- 清除浏览器缓存
- 检查 API 密钥配置
- 验证路由配置

## 📊 部署后检查清单

- [ ] 网站正常加载
- [ ] 所有 AI 功能工作
- [ ] 侧边栏导航正常
- [ ] 设置页面可访问
- [ ] 响应式设计正常
- [ ] HTTPS 证书有效
- [ ] 自定义域名配置（如果使用）

## 🔄 后续维护

### 定期更新
```bash
# 更新依赖
npm update

# 安全检查
npm audit

# 构建测试
npm run build
```

### 监控
- GitHub Actions 使用情况
- GitHub Pages 带宽使用
- API 使用量和成本

### 备份
- 代码备份（Git）
- 配置备份
- 部署文件备份

## 💡 最佳实践

1. **分支策略**：使用 `main` 分支进行部署，`develop` 分支进行开发
2. **环境管理**：区分开发、测试、生产环境
3. **安全**：定期轮换 API 密钥，监控异常访问
4. **性能**：定期优化 Bundle 大小，监控加载速度

## 🆘 获取帮助

- [GitHub Pages 文档](https://docs.github.com/en/pages)
- [GitHub Actions 文档](https://docs.github.com/en/actions)
- [Vite 部署指南](https://vitejs.dev/guide/static-deploy.html)

---

**恭喜！** 您的跨境AI电商代理应用现在具备了完整的 GitHub 部署流程。享受免费的静态网站托管和自动化部署吧！ 🎉