## アソシエーション
  - has_many 複数形で書く
  - brlong_to 単数形で書く
  ```ruby
    belongs_to :user # tweetは一人のユーザがいる
    has_many :comments # tweetはたくさんコメントを持っている
  ```


## ルーティングのネスト


includes

before_action