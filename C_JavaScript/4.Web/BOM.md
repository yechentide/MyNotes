# BOM



/* ------------------------ BOM(Browser Object Model) ------------------------ */

Window          // 全てのBrowser Objectの親となるオブジェクト

Location        // WebページのURLを情報として持つオブジェクト

History         // Webページの閲覧履歴を情報として持つオブジェクト

Document        // Webページ上の部品の情報を持つオブジェクト



/* ------------------------ Window ------------------------ */

​    window.innerHeight()                // 内部の高さ

​    window.innerWidth()                 // 内部の幅

​    window.alert()                      // 警告のポップアップ

​    window.confirm()                    // 確認のポップアップ

​    window.open()                       // windowを開く

​    window.close()                      // windowを閉じる

​    /* 以下windowは省略可 */

​    window.navigator.appCodeName()

​    window.navigator.appName()

​    window.navigator.appVersion()

​    

​    console.log("Hello World!");            // コンソール出力

​    alert("Hello World!");                  // ポップアップ,   OKボタンしかない

​    confirm("Hello World!");                // ポップアップ,   OKとキャンセルボタン

​    prompt("Hello World!");                 // ポップアップ,   OKとキャンセルボタン、及びデータ入力域

    <script>

​        var input = window.prompt("何かを入力して");

​        document.write("入力したのは" + input + "ですね");

​    </script>



/* ------------------------ Location ------------------------ */

/* 以下windowは省略可 */

window.location.href()              // ページのURL

window.location.pathname()          // URLのパス名

window.location.protocol()          // URLのプロトコル (  http  https  file  )



/* ------------------------ History ------------------------ */

/* 以下windowは省略可 */

window.history.back()               // ページを戻る

window.history.forward()            // ページを進む



/* ------------------------ Document ------------------------ */

// Documentオブジェクトは、Webページ上にある全ての部品の情報を持っている。

// これを介して、個々のHTML要素にアクセスできる

// 一般的にはDOMを使っているが、例外的にフォーム要素に対してのみ、name属性を指定してアクセスが可能となる

document.フォーム名.フォーム内要素名