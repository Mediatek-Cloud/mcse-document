# 進階設定

除了在安裝過程中輸入的參數之外，您還可透過修改 `.env` 檔案中的環境變數，來統一設定 MCSE 的各個服務與功能，下面章節會列舉出幾個基本且常用的設定。

`.env` 檔案位於 MCSE 軟件包解壓縮後的目錄下。

```
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

ubuntu@mcse-ubuntu:~/mcse$ vi .env

...
```