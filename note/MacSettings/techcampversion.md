# テックキャンプの開発環境
|基礎カリキュラム|version|
|---|---|
|ruby|2.6.5|
|rails|6.0.0|
|mysql|5.6|


## mysql自動起動
```shell
mkdir ~/Library/LaunchAgents
% ln -sfv /usr/local/opt/mysql\@5.6/*.plist ~/Library/LaunchAgents
% launchctl load ~/Library/LaunchAgents/homebrew.mxcl.mysql\@5.6.plist
```

## mysqlエラー
> mysql@8系の残りカスがあったため、エラーが出た、
> メンターに残りカスをきれいにしてもらってサーバー起動完了。

```shell
Last login: Mon Jun 22 12:13:23 on ttys003
~ % mysql.server status
 ERROR! MySQL is not running
~ % mysql.server start
Starting MySQL
... ERROR! The server quit without updating PID file (/usr/local/var/mysql/TaigaMacBookPro.local.pid).
~ % mysql.server start
Starting MySQL
... ERROR! The server quit without updating PID file (/usr/local/var/mysql/TaigaMacBookPro.local.pid).
~ % mysql.server status
 ERROR! MySQL is not running
~ % brew list
autoconf	icu4c		openssl@1.1	protobuf	ruby-build
gettext		mysql@5.6	pcre2		rbenv		yarn
git		node		pkg-config	readline
~ % ps aux | grep mysql
Taiga            57404   0.2  2.7  4947340 449232   ??  S    12:36PM   0:00.35 /usr/local/opt/mysql@5.6/bin/mysqld --basedir=/usr/local/opt/mysql@5.6 --datadir=/usr/local/var/mysql --plugin-dir=/usr/local/opt/mysql@5.6/lib/plugin --log-error=TaigaMacBookPro.local.err --pid-file=TaigaMacBookPro.local.pid
Taiga            20662   0.1  2.4  4936544 404820   ??  S    11:09AM   0:22.65 /usr/local/Cellar/mysql/8.0.19_1/bin/mysqld --basedir=/usr/local/Cellar/mysql/8.0.19_1 --datadir=/usr/local/var/mysql --plugin-dir=/usr/local/Cellar/mysql/8.0.19_1/lib/plugin --log-error=TaigaMacBookPro.local.err --pid-file=/usr/local/var/mysql/TaigaMacBookPro.local.pid
Taiga            20530   0.0  0.0  4283236   1328   ??  S    11:09AM   0:00.02 /bin/sh /usr/local/Cellar/mysql/8.0.19_1/bin/mysqld_safe --datadir=/usr/local/var/mysql --pid-file=/usr/local/var/mysql/TaigaMacBookPro.local.pid
Taiga            57406   0.0  0.0  4268324    716 s000  S+   12:36PM   0:00.00 grep mysql
Taiga            57307   0.0  0.0  4282104   1176   ??  S    12:36PM   0:00.02 /bin/sh /usr/local/opt/mysql@5.6/bin/mysqld_safe --datadir=/usr/local/var/mysql
~ % sudo -9 kill 57404
sudo: invalid option -- 9
usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user]
            [command]
usage: sudo [-AbEHknPS] [-C num] [-g group] [-h host] [-p prompt] [-T timeout]
            [-u user] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C num] [-g group] [-h host] [-p prompt] [-T timeout]
            [-u user] file ...
~ % sudo kill -9 57404
Password:
kill: 57404: No such process
~ % ps aux | grep mysql
Taiga            20662   0.1  2.4  4936544 404820   ??  S    11:09AM   0:23.89 /usr/local/Cellar/mysql/8.0.19_1/bin/mysqld --basedir=/usr/local/Cellar/mysql/8.0.19_1 --datadir=/usr/local/var/mysql --plugin-dir=/usr/local/Cellar/mysql/8.0.19_1/lib/plugin --log-error=TaigaMacBookPro.local.err --pid-file=/usr/local/var/mysql/TaigaMacBookPro.local.pid
Taiga            20530   0.0  0.0  4283236   1328   ??  S    11:09AM   0:00.02 /bin/sh /usr/local/Cellar/mysql/8.0.19_1/bin/mysqld_safe --datadir=/usr/local/var/mysql --pid-file=/usr/local/var/mysql/TaigaMacBookPro.local.pid
Taiga            60428   0.0  0.0  4268324    716 s000  S+   12:42PM   0:00.00 grep mysql
~ % ps aux | grep mysql
Taiga            61133  30.2  2.7  4940352 449308   ??  S    12:43PM   0:00.34 /usr/local/opt/mysql@5.6/bin/mysqld --basedir=/usr/local/opt/mysql@5.6 --datadir=/usr/local/var/mysql --plugin-dir=/usr/local/opt/mysql@5.6/lib/plugin --log-error=TaigaMacBookPro.local.err --pid-file=TaigaMacBookPro.local.pid
Taiga            61036   0.4  0.0  4286200   1212   ??  S    12:43PM   0:00.02 /bin/sh /usr/local/opt/mysql@5.6/bin/mysqld_safe --datadir=/usr/local/var/mysql
Taiga            20662   0.1  2.4  4936544 404820   ??  S    11:09AM   0:24.13 /usr/local/Cellar/mysql/8.0.19_1/bin/mysqld --basedir=/usr/local/Cellar/mysql/8.0.19_1 --datadir=/usr/local/var/mysql --plugin-dir=/usr/local/Cellar/mysql/8.0.19_1/lib/plugin --log-error=TaigaMacBookPro.local.err --pid-file=/usr/local/var/mysql/TaigaMacBookPro.local.pid
Taiga            20530   0.0  0.0  4283236   1328   ??  S    11:09AM   0:00.02 /bin/sh /usr/local/Cellar/mysql/8.0.19_1/bin/mysqld_safe --datadir=/usr/local/var/mysql --pid-file=/usr/local/var/mysql/TaigaMacBookPro.local.pid
Taiga            61135   0.0  0.0  4268324    716 s000  S+   12:43PM   0:00.00 grep mysql
~ % sudo kill -9 20662
~ % ps aux | grep mysql
Taiga            62253   0.0  0.0  4268324    704 s000  R+   12:45PM   0:00.00 grep mysql
Taiga            62251   0.0  2.7  4951424 450656   ??  S    12:45PM   0:00.36 /usr/local/opt/mysql@5.6/bin/mysqld --basedir=/usr/local/opt/mysql@5.6 --datadir=/usr/local/var/mysql --plugin-dir=/usr/local/opt/mysql@5.6/lib/plugin --log-error=TaigaMacBookPro.local.err --pid-file=TaigaMacBookPro.local.pid
Taiga            62154   0.0  0.0  4285176   1204   ??  S    12:45PM   0:00.02 /bin/sh /usr/local/opt/mysql@5.6/bin/mysqld_safe --datadir=/usr/local/var/mysql
~ % sudo rm -rm /usr/local/var/mysql
rm: illegal option -- m
usage: rm [-f | -i] [-dPRrvW] file ...
       unlink file
~ % sudo rm -rf /usr/local/var/mysql
~ % ps aux | grep mysql
Taiga            62267   0.0  0.0  4268324    704 s000  R+   12:51PM   0:00.00 grep mysql
Taiga            62251   0.0  2.7  4951424 450656   ??  S    12:45PM   0:00.40 /usr/local/opt/mysql@5.6/bin/mysqld --basedir=/usr/local/opt/mysql@5.6 --datadir=/usr/local/var/mysql --plugin-dir=/usr/local/opt/mysql@5.6/lib/plugin --log-error=TaigaMacBookPro.local.err --pid-file=TaigaMacBookPro.local.pid
Taiga            62154   0.0  0.0  4285176   1204   ??  S    12:45PM   0:00.02 /bin/sh /usr/local/opt/mysql@5.6/bin/mysqld_safe --datadir=/usr/local/var/mysql
~ % sudo kill -9 62251
~ % ps aux | grep mysql
Taiga            62276   0.0  0.0  4278564    748 s000  S+   12:52PM   0:00.00 grep mysql
~ % brew install mysql@5.6
Updating Homebrew...
==> Auto-updated Homebrew!
Updated 1 tap (homebrew/core).
==> Updated Formulae
dvc

Warning: mysql@5.6 5.6.47 is already installed and up-to-date
To reinstall 5.6.47, run `brew reinstall mysql@5.6`
~ % brew reinstall mysql@5.6
==> Downloading https://homebrew.bintray.com/bottles/mysql%405.6-5.6.47.catalina
Already downloaded: /Users/Taiga/Library/Caches/Homebrew/downloads/c270819d76ed326059143e1b4c6c6c0ab672e4259c328c140ec71d917babc348--mysql@5.6-5.6.47.catalina.bottle.tar.gz
==> Reinstalling mysql@5.6
==> Pouring mysql@5.6-5.6.47.catalina.bottle.tar.gz
==> /usr/local/Cellar/mysql@5.6/5.6.47/bin/mysql_install_db --verbose --user=Tai
==> Caveats
A "/etc/my.cnf" from another install may interfere with a Homebrew-built
server starting up correctly.

MySQL is configured to only allow connections from localhost by default

To connect:
    mysql -uroot

mysql@5.6 is keg-only, which means it was not symlinked into /usr/local,
because this is an alternate version of another formula.

If you need to have mysql@5.6 first in your PATH run:
  echo 'export PATH="/usr/local/opt/mysql@5.6/bin:$PATH"' >> ~/.zshrc

For compilers to find mysql@5.6 you may need to set:
  export LDFLAGS="-L/usr/local/opt/mysql@5.6/lib"
  export CPPFLAGS="-I/usr/local/opt/mysql@5.6/include"


To restart mysql@5.6 after an upgrade:
  brew services restart mysql@5.6
Or, if you dont want/need a background service you can just run:
  /usr/local/opt/mysql@5.6/bin/mysql.server start
==> Summary
🍺  /usr/local/Cellar/mysql@5.6/5.6.47: 344 files, 155.2MB
~ % echo 'export PATH="/usr/local/opt/mysql@5.6/bin:$PATH"' >> ~/.zshrc
~ % brew reinstall mysql@5.6
==> Downloading https://homebrew.bintray.com/bottles/mysql%405.6-5.6.47.catalina
Already downloaded: /Users/Taiga/Library/Caches/Homebrew/downloads/c270819d76ed326059143e1b4c6c6c0ab672e4259c328c140ec71d917babc348--mysql@5.6-5.6.47.catalina.bottle.tar.gz
==> Reinstalling mysql@5.6
==> Pouring mysql@5.6-5.6.47.catalina.bottle.tar.gz
==> Caveats
A "/etc/my.cnf" from another install may interfere with a Homebrew-built
server starting up correctly.

MySQL is configured to only allow connections from localhost by default

To connect:
    mysql -uroot

mysql@5.6 is keg-only, which means it was not symlinked into /usr/local,
because this is an alternate version of another formula.

If you need to have mysql@5.6 first in your PATH run:
  echo 'export PATH="/usr/local/opt/mysql@5.6/bin:$PATH"' >> ~/.zshrc

For compilers to find mysql@5.6 you may need to set:
  export LDFLAGS="-L/usr/local/opt/mysql@5.6/lib"
  export CPPFLAGS="-I/usr/local/opt/mysql@5.6/include"


To restart mysql@5.6 after an upgrade:
  brew services restart mysql@5.6
Or, if you dont want/need a background service you can just run:
  /usr/local/opt/mysql@5.6/bin/mysql.server start
==> Summary
🍺  /usr/local/Cellar/mysql@5.6/5.6.47: 343 files, 155.2MB
~ % brew services restart mysql@5.6
==> Tapping homebrew/services
Cloning into '/usr/local/Homebrew/Library/Taps/homebrew/homebrew-services'...
remote: Enumerating objects: 24, done.
remote: Counting objects: 100% (24/24), done.
remote: Compressing objects: 100% (21/21), done.
remote: Total 801 (delta 6), reused 13 (delta 2), pack-reused 777
Receiving objects: 100% (801/801), 222.37 KiB | 512.00 KiB/s, done.
Resolving deltas: 100% (324/324), done.
Tapped 1 command (40 files, 301KB).
Stopping `mysql@5.6`... (might take a while)
==> Successfully stopped `mysql@5.6` (label: homebrew.mxcl.mysql@5.6)
==> Successfully started `mysql@5.6` (label: homebrew.mxcl.mysql@5.6)
~ % mysql.server status
 SUCCESS! MySQL running (64364)
~ %

```

## gem sinatra(2.0.8.1)
  > 簡易的なサーバーを立てる

```shell
Fetching sinatra-2.0.8.1.gem
Fetching mustermann-1.1.1.gem
Fetching rack-protection-2.0.8.1.gem
Fetching ruby2_keywords-0.0.2.gem
Successfully installed rack-protection-2.0.8.1
Successfully installed ruby2_keywords-0.0.2
Successfully installed mustermann-1.1.1
Successfully installed sinatra-2.0.8.1
Parsing documentation for rack-protection-2.0.8.1
Installing ri documentation for rack-protection-2.0.8.1
Parsing documentation for ruby2_keywords-0.0.2
Installing ri documentation for ruby2_keywords-0.0.2
Parsing documentation for mustermann-1.1.1
Installing ri documentation for mustermann-1.1.1
Parsing documentation for sinatra-2.0.8.1
Installing ri documentation for sinatra-2.0.8.1
Done installing documentation for rack-protection, ruby2_keywords, mustermann, sinatra after 256 seconds
4 gems installed
```


```shell
~ % brew install imagemagick
Updating Homebrew...
==> Downloading https://homebrew.bintray.com/bottles/libpng-1.6.37.catalina.bott
==> Downloading from https://akamai.bintray.com/c8/c8e74da602c21f978cd7ee3d48997
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/freetype-2.10.2.catalina.bo
==> Downloading from https://akamai.bintray.com/16/16500bbd77b8bbeb9a4ad432c795d
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/jpeg-9d.catalina.bottle.tar
==> Downloading from https://akamai.bintray.com/8f/8f7b82a952fb3937889c7f22da140
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/libtiff-4.1.0.catalina.bott
==> Downloading from https://akamai.bintray.com/44/449bd9123e73e4c4eab85b77322d7
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/ghostscript-9.52.catalina.b
==> Downloading from https://akamai.bintray.com/8c/8cd0efa1e5525f849be3ee1e50e16
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/libde265-1.0.5.catalina.bot
==> Downloading from https://akamai.bintray.com/76/7621e45fa0b119aff03a8c3ff3ed9
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/libffi-3.3.catalina.bottle.
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/pcre-8.44.catalina.bottle.t
==> Downloading from https://akamai.bintray.com/f8/f8ac266e04f984fa55091a43f0fdc
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/gdbm-1.18.1.catalina.bottle
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/sqlite-3.32.3.catalina.bott
==> Downloading from https://akamai.bintray.com/98/98f798c4a62c9db46cc6ac82c499a
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/xz-5.2.5.catalina.bottle.ta
==> Downloading from https://akamai.bintray.com/2d/2dcc8e0121c934d1e34ffdb37fcd7
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/python%403.8-3.8.3.catalina
==> Downloading from https://akamai.bintray.com/67/67cceb372f3b0f45ff90beb70d6e9
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/glib-2.64.3.catalina.bottle
==> Downloading from https://akamai.bintray.com/c7/c7259832a3bf3fe8093962473718a
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/docbook-5.1_1.catalina.bott
==> Downloading from https://akamai.bintray.com/81/8152e5356c47a7b8282f3ed84ee3f
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/docbook-xsl-1.79.2_1.catali
==> Downloading from https://akamai.bintray.com/65/65a5442556a88a865ef377cb73df0
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/gnu-getopt-2.35.2.catalina.
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/xmlto-0.0.28.catalina.bottl
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/shared-mime-info-2.0.catali
==> Downloading from https://akamai.bintray.com/5a/5aefdc7964e569188cb67a49f4a42
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/x265-3.4.catalina.bottle.ta
==> Downloading from https://akamai.bintray.com/51/51c759fb1ae6220caca443ef28171
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/libheif-1.7.0.catalina.bott
==> Downloading from https://akamai.bintray.com/dc/dc3c55be447a590b3bfd0ba5e0a1b
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/liblqr-0.4.2_1.catalina.bot
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/libomp-10.0.0.catalina.bott
==> Downloading from https://akamai.bintray.com/0e/0ea757dbea7bf12141ef1d209d2f3
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/libtool-2.4.6_2.catalina.bo
==> Downloading from https://akamai.bintray.com/af/af317b35d0a394b7ef55fba495073
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/little-cms2-2.11.catalina.b
==> Downloading from https://akamai.bintray.com/b0/b0fe7486871b0fb0e34012f48bce0
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/ilmbase-2.5.2.catalina.bott
==> Downloading from https://akamai.bintray.com/13/13a8f951e15caa1f4f633ec718e4f
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/openexr-2.5.2.catalina.bott
==> Downloading from https://akamai.bintray.com/cd/cd7b32d91f6e70711a4010f2027be
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/openjpeg-2.3.1.catalina.bot
==> Downloading from https://akamai.bintray.com/29/29b9e0e1ed01683fd26a2fb07d7ee
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/webp-1.1.0.catalina.bottle.
==> Downloading from https://akamai.bintray.com/27/27c76a7054277ff5a2e844c5996fc
######################################################################## 100.0%
==> Downloading https://homebrew.bintray.com/bottles/imagemagick-7.0.10-23.catal
==> Downloading from https://akamai.bintray.com/bf/bf19ce6c826be9ab5a42d4e02b74d
######################################################################## 100.0%
==> Installing dependencies for imagemagick: libpng, freetype, jpeg, libtiff, ghostscript, libde265, libffi, pcre, gdbm, sqlite, xz, python@3.8, glib, docbook, docbook-xsl, gnu-getopt, xmlto, shared-mime-info, x265, libheif, liblqr, libomp, libtool, little-cms2, ilmbase, openexr, openjpeg and webp
==> Installing imagemagick dependency: libpng
==> Pouring libpng-1.6.37.catalina.bottle.tar.gz
🍺  /usr/local/Cellar/libpng/1.6.37: 27 files, 1.2MB
==> Installing imagemagick dependency: freetype
==> Pouring freetype-2.10.2.catalina.bottle.tar.gz
🍺  /usr/local/Cellar/freetype/2.10.2: 61 files, 2.3MB
==> Installing imagemagick dependency: jpeg
==> Pouring jpeg-9d.catalina.bottle.tar.gz
🍺  /usr/local/Cellar/jpeg/9d: 21 files, 775.2KB
==> Installing imagemagick dependency: libtiff
==> Pouring libtiff-4.1.0.catalina.bottle.tar.gz
🍺  /usr/local/Cellar/libtiff/4.1.0: 247 files, 3.7MB
==> Installing imagemagick dependency: ghostscript
==> Pouring ghostscript-9.52.catalina.bottle.tar.gz
🍺  /usr/local/Cellar/ghostscript/9.52: 671 files, 87.4MB
==> Installing imagemagick dependency: libde265
==> Pouring libde265-1.0.5.catalina.bottle.tar.gz
🍺  /usr/local/Cellar/libde265/1.0.5: 22 files, 2MB
==> Installing imagemagick dependency: libffi
==> Pouring libffi-3.3.catalina.bottle.tar.gz
==> Caveats
libffi is keg-only, which means it was not symlinked into /usr/local,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

For compilers to find libffi you may need to set:
  export LDFLAGS="-L/usr/local/opt/libffi/lib"
  export CPPFLAGS="-I/usr/local/opt/libffi/include"

For pkg-config to find libffi you may need to set:
  export PKG_CONFIG_PATH="/usr/local/opt/libffi/lib/pkgconfig"

==> Summary
🍺  /usr/local/Cellar/libffi/3.3: 16 files, 489.4KB
==> Installing imagemagick dependency: pcre
==> Pouring pcre-8.44.catalina.bottle.tar.gz
🍺  /usr/local/Cellar/pcre/8.44: 204 files, 5.5MB
==> Installing imagemagick dependency: gdbm
==> Pouring gdbm-1.18.1.catalina.bottle.1.tar.gz
🍺  /usr/local/Cellar/gdbm/1.18.1: 20 files, 602.8KB
==> Installing imagemagick dependency: sqlite
==> Pouring sqlite-3.32.3.catalina.bottle.tar.gz
==> Caveats
sqlite is keg-only, which means it was not symlinked into /usr/local,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

If you need to have sqlite first in your PATH run:
  echo 'export PATH="/usr/local/opt/sqlite/bin:$PATH"' >> ~/.zshrc

For compilers to find sqlite you may need to set:
  export LDFLAGS="-L/usr/local/opt/sqlite/lib"
  export CPPFLAGS="-I/usr/local/opt/sqlite/include"

For pkg-config to find sqlite you may need to set:
  export PKG_CONFIG_PATH="/usr/local/opt/sqlite/lib/pkgconfig"

==> Summary
🍺  /usr/local/Cellar/sqlite/3.32.3: 11 files, 4MB
==> Installing imagemagick dependency: xz
==> Pouring xz-5.2.5.catalina.bottle.tar.gz
🍺  /usr/local/Cellar/xz/5.2.5: 92 files, 1.1MB
==> Installing imagemagick dependency: python@3.8
==> Pouring python@3.8-3.8.3.catalina.bottle.tar.gz
==> /usr/local/Cellar/python@3.8/3.8.3/bin/python3 -s setup.py --no-user-cfg ins
==> /usr/local/Cellar/python@3.8/3.8.3/bin/python3 -s setup.py --no-user-cfg ins
==> /usr/local/Cellar/python@3.8/3.8.3/bin/python3 -s setup.py --no-user-cfg ins
==> Caveats
Python has been installed as
  /usr/local/opt/python@3.8/bin/python3

You can install Python packages with
  /usr/local/opt/python@3.8/bin/pip3 install <package>
They will install into the site-package directory
  /usr/local/opt/python@3.8/Frameworks/Python.framework/Versions/3.8/lib/python3.8/site-packages

See: https://docs.brew.sh/Homebrew-and-Python

python@3.8 is keg-only, which means it was not symlinked into /usr/local,
because this is an alternate version of another formula.

If you need to have python@3.8 first in your PATH run:
  echo 'export PATH="/usr/local/opt/python@3.8/bin:$PATH"' >> ~/.zshrc

For compilers to find python@3.8 you may need to set:
  export LDFLAGS="-L/usr/local/opt/python@3.8/lib"

For pkg-config to find python@3.8 you may need to set:
  export PKG_CONFIG_PATH="/usr/local/opt/python@3.8/lib/pkgconfig"

==> Summary
🍺  /usr/local/Cellar/python@3.8/3.8.3: 4,125 files, 63MB
==> Installing imagemagick dependency: glib
==> Pouring glib-2.64.3.catalina.bottle.tar.gz
==> Caveats
Bash completion has been installed to:
  /usr/local/etc/bash_completion.d
==> Summary
🍺  /usr/local/Cellar/glib/2.64.3: 436 files, 15.7MB
==> Installing imagemagick dependency: docbook
==> Pouring docbook-5.1_1.catalina.bottle.tar.gz
==> xmlcatalog --noout --create /usr/local/etc/xml/catalog
==> xmlcatalog --noout --del file:///usr/local/opt/docbook/docbook/xml/4.2/catal
==> xmlcatalog --noout --add nextCatalog  file:///usr/local/opt/docbook/docbook/
==> xmlcatalog --noout --del file:///usr/local/opt/docbook/docbook/xml/4.1.2/cat
==> xmlcatalog --noout --add nextCatalog  file:///usr/local/opt/docbook/docbook/
==> xmlcatalog --noout --del file:///usr/local/opt/docbook/docbook/xml/4.3/catal
==> xmlcatalog --noout --add nextCatalog  file:///usr/local/opt/docbook/docbook/
==> xmlcatalog --noout --del file:///usr/local/opt/docbook/docbook/xml/4.4/catal
==> xmlcatalog --noout --add nextCatalog  file:///usr/local/opt/docbook/docbook/
==> xmlcatalog --noout --del file:///usr/local/opt/docbook/docbook/xml/4.5/catal
==> xmlcatalog --noout --add nextCatalog  file:///usr/local/opt/docbook/docbook/
==> xmlcatalog --noout --del file:///usr/local/opt/docbook/docbook/xml/5.0/catal
==> xmlcatalog --noout --add nextCatalog  file:///usr/local/opt/docbook/docbook/
==> xmlcatalog --noout --del file:///usr/local/opt/docbook/docbook/xml/5.1/catal
==> xmlcatalog --noout --add nextCatalog  file:///usr/local/opt/docbook/docbook/
==> Caveats
To use the DocBook package in your XML toolchain,
you need to add the following to your ~/.bashrc:

export XML_CATALOG_FILES="/usr/local/etc/xml/catalog"
==> Summary
🍺  /usr/local/Cellar/docbook/5.1_1: 199 files, 8.9MB
==> Installing imagemagick dependency: docbook-xsl
==> Pouring docbook-xsl-1.79.2_1.catalina.bottle.tar.gz
==> xmlcatalog --noout --del file:///usr/local/opt/docbook-xsl/docbook-xsl/catal
==> xmlcatalog --noout --add nextCatalog  file:///usr/local/opt/docbook-xsl/docb
==> xmlcatalog --noout --del https://cdn.docbook.org/release/xsl-nons/1.79.2 /us
==> xmlcatalog --noout --add rewriteSystem https://cdn.docbook.org/release/xsl-n
==> xmlcatalog --noout --add rewriteURI https://cdn.docbook.org/release/xsl-nons
==> xmlcatalog --noout --del https://cdn.docbook.org/release/xsl-nons/current /u
==> xmlcatalog --noout --add rewriteSystem https://cdn.docbook.org/release/xsl-n
==> xmlcatalog --noout --add rewriteURI https://cdn.docbook.org/release/xsl-nons
==> xmlcatalog --noout --del http://docbook.sourceforge.net/release/xsl/1.79.2 /
==> xmlcatalog --noout --add rewriteSystem http://docbook.sourceforge.net/releas
==> xmlcatalog --noout --add rewriteURI http://docbook.sourceforge.net/release/x
==> xmlcatalog --noout --del http://docbook.sourceforge.net/release/xsl/current
==> xmlcatalog --noout --add rewriteSystem http://docbook.sourceforge.net/releas
==> xmlcatalog --noout --add rewriteURI http://docbook.sourceforge.net/release/x
==> xmlcatalog --noout --del file:///usr/local/opt/docbook-xsl/docbook-xsl-ns/ca
==> xmlcatalog --noout --add nextCatalog  file:///usr/local/opt/docbook-xsl/docb
==> xmlcatalog --noout --del https://cdn.docbook.org/release/xsl/1.79.2 /usr/loc
==> xmlcatalog --noout --add rewriteSystem https://cdn.docbook.org/release/xsl/1
==> xmlcatalog --noout --add rewriteURI https://cdn.docbook.org/release/xsl/1.79
==> xmlcatalog --noout --del https://cdn.docbook.org/release/xsl/current /usr/lo
==> xmlcatalog --noout --add rewriteSystem https://cdn.docbook.org/release/xsl/c
==> xmlcatalog --noout --add rewriteURI https://cdn.docbook.org/release/xsl/curr
==> xmlcatalog --noout --del http://docbook.sourceforge.net/release/xsl-ns/1.79.
==> xmlcatalog --noout --add rewriteSystem http://docbook.sourceforge.net/releas
==> xmlcatalog --noout --add rewriteURI http://docbook.sourceforge.net/release/x
==> xmlcatalog --noout --del http://docbook.sourceforge.net/release/xsl-ns/curre
==> xmlcatalog --noout --add rewriteSystem http://docbook.sourceforge.net/releas
==> xmlcatalog --noout --add rewriteURI http://docbook.sourceforge.net/release/x
🍺  /usr/local/Cellar/docbook-xsl/1.79.2_1: 4,910 files, 94.0MB
==> Installing imagemagick dependency: gnu-getopt
==> Pouring gnu-getopt-2.35.2.catalina.bottle.tar.gz
==> Caveats
gnu-getopt is keg-only, which means it was not symlinked into /usr/local,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

If you need to have gnu-getopt first in your PATH run:
  echo 'export PATH="/usr/local/opt/gnu-getopt/bin:$PATH"' >> ~/.zshrc


Bash completion has been installed to:
  /usr/local/opt/gnu-getopt/etc/bash_completion.d
==> Summary
🍺  /usr/local/Cellar/gnu-getopt/2.35.2: 10 files, 164.6KB
==> Installing imagemagick dependency: xmlto
==> Pouring xmlto-0.0.28.catalina.bottle.1.tar.gz
🍺  /usr/local/Cellar/xmlto/0.0.28: 46 files, 142.0KB
==> Installing imagemagick dependency: shared-mime-info
==> Pouring shared-mime-info-2.0.catalina.bottle.tar.gz
==> /usr/local/Cellar/shared-mime-info/2.0/bin/update-mime-database /usr/local/s
🍺  /usr/local/Cellar/shared-mime-info/2.0: 86 files, 4.4MB
==> Installing imagemagick dependency: x265
==> Pouring x265-3.4.catalina.bottle.tar.gz
🍺  /usr/local/Cellar/x265/3.4: 11 files, 35.5MB
==> Installing imagemagick dependency: libheif
==> Pouring libheif-1.7.0.catalina.bottle.tar.gz
==> /usr/local/opt/shared-mime-info/bin/update-mime-database /usr/local/share/mi
🍺  /usr/local/Cellar/libheif/1.7.0: 23 files, 2.4MB
==> Installing imagemagick dependency: liblqr
==> Pouring liblqr-0.4.2_1.catalina.bottle.1.tar.gz
🍺  /usr/local/Cellar/liblqr/0.4.2_1: 24 files, 133.5KB
==> Installing imagemagick dependency: libomp
==> Pouring libomp-10.0.0.catalina.bottle.tar.gz
🍺  /usr/local/Cellar/libomp/10.0.0: 9 files, 1.3MB
==> Installing imagemagick dependency: libtool
==> Pouring libtool-2.4.6_2.catalina.bottle.tar.gz
==> Caveats
In order to prevent conflicts with Apple's own libtool we have prepended a "g"
so, you have instead: glibtool and glibtoolize.
==> Summary
🍺  /usr/local/Cellar/libtool/2.4.6_2: 71 files, 3.7MB
==> Installing imagemagick dependency: little-cms2
==> Pouring little-cms2-2.11.catalina.bottle.tar.gz
🍺  /usr/local/Cellar/little-cms2/2.11: 21 files, 1MB
==> Installing imagemagick dependency: ilmbase
==> Pouring ilmbase-2.5.2.catalina.bottle.tar.gz
🍺  /usr/local/Cellar/ilmbase/2.5.2: 87 files, 1.6MB
==> Installing imagemagick dependency: openexr
==> Pouring openexr-2.5.2.catalina.bottle.tar.gz
🍺  /usr/local/Cellar/openexr/2.5.2: 152 files, 6.6MB
==> Installing imagemagick dependency: openjpeg
==> Pouring openjpeg-2.3.1.catalina.bottle.tar.gz
🍺  /usr/local/Cellar/openjpeg/2.3.1: 516 files, 13.9MB
==> Installing imagemagick dependency: webp
==> Pouring webp-1.1.0.catalina.bottle.tar.gz
🍺  /usr/local/Cellar/webp/1.1.0: 39 files, 2.1MB
==> Installing imagemagick
==> Pouring imagemagick-7.0.10-23.catalina.bottle.tar.gz
🍺  /usr/local/Cellar/imagemagick/7.0.10-23: 1,497 files, 25.6MB
==> Caveats
==> libffi
libffi is keg-only, which means it was not symlinked into /usr/local,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

For compilers to find libffi you may need to set:
  export LDFLAGS="-L/usr/local/opt/libffi/lib"
  export CPPFLAGS="-I/usr/local/opt/libffi/include"

For pkg-config to find libffi you may need to set:
  export PKG_CONFIG_PATH="/usr/local/opt/libffi/lib/pkgconfig"

==> sqlite
sqlite is keg-only, which means it was not symlinked into /usr/local,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

If you need to have sqlite first in your PATH run:
  echo 'export PATH="/usr/local/opt/sqlite/bin:$PATH"' >> ~/.zshrc

For compilers to find sqlite you may need to set:
  export LDFLAGS="-L/usr/local/opt/sqlite/lib"
  export CPPFLAGS="-I/usr/local/opt/sqlite/include"

For pkg-config to find sqlite you may need to set:
  export PKG_CONFIG_PATH="/usr/local/opt/sqlite/lib/pkgconfig"

==> python@3.8
Python has been installed as
  /usr/local/opt/python@3.8/bin/python3

You can install Python packages with
  /usr/local/opt/python@3.8/bin/pip3 install <package>
They will install into the site-package directory
  /usr/local/opt/python@3.8/Frameworks/Python.framework/Versions/3.8/lib/python3.8/site-packages

See: https://docs.brew.sh/Homebrew-and-Python

python@3.8 is keg-only, which means it was not symlinked into /usr/local,
because this is an alternate version of another formula.

If you need to have python@3.8 first in your PATH run:
  echo 'export PATH="/usr/local/opt/python@3.8/bin:$PATH"' >> ~/.zshrc

For compilers to find python@3.8 you may need to set:
  export LDFLAGS="-L/usr/local/opt/python@3.8/lib"

For pkg-config to find python@3.8 you may need to set:
  export PKG_CONFIG_PATH="/usr/local/opt/python@3.8/lib/pkgconfig"

==> glib
Bash completion has been installed to:
  /usr/local/etc/bash_completion.d
==> docbook
To use the DocBook package in your XML toolchain,
you need to add the following to your ~/.bashrc:

export XML_CATALOG_FILES="/usr/local/etc/xml/catalog"
==> gnu-getopt
gnu-getopt is keg-only, which means it was not symlinked into /usr/local,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

If you need to have gnu-getopt first in your PATH run:
  echo 'export PATH="/usr/local/opt/gnu-getopt/bin:$PATH"' >> ~/.zshrc


Bash completion has been installed to:
  /usr/local/opt/gnu-getopt/etc/bash_completion.d
==> libtool
In order to prevent conflicts with Apple's own libtool we have prepended a "g"
so, you have instead: glibtool and glibtoolize.
```
