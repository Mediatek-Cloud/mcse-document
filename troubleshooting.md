# 疑難排除

## 1. 啟動 MCSE 服務後，透過瀏覽器訪問會看到**連線失敗**或是 **This site can’t be reached** 的錯誤訊息。

請檢查您的 **Caddy 伺服器** 與 MCSE 服務的 **Docker 容器 \(Container\)**是否正常運行。

* Caddy: 透過 `ps` 指令看 caddy 是否在運行中。若 `caddy -conf Caddyfile` 不存在，則切換至 MCSE 安裝檔案目錄，執行 Caddy 服務。

  執行範例：
  
  * Caddy 正常運行中 

  ```
	root@mcse-ubuntu:/home/ubuntu/mcse# ps -aux|grep caddy
    ubuntu   13915  0.0  0.3  18816 12788 pts/0    Sl   05:40   0:00 caddy -conf Caddyfile
    ubuntu   19592  0.0  0.0  12944  1088 pts/0    S+   05:44   0:00 grep --color=auto caddy
  ```
  
  * Caddy 服務不存在

  ```
	root@mcse-ubuntu:/home/ubuntu/mcse# ps -aux|grep caddy
    ubuntu   19592  0.0  0.0  12944  1088 pts/0    S+   05:44   0:00 grep --color=auto caddy
    root@mcse-ubuntu:/home/ubuntu/mcse# caddy -conf Caddyfile &
  ```

* Docker 容器 \(Container\): 透過 `docker-compose ps` 指令看每個服務是否在運行中，`STATUS = Up` 或 `STATUS = Up (healthy)`。

	如果無法正常運作，請嘗試停止並重啟此單一服務，或整個 MCSE（請參考[系統管理](./operation.md)章節）

  執行範例：

  ```text
    root@mcse-ubuntu:/home/ubuntu/mcse# docker-compose ps
            Name                      Command                   State                            Ports                     
    -----------------------------------------------------------------------------------------------------------------------
    mcse_api_1             sh scripts/docker.sh             Up               0.0.0.0:3000->3000/tcp                        
    mcse_db_1              docker-entrypoint.sh postgres    Up               0.0.0.0:5433->5432/tcp                        
    mcse_gcm_1             node build/index.js              Up (healthy)     8080/tcp                                      
    mcse_gnatsd_1          /gnatsd -c gnatsd.conf           Up               0.0.0.0:4222->4222/tcp, 6222/tcp, 8222/tcp    
    mcse_graph_1           /bin/sh -c node_modules/.b ...   Up               0.0.0.0:3003->3003/tcp                        
    mcse_image-resizer_1   /bin/run.sh                      Up               0.0.0.0:8002->80/tcp                          
    mcse_layout_1          sh docker/run.sh                 Up               0.0.0.0:3001->80/tcp                          
    mcse_mail_1            node build/app.js                Up (healthy)     8080/tcp                                      
    mcse_mcs_1             /go-mcs server                   Up (healthy)     0.0.0.0:8089->8080/tcp                        
    mcse_minio_1           /usr/bin/docker-entrypoint ...   Up (healthy)   0.0.0.0:9000->9000/tcp                        
    mcse_mqtt_1            sh scripts/run.sh                Up               0.0.0.0:1883->1883/tcp, 0.0.0.0:3011->3011/tcp
    mcse_oauth_1           sh scripts/docker.sh             Up               0.0.0.0:3002->3002/tcp                        
    mcse_proxy_1           /bin/sh -c ./proxy               Up (healthy)     0.0.0.0:4000->4000/tcp                        
    mcse_redis_1           docker-entrypoint.sh redis ...   Up               0.0.0.0:6378->6379/tcp                        
    mcse_service_1         node build/app.js                Up (healthy)     8080/tcp                                      
    mcse_web_1             /bin/sh -c ./web                 Up (healthy)     0.0.0.0:4001->4000/tcp
  ```

