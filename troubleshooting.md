# 疑難排解

1. 啟動 MCSE 服務後，透過瀏覽器訪問會看到**連線失敗**或是 **This site can’t be reached** 的錯誤訊息。

	請檢查您的 **Caddy 伺服器** 與 MCSE 服務的 **Docker 容器 (Container)**是否正常運行。
	* Caddy: 透過 `ps` 指令看 caddy 是否在運行中。
		
		```
$ ps -aux|grep caddy
ubuntu   13915  0.0  0.3  18816 12788 pts/0    Sl   05:40   0:00 caddy -conf Caddyfile
ubuntu   19592  0.0  0.0  12944  1088 pts/0    S+   05:44   0:00 grep --color=auto caddy
		```
		
	* Docker 容器 (Container): 透過 `docker ps` 指令看每個服務是否在運行 (STATUS = Up) 中。
	
	
		```
$ docker ps
CONTAINER ID        IMAGE                                           COMMAND                  CREATED             STATUS                   PORTS                                            NAMES
aa01a6ea0fe4        harbor.wu-boy.com/mcse/web:mcse-web-0.0.1       "/bin/sh -c ./web"       2 hours ago         Up 2 hours (healthy)     0.0.0.0:4001->4000/tcp                           mcse_web_1
a1f90c01fefc        harbor.wu-boy.com/mcse/proxy:mcse-proxy-0.0.1   "/bin/sh -c ./proxy"     2 hours ago         Up 2 hours (healthy)     0.0.0.0:4000->4000/tcp                           mcse_proxy_1
679f9c5ecefa        harbor.wu-boy.com/mcse/layout:mcse-0.0.1        "sh docker/run.sh"       2 hours ago         Up 2 hours               0.0.0.0:3001->80/tcp                             mcse_layout_1
34b474d753ff        harbor.wu-boy.com/mcse/api:mcse-0.0.1           "sh scripts/docker.sh"   2 hours ago         Up 2 hours               0.0.0.0:3000->3000/tcp                           mcse_api_1
b85f647ad197        harbor.wu-boy.com/mcse/ses:mcse-0.0.2           "node build/app.js"      2 hours ago         Up 2 hours (healthy)     8080/tcp                                         mcse_mail_1
074c485438fd        harbor.wu-boy.com/mcse/graphql-api:mcse-0.0.1   "/go-mcs server"         2 hours ago         Up 2 hours (healthy)     0.0.0.0:8089->8080/tcp                           mcse_mcs_1
18ec51930de1        harbor.wu-boy.com/mcse/mqtt:mcse-0.0.1          "sh scripts/run.sh"      2 hours ago         Up 2 hours               0.0.0.0:1883->1883/tcp, 0.0.0.0:3011->3011/tcp   mcse_mqtt_1
880341d350e7        harbor.wu-boy.com/mcse/auth:mcse-0.0.1          "sh scripts/docker.sh"   2 hours ago         Up 2 hours               0.0.0.0:3002->3002/tcp                           mcse_oauth_1
dab4c91c427e        harbor.wu-boy.com/mcse/queue:mcse-0.0.1         "node build/app.js"      2 hours ago         Up 2 hours (healthy)     8080/tcp                                         mcse_service_1
82caf71730e8        harbor.wu-boy.com/mcse/notify:mcse-0.0.1        "node build/index.js"    2 hours ago         Up 2 hours (healthy)     8080/tcp                                         mcse_gcm_1
a9c550f39de3        appleboy/nginx-image-resizer:1.0.0              "/bin/run.sh"            2 hours ago         Up 2 hours               0.0.0.0:8002->80/tcp                             mcse_image-resizer_1
04147a44ed08        redis:3.2.11                                    "docker-entrypoint.s…"   2 hours ago         Up 2 hours               0.0.0.0:6378->6379/tcp                           mcse_redis_1
b08ceaa9e682        harbor.wu-boy.com/mcse/graph:mcse-graph-0.0.1   "/bin/sh -c 'node_mo…"   2 hours ago         Up 2 hours               0.0.0.0:3003->3003/tcp                           mcse_graph_1
ec19c6c35786        nats:latest                                     "/gnatsd -c gnatsd.c…"   2 hours ago         Up 2 hours               6222/tcp, 0.0.0.0:4222->4222/tcp, 8222/tcp       mcse_gnatsd_1
c4ac8e4da260        postgres:9.6.8                                  "docker-entrypoint.s…"   2 hours ago         Up 2 hours               0.0.0.0:5433->5432/tcp                           mcse_db_1
24c71c23ce63        minio/minio                                     "/usr/bin/docker-ent…"   2 hours ago         Up 2 hours (unhealthy)   0.0.0.0:9000->9000/tcp                           mcse_minio_1
		```