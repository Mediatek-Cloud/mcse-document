# 解除安裝作業

若要從系統中完整移除所有 MCSE 服務，可直接執行 `uninstall.sh` 腳本。

請注意，此腳本會刪除所有的資料與檔案（所有的 docker volume 都會被刪除），若有需要存留的資料，請務必在刪除之前自行完成備份。執行後，所有 MCSE 資料皆會消失。

執行 `uninstall.sh` 腳本，會出現提示 `Do you want to delete all data? [Y/N]:` 請直接輸入 `Y` 並且按下 Enter，整個 MCS 全部服務與資料將會被移除。

```
root@mcse-ubuntu:/home/ubuntu# ./uninstall.sh
Do you want to delete all data? [Y/N]: Y

shutdown all docker container.
Stopping root_web_1           ... done
Stopping root_proxy_1         ... done
Stopping root_layout_1        ... done
Stopping root_mcs_1           ... done
Stopping root_mail_1          ... done
Stopping root_api_1           ... done
Stopping root_oauth_1         ... done
Stopping root_gcm_1           ... done
Stopping root_service_1       ... done
Stopping root_mqtt_1          ... done
Stopping root_image-resizer_1 ... done
Stopping root_graph_1         ... done
Stopping root_minio_1         ... done
Stopping root_redis_1         ... done
Stopping root_db_1            ... done
Stopping root_gnatsd_1        ... done
Removing root_web_1           ... done
Removing root_proxy_1         ... done
Removing root_layout_1        ... done
Removing root_mcs_1           ... done
Removing root_mail_1          ... done
Removing root_api_1           ... done
Removing root_oauth_1         ... done
Removing root_gcm_1           ... done
Removing root_service_1       ... done
Removing root_mqtt_1          ... done
Removing root_image-resizer_1 ... done
Removing root_graph_1         ... done
Removing root_minio_1         ... done
Removing root_redis_1         ... done
Removing root_db_1            ... done
Removing root_gnatsd_1        ... done
Removing network root_default
Removing volume root_minio-data
Removing volume root_redis-data
Removing volume root_postgres-data
kill the caddy process: 23072.
remove minio tool and config.
remove caddy process from /etc/rc.local
Uninstall completely.
```


