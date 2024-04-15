# write a docker file 

## commands in docker file
  - FROM: 取得 base image
  - EXPOSE: 容器對外的 port
  - WORKDIR: 接下來的指令在此目錄下執行
  - ADD/COPY: (ADD會包含解壓縮)複製檔案到指定路徑
  - CMD: 容器啟動時執行命令
  - ENV: 環境變數
  - USER: 當前使用者
  - ....其他參考官網介紹


## tips to compact image
  - selecte minized based image
  - docker iterated execute "run"(start/create)->"modified"->"commit" so do as less RUN command as you can
  - delete all packages, folders that are not used at the end

## build image for different architecture
  Q: Docker : exec /usr/bin/sh: exec format error
  - types: x86(amd64), arm64(aarch64)
    Cannot run an x86 built image on an arm64/aarch64 machine.
    it need to rebuild the image using the corresponding architecture
  - reference: https://stackoverflow.com/questions/42494853/standard-init-linux-go178-exec-user-process-caused-exec-format-error
  - run `docker image inspect <image name>`
    see output:
    ```
        "Architecture": "arm64",
        "Variant": "v8",
        "Os": "linux",
    ```
    Using the DOCKER_DEFAULT_PLATFORM environment variable:
    1. `DOCKER_DEFAULT_PLATFORM="linux/amd64" docker build -t test .`
    2. Using the --platform argument, either in the CLI or in your dockerfile:
        `docker build --platform="linux/amd64" -t test .`
        `FROM --platform=linux/amd64 ubuntu:jammy`
  - reference: https://stackoverflow.com/questions/73285601/docker-exec-usr-bin-sh-exec-format-error
  - build for multi-platform image: https://docs.docker.com/build/building/multi-platform/#build-and-run-multi-architecture-images

## reference
  - https://docs.docker.com/engine/reference/builder/
  - https://wild0522.gitbooks.io/yeasy_dp/content/