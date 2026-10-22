# caddy-prebuild

使用 GitHub Actions 构建并发布带有以下模块的 Caddy Docker 镜像：

- `github.com/caddy-dns/cloudflare`
- `github.com/ueffel/caddy-brotli`
- `github.com/mholt/caddy-ratelimit`

## 发布到 Docker Hub

在 GitHub 仓库或组织中配置以下 Actions secrets，并确保组织级 secret 已授权此仓库访问：

- Actions secret `DOCKERHUB_USERNAME`：Docker Hub 登录用户名。
- Actions secret `DOCKERHUB_TOKEN`：Docker Hub access token。

向 `main` 推送变更会构建并发布 `latest` 和 `sha-<commit>` 标签；推送 `v*` 格式的 Git tag 会发布对应版本标签。工作流每天 UTC 凌晨 2 点定时构建并发布镜像。Pull request 会构建镜像但不会登录或推送。也可以通过 Actions 页面手动运行工作流。
