# 使用 Node.js 22 官方镜像作为构建阶段
FROM node:22 AS build

# 设置工作目录
WORKDIR /app

# 复制 package.json 和 package-lock.json
COPY package*.json ./

# 安装依赖
RUN npm install

# 复制应用代码
COPY . .

# 构建应用
RUN npm run build  # 确保这一命令输出到 dist 目录

# 使用 Nginx 作为生产环境服务器
FROM nginx:alpine

# 复制 Nginx 配置文件
COPY nginx.conf /etc/nginx/conf.d/default.conf

# 复制构建好的文件到 Nginx 目录
COPY --from=build /app/dist /usr/share/nginx/html

# 暴露 Nginx 默认端口
EXPOSE 80

# 启动 Nginx
CMD ["nginx", "-g", "daemon off;"]