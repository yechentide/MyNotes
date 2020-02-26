# 基本の基本



### Webページで使う

1. HTMLファイルに書く

   `<script> ...... </script>`

2. 外部ファイルを読み込む

   `<script type="text/javascript" src="......">   </script>`



### js無効のブラウザへの対処

```html
<script>
// <! --
    .....
// -- >
</script>
<noscript>無効です</noscript>
```



### strictモード

より厳格なエラーチェックを行うモードで、プログラム全体or関数単位で設定できる。

`"use strict";` をプログラムor関数の先頭に書くとこのモードになる

