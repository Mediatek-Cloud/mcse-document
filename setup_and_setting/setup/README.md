# 安裝與移除

以下幾個章節，會帶您透過 MCSE 腳本一步一步的完成安裝或是移除 MCSE 整套服務。

MCSE 相關的執行腳本位於 MCSE 軟件包解壓縮後的目錄下，包括 `install.sh` 與 `uninstall.sh`。在您的 Ubuntu 環境執行 MCSE 相關操作時，請使用 `root` 權限。

```text
ubuntu@mcse-ubuntu:~/mcse$ ls -al
total 60
drwxrwxr-x  7 ubuntu ubuntu 4096 Sep  3 09:59 .
drwxr-xr-x 10 ubuntu ubuntu 4096 Sep  3 09:57 ..
drwxr-xr-x  4 root   root   4096 Aug 30 06:48 backup
drwxrwxr-x  2 ubuntu ubuntu 4096 Aug 29 10:00 bin
-rw-r--r--  1 ubuntu ubuntu  853 Sep  3 09:59 Caddyfile
-rw-r--r--  1 ubuntu ubuntu 9424 Sep  3 09:46 docker-compose.yml
-rw-r--r--  1 ubuntu ubuntu  530 Sep  3 09:59 .env
drwxr-xr-x  2 ubuntu ubuntu 4096 Aug  2 07:13 images
-rwxr-xr-x  1 ubuntu ubuntu 3421 Sep  3 09:57 install.sh
drwxrwxr-x  3 ubuntu ubuntu 4096 Aug 29 10:01 minio
drwxr-xr-x  2 ubuntu ubuntu 4096 Aug  6 01:20 sql
-rwxr-xr-x  1 ubuntu ubuntu  645 Aug 27 07:00 uninstall.sh

...
```

