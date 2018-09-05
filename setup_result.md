# 驗證安裝結果

1. 打開瀏覽器，輸入 MCSE 網址（MCSE www 服務的主機名稱)，例如：www.mcs.example.com，能看到如下的登入畫面則代表網頁服務啟動成功。
	
	![](./images/web_login.png)

2. 要檢查每個微服務的運行狀況，則可在 Terminal 視窗下，執行底下指令 (請使用 root 帳號):


	```
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
	mcse_minio_1           /usr/bin/docker-entrypoint ...   Up (unhealthy)   0.0.0.0:9000->9000/tcp                        
	mcse_mqtt_1            sh scripts/run.sh                Up               0.0.0.0:1883->1883/tcp, 0.0.0.0:3011->3011/tcp
	mcse_oauth_1           sh scripts/docker.sh             Up               0.0.0.0:3002->3002/tcp                        
	mcse_proxy_1           /bin/sh -c ./proxy               Up (healthy)     0.0.0.0:4000->4000/tcp                        
	mcse_redis_1           docker-entrypoint.sh redis ...   Up               0.0.0.0:6378->6379/tcp                        
	mcse_service_1         node build/app.js                Up (healthy)     8080/tcp                                      
	mcse_web_1             /bin/sh -c ./web                 Up (healthy)     0.0.0.0:4001->4000/tcp        
	```

	看到每個服務都是 `Up` 狀態，就代表安裝並且啟動成功。
