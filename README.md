(イ) ローカルリポジトリの設定<br>
ローカルリポジトリを作成するディレクトリにおいてコマンドライン上で<br>
$ git clone git@github.com:Kitahara43965/todo.git<br>
$ mv todo (ローカルリポジトリ名)<br>
とすればリモートリポジトリのクローンが生成され、所望のローカルリポジトリ名のディレクトリが得られます。<br>
<br>
(ロ) dockerの設定<br>
  ローカルリポジトリで<br>
dockerが起動していることを確認した上で<br>
$ docker-compose up -d --build<br>
とします。<br>
$ cd docker/php<br>
$ docker-compose exec php bash<br>
でphpコンテナ内に入り、<br>
$ composer install<br>
でcomposerをインストールします。<br>
<br>
(ハ) webアプリの立ち上げ<br>
(ハ-1) phpコンテナ上で<br>
cp .env.example .env<br>
と入力し、.envファイルを複製します。<br>
(ハ-2) .envファイル(11行目以降)では<br>
DB_HOST=mysql<br>
DB_PORT=3306<br>
DB_DATABASE=laravel_db<br>
DB_USERNAME=laravel_user<br>
DB_PASSWORD=laravel_pass<br>
とします。<br>
(ハ-3) phpコンテナ上で<br>
php artisan key:generate<br>
と入力します。<br>
<br>
以上でwebアプリが起動します。<br>
