# 設定 DNS records

為了讓您的物聯網裝置、使用者以及 MCSE 服務本身能夠透過網址互相連結訪問。您需要預先為 MCSE 的幾個主要服務申請 DNS records。請將下方 example.com 置換成您專屬的網域名稱。

| 主機名稱/別名 \(Name\) | 紀錄類型 \(Type\) | IP 位址/主機名稱 | 用途 |
| :---: | :---: | :---: | :--- |
| mcs.example.com | A | 安裝 MCSE 服務主機的 IP | 此為 MCSE 主要的主機名稱，稍後您會需要在在安裝腳本中輸入此網域名稱。 |
| www.mcs.example.com | CNAME | mcs.example.com | 主要用來提供網頁、登入等服務。MCSE 安裝完畢後，開啟瀏覽器，輸入此網址則可訪問到 MCSE 的網頁。 |
| api.mcs.example.com | CNAME | mcs.example.com | 主要用來提供後端 API 等服務，包括物聯網裝置上傳、獲取資料點的 APIs。 |
| mqtt.mcs.example.com | CNAME | mcs.example.com | 主要用來提供 MQTT publish/Subscribe 通訊協定的服務。 |
| gq.mcs.example.com | CNAME | mcs.example.com | 主要用來提供後端服務，像是場景\(Scene\)功能。 |
| image.mcs.example.com | CNAME | mcs.example.com | 主要用來提供圖片讀取服務，像是產品原型或是場景\(Scene\)底圖。 |
| minio.mcs.example.com | CNAME | mcs.example.com | 主要用來提供檔案的儲存服務，像是上傳的圖片與固件。 |

當然，您可以將 MCSE 的主要 A record 命名成任何符合您的應用或企業名稱相關的網址，而其他的 MCSE 服務的網址則保持服務名稱，例如 www, api, mqtt 等加上 A record 的命名規則。

稍後，在您使用 MCSE 安裝腳本進行自動安裝時，需將網域名稱填入（上述設定的 DNS A record），詳細安裝步驟請參考後續章節。

