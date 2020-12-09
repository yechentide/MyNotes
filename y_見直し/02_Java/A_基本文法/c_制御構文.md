# 制御構文

## ループ

### for文

```java
for(初期化; 条件判定; 変化) {
    // ...
}
```

### 拡張for文

```java
for(型 定数名 : 配列など) {
    // ...
}
```

### while文

```java
while(条件) {
    // ...
}
```

### do-while文

最低でも一回は処理を実行する

```java
do{
    // ...
} while(条件)
```

## 条件分岐

### if文

```java
if(条件式) {
    // ...
} else if(条件式) {
    // ...
} else {
    // ...
}
```

### switch文

```java
switch(式) {
    case 値1:
        // ...
        break;
    case 値2:
    case 値3:
        // ...
        break;
    default:
        // ...
        break;
}
```

### 新しいswitch文

Java12以降。プレビュー機能なのでオプション`--enable-preview`をつける
また、値を返す式として使えるようになった
１行なら式の結果をそのまま返すが、複数行のブロック文だと、
Java12では`break 返す値`、Java13では`yield 返す値`で値を返す

```java
switch(式) {
    case 値1,値2 -> /*１行の処理*/
    case 値3 -> /*１行の処理*/
    default -> {
        /*複数行の処理*/
    }
}
```

## その他

### break文

`break`：　処理の流れを強制的に終了し、そのブロックから抜ける

```java
ラベル:

break ラベル;
```

### continue文

`continue`：　ブロック内の処理を飛ばし、ブロックの先頭に戻って次の処理を続ける

### 例外処理

調べる
