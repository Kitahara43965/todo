(イ) ローカルリポジトリの設定
ローカルリポジトリを作成するディレクトリにおいてコマンドライン上で
$ git clone git@github.com:Kitahara43965/todo.git
$ mv todo (ローカルリポジトリ名)
とすればリモートリポジトリのクローンが生成され、所望のローカルリポジトリ名のディレクトリが得られます。

(ロ) dockerの設定
  ローカルリポジトリで
dockerが起動していることを確認した上で
$ docker-compose up -d --build
とします。
$ cd docker/php
$ docker-compose exec php bash
でphpコンテナ内に入り、
$ composer install
でcomposerをインストールします。

(ハ) webアプリの立ち上げ
(ハ-1) phpコンテナ上で
cp .env.example .env 
と入力し、.envファイルを複製します。
(ハ-2) .envファイル(11行目以降)では
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=laravel_db
DB_USERNAME=laravel_user
DB_PASSWORD=laravel_pass
とします。
(ハ-3) phpコンテナ上で 
php artisan key:generate
と入力します。

以上でwebアプリが起動します。



























