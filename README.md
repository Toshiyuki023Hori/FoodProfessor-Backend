# Food Professor BackEnd

### 環境構築(Back 用)

1. (任意のディレクトリ下で)`git clone REPO_URL`
2. `docker-compose build`
3. `docker-compose up -d`

   **すぐに手順 4 にいかないこと**
   db コンテナで、`docker-entrypoint-initdb.d`配下のスクリプトが完了されてから手順 5 を実施

```
# dbコンテナのログを表示して、スクリプトが完了されるか監視
$ docker logs foodprofessor_db_1 --follow
...
ログ
...
[Entrypoint]: /usr/local/bin/docker-entrypoint.sh: running /docker-entrypoint-initdb.d/00_create.sql
[Entrypoint]: /usr/local/bin/docker-entrypoint.sh: running /docker-entrypoint-initdb.d/01_grant.sql
```

上記のように、`.sql`ファイルが実行された表示が出れば完了

4. `docker-compose run api bundle exec rake db:create`
5. DONE!!