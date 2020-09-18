* App install
    * Mac app store
        * Twitter
        * line
        * Slack
        * Evernote
        * Skype
        * xcode
        * CopyClip - Clipboard History
        <!-- * paste -->
        <!-- * display menu -->
        <!-- * Go fo gmail -->
        * Bettor Snap Tool
        * Bettor Touch Tool
        <!-- * app ceran -->

    * web app
        * chrome
            * youtube
            * google calendar
        <!-- * google japanese input ime -->
        <!-- * github -->
        * vscode
        * db browser for sqlite
        * elecom_mouse_uril
        * Scroll Reverser
        * intel power gadget
        * BetterTouchTool
        * TrashMe
        * App Cleaner & Uninstaller

---

# Settings

- screenshotの保存先変更
    - 変更方法
    ~~~ shell
    ~ % defaults write com.apple.screencapture location ~/保存先のパス
    ~ % killall SystemUIServer # 再起動コマンド(いらんかも)
    ~~~
    - 元の保存先に戻す方法
    ```shell
    ~ % defaults delete com.apple.screencapture location;
    ~ % killall SystemUIServer # 再起動コマンド(いらんかも)
    ```

- font-family(**Ricty Diminished**)

## shellプロンプト設定(zsh)
> [カスタマイズ項目](./Terminal/prompt.md)

## AutoBoot設定
> PCの蓋を開けたときに起動するかどうかの設定
- 現在の設定
```shell
% sudo nvram AutoBoot=%01
```
- 純正の設定
```shell
% subo nvram AutoBoot=%03
```



<!-- ``` shell
# .bashrc

PS1="\W $ "

# $PATH 修正？
export BASH_SILENCE_DEPRECATION_WARNING=1

# Taigaディレクトリ移動
# cd Taiga
eval "$(rbenv init -)"
``` -->

<!-- ```shell
# .zshrc

export PS1="%~ "

# rails $PATH 修正
export PATH="$HOME/.rbenv/shims:$PATH"

# Taigaディレクトリ移動
# cd Taiga

# export PATH=$HOME/.nodebrew/current/bin:$PATH
``` -->
