
Dockerコンテナイメージをビルド
(少し時間がかかります)
```
docker compose build
```

Railsアプリケーション作成
```
docker compose run web rails new . --force --no-deps --database=postgresql
```


```
docker compose run web bundle install
```

DB作成
`config/database.yml`に以下の内容を追加。
```
efault: &default
  adapter: postgresql
  encoding: unicode
+  host: db
+  username: postgres
+  password: password
  pool: 5

development:
  <<: *default
  database: myapp_development

test:
  <<: *default
  database: myapp_test
```

データベース作成コマンド
```
docker-compose run web rails db:create
```

コンテナの起動
```
docker compose up -d
```

ブラウザでローカルホストにアクセス
```
 url: http://localhost:3000/
 ```