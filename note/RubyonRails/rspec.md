# RSpec Test
[rspecGitHub](https://github.com/rspec/rspec-rails)
## gem install
  - `rspec-rails` development test環境
    > テストをするためのgem
    ```shell
      # RSpecよう設定ファイル作成コマンド
      % rails g rspec:install
      Running via Spring preloader in process 9045
            create  .rspec
            create  spec
            create  spec/spec_helper.rb
            create  spec/rails_helper.rb
    ```

    - .rspecに追記
      ```.rspec
        --format documentation
      ```
      テストを行うappディレクトリで以下を実行する
      ```shell
        % bundle exec rspec
        NO examples found.

        Finished in 0.00031 seconds (files took 0.19956 seconds to load)
        0 examples, 0 failures
      ```
      とでればRSpec利用準備完了
  - `factory_bot_rails` development test環境
    > rspecに渡すパラメータを自動作成する感じ
  - `rails-controller-testing` development test環境
    > コントローラーをテストするgem
  - `web-console` development環境(test環境に記載すると不具合が出る可能性あり)
    > 謎すぎ
  - `faker` development test環境
    > Factorybotのvalueを自動生成するgem

    FactoryBotとFakerを組み合わせるため、`spec/rails_helper.rb`に以下を追記する
    ```ruby
      RSpec.configure do |config|
        config.include FactoryBot::Syntax::Methods
         #〜省略〜
      end
    ```

## ファイル構成
    - spec
      - rails_helper.rb
      - spec_helper.rb
    - .rspec
  > gem`rspec-rails`をinstallして`rails g rspec:install`すると上記ファイルが作成される

  ### 各テストを行う場合は下記ファイル構成にしてテストコードを記載する
  **各ファイル名は`対応するクラス名_spec.rb`にする**

    - spec
      - models
        - specfiles
      - controllers
        - specfiles
      - factories
        - specfiles
    - rails_helper.rb
    - spec_helper.rb
    - .rspec
  model, controllerを別で記載してテストを実施する


```
  とりあえず実行準備編で中身はもう少し理解して記載する
```

- controller_spec.rb
``` ruby
describe ◯◯Controller do
  describe 'HTTPメソッド名 #アクション名' do
    it "インスタンス変数は期待した値になるか？" do
      "擬似的にリクエストを行ったことにするコードを書く"
      "エクスペクテーションを書く"
    end

    it "期待するビューに遷移するか？" do
      "擬似的にリクエストを行ったことにするコードを書く"
      "エクスペクテーションを書く"
    end
  end

```


Devise
deviseをrspecで使用する準備
`/spec/support/controller_macros.rb`
```ruby
module ControllerMacros
  def login(user)
    @request.env["devise.mapping"] = Devise.mappings[:user]
    sign_in user
  end
end
```

`/spec/rails_helper.rb`
```ruby
RSpec.configure do |config|
  Dir[Rails.root.join("spec/support/**/*.rb")].each { |f| require f }
  config.include Devise::Test::ControllerHelpers, type: :controller
  config.include ControllerMacros, type: :controller
  # ~省略~
end
```



テストを記述していく上でのポイントは、以下のようになります。
- example１つにつき、結果を一つだけ期待している
- どのテストも明示的である
- 期待できる値が返ってくるときと、そうでないときを両方テストする
- FactoryBotを上手く利用して、すっきりとまとめる
- Fakerでダミーデータを作成する
- テスト内で使用する変数は、インスタンス変数として定義するのではなく、letを使用する

RSpec参考リンク
[【rspec-rails】のGitHubページ](https://github.com/rspec/rspec-rails)
RSpecを使用してテストを行うので、初めにGitHubのREADMEは読んでおきましょう。
[使えるRSpec入門・その1「RSpecの基本的な構文や便利な機能を理解する」](http://qiita.com/jnchito/items/42193d066bd61c740612#subject-%E3%82%92%E4%BD%BF%E3%81%A3%E3%81%A6%E3%83%86%E3%82%B9%E3%83%88%E5%AF%BE%E8%B1%A1%E3%81%AE%E3%82%AA%E3%83%96%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88%E3%82%921%E7%AE%87%E6%89%80%E3%81%AB%E3%81%BE%E3%81%A8%E3%82%81%E3%82%8B)
とても丁寧にRSpecの基本を説明した名記事です。量が多いので、テストを記述していて詰まったときに呼んでみると回答への緒が見つかることが多いです。
[Ruby on Rails、RSpecを使ってコントローラのテストを書いてみる](http://blog.naichilab.com/entry/2016/01/19/011514)
コントローラのテストについて詳しくまとめてあります。コントローラのテストを詳しく説明した記事は少ないので是非参考にしてください。

[FakerのGitHub](https://github.com/stympy/faker)


rails g rspec:model user
rails g rspec:job users
rails g rspec:view users
rails g rspec:helper users
rails g rspec:feature users
