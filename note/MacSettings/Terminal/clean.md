``` sh
  #!/bin/sh

  sudo rm -rf ~/Library/Developer/Xcode/DerivedData/*
  echo "clean Xcode/DerivedData!"
  sudo rm -rf ~/Library/Developer/Xcode/Archives/*
  echo "clean Xcode/Archives!"
  sudo rm -rf ~/Library/Caches/*
  echo "clean Library/Caches!"
  sudo rm -rf ~/Library/Logs/iOS\ Simulator
  echo "clean iOS logs"
  # 全てのシミュレーターのキャッシュを一度で削除する場合
  sudo rm -rf ~/Library/Developer/Xcode/iOS\ DeviceSupport/*
  echo "clean simulator cache"
```

これをHOMEディレクトリにでも置いておく

` $ vi ~/clean.sh `

gistの内容を貼り付けて保存。

なんか重くなったなーと思ったらシェルの実行

` sh clean.sh  `

```
Password:
clean Xcode/DerivedData!
clean Xcode/Archives!
rm: /Users/~~/Library/Caches/CloudKit/com.apple.Safari: Operation not permitted
rm: /Users/~~/Library/Caches/CloudKit: Operation not permitted
rm: /Users/~~/Library/Caches/Google/Chrome: Directory not empty
rm: /Users/~~/Library/Caches/Google: Directory not empty
rm: /Users/~~/Library/Caches/com.apple.Safari: Operation not permitted
rm: /Users/~~/Library/Caches/com.apple.Safari.SafeBrowsing: Operation not permitted
rm: /Users/~~/Library/Caches/com.apple.safaridavclient: Operation not permitted
clean Library/Caches!
clean iOS logs
clean simulator cache
```


## 以下本文


iOSアプリ開発をしているとコンパイル回数が多いせいか、結構Macが重くなります。

不要なログ的なデータ削除だったり、メモリやCPUの開放だったりで軽くなることが多々有ります。



## メモリ解放

```
sudo purge
```


## メモリ解放（そこそこ時間かかります）

```
du -sx /
```

↑はハードディスクのの容量をディレクトリごとに表示してくれるコマンドですが、そのチェック処理中に開放し忘れてた処理を開放するらしいので結果メモリの開放になるようです。
実際、activity monitorで確認しても開放されます。


## アプリとOSのキャッシュのアップデート

```
sudo update_dyld_shared_cache -force
```

## ドライバキャッシュのクリア
```
sudo kextcache -system-caches
```
カーネルエクステンションというドライバのキャッシュをクリアします。

## カーネルキャッシュの更新
```
sudo kextcache -system-prelinked-kernel
```

## メンテナンススクリプトの手動実行
```
sudo periodic daily weekly monthly
```

上記の最終実行日の確認
```
ls -l /var/log/*.out
```

メンテナンススクリプトは真夜中に自動的に実行さるやつです。
しかし、その真夜中の時間帯にMacの電源を切っていると実行されませんので、いつもちゃんと電源切ってる人は手動実行してあげるといいかもです

---

### iOS開発やってるなら下記は定期的にやったほうがいい

アプリのビルドキャッシュ的なものが消えるので、フルコンパイルになるので、開発作業中なら注意

## ビルド情報の削除

```
sudo rm -rf ~/Library/Developer/Xcode/DerivedData
```

## アーカイブの削除

```
sudo rm -rf ~/Library/Developer/Xcode/Archives
```

## キャッシュの削除

```
sudo rm -rf ~/Library/Caches
```

---

## Dockerの掃除

### Image,Container,Volumeの数や容量の確認
```sh
docker system df -v
```
イメージ確認
```sh
docker image ls
```


### 使われてないimageを全て削除
```sh
docker system prune
```
### 既存のimage~使われていないimageを全て削除
```sh
docker system prune -a
```
### volumeを削除
```sh
docekr system prune --volumes
```
