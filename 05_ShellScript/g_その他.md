# その他

## コマンド

### echo

- オプション `-n` : 改行(newline)が抑制される
- オプション `-e` : エスケープキャラクタが有効になる

```shell
$ echo -n "abc"; echo "def"
abcdef
$ echo "Hello\tWolrd"
Hello\tWolrd
$ echo -e "Hello\tWolrd"
Hello   Wolrd
```

### read

入力を受け付ける。入力を待っている時、スクリプトが続かない

```shell
read NAME
echo "Hello, $NAME!"
```

### printf

- オプション `-v var` : 出力結果を変数varに格納する

### source

filenameで指定したシェルスクリプトを読み込める

`.`はsourceの別名

```shell
source test.sh
. aaa.sh
```

### 選択させる

```shell
select option in CODE DIE
do
	echo "you pressed ${option}"
	break
done

# 1) CODE
# 2) DIE
# #? 2
# you pressed DIE
```

### ファイルを読み込む

```shell
./readFile.sh data.txt

# readFile.sh
i=1
while read line #受け取ったデータを１行ずつ処理↲
do
	echo "${i}: ${line} "
	i=`expr $i + 1`
done <$1		#第一引数(ファイル)の指定
```

#### splitみたいな機能

IFSはシェル変数で文字列を分割する区切り文字が設定されている

デフォルトは半角スペース、タブ、改行となる

```shell
# 半角スペース区切り
while read c1 c2
do
  echo "$c1 + $c2 = $((c1 + c2))"
done < input.txt

# カンマ区切り：IFSで区切り文字を指定
while IFS=, read c1 c2
do
  echo "$c1 + $c2 = $((c1 + c2))"
done < input.txt
```

## デモ

### ファイルを読み込む

* 半角スペース区切り

    ```shell
    while read c1 c2
    do
      echo "$c1 + $c2 = $((c1 + c2))"
    done < input.txt
    ```

* カンマ区切り

    IFSはシェル変数で、文字列を分割する区切り文字が設定されている。デフォルトは半角スペース、タブ、改行になる

    ```shell
    while IFS=, read c1 c2
    do
      echo "$c1 + $c2 = $((c1 + c2))"
    done < input.txt
    ```

### ディレクトリの一覧

```shell
for dir in `find $(pwd) -mindepth 1 -type d`; do echo $dir; done
```

### ファイル・ディレクトリの存在チェック

```shell
if [ -e input.txt ]; then echo "file is exists"; else echo "file is not exists"; fi
```

- ファイルの存在チェックは`-f`
- ディレクトリの存在チェックは`-d`
- シンボリックリンクの存在チェックは`-L`

### ディレクトリのシンボリックリンク

```shell
if [ -d dir1 -a -L dir1 ]; then echo "dir is symbolic link"; else echo "dir is not symbolic link"; fi
```

## 参考サイト

[Bashシェルスクリプトの書き方（基本）のおさらいメモ](https://qiita.com/rubytomato@github/items/173a812d7a8ec4646955)

[★★★Bashの便利な構文だがよく忘れてしまうものの備忘録](https://qiita.com/Ping/items/57fd75465dfada76e633)

[★★プログラマーの君！ 騙されるな！ シェルスクリプトはそう書いちゃ駄目だ！！ という話](https://qiita.com/piroor/items/77233173707a0baa6360)

[★★初心者向け、「上手い」シェルスクリプトの書き方メモ](https://qiita.com/m-yamashita/items/889c116b92dc0bf4ea7d)

[★シェルスクリプトを書くときに気をつける9箇条](https://qiita.com/b4b4r07/items/9ea50f9ff94973c99ebe)

[初心者向けシェルスクリプトの基本コマンドの紹介](https://qiita.com/zayarwinttun/items/0dae4cb66d8f4bd2a337)

[シェルスクリプトBash入門](https://qiita.com/ebisennet/items/573618ab827ce1660b0e)

[Shell Scriptの基本](https://qiita.com/tsukasa_wear_parker/items/c129541654308f0ee505)

