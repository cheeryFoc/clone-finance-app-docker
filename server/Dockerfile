# 使用 Node.js 官方镜像
FROM node:22

# 设置工作目录
WORKDIR /app

# 复制 package.json 和 package-lock.json
COPY package*.json ./

# 安装依赖
RUN npm install --legacy-peer-deps

# 复制所有文件
COPY . .

# 暴露端口
EXPOSE 8080

# 启动后端应用
CMD ["npm", "run", "dev"]