# 停止服務

## 停止全部服務

請先切換目錄到放置 `docker-compose.yml` 的目錄，並且執行 `docker-compose stop` 指令來停止全部的 MCSE 服務。

執行範例：

```
root@mcse-ubuntu:/home/ubuntu/mcse# docker-compose stop
Stopping mcse_web_1           ... done
Stopping mcse_layout_1        ... done
Stopping mcse_mail_1          ... done
Stopping mcse_proxy_1         ... done
Stopping mcse_oauth_1         ... done
Stopping mcse_gcm_1           ... done
Stopping mcse_mqtt_1          ... done
Stopping mcse_image-resizer_1 ... done
Stopping mcse_graph_1         ... done
Stopping mcse_service_1       ... done
Stopping mcse_mcs_1           ... done
Stopping mcse_api_1           ... done
Stopping mcse_gnatsd_1        ... done
Stopping mcse_redis_1         ... done
Stopping mcse_minio_1         ... done
Stopping mcse_db_1            ... done
```


## 停止單一服務

請先切換目錄到放置 `docker-compose.yml` 的目錄，並且執行 `docker-compose stop 服務名稱` 指令來停止指定的 MCSE 服務。

執行範例：

```
root@mcse-ubuntu:/home/ubuntu/mcse# docker-compose stop web
Stopping mcse_web_1 ... done
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
````