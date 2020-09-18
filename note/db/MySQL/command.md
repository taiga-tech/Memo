※ MySQL8には一部対応してないので注意

[インストール方法](/MacSettings/local.md)

**mysql起動・停止**

```shell -session:shell
  % mysql.server start  # 開始
  % mysql.server status # 確認
  % mysql.server stop   # 停止
```

# MySQLモニター

## ログイン

```shell -session:shell
  # localhostのMySQLサーバに接続する場合
  % mysql -u [ユーザー名] -p

  # 外部MySQLサーバに接続する場合
  % mysql -u [ユーザー名] -p -h [host名] -P [ポート番号]
```

-p オプションはパスワード設定しているときのみ付与する

＜ プチ情報 ＞
・ログイン後はmysqlコマンドしか使えない。
・ログイン中に打つコマンドは基本的に最後に「;(セミコロン)」を入れる。

## ログアウト

いろいろとある。

```shell -session:mysql-shell
  mysql > \q
  mysql > quit
  mysql > exit
```

## ヘルプ

``` -session:mysql-shell
  mysql > help
  mysql > \h
```

# ユーザー操作(rootログイン後)

## ユーザー情報取得

```shell -session:mysql-shell
  mysql > SELECT Host, User, Password FROM mysql.user;
  +------------------+------+----------+
  | Host             | User | Password |
  +------------------+------+----------+
  | localhost        | root |          |
  | 127.0.0.1        | root |          |
  | ::1              | root |          |
  | localhost        |      |          |
  +------------------+------+----------+
  4 rows in set (0.00 sec)
```

## ユーザーの追加

ユーザー名：testuser
パスワード：password ※ MySQL8以上では
ホスト名：localhost

```shell -session:mysql-shell
  mysql > create user `testuser`@`localhost` IDENTIFIED BY 'password';
```
このままでは「testuser」はDB作成もできないので、権限を付与してあげます（次の項目）

## ユーザーにDB操作権限を付与
> root ユーザーで実行する

対象：testuser@localhost
対象のパスワード：password
操作できるDB名：test_db

```shell -session:mysql-shell
  mysql > grant all privileges on test_db.* to testuser@localhost IDENTIFIED BY 'password';
```

```shell
  mysql > GRANT [権限] ON [適用対象のデータベース].[適用対象のテーブル] TO 'ユーザ名'@'ホスト名' IDENTIFIED BY 'パスワード';
```
- 全権付与
```shell
  mysql> grant all on *.* to '[ユーザー名]'@'localhost';
```


- 権限について

|command|動作|
|---|---|
|ALL|GRANT OPTION（権限の付与）以外の全てを許可する|
|ALTER|ALTER TABLE（テーブルの変更）の使用を許可する|
|ALTER ROUTINE|ストアドルーチンの変更・削除を許可する|
|CREATE|データベースとテーブルの作成を許可する|
|CREATE ROUTINE|ストアドルーチンの作成を許可する|
|CREATE USER|ユーザの作成・変更・削除を許可する|
|DELETE|DELETE文の使用を許可する|
|DROP|DROP文の使用を許可する|
|EVENT|イベントスケジューラのイベント作成を許可する|
|INDEX|インデックスの作成と削除を許可する|
|INSERT|INSERT文の使用を許可する|
|SELECT|SELECT文の使用を許可する|
|SHOW DATABASES|SHOW DATABASEで全データベースの表示を許可する|
|SHUTDOWN|mysqladmin shutdownの使用を許可する|
|TRIGGER|トリガの作成・削除を許可する|
|UPDATE|UPDATE文の使用を許可する|
|USAGE|「権限なし」を設定する|

## ユーザーにパスワードをセットする

### ログイン中のユーザーのパスワードを設定する場合

```shell -session:mysql-shell
  mysql > set password = password('hogehoge123');
```

### 特定のユーザーのパスワードを設定する場合

ユーザー名：testuser
新パスワード：hogehoge123
ホスト名：localhost

```shell -session:mysql-shell
  mysql > set password for 'testuser'@'localhost' = password('hogehoge123');
```

## ユーザー削除
  ```shell -session:mysql-shell
  mysql> drop user 'test_user'@'localhost';
  ```


# データベース関連

## データベース一覧の表示

```shell -session:mysql-shell
  mysql > show databases;
```

## データベースの追加(test_dbを追加する場合)

```shell -session:mysql-shell
  mysql > create database test_db;
```

## データベースの選択(test_dbを選択する場合)

```shell -session:mysql-shell
  mysql > use test_db;
```

## データベースの削除
  ```shell -session:mysql-shell
    mysql > drop database test_db;
  ```

# テーブル関連

## テーブル一覧の表示

```shell -session:mysql-shell
  mysql > show tables;
```
もっと詳細が知りたければ

```shell -session:mysql-shell
  mysql > show table status;
```

## テーブルの作成

```shell -session:mysql-shell
  mysql > CREATE TABLE [テーブル名] (
    [フィールド名] [データ型] [オプション]
  ) ENGINE=[InnoDB/MyISAM] DEFAULT CHARSET=[文字コード];
```

＜ サンプル ＞

```shell -session:mysql-shell
  mysql > CREATE TABLE `m_users` (
            `id` int NOT NULL AUTO_INCREMENT PRIMARY KEY COMMENT "ID",
            `user_name` VARCHAR(100) NOT NULL COMMENT "ユーザー名",
            `mail_address` VARCHAR(200) NOT NULL COMMENT "メールアドレス",
            `password` VARCHAR(100) NOT NULL COMMENT "パスワード",
            `created` datetime DEFAULT NULL COMMENT "登録日",
            `modified` datetime DEFAULT NULL COMMENT "更新日"
          ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

括弧以降は書かなくてもおｋ。
MySQLの設定ファイルできちんと設定できれいれば、
設定された値（もしくはデフォルト値）がセットされるので。

## テーブルの削除

```shell -session:mysql-shell
  mysql > DROP TABLE [テーブル名]
```

## テーブル名の変更
```shell -session:mysql-shell
  mysql > ALTER TABLE [旧テーブル名] RENAME [新テーブル名]
```

## テーブルにカラムの追加
```shell -session:mysql-shell
  mysql > ALTER TABLE [テーブル名] ADD [追加カラム名] [型] [必要であればオプション等];

  # 例(動作確認してないのであやふやですがこんな感じ)
  #  users に tel という int型のカラム を デフォルトNULL で定義し、コメントには 電話番号 といれておき、 mail_addressカラムの後ろ に追加する
  mysql > ALTER TABLE users ADD tel int DEFAULT NULL COMMENT "電話番号"  AFTER mail_address
```

## テーブル設計の確認

```shell -session:mysql-shell
  mysql > desc [テーブル名]
  +------------------+--------------+------+-----+---------+----------------+
  | Field            | Type         | Null | Key | Default | Extra          |
  +------------------+--------------+------+-----+---------+----------------+
  | id               | int(11)      | NO   | PRI | NULL    | auto_increment |
  | user_name        | varchar(100) | NO   |     | NULL    |                |
  | mail_address     | varchar(200) | NO   |     | NULL    |                |
  | password         | varchar(100) | NO   |     | NULL    |                |
  | created          | datetime     | YES  |     | NULL    |                |
  | modified         | datetime     | YES  |     | NULL    |                |
  +------------------+--------------+------+-----+---------+----------------+
```

もっと詳細が知りたければ

```shell -session:mysql-shell
  mysql > SHOW FULL COLUMNS FROM [テーブル名];
  +------------------+--------------+-----------------+------+-----+---------+----------------+---------------------------------+----------------+
  | Field            | Type         | Collation       | Null | Key | Default | Extra          | Privileges                      | Comment        |
  +------------------+--------------+-----------------+------+-----+---------+----------------+---------------------------------+----------------+
  | id               | int(11)      | NULL            | NO   | PRI | NULL    | auto_increment | select,insert,update,references | ID             |
  | user_name        | varchar(100) | utf8_general_ci | NO   |     | NULL    |                | select,insert,update,references | ユーザー名     |
  | mail_address     | varchar(200) | utf8_general_ci | NO   |     | NULL    |                | select,insert,update,references | メールアドレス |
  | password         | varchar(100) | utf8_general_ci | NO   |     | NULL    |                | select,insert,update,references | パスワード     |
  | created          | datetime     | NULL            | YES  |     | NULL    |                | select,insert,update,references | 登録日         |
  | modified         | datetime     | NULL            | YES  |     | NULL    |                | select,insert,update,references | 更新日         |
  +------------------+--------------+-----------------+------+-----+---------+----------------+---------------------------------+----------------+
```

# レコード操作関連

## 追加

```shell -session:mysql-shell
  mysql > INSERT INTO [テーブル名] [フィールド名] VALUES [値]
```

＜サンプル＞

```shell -session:mysql-shell
  mysql > INSERT INTO m_users (user_name, mail_address, password, created, modified)
            VALUES ("Qii Taro", "qiitaro@hoge.com", "123123", now(), now())
```

**now()** ・・・ 現在の日時が入力される関数

## 更新

```shell -session:mysql-shell
  mysql > UPDATE [テーブル名] SET [フィールド名]=[値] [条件式]
```

＜サンプル＞

```shell -session:mysql-shell
  mysql > UPDATE m_users SET user_name="Qii Takao", mail_address="qiitakao@hoge.com" WHERE id = 5;
```

- 条件式が無しだと、対象が全レコードになります。
- カンマ区切りで複数フィールド更新できます。


## 削除

### 全レコード削除

```shell -session:mysql-shell
  mysql > DELETE FROM [テーブル名]
```

### 一部レコード削除

```shell -session:mysql-shell
  mysql > DELETE FROM [テーブル名] WHERE [条件式]
```

＜サンプル＞

```shell -session:mysql-shell
  mysql > DELETE FROM m_users WHERE id > 5 AND del_flg = 1;
```

# トランザクション

デフォルトではクエリの実行が即座にコミット（反映）されるようになっています。
ただ、システム運用をしている上でクエリを実行する必要が出てくるシーンに遭遇することもあると思います。

トランザクションの機能を活用すると、実際にUPDATEなどのクエリを実行してSELECTで結果を確認したあとに、
　意図通りに変更できていれば、反映
　意図通りに変更できてなければ、反映させない
ということができます。

トランザクションはCOMMIT/ROLLBACKをすると終了します。

< 例 >

```shell -session:mysql-shell
  mysql > START TRANSACTION;
  mysql > UPDATE m_users SET user_name="Huga Hogeo", mail_address="huga@hoge.com" WHERE id = 5;
  mysql > UPDATE m_users SET user_name="Hoge Hugao", mail_address="hoge@huga.com" WHERE id = 6;
  mysql > SELECT * FROM m_users WHERE id IN(5,6);
  # ここで状態確認をしたりする
  mysql > COMMIT;
```

詳しくはこちら https://dev.mysql.com/doc/refman/5.6/ja/commit.html
`START TRANSACTION;`: トランザクションの開始
`COMMIT;`: コミット

## トランザクションの開始
```shell -session:mysql-shell
  mysql > START TRANSACTION;
```

## コミット
```shell -session:mysql-shell
  mysql > COMMIT;
```

## ロールバック
```shell -session:mysql-shell
  mysql > ROLLBACK;
```

# データベースのダンプ

## ダンプをとる

### 全データベースを対象とする


```shell -session:shell
  % mysqldump -u [ユーザー名] -p -x --all-databases > [出力ファイル名]
```

### test_dbデータベースを対象とする

```shell -session:shell
  % mysqldump -u [ユーザー名] -p -x test_db > [出力ファイル名]
```

### test_dbデータベースのusersテーブルを対象とする

```shell -session:shell
  % mysqldump -u [ユーザー名] -p -x test_db users > [出力ファイル名]
```

### test_dbデータベースのusersテーブルのデータ内でidが５未満を対象とする

```shell -session:shell
  % mysqldump -u [ユーザー名] -p -x test_db users --where="id < 5" > [出力ファイル名]
```

### 出力ファイル名について

　拡張子は何でもよかったと思います。
　自分は「***.dump」とかにします。

## リストア

```shell -session:shell
  % mysql -u[ユーザー名] -p new_db < [ダンプファイル名]
```

# その他

## 見え方の変更

### ＠ promptコマンドで「mysql > ....」という形をカスタムする

デフォルトで `mysql>` という形だが、カスタマイズできるらしい。
ほぉ。
[サイト](http://nippondanji.blogspot.jp/2009/03/mysql.html)を参考に書いてみました。

```shell -session:mysql-shell
  mysql> \R \d(\U) >\_
  PROMPT set to '\d(\U) >\_'
  test_db(root@localhost) >
```

・『/d』⇒ 利用中のデータベース名
・『/U』⇒ ユーザー名@ホスト名

### ＠ pagerコマンドでクエリの結果を見やすくする　～pager less～

pagerというコマンドが便利だとの情報をコメントからいただきましたので、
pager less をさっそく使ってみました。（[tukiyo3さん](http://qiita.com/CyberMergina/items/f889519e6be19c46f5f4#comment-4b0c4e80922e5e6863c2)ありがとうございます！）

```shell -session:mysql-shell
  mysql> pager less -S
  PAGER set to 'less -S'
  mysql>
```

この状態で横になが～くなってしまう、テーブル詳細を表示すると
ビューアーが立ち上がり、結果が表示されました！
結果が折り返されず左右矢印キーで操作できます。
ビューアーの終了はqキー、
lessの設定を終わるときは `nopager` というコマンドで元に戻ります。

[参考記事](http://qiita.com/nao58/items/f651d9f2d0f420f87a50)の方にlessの他のオプションも書かれております。

## SQL実行結果をファイルに出力

```shell -session:shell
  % mysql -uroot -p -e "select * from users" test_db > /tmp/mysql.txt
```

参考サイト：[MySQLの出力結果をファイルにはきだしたいとき](http://d.hatena.ne.jp/fukumura/20110223/1298460946)


## RailsAppのdbをmysqlにする時のエラー解消方
  ```shell
    bundle config --local build.mysql2 "--with-ldflags=-L/usr/local/opt/openssl/lib" # こっちしたけどならんかった
    bundle config --local build.mysql2 "--with-ldflags=-L/usr/local/opt/openssl/lib --with-cppflags=-I/usr/local/opt/openssl/include" # こっちは問題ない
  ```



`CLEARDB_DATABASE_URL => mysql://[username]:[password]@[host]/[database name]?reconnect=true`
