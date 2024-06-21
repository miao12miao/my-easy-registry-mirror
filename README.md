# Easy Registry Mirror

简体中文 | [English](./i18n/README.us-en.md)

在国内日渐严峻的网络下，无论是公司还是个人，自建仓库是非常必要的，这个项目用于快速搭建一个`Docker`私有仓库，并且无需修改已运行的`Dockerfile`/`docker-compose.yaml`，几乎没有迁移成本；未来会支持更多`npm`、`maven`、`pip`等仓库。

## Trying

```bash
git clone https://github.com/shencangsheng/easy-registry-mirror.git
cd easy-registry-mirror
chmod +x ctl
./ctl help
./ctl docker install
./ctl docker sync help
```

## Features

1. Docker Registry
2. Auto Sync Docker Images

## Upcoming Features

1. npm Registry

## Principle

```mermaid
graph TD;
    A[Docker Request] --> B[Docker Registry Proxy];
    B --> C{docker pull?};
    C -- Yes --> D[docker pull image];
    C -- No --> E[Docker Registry Server];
    D --> F[Upload Docker Registry];
    F --> E
    E -- Response --> B
    B -- Response --> A
```

## Credits

This project was inspired by the [shencangsheng/registry-mirror-proxy](https://github.com/shencangsheng/registry-mirror-proxy) available in the GitHub project.

## 疑难杂症

如果已经因为网络无法获取到镜像，那么点击 [Releases](https://github.com/shencangsheng/easy-registry-mirror/releases/tag/v1.0.0) 下载项目所需要的基础镜像，运行 `gunzip -c xxx.tar.gz | docker load` 来载入镜像，`./ctl magic help` 来了解如何使用

## License

A short snippet describing the license (MIT)

MIT © Cangsheng Shen
