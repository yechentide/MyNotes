# 関数

## 関数

シェルスクリプトでは、関数を書いて引用することができる

キーワード`function`は省略可能

```shell
#関数を指定します
function MyFunction () { 
    echo "関数のechoです。"
}
function MyParamFunc() {
    echo "引数1:$1 引数2:$2"
}

#関数を呼び出します
MyFunction
MyParamFunc param1 param2
```
