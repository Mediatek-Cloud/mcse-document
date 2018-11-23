# 備份資料

## 進入容器內備份

找到 `docker-compose.yml` 內的 `db` 區段，如下:

```yml
  db:
    image: postgres:9.6.8
    restart: always
    ports:
      - "5433:5432"
    volumes:
      - postgres-data:/var/lib/postgresql/data
    logging:
      options:
        max-size: "100k"
        max-file: "3"
    environment:
      POSTGRES_DB: ${DB_DATABASE}
      POSTGRES_USER: ${DB_USERNAME}
      POSTGRES_PASSWORD: ${DB_PASSWORD}
```

進入容器內執行備份指令

```sh
$ docker-compose exec db /bin/bash
root@22920952ac81:/#
```

備份指令如下:

```sh
# pg_dump [資料庫名稱] -U [帳號] -f [備份檔案名稱.backup.sql]
$ pg_dump mcs -U mediatek -f mcs.sql
```

完成後可以在根目錄 `/` 發現 `mcs.sql`，透過底下指令離開容器

```sh
$ exit
```

## 拿出備份資料

離開容器後，該如何拿到上述備份資料，先透過 `docker ps` 找到資料庫的容器名稱

```
$ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                    NAMES
22920952ac81        postgres:9.6.8      "docker-entrypoint.s…"   17 minutes ago      Up 17 minutes       0.0.0.0:5433->5432/tcp   mcs-local_db_1_ed2b69301f5b
```

可以看到名稱是 `mcs-local_db_1_ed2b69301f5b`，接著用 `docker cp` 指令將備份檔案從容器中拿到 Host 主機

```
$ docker cp mcs-local_db_1_ed2b69301f5b:/mcs.sql .
```
