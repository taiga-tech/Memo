(2020/05/29)

# 開発環境構築
  環境
  MacBookPro 16inch 2019

  **初期Version**
  |content|version|
  |---|---|
  |MacOS|Catalina 10.15.5|
  |xcode command line tools|null|
  |homebrew|nill|
  |git|2.24.3|
  |rbenv|null|
  |ruby-build|null|
  |Ruby|2.6.3|
  |Ruby on Rails|null|
  |node|null|
  |yarn|null|
  |MySQL|null|

  **現在Version** (2020/05/29更新)
  |content|version|
  |---|---|
  |MacOS|Catalina 10.15.5|
  |xcode command line tools|unknown|
  |homebrew|2.2.17|
  |git|2.26.2|
  |rbenv|1.1.2|
  |ruby-build|20200520|
  |Ruby|2.6.3|
  |Ruby on Rails|6.0.3.1|
  |node|14.3.0|
  |npm|6.14.5|
  |yarn|1.22.4|
  |MySQL|8.0.19|

## homebrew install
  > まず初めに homebrew [macOS用 パッケージマネージャー] をインストールする
  > homebrewは、macOSでのパッケージインストールを簡単にするパッケージ管理システムです。
  > これより下は、homebrewをインストールした前提です。
---

  - バージョン確認
    ```shell
    # 未インストールの場合
      ~ % brew -v
      brew: command not found # 「見つからない」と出る

    # インストール済の場合
      ~ % brew -v
      Homebrew 2.2.17 # バージョンが出る
      Homebrew/homebrew-core (git revision 902c3; last commit 2020-05-27)
    ```
    homebrewが未インストールの場合は下のコマンドを実行する。
    <br>
  - インストールコマンド
    ```shell
      ~ % /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
      ==> This script will install:
      /usr/local/bin/brew
      /usr/local/share/doc/homebrew
      /usr/local/share/man/man1/brew.1
      /usr/local/share/zsh/site-functions/_brew
      /usr/local/etc/bash_completion.d/brew
      /usr/local/Homebrew
      ==> The following new directories will be created:
      /usr/local/bin
      /usr/local/etc
      /usr/local/include
      /usr/local/lib
      /usr/local/sbin
      /usr/local/share
      /usr/local/var
      /usr/local/opt
      /usr/local/share/zsh
      /usr/local/share/zsh/site-functions
      /usr/local/var/homebrew
      /usr/local/var/homebrew/linked
      /usr/local/Cellar
      /usr/local/Caskroom
      /usr/local/Homebrew
      /usr/local/Frameworks

      Press RETURN to continue or any other key to abort
      # [ここでreturnキーを押す]
      Password:
      # [ここでPCログイン時のパスワードを入力]
      ==> /usr/bin/sudo /bin/mkdir -p /usr/local/bin /usr/local/etc /usr/local/include /usr/local/lib /usr/local/sbin /usr/local/share /usr/local/var /usr/local/opt /usr/local/share/zsh /usr/local/share/zsh/site-functions /usr/local/var/homebrew /usr/local/var/homebrew/linked /usr/local/Cellar /usr/local/Caskroom /usr/local/Homebrew /usr/local/Frameworks
      ==> /usr/bin/sudo /bin/chmod g+rwx /usr/local/bin /usr/local/etc /usr/local/include /usr/local/lib /usr/local/sbin /usr/local/share /usr/local/var /usr/local/opt /usr/local/share/zsh /usr/local/share/zsh/site-functions /usr/local/var/homebrew /usr/local/var/homebrew/linked /usr/local/Cellar /usr/local/Caskroom /usr/local/Homebrew /usr/local/Frameworks
      ==> /usr/bin/sudo /usr/sbin/chown Taiga /usr/local/bin /usr/local/etc /usr/local/include /usr/local/lib /usr/local/sbin /usr/local/share /usr/local/var /usr/local/opt /usr/local/share/zsh /usr/local/share/zsh/site-functions /usr/local/var/homebrew /usr/local/var/homebrew/linked /usr/local/Cellar /usr/local/Caskroom /usr/local/Homebrew /usr/local/Frameworks
      ==> /usr/bin/sudo /usr/bin/chgrp admin /usr/local/bin /usr/local/etc /usr/local/include /usr/local/lib /usr/local/sbin /usr/local/share /usr/local/var /usr/local/opt /usr/local/share/zsh /usr/local/share/zsh/site-functions /usr/local/var/homebrew /usr/local/var/homebrew/linked /usr/local/Cellar /usr/local/Caskroom /usr/local/Homebrew /usr/local/Frameworks
      ==> /usr/bin/sudo /bin/mkdir -p /Users/Taiga/Library/Caches/Homebrew
      ==> /usr/bin/sudo /bin/chmod g+rwx /Users/Taiga/Library/Caches/Homebrew
      ==> /usr/bin/sudo /usr/sbin/chown Taiga /Users/Taiga/Library/Caches/Homebrew
      ==> Downloading and installing Homebrew...
      remote: Enumerating objects: 87, done.
      remote: Counting objects: 100% (87/87), done.
      remote: Compressing objects: 100% (78/78), done.
      remote: Total 137458 (delta 18), reused 62 (delta 9), pack-reused 137371
      Receiving objects: 100% (137458/137458), 33.34 MiB | 13.42 MiB/s, done.
      Resolving deltas: 100% (101047/101047), done.
      From https://github.com/Homebrew/brew
      * [new branch]      master     -> origin/master
      * [new tag]             0.1        -> 0.1
      * [new tag]             0.2        -> 0.2
      * [new tag]             0.3        -> 0.3
      .
      .
      略
      .
      .
      * [new tag]             2.2.7      -> 2.2.7
      * [new tag]             2.2.8      -> 2.2.8
      * [new tag]             2.2.9      -> 2.2.9
      HEAD is now at 43ae03d6e Merge pull request #7657 from SMillerDev/fix/artifact_in_pr
      ==> Homebrew is run entirely by unpaid volunteers. Please consider donating:
        https://github.com/Homebrew/brew#donations
      ==> Tapping homebrew/core
      Cloning into '/usr/local/Homebrew/Library/Taps/homebrew/homebrew-core'...
      remote: Enumerating objects: 137, done.
      remote: Counting objects: 100% (137/137), done.
      remote: Compressing objects: 100% (90/90), done.
      remote: Total 725972 (delta 82), reused 86 (delta 47), pack-reused 725835
      Receiving objects: 100% (725972/725972), 294.39 MiB | 14.15 MiB/s, done.
      Resolving deltas: 100% (479443/479443), done.
      Tapped 2 commands and 5028 formulae (5,297 files, 322.6MB).
      Already up-to-date.
      ==> Installation successful!

      ==> Homebrew has enabled anonymous aggregate formulae and cask analytics.
      Read the analytics documentation (and how to opt-out) here:
        https://docs.brew.sh/Analytics
      No analytics data has been sent yet (or will be during this `install` run).

      ==> Homebrew is run entirely by unpaid volunteers. Please consider donating:
        https://github.com/Homebrew/brew#donations

      ==> Next steps:
      - Run `brew help` to get started
      - Further documentation:
          https://docs.brew.sh
    ```
    途中でEnterや、パスワードを求められるため、指示通りに入力するとインストールが完了する。
    バージョン確認をしてインストールが正常に行われたか確認する。
  -  PATH設定必要かも
  - 色んなコマンドがある=>[homebrew command集](./Terminal/command.md)
<br>

## Git install
---
  - バージョン確認
    ```shell
      # 未インストールの場合
      ~ % git --version
      zsh: command not found
      # command line toolsをインストールするよう、勧められる

      # インストール済の場合
      ~ % git --version
      git version 2.26.2 # 現在のバージョンが出る
    ```

  - Gitの最新版をインストールするコマンド
    ```shell
      ~ % brew install git
      ==> Downloading https://homebrew.bintray.com/bottles/gettext-0.20.2_1.catalina.bottle.tar.gz
      ==> Downloading from https://akamai.bintray.com/71/71f4ded03e8258b5e6896eebb00d26ed48307fbebece1a884b17ca3fb40e3121?__gda__=exp=1590690028~hmac=29093df03feab863dc7051d44ac4f43e2d91eb15038fff37828a159b7ef5f935&response-con
      ######################################################################## 100.0%
      ==> Downloading https://homebrew.bintray.com/bottles/pcre2-10.35.catalina.bottle.tar.gz
      ==> Downloading from https://akamai.bintray.com/6a/6a1e59a5db23d684f92d2bf695601d1b466f3e9d5407f704ba4679d885d13cef?__gda__=exp=1590690029~hmac=81144bb218aebbe59137b2f4d06cc560162525d5d68abf6bbc08cf13c7fa2b17&response-con
      ######################################################################## 100.0%
      ==> Downloading https://homebrew.bintray.com/bottles/git-2.26.2_1.catalina.bottle.tar.gz
      ==> Downloading from https://akamai.bintray.com/87/8796a6c37723ae33d22fe5bfc249b9135b309c87ec2b41e6025d726df1a2dee6?__gda__=exp=1590690030~hmac=c78051a3a88ed560501d044e8d899ca0519dc16b5f921f663d0c2d5fff6fda51&response-con
      ######################################################################## 100.0%
      ==> Installing dependencies for git: gettext and pcre2
      ==> Installing git dependency: gettext
      ==> Pouring gettext-0.20.2_1.catalina.bottle.tar.gz
      🍺  /usr/local/Cellar/gettext/0.20.2_1: 1,923 files, 18.6MB
      ==> Installing git dependency: pcre2
      ==> Pouring pcre2-10.35.catalina.bottle.tar.gz
      🍺  /usr/local/Cellar/pcre2/10.35: 230 files, 6.0MB
      ==> Installing git
      ==> Pouring git-2.26.2_1.catalina.bottle.tar.gz
      ==> Caveats
      The Tcl/Tk GUIs (e.g. gitk, git-gui) are now in the `git-gui` formula.

      Bash completion has been installed to:
        /usr/local/etc/bash_completion.d

      zsh completions and functions have been installed to:
        /usr/local/share/zsh/site-functions

      Emacs Lisp files have been installed to:
        /usr/local/share/emacs/site-lisp/git
      ==> Summary
      🍺  /usr/local/Cellar/git/2.26.2_1: 1,471 files, 46.4MB
      ==> Caveats
      ==> git
      The Tcl/Tk GUIs (e.g. gitk, git-gui) are now in the `git-gui` formula.

      Bash completion has been installed to:
        /usr/local/etc/bash_completion.d

      zsh completions and functions have been installed to:
        /usr/local/share/zsh/site-functions

      Emacs Lisp files have been installed to:
        /usr/local/share/emacs/site-lisp/git
    ```

  - バージョン確認をして最新バージョンがインストールされているか確認して、最新バージョンが表示されていたらインストール完了
  - 最新バージョンではない場合は、パスが、初期状態でインストールされたのパスになっているため、homebrewでインストールしたgitのパスを通す。
    - 現在のgitのパスを確認する
      ```shell
        ~ % which git
        /usr/bin/git # 初期状態でインストールされたgitパス

        ~ % which git
        /usr/local/bin/git # homebrewでインストールしたgitパスを通した後
      ```
    - .zshrcにパスを追記する
      ```shell
        # .zshrc
          # export PATH=$PATH"通したいPATH":$PATH
          export "PATH=/usr/local/Cellar/git/2.26.2/bin":$PATH # homebrewのパスを追記
      ```
    - バージョン確認をして、最新バージョンになって入れば完了。
<br>


## Ruby install
---
  - バージョン確認
    ```shell
      ~ % ruby -v # 初期状態の場合
      ruby 2.6.3p62 (2019-04-16 revision 67580) [universal.x86_64-darwin19]

      ~ % ruby -v # インストール済の場合
      ruby 2.7.1p83 (2020-03-31 revision a0c7c23c9c) [x86_64-darwin19] # バージョンが表示される。
    ```
    バージョンが表示されていれば、Rubyを使用することは可能だが、
    今後バージョンを複数使用することが予想されるため、「rbenv」を使用してRubyをインストールする。
<br>

  - **rbenvとruby-buildのインストール**
    > Rubyのバージョンを簡単に切り替えることができるパッケージ。

    - homebrewインストール後に、rbenv, ruby-buildのバージョン確認をする。
      ```shell
      # 未インストールの場合
        ~ % rbenv -v
        rbenv: command not found: rbenv # 「見つからない」と出る
        ~ % ruby-build --version
        ruby-build: command not found: ruby-build # 多分「見つからない」と出る

      # インストール済の場合
        ~ % rbenv -v
        rbenv 1.1.2 # バージョンが出る
        ~ % ruby-build --version
        ruby-build 20200520 # バージョンが出る
      ```

    - rbenvとruby-buildのインストールコマンド

      ```shell
        ~ % brew install rbenv ruby-build
        Updated 1 tap (homebrew/core).
        ==> Updated Formulae
        when

        ==> Downloading https://homebrew.bintray.com/bottles/autoconf-2.69.catalina.bottle.4.tar.gz
        ==> Downloading from https://akamai.bintray.com/ca/ca510b350e941fb9395522a03f9d2fb5df276085d806ceead763acb95889a368?__gda__=exp=1590693825~hmac=2abc4b880276f9e7c6ee18541282a5ac8627a13c9f59f633e3d8e084f5f82f93&response-con
        ######################################################################## 100.0%
        ==> Downloading https://homebrew.bintray.com/bottles/pkg-config-0.29.2_3.catalina.bottle.tar.gz
        ==> Downloading from https://akamai.bintray.com/80/80f141e695f73bd058fd82e9f539dc67471666ff6800c5e280b5af7d3050f435?__gda__=exp=1590693827~hmac=4cbba2400e8c2b5b6d755b29610bf7cd03c56d4832cc1429ca75cd9e1af99edc&response-con
        ######################################################################## 100.0%
        ==> Downloading https://homebrew.bintray.com/bottles/readline-8.0.4.catalina.bottle.tar.gz
        ==> Downloading from https://akamai.bintray.com/6a/6ae1c8e7c783f32bd22c6085caa4d838fed7fb386da7e40ca47b87ec9b1237d6?__gda__=exp=1590693828~hmac=facde2e5bb2ba9cda09bc50b36d91c02821770f4f8c36c594302e91fa04ead44&response-con
        ######################################################################## 100.0%
        ==> Downloading https://github.com/rbenv/ruby-build/archive/v20200520.tar.gz
        ==> Downloading from https://codeload.github.com/rbenv/ruby-build/tar.gz/v20200520
        ######################################################################## 100.0%
        ==> Downloading https://homebrew.bintray.com/bottles/rbenv-1.1.2.catalina.bottle.tar.gz
        ######################################################################## 100.0%
        ==> Installing dependencies for rbenv: autoconf, pkg-config, readline and ruby-build
        ==> Installing rbenv dependency: autoconf
        ==> Pouring autoconf-2.69.catalina.bottle.4.tar.gz
        🍺  /usr/local/Cellar/autoconf/2.69: 67 files, 3.0MB
        ==> Installing rbenv dependency: pkg-config
        ==> Pouring pkg-config-0.29.2_3.catalina.bottle.tar.gz
        🍺  /usr/local/Cellar/pkg-config/0.29.2_3: 11 files, 623.7KB
        ==> Installing rbenv dependency: readline
        ==> Pouring readline-8.0.4.catalina.bottle.tar.gz
        ==> Caveats
        readline is keg-only, which means it was not symlinked into /usr/local,
        because macOS provides BSD libedit.

        For compilers to find readline you may need to set:
          export LDFLAGS="-L/usr/local/opt/readline/lib"
          export CPPFLAGS="-I/usr/local/opt/readline/include"

        For pkg-config to find readline you may need to set:
          export PKG_CONFIG_PATH="/usr/local/opt/readline/lib/pkgconfig"

        ==> Summary
        🍺  /usr/local/Cellar/readline/8.0.4: 48 files, 1.5MB
        ==> Installing rbenv dependency: ruby-build
        ==> ./install.sh
        ==> Caveats
        ruby-build installs a non-Homebrew OpenSSL for each Ruby version installed and these are never upgraded.

        To link Rubies to Homebrews OpenSSL 1.1 (which is upgraded) add the following
        to your ~/.zshrc:
          export RUBY_CONFIGURE_OPTS="--with-openssl-dir=$(brew --prefix openssl@1.1)"

        Note: this may interfere with building old versions of Ruby (e.g <2.4) that use
        OpenSSL <1.1.
        ==> Summary
        🍺  /usr/local/Cellar/ruby-build/20200520: 497 files, 248.0KB, built in 2 seconds
        ==> Installing rbenv
        ==> Pouring rbenv-1.1.2.catalina.bottle.tar.gz
        🍺  /usr/local/Cellar/rbenv/1.1.2: 36 files, 69KB
        ==> Downloading https://github.com/rbenv/ruby-build/archive/v20200520.tar.gz
        Already downloaded: /Users/Taiga/Library/Caches/Homebrew/downloads/c01341f0263e1b05dab215f6dd08d54966fab1133384d6cbca34f867802f5fb8--ruby-build-20200520.tar.gz
        ==> Caveats
        ==> readline
        readline is keg-only, which means it was not symlinked into /usr/local,
        because macOS provides BSD libedit.

        For compilers to find readline you may need to set:
          export LDFLAGS="-L/usr/local/opt/readline/lib"
          export CPPFLAGS="-I/usr/local/opt/readline/include"

        For pkg-config to find readline you may need to set:
          export PKG_CONFIG_PATH="/usr/local/opt/readline/lib/pkgconfig"

        ==> ruby-build
        ruby-build installs a non-Homebrew OpenSSL for each Ruby version installed and these are never upgraded.

        To link Rubies to Homebrews OpenSSL 1.1 (which is upgraded) add the following
        to your ~/.zshrc:
          export RUBY_CONFIGURE_OPTS="--with-openssl-dir=$(brew --prefix openssl@1.1)"

        Note: this may interfere with building old versions of Ruby (e.g <2.4) that use
        OpenSSL <1.1.
      ```

    - バージョン適応ファイル？を作るコマンドを.zshrcに追加する。
      ```shell
        eval "$(rbenv init -)"
      ```

    - バージョン確認をして最新バージョンがインストールされているか確認する。
    <br>
    - 現在インストール出来るバージョンを確認するコマンド
      ```shell
        ~ % rbenv install -l
        2.5.8
        2.6.6
        2.7.1 # 今回はこれをインストールする
        jruby-9.2.11.1
        maglev-1.0.0
        mruby-2.1.0
        rbx-4.15
        truffleruby-20.1.0

        Only latest stable releases for each Ruby implementation are shown.
        Use 'rbenv install --list-all' to show all local versions.
      ```
      このリストの中から欲しいバージョンを選ぶ

      > ※欲しいバージョンがない場合はrbenvのバージョンが古い可能性があるため、
      > ` ~ % brew upgrade rbenv ruby-build`を実行してアップグレードする。

    - 指定のバージョンをインストールする。
      ```shell
        ~ % rbenv install 2.7.1 # バージョンを指定してインストールする。
        Downloading openssl-1.1.1g.tar.gz...
        -> https://dqw8nmjcqpjn7.cloudfront.net/ddb04774f1e32f0c49751e21b67216ac87852ceb056b75209af2443400636d46
        Installing openssl-1.1.1g...
        Installed openssl-1.1.1g to /Users/Taiga/.rbenv/versions/2.7.1

        Downloading ruby-2.7.1.tar.bz2...
        -> https://cache.ruby-lang.org/pub/ruby/2.7/ruby-2.7.1.tar.bz2
        Installing ruby-2.7.1...
        ruby-build: using readline from homebrew
        Installed ruby-2.7.1 to /Users/Taiga/.rbenv/versions/2.7.1
      ```

    - 指定したバージョンがインストールされているか確認する
      ```shell
        ~ % rbenv versions
        * system (set by /Users/Taiga/.rbenv/version)
          2.7.1
      ```

    - 現在は指定したバージョンをインストールしただけなので、globalのバージョンを変更する。
      ```shell
        ~ % rbenv global 2.7.1
      ```

    - globalの変更後にRubyのバージョン確認をして、変更したバージョンが表示されていれば正常にインストール完了。

<br>

## Ruby on Rails install
---
  - バージョン確認
    ```shell
    # 未インストールの場合
      ~ % rails -v
      Rails is not currently installed on this system. To get the latest version, simply type:

          $ sudo gem install rails

      You can then rerun your "rails" command.

    # インストール済の場合
      ~ % rails -v
      Rails 6.0.3.1 # バージョンが表示される
    ```

  - 最新バージョンインストール
    ```shell
      ~ % gem install rails
      Fetching concurrent-ruby-1.1.6.gem
      Fetching i18n-1.8.2.gem
      Fetching thread_safe-0.3.6.gem
      .
      .
      .
      略
      .
      .
      .
      Fetching sprockets-4.0.0.gem
      Fetching sprockets-rails-3.2.1.gem
      Successfully installed concurrent-ruby-1.1.6

      HEADS UP! i18n 1.1 changed fallbacks to exclude default locale.
      But that may break your application.

      If you are upgrading your Rails application from an older version of Rails:

      Please check your Rails app for 'config.i18n.fallbacks = true'.
      If youre using I18n (>= 1.1.0) and Rails (< 5.2.2), this should be
      'config.i18n.fallbacks = [I18n.default_locale]'.
      If not, fallbacks will be broken in your app by I18n 1.1.x.

      If you are starting a NEW Rails application, you can ignore this notice.

      For more info see:
      https://github.com/svenfuchs/i18n/releases/tag/v1.1.0

      Successfully installed i18n-1.8.2
      Successfully installed thread_safe-0.3.6
      Successfully installed tzinfo-1.2.7
      .
      .
      .
      略
      .
      .
      .
      Parsing documentation for sprockets-rails-3.2.1
      Installing ri documentation for sprockets-rails-3.2.1
      Parsing documentation for rails-6.0.3.1
      Installing ri documentation for rails-6.0.3.1
      Done installing documentation for concurrent-ruby, i18n, thread_safe, tzinfo, zeitwerk, activesupport, rack, rack-test, mini_portile2, nokogiri, crass, loofah, rails-html-sanitizer, rails-dom-testing, builder, erubi, actionview, actionpack, activemodel, activerecord, globalid, activejob, mini_mime, mail, actionmailer, nio4r, websocket-extensions, websocket-driver, actioncable, mimemagic, marcel, activestorage, actionmailbox, actiontext, thor, method_source, railties, sprockets, sprockets-rails, rails after 31 seconds
      40 gems installed
    ```
  <!-- - 指定のバージョンをインストールするコマンド
    ```shell
      gem install -v 6.0.3.1 rails
    ``` -->
  - バージョン確認をして、最新のバージョンが表示されていたらインストール成功

  - バージョンを変更する方法
    > 作成中


### Node.js install
  > Ruby on Rails 6 からwebpackが必要になり、webpackのインストールにはnodeが必要。
---
  - バージョン確認
    ```shell
    # 未インストールの場合
      ~ % node -v
      zsh: command not found: node # 見つからない

    # インストール済の場合
      ~ % node -v
      v14.3.0 # バージョンが表示される
    ```

  - 最新バージョンインストールコマンド
    ```shell
      ~ % brew install node
      ==> Downloading https://homebrew.bintray.com/bottles/icu4c-66.1.catalina.bottle.
      ==> Downloading from https://akamai.bintray.com/f0/f01dbe4266d1180c1da01d973200e
      ######################################################################## 100.0%
      ==> Downloading https://homebrew.bintray.com/bottles/node-14.3.0.catalina.bottle
      ==> Downloading from https://akamai.bintray.com/e3/e34c4c25365bc0f5cc245d791dd93
      ######################################################################## 100.0%
      ==> Installing dependencies for node: icu4c
      ==> Installing node dependency: icu4c
      ==> Pouring icu4c-66.1.catalina.bottle.tar.gz
      ==> Caveats
      icu4c is keg-only, which means it was not symlinked into /usr/local,
      because macOS provides libicucore.dylib (but nothing else).

      If you need to have icu4c first in your PATH run:
        echo 'export PATH="/usr/local/opt/icu4c/bin:$PATH"' >> ~/.zshrc
        echo 'export PATH="/usr/local/opt/icu4c/sbin:$PATH"' >> ~/.zshrc

      For compilers to find icu4c you may need to set:
        export LDFLAGS="-L/usr/local/opt/icu4c/lib"
        export CPPFLAGS="-I/usr/local/opt/icu4c/include"

      For pkg-config to find icu4c you may need to set:
        export PKG_CONFIG_PATH="/usr/local/opt/icu4c/lib/pkgconfig"

      ==> Summary
      🍺  /usr/local/Cellar/icu4c/66.1: 258 files, 70.4MB
      ==> Installing node
      ==> Pouring node-14.3.0.catalina.bottle.tar.gz
      ==> Caveats
      Bash completion has been installed to:
        /usr/local/etc/bash_completion.d
      ==> Summary
      🍺  /usr/local/Cellar/node/14.3.0: 4,659 files, 60.8MB
      ==> Caveats
      ==> icu4c
      icu4c is keg-only, which means it was not symlinked into /usr/local,
      because macOS provides libicucore.dylib (but nothing else).

      If you need to have icu4c first in your PATH run:
        echo 'export PATH="/usr/local/opt/icu4c/bin:$PATH"' >> ~/.zshrc
        echo 'export PATH="/usr/local/opt/icu4c/sbin:$PATH"' >> ~/.zshrc

      For compilers to find icu4c you may need to set:
        export LDFLAGS="-L/usr/local/opt/icu4c/lib"
        export CPPFLAGS="-I/usr/local/opt/icu4c/include"

      For pkg-config to find icu4c you may need to set:
        export PKG_CONFIG_PATH="/usr/local/opt/icu4c/lib/pkgconfig"

      ==> node
      Bash completion has been installed to:
        /usr/local/etc/bash_completion.d
    ```

  - バージョン確認して最新のバージョンが表示されたら正常にインストール完了

### yarn install
> nodeのパッケージマネージャ
---
  - バージョン確認
    ```shell
      ~ % yarn -v
      zsh: command not found: yarn
      ~ % yarn -v
      1.22.4
    ```

  - 最新バージョンのインストールコマンド
    ```shell
      ~ % brew install yarn
      ==> Downloading https://yarnpkg.com/downloads/1.22.4/yarn-v1.22.4.tar.gz
      ==> Downloading from https://github-production-release-asset-2e65be.s3.amazonaws
      ######################################################################## 100.0%
      🍺  /usr/local/Cellar/yarn/1.22.4: 14 files, 5MB, built in 1 second
    ```


### workpack install
> 一度インストールすると次からは勝手にwebackの作成コマンドが実行される。
---
  - webpackをインストールするような案内が出たら下記コマンドでインストールする。
    ```shell
      ~ % rails webpack:install
            create  config/webpacker.yml
      Copying webpack core config
            create  config/webpack
            create  config/webpack/development.js
            create  config/webpack/environment.js
            create  config/webpack/production.js
            create  config/webpack/test.js
      Copying postcss.config.js to app root directory
            create  postcss.config.js
      Copying babel.config.js to app root directory
            create  babel.config.js
      Copying .browserslistrc to app root directory
            create  .browserslistrc
      The JavaScript app source directory already exists
            apply  /Users/Taiga/.rbenv/versions/2.7.1/lib/ruby/gems/2.7.0/gems/webpacker-4.2.2/lib/install/binstubs.rb
        Copying binstubs
            exist    bin
            create    bin/webpack
            create    bin/webpack-dev-server
            append  .gitignore
      Installing all JavaScript dependencies [4.2.2]
              run  yarn add @rails/webpacker@4.2.2 from "."
      yarn add v1.22.4
      info No lockfile found.
      [1/4] 🔍  Resolving packages...
      warning @rails/webpacker > node-sass > request@2.88.2: request has been deprecated, see https://github.com/request/request/issues/3142
      warning @rails/webpacker > node-sass > node-gyp > request@2.88.2: request has been deprecated, see https://github.com/request/request/issues/3142
      warning @rails/webpacker > webpack > watchpack > watchpack-chokidar2 > chokidar@2.1.8: Chokidar 2 will break on node v14+. Upgrade to chokidar 3 with 15x less dependencies.
      warning @rails/webpacker > webpack > watchpack > watchpack-chokidar2 > chokidar > fsevents@1.2.13: fsevents 1 will break on node v14+ and could be using insecure binaries. Upgrade to fsevents 2.
      warning @rails/webpacker > webpack > micromatch > snapdragon > source-map-resolve > resolve-url@0.2.1: https://github.com/lydell/resolve-url#deprecated
      warning @rails/webpacker > webpack > micromatch > snapdragon > source-map-resolve > urix@0.1.0: Please see https://github.com/lydell/urix#deprecated
      [2/4] 🚚  Fetching packages...
      [3/4] 🔗  Linking dependencies...
      [4/4] 🔨  Building fresh packages...
      success Saved lockfile.
      success Saved 608 new dependencies.
      info Direct dependencies
      ├─ @rails/actioncable@6.0.3
      ├─ @rails/activestorage@6.0.3
      ├─ @rails/ujs@6.0.3
      .
      .
      .
      略
      .
      .
      .
      ├─ webpack-dev-middleware@3.7.2
      ├─ webpack-dev-server@3.11.0
      └─ ws@6.2.1
      ✨  Done in 8.73s.
    ```



## MySQL install
---
  - バージョン確認
    ```shell
    # 未インストールの場合
      ~ % mysql --version
      zsh: command not found: mysql

    # インストール済の場合
      ~ % mysql --version
      mysql  Ver 8.0.19 for osx10.15 on x86_64 (Homebrew)
    ```

  - 最新バージョンインストールコマンド
    ```shell
      ~ % brew install mysql
      Updating Homebrew...
      ==> Auto-updated Homebrew!
      Updated 1 tap (homebrew/core).
      ==> New Formulae
      immudb
      ==> Updated Formulae
      console_bridge      docker              python@3.8          youtube-dl
      contentful-cli      docker-completion   scrcpy
      create-dmg          glib-networking     subversion
      dartsim             ice                 urdfdom

      ==> Downloading https://homebrew.bintray.com/bottles/openssl%401.1-1.1.1g.catali
      ==> Downloading from https://akamai.bintray.com/19/1926679569c6af5337de812d86f4d
      ######################################################################## 100.0%
      ==> Downloading https://homebrew.bintray.com/bottles/protobuf-3.12.1.catalina.bo
      ==> Downloading from https://akamai.bintray.com/5a/5a8215a162e0b88fde57874602dd8
      ######################################################################## 100.0%
      ==> Downloading https://homebrew.bintray.com/bottles/mysql-8.0.19_1.catalina.bot
      ==> Downloading from https://akamai.bintray.com/e5/e5a5455d254260e9ca9821cb9c5e9
      ######################################################################## 100.0%
      ==> Installing dependencies for mysql: openssl@1.1 and protobuf
      ==> Installing mysql dependency: openssl@1.1
      ==> Pouring openssl@1.1-1.1.1g.catalina.bottle.tar.gz
      ==> Caveats
      A CA file has been bootstrapped using certificates from the system
      keychain. To add additional certificates, place .pem files in
        /usr/local/etc/openssl@1.1/certs

      and run
        /usr/local/opt/openssl@1.1/bin/c_rehash

      openssl@1.1 is keg-only, which means it was not symlinked into /usr/local,
      because macOS provides LibreSSL.

      If you need to have openssl@1.1 first in your PATH run:
        echo 'export PATH="/usr/local/opt/openssl@1.1/bin:$PATH"' >> ~/.zshrc

      For compilers to find openssl@1.1 you may need to set:
        export LDFLAGS="-L/usr/local/opt/openssl@1.1/lib"
        export CPPFLAGS="-I/usr/local/opt/openssl@1.1/include"

      For pkg-config to find openssl@1.1 you may need to set:
        export PKG_CONFIG_PATH="/usr/local/opt/openssl@1.1/lib/pkgconfig"

      ==> Summary
      🍺  /usr/local/Cellar/openssl@1.1/1.1.1g: 8,059 files, 18MB
      ==> Installing mysql dependency: protobuf
      ==> Pouring protobuf-3.12.1.catalina.bottle.1.tar.gz
      ==> Caveats
      Emacs Lisp files have been installed to:
        /usr/local/share/emacs/site-lisp/protobuf
      ==> Summary
      🍺  /usr/local/Cellar/protobuf/3.12.1: 269 files, 19.8MB
      ==> Installing mysql
      ==> Pouring mysql-8.0.19_1.catalina.bottle.tar.gz
      ==> /usr/local/Cellar/mysql/8.0.19_1/bin/mysqld --initialize-insecure --user=Tai
      ==> Caveats
      Weve installed your MySQL database without a root password. To secure it run:
          mysql_secure_installation

      MySQL is configured to only allow connections from localhost by default

      To connect run:
          mysql -uroot

      To have launchd start mysql now and restart at login:
        brew services start mysql
      Or, if you dont want/need a background service you can just run:
        mysql.server start
      ==> Summary
      🍺  /usr/local/Cellar/mysql/8.0.19_1: 286 files, 288.8MB
      ==> Caveats
      ==> openssl@1.1
      A CA file has been bootstrapped using certificates from the system
      keychain. To add additional certificates, place .pem files in
        /usr/local/etc/openssl@1.1/certs

      and run
        /usr/local/opt/openssl@1.1/bin/c_rehash

      openssl@1.1 is keg-only, which means it was not symlinked into /usr/local,
      because macOS provides LibreSSL.

      If you need to have openssl@1.1 first in your PATH run:
        echo 'export PATH="/usr/local/opt/openssl@1.1/bin:$PATH"' >> ~/.zshrc

      For compilers to find openssl@1.1 you may need to set:
        export LDFLAGS="-L/usr/local/opt/openssl@1.1/lib"
        export CPPFLAGS="-I/usr/local/opt/openssl@1.1/include"

      For pkg-config to find openssl@1.1 you may need to set:
        export PKG_CONFIG_PATH="/usr/local/opt/openssl@1.1/lib/pkgconfig"

      ==> protobuf
      Emacs Lisp files have been installed to:
        /usr/local/share/emacs/site-lisp/protobuf
      ==> mysql
      Weve installed your MySQL database without a root password. To secure it run:
          mysql_secure_installation

      MySQL is configured to only allow connections from localhost by default

      To connect run:
          mysql -uroot

      To have launchd start mysql now and restart at login:
        brew services start mysql
      Or, if you dont want/need a background service you can just run:
        mysql.server start
    ```

  - バージョン確認する、インストールが成功していたら初期設定をする
<br>

  - MySQL初期設定
    ```shell
      ~ % mysql_secure_installation
      mysql_secure_installation: [ERROR] unknown variable 'prompt=\U [\d] \R:\m>\_'.

      Securing the MySQL server deployment.

      Connecting to MySQL using a blank password.

      VALIDATE PASSWORD COMPONENT can be used to test passwords
      and improve security. It checks the strength of password
      and allows the users to set only those passwords which are
      secure enough. Would you like to setup VALIDATE PASSWORD component?

      Press y|Y for Yes, any other key for No: # [空Enter]

      Please set the password for root here.

      New password: # [rootユーザーのパスワードを入力]
      Re-enter new password: # [rootユーザーのパスワードを再度入力]

      # [残りは全て y でokです]
      By default, a MySQL installation has an anonymous user,
      allowing anyone to log into MySQL without having to have
      a user account created for them. This is intended only for
      testing, and to make the installation go a bit smoother.
      You should remove them before moving into a production
      environment.

      Remove anonymous users? (Press y|Y for Yes, any other key for No) : [y]

      Success.


      Normally, root should only be allowed to connect from
      'localhost'. This ensures that someone cannot guess at
      the root password from the network.

      Disallow root login remotely? (Press y|Y for Yes, any other key for No) : # [y]

      Success.

      By default, MySQL comes with a database named 'test' that
      anyone can access. This is also intended only for testing,
      and should be removed before moving into a production
      environment.


      Remove test database and access to it? (Press y|Y for Yes, any other key for No) : # [y]

      - Dropping test database...
      Success.

      - Removing privileges on test database...
      Success.

      Reloading the privilege tables will ensure that all changes
      made so far will take effect immediately.

      Reload privilege tables now? (Press y|Y for Yes, any other key for No) : # [y]
      Success.

      All done!
    ```

  - All done! と表示されると設定完了
  - 設定ミスの場合は、my.cnfというファイルを探して消す。(強引な方法)
  - [コマンド集](/MySQL/command.md)
  - [rails導入方法](/RubyonRails/changemysql.md)


## 今後導入予定

  - CocoaPods
  > rails => ios する？
