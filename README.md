### ブラウザからのリクエストを受け取るのは誰か？

- nginx

### PHP（Laravel）のコードを実行するのは誰か？

- php

### データを永続化するのは誰か？

- mysql(volume)

## ディレクトリ

```
project-root/
├── docker/
│   └── nginx/         # Nginx の設定ファイル
├── Dockerfile         # PHP コンテナ用（プロジェクトルート直下）
├── （Laravel のファイル群）
├── docker-compose.yml
└── .env
```
