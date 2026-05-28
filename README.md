# laravel-docker

## 概要

laravelのdockerコンテナ環境を構築するための学習リポジトリ

## ディレクトリ

```
root
├── docker/
│   └── nginx/
├── Dockerfile
├── （Laravel のファイル）
├── docker-compose.yml
└── .env
```

## クイックスタート

1. 環境変数をコピー

    ```shell
    $ cp .env.example .env
    ```

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

7. 確認
    - [Laravel Welcome Page](http://localhost:8080)
    - [phpMyAdmin](http://localhost:8888)
    - [Mailpit](http://localhost:8025)

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
