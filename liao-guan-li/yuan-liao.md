# 還原資料

## 查找資料庫容器名稱

```
$ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                    NAMES
22920952ac81        postgres:9.6.8      "docker-entrypoint.s…"   17 minutes ago      Up 17 minutes       0.0.0.0:5433->5432/tcp   mcs-local_db_1_ed2b69301f5b
```

## 將備份檔案傳入容器

```
$ docker cp mcs.sql mcs-local_db_1_ed2b69301f5b:/backup.sql
```

## 進入容器還原資料庫

```sh
$ docker-compose exec db /bin/bash
root@22920952ac81:/#
```

## 還原指令

```sh
# psql -f [備份檔案名稱.backup.sql] [資料庫] [帳號]
$ psql -f backup.sql mcs mediatek
SET
SET
SET
SET
SET
 set_config
------------

(1 row)

SET
SET
SET
CREATE EXTENSION
COMMENT
...
```

