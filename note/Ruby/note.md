# Ruby文法

## if文
if=『もし〜だったら〜』
eleif=『もし〜じゃなかったら〜』
else=『もし〜でも〜でもなかったら~』
  &&=『〜が〜かつ〜だったら』
  ||=『〜が〜または〜だったら』
例
```ruby
  number = 48

  if number % 3 == 0 && number % 5 == 0 （もし３の倍数かつ、５の倍数だったら）
    puts "15の倍数です"

  elsif number % 5 == 0 (もし５の倍数だったら)
    puts "5の倍数です"

  elsif number % 3 == 0 (もし３の倍数だったら)
    puts "3の倍数です"

  else (もし３の倍数でも５の倍数でもなかったら)
    puts "3の倍数でも5の倍数でもありません"

  end
```
結果
```ruby
  「３の倍数です」
```

## 変数
変数に複数の要素を入れて選択する（[]の中が要素）
```ruby
  names = [”仲野”,"大雅"]（仲野＝０大雅＝１）
```
[]にインデックス番号を入力して出力
```ruby
  puts "私の苗字は#{names[0]}です"
  puts "私の下の名前は#{names[1]}です"
```
結果
```ruby
  私の苗字は仲野です
  私の下の名前は大雅です
```
## ループ文

each=繰り返し
例
```ruby
  languages = ["日本語", "英語", "スペイン語"]
  border = "----------"
  languages.each do |language|
    puts border
    puts "#{language}を話せます"
  end
```

結果
```ruby
  ----------
  日本語を話せます
  ----------
  英語を話せます
  ----------
  スペイン語を話せます
```

nil=putsハッシュ[キー]でキーが存在しない場合の特別な値

eachとifを使う場合はどちらのendも必要

## 関数
def=メソッド(関数)を定義する（メソッド＝なんでもいい）
例
```ruby
  def nakano
    puts "仲野です"
    puts "大雅です"
  end

  nakano
```

結果
```ruby
  仲野です
  大雅です
```

### 引数
例
```ruby
  def nakano(name)
    puts "こんにちは私は#{name}です"
  end
  nakano("仲野大雅")
  nakano("Nakano Taiga")
```

結果
```ruby
  こんにちは私は仲野大雅です
  こんにちは私はNakanoTaigaです
```

例２
```ruby
  def nakano(name,uname)
    puts "私の苗字は#{name}です"
    puts "下の名前は#{uname}です"
  end

  nakano("仲野","大雅")
```
結果
```ruby
  私の苗字は仲野です
  下の名前は大雅です
```

return=戻り値
例
```ruby
  def discount(price)
    return price / 2
  end

  puts "テレビがセール中です！"
  half_price = discount(15000)
  puts "特別価格で#{half_price}円です"
```

結果
```ruby
  テレビがセール中です！
  特別価格で7500円です
```
例２
```ruby
  # shipping_free?メソッドを定義してください
  def shipping_free? (price)
    return price >= 5000
  end

  # if文の条件式でshipping_free?メソッドを呼び出してください
  if shipping_free?(3000)
    puts "5000円以上のお買い上げなので送料はいただきません"
  else
    puts "追加で送料をいただきます"
  end
```
結果
```ruby
  追加で送料をいただきます
```
例３
```ruby
  def price_with_shipping(price)
    # priceが5000以上のとき、戻り値としてpriceを返すif文
  if price >= 5000
    return price
  end

    # priceに500を加えた値を戻り値として返してください
    return price + 500
  end

  puts "商品の合計金額は3000円です"
  puts "お支払い金額は、送料込みで#{price_with_shipping(3000)}円です"
  puts "-----------"
  puts "商品の合計金額は10000円です"
  puts "お支払い金額は、送料込みで#{price_with_shipping(10000)}円です"
```

結果
```ruby
  商品の合計金額は3000円です
  お支払い金額は、送料込みで3500円です
  ----------
  お支払い金額は10000円です
  お支払い金額は、送料込みで10000円です
```
キーワード引数
例
```ruby
  # キーワード引数を使うように書き換えてください
  def buy(item:, price:, count:)
    puts "#{item}を#{count}台のお買い上げです"
    puts "合計金額は#{price * count}円です"
  end

  # キーワード引数を使うように書き換えてください
  buy(item:"テレビ", price:15000, count:2)
```
self=
インスタンスメソッドの中では、特殊な変数「self」を用いて「self.変数名」とすることで、インスタンス変数を扱うことができるようになります。
インスタンスメソッドでは、変数「self」に、呼び出したインスタンス自身が代入されています。

-=とは
「演算子の左側の値から右側の値を引き算して、その結果を左側に代入してね～」を意味する演算子

class継承する場合は require "./継承したいファイル名" を使う
class 子クラス < 子クラス
