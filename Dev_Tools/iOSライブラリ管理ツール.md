# ライブラリ管理ツール

## Swift Package Manager

### 使い方

Xcodeの`File > Swift Package > Add Package Dependency...`でライブラリを追加できる

## CocoaPods

### CocoaPodsをインストールする

rubyを使ってインストールする。インストール先を指定できる

```shell
gem install cocoapods
gem install -n /usr/local/bin cocoapods
```

### CocoaPodsでライブラリを導入する

[CocoaPodsでライブラリを簡単に管理する](https://qiita.com/yamashi/items/f69ce0dd3e25d75ec6c3)
[CocoaPodsのつかいかた](https://qiita.com/KakeruFukuda/items/369b71d074c12b449e09)
[CocoaPodsのインストールの仕方と使い方](https://satoriku.com/cocoapods/)

1. プロジェクトのルートディレクトリに移動する
2. `Podfile`というファイルを作成する (または`pod init`コマンドで作成)
3. 利用したいライブラリをPodfileファイルに記述する
   プラットフォーム、サポートバージョン、プロジェクト名、導入したいライブラリを指定する

    ```cocoapods
        platform :ios, '11.0'
        use_frameworks!

        # コメント
        target 'ProjectName' do
            pod 'AFNetworking', '~> 2.6'
            pod 'ORStackView', '~> 3.0'
            pod 'SwiftyJSON'
        end
    ```

4. `pod install`コマンドでライブラリ導入開始 (ライブラリの変更がある場合は`pod update`で更新する)
5. 新しく生成されたワークスペースを開いてコーディング開始

### ライブラリを公開

[Making a CocoaPod](https://guides.cocoapods.org/making/making-a-cocoapod.html)

1. podspecを作成＆編集

    ```shell
    pod spec create <ライブラリ名>
    ```

2. podspecファイルをチェック

    ```shell
    pod lib lint
    ```

3. CocoaPods Trunkへのアカウント登録(初回のみ)  
   登録情報は`pod trunk me`で確認できる

    ```shell
    pod trunk register <メールアドレス> <開発者名>
    ```

4. ライブラリを公開・更新

    ```shell
    pod trunk push ライブラリ名.podspec
    pod trunk push ライブラリ名.podspec --allow-warnings
    ```

5. 特定バージョンを削除

    ```shell
    pod trunk delete <ライブラリ名> x.x.x
    pod cache clean --all
    ```

## Carthage

### Carthageをインストールする

homebrewを使ってインストールする

```shell
brew install carthage
```

### Carthageでライブラリを導入する

[iOSのCarthage導入手順と注意点](https://blog.mothule.com/ios/carthage/ios-carthage-install-guide)
[Carthageの使い方を体系的に理解する](https://blog.mothule.com/ios/carthage/ios-carthage)
