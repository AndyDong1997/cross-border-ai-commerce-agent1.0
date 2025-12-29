# Hostinger 部署指导

## 项目概述
您的跨境AI电商代理应用已成功构建，准备部署到 Hostinger。

## 构建文件说明
- **dist/** 目录包含所有需要上传的文件
- **dist/.htaccess** 配置文件用于 URL 重写和性能优化
- **dist/assets/** 目录包含所有压缩优化的 JavaScript 和 CSS 文件

## 部署步骤

### 1. 准备上传文件
您需要上传 `dist` 目录中的所有内容到 Hostinger 的 `public_html` 目录。

### 2. Hostinger File Manager 部署（推荐）

#### 方法一：使用 Hostinger File Manager
1. 登录您的 Hostinger 账户
2. 进入 **控制面板 (hPanel)**
3. 点击 **File Manager**
4. 导航到 **public_html** 目录
5. **删除默认的 index.html 文件**（如果存在）
6. 上传 dist 目录中的所有文件：
   - index.html
   - .htaccess
   - assets/ 文件夹（包含所有 .js 和 .css 文件）

#### 方法二：使用 FTP 客户端
1. 使用 FTP 客户端（如 FileZilla）
2. 连接到您的 Hostinger 账户
3. 导航到 public_html 目录
4. 上传 dist 目录中的所有文件

### 3. 域名配置
- 如果使用主域名：将文件放在 `public_html` 根目录
- 如果使用子域名：创建相应的子目录（如 `public_html/subdomain/`）

### 4. 环境变量配置
**重要提示：** 您的应用需要 Gemini API 密钥才能正常工作。

在 Hostinger 中设置环境变量的方法：

#### 方法一：通过 .htaccess 文件（不推荐用于敏感信息）
```apache
SetEnv GEMINI_API_KEY "您的实际API密钥"
```

#### 方法二：修改构建的文件（推荐）
由于这是客户端应用，您需要将 API 密钥直接嵌入到应用中：

1. 编辑 `dist/assets/index-*.js` 文件
2. 搜索 `PLACEHOLDER_API_KEY`
3. 替换为您的实际 Gemini API 密钥

**安全提醒：** 这将使 API 密钥公开可见。考虑使用后端代理或环境变量方案。

### 5. SSL 证书配置
1. 在 Hostinger 控制面板中启用 SSL
2. 强制 HTTPS 重定向
3. 测试所有页面是否正确加载

### 6. 测试部署
1. 访问您的域名
2. 测试所有功能：
   - AI 助手功能
   - 侧边栏导航
   - 设置页面
   - API 密钥检查器

## 文件结构
部署后的文件结构应该如下：
```
public_html/
├── index.html
├── .htaccess
└── assets/
    ├── ai-BNLjCP8u.js
    ├── index-ccMY76qC.js
    └── vendor-DmnVtGYe.js
```

## 性能优化
已包含的 .htaccess 文件提供：
- Gzip 压缩
- 浏览器缓存优化
- SPA 路由支持

## 故障排除

### 页面显示空白
- 检查浏览器控制台是否有 JavaScript 错误
- 确认所有文件正确上传
- 验证 API 密钥配置

### 404 错误
- 确保 .htaccess 文件正确上传
- 检查 URL 重写规则是否生效

### API 功能不工作
- 验证 Gemini API 密钥是否正确设置
- 检查 API 密钥是否有效且有足够配额

## 后续维护
- 定期更新依赖包
- 监控 API 使用量
- 备份部署文件

## 联系支持
如果遇到部署问题，请联系 Hostinger 技术支持并提供此部署指南。