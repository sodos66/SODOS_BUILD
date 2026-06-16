FROM node:23-alpine AS runner

WORKDIR /app

ENV NODE_ENV=production
ENV NITRO_PORT=3000
ENV HOST=0.0.0.0

# 安装 unzip
RUN apk add --no-cache unzip

# 复制压缩包
COPY web.zip /tmp/web.zip

# 解压到 app 目录
RUN unzip -q /tmp/web.zip -d /app \
    && rm /tmp/web.zip

# 确保 index.mjs 存在
# (Nuxt3 的 output 都是 .output 目录)
WORKDIR /app/.output

EXPOSE 3000

CMD ["node", "./server/index.mjs"]
