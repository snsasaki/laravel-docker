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

## クイックスタート

1. 環境変数をコピー

    ```shell
    $ cp .env.example .env
    ```

    既に `.env` がある場合は、`.env.example` を参考に `APP_URL`、`DB_*`、`MAIL_*` の値を Docker 用に合わせてください。

2. コンテナをビルドして起動

    ```shell
    $ docker compose up -d --build
    ```

3. PHP 依存パッケージをインストール

    ```shell
    $ docker compose exec app composer install
    ```

4. アプリケーションキーを作成

    ```shell
    $ docker compose exec app php artisan key:generate
    ```

5. ファイルの権限を変更

    ```shell
    $ docker compose exec app bash -c "chmod -R 775 storage bootstrap/cache"
    ```

6. マイグレーションと初期データ投入

    ```shell
    $ docker compose exec app php artisan migrate:fresh --seed
    ```

## コマンド

- コンテナの起動

    ```shell
    $ docker compose up -d --build
    ```

- コンテナ削除

    ```shell
    $ docker compose down -v
    ```

- コンテナの起動状況確認

    ```shell
    $ docker compose ps
    ```

- ログ確認

    ```shell
    $ docker compose logs
    ```

- マイグレーション

    ```shell
    $ docker compose exec app php artisan migrate
    ```
