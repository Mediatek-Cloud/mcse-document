# 設定 SMTP

MCSE 在以下幾個情況會寄發電子郵件到指定的使用者信箱。

1. 帳號註冊認證信
2. 重設密碼確認信
3. 觸發動作的電子郵件通知
4. 共享原型與裝置的通知信

MCSE 預設提供了一組免費的 SMTP 郵件帳號，但因為額度限制，強烈建議在正式營運時，將其換成您自己或組織的郵件帳號。

其修改方式如下：

1. 在 MCSE 的安裝檔案目錄下，編輯 `.env` 檔案中的以下幾個環境參數
   * SMTP\_USER：您用來登入 SMTP 郵件服務器的帳號名稱
   * SMTP\_PASSWORD：您用來登入 SMTP 郵件服務器的帳號密碼
   * SMTP\_HOST：SMTP 郵件服務器的網址
   * SMTP\_PORT：SMTP 郵件服務器的連接埠
   * SMTP\_SSL：是否使用 SSL 連線

     以下用 SMTP2GO 這個免費的 SMTP 郵件服務器為例，其設定說明可以參考 [https://www.smtp2go.com/setup/](https://www.smtp2go.com/setup/)

     ```text
     SMTP_USER=mcse
     SMTP_PASSWORD=dHk2cG9ibjIyxxxx
     SMTP_HOST=mail.smtp2go.com
     SMTP_PORT=465
     SMTP_SSL=true
     ```
2. 修改完成後，儲存 `.env` 檔案，並重新啟動 MCSE 服務，使新的設定生效。或是接續完成其他進階設定後，再一起重啟服務。

   ```text
    $ docker-compose stop
    $ docker-compose up -d
   ```

   執行範例：

   ```text
    root@mcse-ubuntu:/home/ubuntu/mcse# docker-compose stop
    Stopping mcse_web_1           ... done
    Stopping mcse_layout_1        ... done
    Stopping mcse_mail_1          ... done
    Stopping mcse_proxy_1         ... done
    Stopping mcse_oauth_1         ... done
   ...

   root@ip-172-31-17-68:/home/ubuntu/mcse# docker-compose up -d
    Starting mcse_redis_1         ... done
    Starting mcse_image-resizer_1 ... done
    Starting mcse_graph_1         ... done
    Starting mcse_gnatsd_1        ... done
    Starting mcse_db_1            ... done
    ...
   ```

**注意事項：**

1. 若您使用的是 Gmail 信箱，建議您先開啟 Google 帳戶的兩步驟驗證功能，並透過應用程式密碼來登入 Gmail 信箱，或是設定允許安全性較低的應用程式存取您的帳戶。詳請請參考 [Gmail 說明文件 -&gt; 疑難排解 -&gt; 無法登入電子郵件程式](https://support.google.com/mail/answer/7126229)的說明。
2. 若您使用的是公司內部信箱，請先確認安裝 MCSE 的主機是能夠連接到此 SMTP 郵件服務器的。可透過 telnet 指令來測試，以上述 SMTP2GO 郵件服務器為例：
   * 成功

     ```text
       $ telnet mail.smtp2go.com 465
       Trying 173.255.233.87...
       Connected to mail.smtp2go.com.
     ```

   * 失敗

     ```text
       $ telnet mail.smtp2go.com 466
       Trying 66.228.43.14...
       telnet: Unable to connect to remote host: Connection refused
     ```

