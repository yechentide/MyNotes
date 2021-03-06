# テキスト関連

## 引用

### 長めの引用

段下げして表示される。citeには引用元のURLを指定できる。
`<blockquote cite="...">サンプルテキスト</blockquote>`

### 短めの引用

最初を最後に引用符をつけて表示される。
`<q cite="...">サンプルテキスト</q>`

### 作品のタイトル

作品や仕事のタイトル。イタリック体で表示される。
`<cite>サンプルテキスト</cite>`

### 編集者へ

イタリック体で表示される。
`<address>サンプルテキスト</address>`

### 用語の定義

イタリック体で表示される。
`<dfn>サンプルテキスト</dfn>`

### 強調表示

イタリック体で表示される。
`<em>サンプルテキスト</em>`

### 重要箇所

太字で表示される。
`<strong>サンプルテキスト</strong>`

## その他

### 主題の変わり目

HTML5からは話題の変わり目で使うと定義している。
段落レベルの変わり目で使う。
セクションレベルはsectionを使う
`<hr>`

### 追加と削除

属性に、cite="ファイルのURL", datetime="変更した日時"を指定できる
`<ins>追加された部分を示す。一般的には下線つき</ins>`
`<del>削除された部分を示す。一般的には取消線つき</del>`

### ruby

任意のテキストにふりがな(ルビ)をふることができる

```html
自転車で<ruby>濃昼<rt>ごきびる</rt></ruby>海水浴場に行った
```

ルビを対応しないブラウザ：

```html
<ruby>濃昼   <rp>(</rp>   <rt>ごきびる</rt>   <rp>)</rp>   </ruby>
```
