# markdownの使い方

## 見出し

```markdown
# 大きい見出し
## ちょい大きい見出し
### 普通見出し
#### ちょい小さい見出し
##### 小さい見出し
###### かなり小さい見出し
```

## リスト

### 順序なし

```markdown
- リスト
    - リスト
    - リスト
* リスト
    * リスト
    * リスト

+ リスト
```

### 順序あり

```markdown
1. リスト
2. リスト
3. リスト
    1. リスト
    2. リスト

1. 数字は
1. 何でもよいが
1. 表示する際は
1. 必ず順番通りになってしまう
```

### チェックボックス

```markdown
- [x] 項目１
- [ ] 項目２
```

## 段落と改行

### 段落

改行を２回する

### 改行

改行をするには行末に空白を2個入れる(半角スペースを最後に2つ)  
~~Typoraでは`shift` + `enter`も可~~

## 強調表現

`*`1個で*斜体で強調*  
`**`2個で**太字で強調**  
`***`3個で***斜体&太字で強調***
フォントにMeiryoとか使ってると、斜体で表示されないので注意。  
まあ斜体はあんま使いどころないので太字で強調だけ覚えておきましょう。

## ソースコードの書き方

### 一行だけ

シングルクォートじゃなくて==バッククォート==！
`loadImage()`

### 複数行

#### そのまま

```markdown
\```            ←\は取り除いく
void setup(){
    size(600,600);
    noStroke();
}
\```            ←\は取り除く
```

### SyntaxHighlight

最初のバッククォートの後に言語名

```markdown
\```processing      ←\は取り除いく
void setup(){
    size(600,600);
    noStroke();
}
\```                ←\は取り除いく
```

## 引用

> 引用したい文の文頭に">"をいれる  
> うぇーい
>> 二重引用には">>"を文頭におく  
>> うぇーい

## 注釈

```markdown
テキスト[^記号]
[^記号]:注釈内容
```

テキスト[^カーソルをここに]  
[^カーソルをここに]:注釈内容

## 線

### 水平線

区切りたい時に使う。  
アスタリスクとかハイフンを3つ以上連続で繋げればいいんだけど、それぞれの間に空白があっても構わない。

```markdown
***
* * *
------------
- - -
_________
_ _ _ _ _ _
```

上記の**どれでも**可！

### 打ち消し線

`~~`で囲む  
~~サンプル~~

## リンク

### リンクだけ

URLを**貼り付けるだけ**でオッケー！

### 名前付きリンク

```markdown
[名前](URL)
```

[Boostnote](https://b00st.io/jp/)

## 画像

```markdown
![画像タイトル](画像URL)
```

## 表

1段目がヘッダで2段目は中央揃えなどの指定法  
ヘッダとそろえ方の指定は**必須**！
|  ヘッダ  | ヘッダ |   ヘッダ |
| :------: | :----- | -------: |
| 中央揃え | 左揃え |   右揃え |
| あんぱん | を     | 食べたい |

## 文法サポートをONにして使えるもの

### ~下付き文字~

`~`で囲む

### ^上付き文字^

`^`で囲む

### ==ハイライト==

`==`で囲む

### LaTeXで数式を表現

`$`でLaTexを囲む。複数行の場合は`$$`を使う  
[typora 数式個人的なまとめ](https://qiita.com/RyosukeKamimura/items/9178a9cbd72196236eaf)

```markdown
$ \ce{CH4 + 2 $\left( \ce{O2 + 79/21 N2} \right)$} $
$ \textcolor{red}{文字色を赤色にする方法} $
$$
a = \frac{1}{b}
\tag{1}
$$
```

$ \ce{CH4 + 2 $\left( \ce{O2 + 79/21 N2} \right)$} $

$ \textcolor{red}{文字色を赤色にする方法} $
$$
a = \frac{1}{b}
\tag{1}
$$

## その他

### HTMLタグ

HTMLタグをそのまま使える！

### 顔文字

顔文字コードを`:`で囲む

### 図形を描く

フローチャート、シーケンス図、ガントチャートなど
