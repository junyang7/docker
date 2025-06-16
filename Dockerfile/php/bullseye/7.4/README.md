# 基础配置

docker buildx rm multiarch-builder
docker buildx create --use --name multiarch-builder
docker buildx inspect --bootstrap

# 编译加载（开启系统代理）

docker buildx build --platform linux/amd64,linux/arm64 -t junyang7/php:7.4-fpm-bullseye --push . > build_output.log 2>&1
docker buildx build --platform linux/amd64,linux/arm64 -t junyang7/php:7.4-fpm-bullseye --push . | tee build_output.log
