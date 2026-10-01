# zcode-bookstore-vod

智慧书城 × Lite VOD 媒资平台联合代码仓（仅源码，不含分步文档）。

## 目录

| 目录 | 说明 | 默认端口 |
| --- | --- | --- |
| `lite-vod/` | 媒资：`vod-api` + `vod-worker` + `vod-common` | API `8080` · Worker `8082` |
| `smart_bookstore/` | 智慧书城后端（+ 可选 Nginx 静态） | `8081` |

两边用 HTTP 契约联接，关联键为 `fileId`。书城生产上传 / 读章走媒资 `/internal/medias/**` + `X-Internal-Token`。

## 本地启动（摘要）

1. 准备 MySQL / Redis / RabbitMQ / MinIO（或按各模块 `docker-compose.yml`）
2. 书城：复制 `application-local.yaml.example` → `application-local.yaml`（勿提交）
3. 媒资：参考 `lite-vod/.env.example`，按需设置 `VOD_INTERNAL_TOKEN` 等
4. 分别启动 `lite-vod` 与 `smart_bookstore`

## 注意

- 本仓**不含** `docs/` 分步实现文档
- 不要提交 `application-local.yaml`、`.env`、密钥与真实 API Key
