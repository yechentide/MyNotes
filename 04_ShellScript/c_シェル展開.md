# シェル展開

## ブレース展開 (Brace Expansion)

`"`で囲むと展開されない

```shell
echo a{1,2,3}			# a1 a2 a3
echo "a{1,2,3}"			# a{1,2,3}
```

## シーケンス式 (sequence expression)

シーケンス式 `{x..y}` を使って連番を生成できる

```shell
for i in {1..10}; do echo $i; done
```

`{x..y..incr}`という書き方で増分を指定できる

```shell
for i in {1..10..3}; do echo $i; done
```

数値以外に文字も指定できる

```shell
for i in {a..f}; do echo $i; done
```

## シェル変数展開 (Shell Parameter Expansion)

### `${parameter}`

基本的な展開

### `${paramter:-word}`

変数 `parameter` が未定義かnull文字の場合、代わりに `word` が展開される。wordを変数paramterに保存しない

```shell
now=
echo ${now:-$(date)}		# 2020年 12月 3日 木曜日 11時47分57秒 JST
```

### `${parameter:=word}`

動作は`:-`と同じ。ただしwordを変数paramterに保存する

```shell
now=
echo ${now:=$(date)}		# 2020年 12月 3日 木曜日 11時47分57秒 JST
echo $now					# 2020年 12月 3日 木曜日 11時47分57秒 JST
```

### `${parameter:?word}`

変数 `parameter` が未定義かnull文字の場合、`word`の展開された結果が標準エラーに出力される

`word`が未定義の場合は、代わりのメッセージが出力される

```shell
now=
echo ${now:?}				# bash: now: parameter null or not set
echo ${now:?"is null"}		# bash: now: is null
```

### `${parameter:+word}`

変数 `parameter` が定義されている（未定義かnull文字以外）場合、`word` が展開され、それ以外の場合は空文字が展開される

wordを変数paramterに保存しない

```shell
now=$(date +"%Y/%m/%d")
echo ${now:+"today is $now"}		# today is 2019/04/30
```

## 部分文字列展開 (Substring Expansion)

### `${parameter:offset}`

```shell
var=0123456789abc
echo ${var:5}			# 56789abc
```

### `${parameter:offset:length}`

```shell
var=0123456789abc
echo ${var:5:3}			# 567
```

### 

## パターンに一致する部分を削除

### `${parameter#word}`

`parameter`の左側から`word`で指定するパターンに最短一致する部分を削除して展開する

### `${parameter##word}`

`parameter`の左側から`word`で指定するパターンに最長一致する部分を削除して展開する

```shell
var=123123123abc456456456

echo ${var#12*3}		# 123123abc456456456
echo ${var##12*3}		# abc456456456
```

### `${parameter%word}`

`parameter`の右側から`word`で指定するパターンに最短一致する部分を削除して展開する

### `${parameter%%word}`

`parameter`の右側から`word`で指定するパターンに最長一致する部分を削除して展開する

```shell
var=123123123abc456456456

echo ${var%45*6}		# 123123123abc456456
echo ${var%%45*6}		# 123123123abc
```

## パターンに一致する部分を置換

### `${parameter/pattern/string}`

最短一致

```shell
var=123123123abc456456456
echo ${var/[[:digit::]]/*}		# *23123123abc456456456
```

### `${parameter//pattern/string}`

最長一致

```shell
var=123123123abc456456456
echo ${var//[[:digit::]]/*}		# *********abc*********
```

## コマンド置換 (Command Substitution)

### バッククォート

従来からある記法

```shell
NOW=`date "+%Y/%m/%d %H:%M:%S"`		# 2020/12/03 12:02:51
```

### `$( )`

新しい記法。ネスト(入れ子)ができる

```shell
NOW=$(date "+%Y/%m/%d %H:%M:%S")	# 2020/12/03 12:02:51
```

## 算術展開 (Arithmetic Expansion)

### `$((算術式))`

```shell
x=10; y=5
echo $x $y							# 10 5
echo "x + y = $(( x + y ))"			# x + y = 15
```


