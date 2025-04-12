# 医影随护网页应用部署指南

本文档提供如何部署医影随护网页应用的详细步骤。

## 文件结构

- `index.html`: 应用入口文件
- `assets/`: 静态资源文件
- `web.config`: IIS服务器配置
- `.htaccess`: Apache服务器配置
- `nginx.conf.example`: Nginx服务器配置示例

## 部署步骤

### 1. 选择服务器类型

根据您的服务器类型，准备相应的配置文件：

- **Nginx服务器**: 使用`nginx.conf.example`
- **Apache服务器**: 已包含`.htaccess`
- **IIS服务器**: 已包含`web.config`

### 2. Nginx部署

1. 修改`nginx.conf.example`中的域名和路径
   ```
   server_name your-domain.com;
   root /path/to/your/dist;
   ```

2. 将配置文件添加到Nginx配置中
   ```
   cp nginx.conf.example /etc/nginx/sites-available/your-site
   ln -s /etc/nginx/sites-available/your-site /etc/nginx/sites-enabled/
   ```

3. 重启Nginx
   ```
   nginx -t
   systemctl restart nginx
   ```

### 3. Apache部署

1. 确保已启用以下模块:
   - mod_rewrite
   - mod_expires
   - mod_deflate

2. 将整个文件夹上传到网站根目录

### 4. IIS部署

1. 确保安装了URL Rewrite模块
2. 将整个文件夹上传到网站根目录

### 5. 其他托管服务

如果使用其他托管服务（如Netlify、Vercel等）:

1. 根据服务商要求准备配置文件
2. 通常只需上传整个文件夹即可

## API配置

应用已配置为连接到以下API服务器:
```
https://enzkmpypbsrx.sealoshzh.site/api
```

如需更改API配置，请修改`index-B_XG-FMA.js`中的相关部分。

## 故障排除

1. **页面刷新404错误**: 确保重写规则配置正确
2. **API连接问题**: 检查CORS配置和网络连接
3. **静态资源加载失败**: 检查文件路径和权限 