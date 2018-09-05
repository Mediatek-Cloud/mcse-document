# 啟動服務

## 啟動所有服務

請先切換目錄到放置 `docker-compose.yml` 的目錄，並且執行 `docker-compose up -d` 指令來啟動全部的 MCSE 服務。

執行範例：

```
root@mcse-ubuntu:/home/ubuntu/mcse# docker-compose up -d
Starting mcse_redis_1         ... done
Starting mcse_image-resizer_1 ... done
Starting mcse_graph_1         ... done
Starting mcse_gnatsd_1        ... done
Starting mcse_db_1            ... done
Starting mcse_minio_1         ... done
Starting mcse_oauth_1         ... done
Starting mcse_mqtt_1          ... done
Starting mcse_service_1       ... done
Starting mcse_gcm_1           ... done
Starting mcse_mail_1          ... done
Starting mcse_mcs_1           ... done
Starting mcse_api_1           ... done
Starting mcse_layout_1        ... done
Starting mcse_proxy_1         ... done
Starting mcse_web_1           ... done
```


## 啟動單一服務

請先切換目錄到放置 `docker-compose.yml` 的目錄，並且執行 `docker-compose up -d 服務名稱` 指令來啟動指定的 MCSE 服務。

執行範例：

```
root@mcse-ubuntu:/home/ubuntu/mcse# docker-compose up -d api
mcse_gnatsd_1 is up-to-date
mcse_redis_1 is up-to-date
mcse_minio_1 is up-to-date
mcse_db_1 is up-to-date
Starting mcse_api_1 ... done
```

其中 `服務名稱` 請參考 docker-compose 內定義的各項服務。見底下的範例，`proxy`、`web`、`api` 為服務名稱。

```
ubuntu@mcse-ubuntu:~/mcse$ cat docker-compose.yml 
version: '2'

services:
  proxy:
    image: docker.mediatek.io/mcse/proxy:mcse-proxy-0.0.1
    ports:
      - "4000:4000"
...

  web:
    image: docker.mediatek.io/mcse/web:mcse-web-0.0.1
    ports:
      - "4001:4000"
    restart: always
...

 api:
    image: docker.mediatek.io/mcse/api:mcse-0.0.1
    depends_on:
      - db
      - redis
      - minio
      - gnatsd
    restart: always
    ports:
      - "3000:3000"
...
```
