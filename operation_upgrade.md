# 版本升級

## 升級 API 服務

假設現在要升級 API 服務該怎麼升級 (從 0.0.1 升級到 0.0.2)


版號由 Mediatek 團隊告知

### 修改 docker-compose 檔案


找到底下:


```
  api:
    image: harbor.wu-boy.com/mcse/api:mcse-0.0.1
```


將 0.0.1 換成 0.0.2


```
  api:
    image: harbor.wu-boy.com/mcse/api:mcse-0.0.2
```

### 下載映像檔

下載單一服務映像檔

```
$ docker-compose pull api
Pulling api ... done
```


假設有多個服務需要升級，可以使用底下指令


```
$ docker-compose pull
Pulling minio         ... done
Pulling image-resizer ...
Pulling db            ...
Pulling redis         ...
Pulling mcs           ...
Pulling proxy         ...
Pulling web           ... done
Pulling oauth         ...
Pulling mqtt          ...
Pulling gnatsd        ...
Pulling mail          ...
Pulling gcm           ...
Pulling service       ...
Pulling api           ...
Pulling layout        ... done
Pulling graph         ...
```



### 停止及刪除 API 服務


```
$ docker-compose stop api
Stopping root_api_1 ... done
$ docker-compose rm -f api
Going to remove root_api_1
Removing root_api_1 ... done
```


### 啟動 API 服務

```
$ docker-compose up -d api
Creating root_api_1    ... done
```