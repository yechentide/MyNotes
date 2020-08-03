# 新しいMacのセットアップ

## Macの環境設定

### OSアップデートを遮断

```shell
softwareupdate --ignore "macOS Catalina"
```

### システム設定

* ファイアウォール起動
* キーボード
* Dock
* iCould

### Finderの設定

* サイドバー

### Xcodeのインストール

## アプリのインストール

### homebrewを導入

自身のインストール場所：　/usr/local/Homebrew
アプリのインストール先：　/usr/local/Cellar

### brew caskコマンドを使えるように

自身のインストール場所：　/usr/local/Homebrew/Library/Homebrew/Cask
アプリのインストール先：　/usr/local/Caskroom

### 必要なものをbrewでインストール

```shell
brew install cask fish zsh git jq wget

brew cask install adoptopenjdk11 baidunetdisk coteditor gimp
brew cask install google-chrome iterm2 jetbrains-toolbox keka
brew cask install kugoumusic magicavoxel mindmaster neteasemusic
brew cask install processing qq qqmusic sogouinput steam
brew cask install sublime-text typora visual-studio-code
brew cask install wireshark xmind Termius

brew install nodebrew nodenv rbenv
brew install yarn --????????
```

### その他のアプリ

* Office 365
* 写真画像エディタPixelstyle
* GIPHY CAPTURE
