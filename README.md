# xAI API 反向代理

一键部署你自己的 xAI API 代理服务，支持自定义域名。

## 一键部署

[<img src="https://vercel.com/button" alt="Deploy with Vercel"/>](https://vercel.com/new/clone?repository-url=https://github.com/lizheyong/xai-reverse-proxy&project-name=xai-reverse-proxy&repository-name=xai-reverse-proxy&demo-title=xAI%20API%20Proxy&demo-description=Simple%20reverse%20proxy%20for%20xAI%20API){:target="_blank"}

## 部署步骤

### 1. 部署到 Vercel
- 点击上方 "Deploy with Vercel" 按钮
- 使用 GitHub 账号登录 Vercel
- 选择要部署的仓库名称
- 点击 Deploy 开始部署

### 2. 配置环境变量（可选）
在 Vercel 项目设置中添加环境变量：
- `PROJECT_NAME`: 你的项目名称

### 3. 绑定自定义域名
- 在 Vercel 控制台进入你的项目
- 点击 "Settings" -> "Domains"
- 添加你的自定义域名，如 `xai-api.example.com`
- 在你的域名服务商添加以下 DNS 记录：
	类型: CNAME
	主机记录: xai-api（根据你的需求设置）
	记录值: cname.vercel-dns.com
- 等待 DNS 解析生效（通常需要几分钟到几小时）

### 4. 使用示例

```bash
curl https://你的域名/v1/chat/completions \
-H "Content-Type: application/json" \
-H "Authorization: Bearer your-xai-api-key" \
-d '{
 "model": "grok-beta",
 "messages": [{"role": "user", "content": "Hello!"}]
}'
```

## 项目结构
```
├── README.md
├── index.js
├── node_modules
├── package-lock.json
├── package.json
└── vercel.json
```

## 本地开发
### 安装依赖
```
npm install
```
### 本地运行
```
npm start
```
### 部署到 Vercel
```
vercel deploy --prod
```
## 注意事项
### 为什么需要自定义域名？
避免 API 请求被墙

更好的可访问性

便于管理多个部署

### DNS 解析注意事项
建议使用 CNAME 记录

如果使用 Cloudflare，建议开启 Proxy 状态

确保 SSL/TLS 加密已启用

## 常见问题
Q: 如何更新部署？

A: 直接推送代码到 GitHub，Vercel 会自动重新部署

Q: 如何查看运行日志？

A: 在 Vercel 控制台的 "Deployments" 页面查看

