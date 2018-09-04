# 申請第三方服務


1. **Google GCM**

	MCSE 的觸發通知中的**手機推播**是透過 **Google Cloud Messaging (GCM)** 將訊息推送到裝有 MCSE Mobile App 的手機上，藉以讓使用者立即收到裝置感測的數值。因此，若要在 MCSE 中使用此功能您必須先至 Google 申請相關的金鑰與權限。
	
	* 先在 Google Cloud Platform [https://console.cloud.google.com/Google](https://console.cloud.google.com/Google) 建立一個專案，並在此專案的 **API 和服務** 中建立一個 Google Cloud Messaging API 的使用憑證並取得金鑰
	* 教學文件: [https://cloud.google.com/docs/authentication/api-keys](https://cloud.google.com/docs/authentication/api-keys)
	* 在 MCSE 設定檔中將您剛剛建立的**專案編號**填入 **GCM\_SENDER\_ID** 中 ，**API 金鑰**填入 **GCM\_API\_KEY**。稍後會在進階設定章節中，詳細解釋此步驟。

	
2. **Google GA (非必要)**

	用來分析使用者在 Web Console 上的使用行為。預設使用 MCSE 的提供的帳號，若您想要自行分析網頁使用行為，您必須先在 [Google Analytics](https://analytics.google.com/) 申請一組專用的 GA ID。 