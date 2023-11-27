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


## reference
  - https://docs.docker.com/engine/reference/builder/
  - https://wild0522.gitbooks.io/yeasy_dp/content/