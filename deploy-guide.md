# 部署指南

## 环境要求

- Node.js >= 18
- Docker >= 20.10
- Kubernetes >= 1.25

## 部署步骤

### 1. 构建 Docker 镜像

```bash
docker build -t myapp:latest .
```

### 2. 推送到镜像仓库

```bash
docker push myregistry/myapp:latest
```

### 3. 部署到 Kubernetes

```bash
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
```

## 环境变量配置

| 变量名 | 说明 | 默认值 |
|--------|------|--------|
| PORT | 服务端口 | 3000 |
| DB_HOST | 数据库地址 | localhost |
| DB_PORT | 数据库端口 | 5432 |
| REDIS_URL | Redis 地址 | redis://localhost:6379 |

## 健康检查

服务启动后，访问 `/health` 端点确认服务状态：

```bash
curl http://localhost:3000/health
```

## 回滚方案

如果部署出现问题，使用以下命令回滚：xxxx

```bash
kubectl rollout undo deployment/myapp
```
