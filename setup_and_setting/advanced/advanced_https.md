# 使用 HTTPS

MCSE 預設安裝後，是使用 HTTP 協定，然而為了增加資料傳輸的安全性，您可能會希望所有裝置與用戶都能透過 HTTPS 訪問 MCSE 服務。以下會介紹如何透過 Caddy 本身提供的 **Automatic HTTPS** 功能來申請並啟用 HTTPS 服務。

操作步驟如下：

### 1. 修改 Caddyfile 檔案

`Caddyfile` 置於 MCSE 的安裝目錄下，將檔案中每個服務的通訊協定由 `http://` 改成 `https://`。

執行範例：

```text
$ vi Caddyfile
```

```text
https://www.mcs.example.com {
  proxy /oauth localhost:3002 {
    websocket
    transparent
...

https://api.mcs.example.com {
  proxy /mcs/v3 localhost:8089 {
    websocket
    transparent
...
```

### 2. 修改 .env

`.env` 置於 MCSE 的安裝目錄下，將檔案中的 **PROTOCOL** 參數改成 https

```text
$ vi .env
```

```text
...
PROTOCOL=https
S3_SSL=false
```

### 3. 重新啟動 Caddy 網頁服務器

停止：

```text
$ kill $(ps aux | grep Caddyfile | grep -v grep | awk -F" " '{print $2}')
```

再啟動：

```text
$ caddy -conf=Caddyfile -email=your@email.com &
```

### 4. 重新啟動 MCSE 所有服務

停止：

```text
$ docker-compose down
Stopping mcse_web_1           ... done
Stopping mcse_proxy_1         ... done
Stopping mcse_layout_1        ... done
Stopping mcse_api_1           ... done
...
```

再啟動：

```text
$ docker-compose up -d
root_db_1 is up-to-date
Creating root_graph_1 ...
root_redis_1 is up-to-date
Creating root_image-resizer_1 ...
Creating root_graph_1         ... done
Creating root_image-resizer_1 ... done
Creating root_mqtt_1          ... done
Creating root_oauth_1         ... done
Creating root_service_1       ... done
...
```

## 備註

此作法是使用 Caddy + Let's Encrypt 快速實現 HTTPS 服務器，若要使用自有憑證，請參考公司現行的作法，或聯絡我們。

