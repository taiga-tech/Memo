(2020/06/04)

# MySQL導入方法

## デフォルトのdbをMySQLにする
- 導入前にMySQLがインストールされているか確認する
  ```shell
    % mysql --version
    mysql  Ver 8.0.19 for osx10.15 on x86_64 (Homebrew)
  ```
  バージョンが出てきたら導入可能

<br>

- `rails new` のときにオプションをつける
  ```shell
    % rails new アプリ名 -d mysql
  ```
  アプリ名の後に`-d mysql`をつけると、デフォルトのdbがMySQLになる
<br>

- config/database.ymlファイルを編集する
  ```yaml
    default: &default
    adapter: mysql2
    encoding: utf8mb4
    pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
    username: ユーザー名
    password: パスワード
    host: ホスト名
    socket: /tmp/mysql.sock
  ```
  任意のユーザ名、パスワード、ホスト名を追記する。

## 隠したい情報を環境変数で管理する
  - 環境変数を管理できるgem(dotenv-rails)をインストールする
    - gemfileにdotenv-railsを追記する
      ```gemfile
        gem "dotenv-rails"
      ```
    - bundle installする
  - 環境変数を定義する
    - アプリ直下のルートディレクトリに.envファイルを追加する
    - .envファイルに環境変数を定義する
      ```.env
        DB_USERNAME = ユーザー名
        DB_PASSWORD = パスワード
        DB_HOST = ホスト名
      ```
  - 環境変数が正確に定義されているか確認する
    ```rails console
      irb(main):001:0> ENV["DB_USERNAME"]
      => "mysqlapp_user"
    ```
    環境変数が定義されているのを確認したら、
  - database.ymlを環境変数に変更する
    `<%= ENV["環境変数名"] %>`と変更すると`.env`で定義した情報に置き換わる。
    ```yaml
      default: &default
      adapter: mysql2
      encoding: utf8mb4
      pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
      username: <%= ENV["DB_USERNAME"] %>
      password: <%= ENV["DB_PASSWORD"] %>
      host: <%= ENV["DB_HOST"] %>
      socket: /tmp/mysql.sock
    ```
    > 環境に応じてdelelopmentとtestにも書き換える

    `<%= ENV["環境変数名"] %>`と変更すると`.env`で定義した情報に置き換わる。
  - `.env`がgithubに共有されないようにする
    このままgithubに上げてしまうと`.env`ファイルの中身が見えて重要な情報まで見えてしまうので、`.gitignore`に`/.env`を追記してgithubから見えないようにする。
