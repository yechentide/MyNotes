# Gitの基本

## 初期設定

```shell
git config --global user.name "開発者の名前"
git config --global user.email "開発者のメールアドレス"
```

他にも設定しておくと便利な項目がある

```shell
// ユーザー名とパスワードのキャッシュを有効に
git config --global credential helper osxkeychain
// git statusなどで日本語ファイル名をエスケープせずに表示
git config --global core.quotepath fasle
```

## 基本コマンド

### リポジトリの作成

```shell
git init
```

### リポジトリのクローン

```shell
git clone https://.......
```

### 既存のリポジトリをリモートに追加

```shell
git remote add origin <リポジトリのURI>
```

### 状態を確認

```shell
git status
```

### ファイルの削除

```shell
git rm ファイル
```

### ファイルの移動＆名前変更

```shell
git mv 元のファイル 移動先/新しい名前
```

### コミットログの確認

```shell
git log
git log -n <表示件数上限>
git log --oneline
git log --grep="<検索パターン>"
git log <ファイルパス>
git log --graph
```

### gitコマンド実行履歴

```shell
git reflog
```

### 変更内容の確認

```shell
git diff
git diff <ファイル>
```

## 戻す系

### 特定のコミットに戻す

```shell
git checkout <コミットハッシュ>
```

### 特定のファイルを特定のコミットに戻す

```shell
git checkout <コミットハッシュ> <ファイル>
```

### リポジトリを最新のコミットに戻す

```shell
git checkout <ブランチ名>
```

### 過去のコミットを打ち消す(削除ではなくプラマイゼロ)

```shell
git revert <コミットハッシュ>
```

## プッシュ

### ファイルを登録する

```shell
git add ファイル
```

### 登録したファイルをリセット

```shell
git reset
git reset ファイル
```

### ファイルの変更を保存(コミット)

```shell
git commit -m "メッセージ"
```

### 変更をリモートに反映

```shell
git push -u origin <ブランチ名>
git push -u origin master
```

## タグ関係

[Gitのtagを理解する](https://qiita.com/k-penguin-sato/items/c62b47dd79f144c68dad)

### ローカルタグ一覧

```shell
git tag
```

### タグをつける

```shell
git tag <tag-name>
git tag -a <tag-name> -m "message"
```

### リモートに反映

```shell
git push origin <tag-name>
git push origin --tags
```

### ローカルタグを削除

```shell
git tag -d <tag-name>
```

### リモートタグを削除

```shell
git push origin --delete <tag-name>
```

### タグの詳細情報

```shell
git show <タグ名>
```

## ブランチ

### ブランチを作成

```shell
git branch <ブランチ名>
```

### ブランチのリスト

```shell
git branch
```

### ブランチを削除

```shell
git branch -d <ブランチ名>
```

### ブランチを切り替える

```shell
git checkout <ブランチ名>
```

### ブランチを新規作成＆切り替え

```shell
git checkout -b <ブランチ名>
```

### 現在のブランチと指定したブランチをマージ

```shell
git merge <マージするブランチ名>
```

### ブランチ名変更

```shell
git branch -m <元の名前> <新しい名前>
```

## 参考サイト

[Qiita - 【Git】基本コマンド](https://qiita.com/konweb/items/621722f67fdd8f86a017)

[Qiita - Gitの基本的な使い方メモ](https://qiita.com/opengl-8080/items/451c5967cbbc262f4f0d)

[Qiita - GitHubの使い方と実践](https://qiita.com/nnahito/items/565f8755e70c51532459)

[Qiita - いまさらだけどGitを基本から分かりやすくまとめてみた](https://qiita.com/gold-kou/items/7f6a3b46e2781b0dd4a0)

## Gitコマンドのオプション

```plain
usage: git [--version] [--help] [-C <path>] [-c <name>=<value>]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | -P | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           <command> [<args>]

These are common Git commands used in various situations:

start a working area (see also: git help tutorial)
   clone             Clone a repository into a new directory
   init              Create an empty Git repository or reinitialize an existing one

work on the current change (see also: git help everyday)
   add               Add file contents to the index
   mv                Move or rename a file, a directory, or a symlink
   restore           Restore working tree files
   rm                Remove files from the working tree and from the index
   sparse-checkout   Initialize and modify the sparse-checkout

examine the history and state (see also: git help revisions)
   bisect            Use binary search to find the commit that introduced a bug
   diff              Show changes between commits, commit and working tree, etc
   grep              Print lines matching a pattern
   log               Show commit logs
   show              Show various types of objects
   status            Show the working tree status

grow, mark and tweak your common history
   branch            List, create, or delete branches
   commit            Record changes to the repository
   merge             Join two or more development histories together
   rebase            Reapply commits on top of another base tip
   reset             Reset current HEAD to the specified state
   switch            Switch branches
   tag               Create, list, delete or verify a tag object signed with GPG

collaborate (see also: git help workflows)
   fetch             Download objects and refs from another repository
   pull              Fetch from and integrate with another repository or a local branch
   push              Update remote refs along with associated objects

'git help -a' and 'git help -g' list available subcommands and some
concept guides. See 'git help <command>' or 'git help <concept>'
to read about a specific subcommand or concept.
See 'git help git' for an overview of the system.

```
