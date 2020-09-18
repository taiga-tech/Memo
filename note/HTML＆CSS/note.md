# HTML&CSSnote

## レスポンシブデザイン
  - タブレット（1000pxより小さい）→@media(max-width:1000px){}
  - スマホ（670pxより小さい）→@media(max-width:670px){}

## listの隙間を埋める
  > たまにliの左右に少し隙間が開くことがあるため、下記を実行すると問題解決するが、ul全体で指定してしまうと他のlistに影響が出るためclassの指定必須
  - ulタグのfont-sizeを0pxにする
  ```html
  <!-- index.html -->
    <ul>
      <li>test1</li>
      <li>test2</li>
      <li>test3</li>
    </ul>
  ```
  ```css
  /* style.css */
    ul {
      font-size: 0;
    }
  ```
  > 他にも改行をしない方法などがあるが、cssに指定するほうが、シンプルな気がする。

## aタグの下線が消えない場合
  > aタグ全体にstyleを指定しても実行できない場合は親要素も絡めてstyleを指定すると成功確率UP
  - 成功例
  ```html
  <!-- index.html -->
    <a>テスト</a>
  ```
  ```css
  /* style.css */
    a {
      text-decoration: none;
    }
  ```
  - 失敗例
  ```html
  <!-- index.html -->
    <div>
      <a>テスト</a>
    </div>
  ```
  ```css
  /* style.css */
    a {
      text-decoration: none;
    }
  ```
  - 訂正例
  ```css
  /* style.css */
    div a {
      text-decoration: none;
    }
  ```
