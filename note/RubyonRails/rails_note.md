# Ruby on Rails
---

  |コンポーネント（構成要素）|説明|備考|
  |:--|:--|:--|
  |Model（モデル）|データベースを取り扱う|データベースへの格納方法は、Modelに隠ぺいする|
  |View（ビュー）|画面表示を取り扱う<br>(トリガー)|表示方法は、Viewに隠ぺいする|
  |Controller（コントローラー）|（ユーザーの入力を受けて）ModelとViewにアレコレ指示する|データベースへの格納方法や表示方法は知らない

---
## RailsAppの準備
### 1.RailsApp自動生成
  ターミナルで`％ rails new アプリケーション名　オプション名`を実行してフレームワーク生成
  例
  > `rails new アプリケーション名　−d mysql` データベースをMySQLに変更する
---

### 2.ページ自動生成
  ターミナルで`$ rails g controller コントローラ名 アクション名`を実行して、「controller」、「viwe」、「routing」を生成

---

### 3.コントローラにページを追加する
  「routes.rb」にルート追加して、「コントローラ名_controller.rb」フォルダにアクション追加、「view」フォルダの該当ビューファイル追加

例文
  ~~~ ruby
  # config/routes.rb
  # get "URL" => "コントローラ名#アクション名" を追加する
  get "/" => "home#top"
  get "about" => "home#about"
  ~~~

  ~~~ruby
  # controllers/home_contrller.rb
  # def アクション名
  # end
  # を追加する
  def top
  end
  def about
  end
  ~~~

---

### 4.modelを作成
  `rails g model `モデル名(単数形) カラム名:データ型 ...`

  ### scafoldでCRUD機能「routing」、「controller」、「model」を自動生成できるため、手軽に管理画面などを自動生成できる
  `rails g scafold モデル名　カラム名:データ型　...`

---

## routing
---

## Controller
---

## Model
---
- バリテーション

- アソシエーション
  >- has_one
  >>
  >- has_many
  >>
  >- bolongs_to
  >>


## DB
---