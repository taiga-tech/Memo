# Docker

- DockerTemplateを新しいディレクトリに追加する
  ```shell
    % mkdir app_name # 任意のアプリ名
    % cd app_name
  ```
  作ったディレクトリにtemplateを移動する

- `Dockerfile`と`docker-compose`のアプリ名を先ほど作ったapp_nameに変更する(計6箇所)

- rails new する
  ```shell
    % docker-compose run web rails new . --force --no-deps --database=mysql --skip-test --webpacker
  ```

- 必要であればgemを追加する
  ```Gemfile
    gem "dotenv-rails" # 環境変数.env用
  ```

- イメージをビルドする
  ```shell
    % docker-compose build
  ```

- `config/database.yml`の編集
  ```yml
    default: &default
      adapter: mysql2
      encoding: utf8
      pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
      username: <%= ENV.fetch("MYSQL_USERNAME") %>
      password: <%= ENV.fetch("MYSQL_PASSWORD") %>
      host: <%= ENV.fetch("MYSQL_HOST") %>

    development:
      <<: *default
      database: myapp_development

    test:
      <<: *default
      database: myapp_test

    production:
      <<: *default
      database: myapp_production
      username: myapp
      password: <%= ENV['MYAPP_DATABASE_PASSWORD'] %>
  ```

- 環境変数の設定
  ```.env
    MYSQL_USERNAME=root
    MYSQL_PASSWORD=password
    MYSQL_HOST=db
  ```

- db:createする
  ```shell
    % docker-compose run --rm web rails db:create
  ```
