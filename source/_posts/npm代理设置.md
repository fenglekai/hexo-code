---
thumbnail: 'https://picsum.photos/1280/720?random=8 #111'
title: npm代理设置
date: 2022-06-27 08:59:39
tags:
- NPM
---

### npm代理设置

> npm config set proxy http://127.0.0.1:8002
> npm config set https-proxy http://127.0.0.1:8002

### npm有验证的代理设置

> npm config set proxy http://username:password@127.0.0.1:8002
> npm confit set https-proxy http://username:password@127.0.0.1:8002

### npm查看代理设置

> npm config get or npm config list

### npm删除代理设置

> npm config delete proxy and npm config delete https-proxy