# 変数＆定数&型

## 定数

`const`キーワードを使用して宣言する

定数は、`文字(character)`、`文字列(string)`、`boolean`、`数値(numeric)`のみで使える

==定数は`:=`を使用して宣言することはできない==

## 変数

`var`キーワードで宣言する

複数の変数の後に型を書くことで複数の変数を同時に定義できる

初期値が与えられている場合、変数の型宣言は必要ない

初期化されてない場合、数値型は0、真理型はfalse、文字列型は空文字列になる

```go
var num int
var var1, var2, var3 bool

var str = "Go Programming Language"
var num = 2

var str, num, bool = "Go language", 23, true
```

関数内では`:=`を使った変数宣言もできる

```go
func main(){
   str := "Hello World"
   fmt.Println(str) //=> Hello World
}
```

## 型

`int uint uintptr`型は、OSによって32ビットか64ビットになる

* 真理型：`bool`

* 文字列型：`string`

* 整数型：`int  int8  int16  int32  int64 uint uint8 uint16 uint32 uint64 uintptr`

* 小数型：`float32 float64`

* その他：

    ```go
    byte	// uint8 の別名
    rune	// int32 の別名。Unicode のコードポイントを表す
    complex64
    complex128
    ```

==Goでは暗黙的な型変換は許されていない==

型を変換するときには、`型名(変換したい値)`で変換を行う