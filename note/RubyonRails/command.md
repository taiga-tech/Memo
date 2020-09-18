(2020/06/20)

# Rails command集
---
## **rails new アプリケーション名**
  新規アプリ作成コマンド
  アプリケーション名の後にオプションを付けることが出来る。
  - 先に「sample_app」とういう名前のフォルダを作成し、「sample_app」に移動して、`rails new .(ドット)`とすると、「sample_app」がアプリケーション名となってアプリが作成される。
    使用例
    ```shell
      ~ % mkdir sample_app
      ~ % cd sample_app
      sample_app % rails new .
      .
      .
      .
      .
      .
    ```
    ディレクトリの動き
    ```
    - home
      |- sample_app
        |- app
        |- bin
        |- config
        .
        .
        .
        .
        .
    ```
    > [railsのバージョンを指定するときに使用する可能性がある。](http://blowitech.hatenablog.jp/entry/2016/11/15/094636)

<br>

## **rails server**
  rails ローカルサーバー立ち上げコマンド
  `rails s`に省略できる
  ```shell
  # 初期値
    localhost:3000
    127.0.0.1:3000
  ```
  どちらかでアクセスできる
  - オプション
    - ポート番号を一時的に変更する
    ``` shell
      % rails s -p 5000
        # 127.0.0.1:5000
    ```
    > 初期値を変更する場合は`config/puma.rb`を編集する

    - IPアドレスを一時的に変更する
    ```shell
      % rails s -b 192.168.*.*
        # 192.168.*.*:3000
    ```
    > 同じIPに接続されている場合はスマホでもアクセスできる

<br>

## **rails console**
  rails環境上でrubyを実行するコマンド
  `rails c`に省略できる
<br>

## **rails g controller コントローラー名 アクション名・・・**
  contorllerとviewを作成するコマンド
<br>

## **rails g model テーブル名(単数形, 文頭大文字) カラム名:データ型**
  modelとマイグレーションファイルを作成するコマンド
<br>

## **rails db:migrate**
  マイグレーションファイルの設定をdbに反映させるコマンド
  > マイグレーションファイルを設定後に実行する

<br>


## **rails db:migrate:status**
  マイグレーションファイルのステータスを表示するコマンド
  ステータスが`up`の場合は、dbに反映済み
  `down`の場合は、反映前なのでマイグレーションファイルを修正できる
  >- **rails db:rollback**
  マイグレーションファイルのステータスを一つ前にする
  >- **rails db:migrate:down VERSION=マイグレーションID**
  マイグレーションIDを指定してステータスを`down`にする
  >- **rails db:migrate:reset**
  マイグレーションファイルのリセット(dbのデータが全部消える)
<br>

## rails g migration
- `rails g migration Addカラム名To追加先テーブル名 追加するカラム名:型`
- `rails g migration Removeカラム名From削除元テーブル名 削除するカラム名：型`


## **rails g scaffold モデル名 項目1:タイプ 項目2:タイプ･･･**
  ScaffoldはCRUDを自動生成するコマンド、データの管理部分によく使われる
  model, controller, viewを自動生成する、routingも自動生成のため、変更する場合は全部書き換えが必要。
  - scaffoldを削除する
    ```shell
      % rails g scaffold user neme:text mail:integer
    ```
    nameをnemeにしてしまった場合、作り直すときに削除したい場合
    ``` shell
      % rails destroy scaffold user
    ```
    と、scaffold名を指定して削除する、`status`が`up`の場合は`down`にする必要あり

## bundle update

## bundle install

## rails g devise:install

## rails g devise モデル名

## rails g devise:views

## EDITOR='code --wait' rails credentials:edit



[ルーティング](http://localhost:3000/rails/info/routes)
