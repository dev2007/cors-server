# cors-server

## 用途
解决 `gitalk` 报错 `Error:Network Error`

API 层面原因为：国内的 `https://cors-anywhere.azm.workers.dev/https://github.com/login/oauth/access_token` 接口被墙，导致 `gitalk` 无法获取 `token` 问题

## 原理
借助 `vercel` 部署该服务，搭建一个跨域服务替换 `gitalk` 被墙的服务

## 部署方法

1. vercel 使用 github 登录后，授权访问该项目
2. 在 vercel 新建项目，选择 github 项目为该项目
3. 部署成功后获得一个 vercel 分配的域名，如 `cors-server-inky.vercel.app`
4. 也可以向 vercel 添加自定义域名

## gitalk 配置

将 gitalk 中的 `proxy` 配置指定为：`https://{domain}/github_access_token` 即可,

示例： proxy: 'https://cors-server-inky.vercel.app/github_access_token'

也可以使用我配置的服务域名：`https://cors-server.bookhub.tech/github_access_token`

如果不放心，可以 `fork` 该项目然后自己注册 `vercel` 进行部署配置

