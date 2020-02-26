# jQuery



/* ------------------------------ jQuery ------------------------------ */

/***利用の準備

​    ① http://jquery.com/ でダウンロードして、<>script src=""></script>で読み込む

​    ② GoogleサーバーのjQueryを直接読み込む

        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>

*/

/***プラグイン

​    ① LightBox

​        https://lokeshdhakar.com/projects/lightbox2/

*/



// 基本の書き方

$(document).ready(  function(){/*ここにjQueryコード*/}  );        // readyメソッドはHTMLタグ解析後に実行される

$(function(){

​    $("セレクタ").メソッド()        // DOM操作の基本書式。セレクタはcssのセレクタ

});



$("msg").css("font-size", "30px");



// 要素の抽出

​    // ①フィルタ機能を利用して、セレクタで取得した要素に対して絞り込む

​        $("セレクタフィルタ").メソッド()

​        /*例*/

​            $("li:first").css("color","red");

​            $("li:not(:first)").css("background-color","red");

​        /***フィルタ一覧

​         \* :first               先頭の要素

​         \* :last                末尾の要素

​         \* :even                奇数番目の要素

​         \* :odd                 偶数番目の要素

​         \* :contains(文字列)     指定した文字列を含む要素

​         \* :not(要素)            指定した要素を除外する

​         \* :eq(インデックス)      指定したインデックスを持つ要素

​         \* :selected            選択状態になっている要素

​         \* :checked             チェックが入っている要素

​         \* [属性名=値]           指定した属性値を持つ要素

​        */

​    // ②ある要素群から条件を指定して要素を絞り込む

​        要素群.filter("セレクタやフィルタ");

​            /*例１*/

​                var elm = $("#fruits > li");            // 取得した要素を変数に代入することで、重複な要素検索を避け、処理速度を上げる

​                elm.css("background-color", "red");

​                elm.filter(":even").css("color", "white");

​            /*例２*/

​                // メソッドチェーン

​                $("#fruits > li").css("background-color", "red").filter(":even").css("color", "white");

​        要素群.find("セレクタやフィルタ");

​            // 要素群の子孫要素の中から、条件に合うものを探す



// 内容と属性の変更

​    要素.html(値);

​        // 要素に含まれる内容を操作する。引数指定しない場合は内容を返す。指定する場合は内容を上書きする。

​        // 対象要素が複数の場合、変更は全てを変更、取得は先頭を取得

​    要素.val(値);

​        // value属性値を操作する。引数指定しない場合は内容を返す。指定する場合は内容を上書きする。

​        // 対象要素が複数の場合、変更は全てを変更、取得は先頭を取得

​    要素.attr("属性名",値);

​        // value以外の属性値を変更する。第２引数を指定しない場合は内容を返す。指定する場合は内容を上書きする。

​        // 対象要素が複数の場合、変更は全てを変更、取得は先頭を取得

​    要素.removeAttr("属性名");

​        // 指定した属性を全ての要素から削除する

​        // 要素.attr("属性名","");でも削除できる

​        // しかし、selectedなどの値がない属性はremoveAttr()で削除できない

​    要素.on("イベント名", 関数に渡す引数, 関数名or関数式);

​        // イベントハンドラを登録する

​        // イベント名は、on をつけない

​        // 引数がないときは、第２引数は省略可能

​        /*例*/ $("#btn").on(   "click", function(){}   );

​        /*例*/ $("#btn").on(   "click", {name: "よしお"}, function(event){alert(event.data.name + "さん、こんにちは!")}   );

​    要素.off("イベント名", 関数名);

​        // イベントハンドラを削除する

​        // 第２引数の関数名を省略する場合、指定したイベントに設定された全ての関数が削除される

​    $(this)

​        // イベント発生元の特定

​    要素.css("プロパティ", "値");

​        // CSSプロパティを一つ一つ指定する

​    要素.addClass("CSSクラス名");

​        // 要素に対してCSSクラスを追加する

​    要素.removeClass("CSSクラス名");

​        // 要素からCSSクラスを削除する

​    要素.toggleClass("CSSクラス名");

​        // CSSクラスの追加と削除を交互に繰り返す

​        /*例*/ $("input").on(   "change",function(){ $("#area1, #area2").toggleClass("active passive"); }   );



// 要素の挿入

​    要素.append("HTML要素");

​        // 要素内の末尾に新しい要素を挿入する。（子要素の追加）

​    要素.prepend("HTML要素");

​        // 要素内の先頭に新しい要素を挿入する。（子要素の追加）

​    要素.after("HTML要素");

​        // 要素の後に新しい要素を追加する。

​    要素.before("HTML要素");

​        // 要素の前に新しい要素を追加する。

​    要素.empty();

​        // 要素の子要素を全て削除する

​    要素.replaceWith("HTML要素");

​        // 要素を指定した別の要素で置き換える



// アニメーション

​    要素.show(速度);

​    要素.hide(速度);

​    要素.toggle(速度);

​        // 要素を表示・非表示・表示状態を交互に切り替える。

​        // 引数は、"slow"(600ms), "normal"(400ms), "fast"(200ms), およびミリ秒と指定できる

​        // 引数を省略すると、0msとなる

​    要素.slideDown(速度);

​    要素.slideUp(速度);

​        // slideDown()で要素を表示し、slideUp()で要素を非表示する

​        // 引数はshow()と同じだが、省略すると"normal"(400ms)となる

​    要素.fadeIn(速度);

​    要素.fadeOut(速度);

​        // fadeIn()で要素を表示し、fadeOut()で要素を非表示する

​        // 要素の透明度のみが変化する

​        // 引数はshow()と同じだが、省略すると"normal"(400ms)となる



// 独自アニメーション

​    要素.animate(   {CSSプロパティ群}, 速度, イージング, callback関数   );

​    // イージングは、アニメーションの実行速度に緩急をつけるもの。"linear"は一定速度、"swing"は出だし遅く後半速め

​    // callback関数は、アニメーション完了後に実行する関数。第２引数(速度)以降は省略可能











/* -------------------- HTMLが読み終わるまで、スクリプトの実行を待たせる -------------------- */

$(document).ready(   function(){}   );

$(   function(){}   );



/* -------------------- 基本構文 -------------------- */

$("セレクタ").html("変更内容");         // 内容変更

$("セレクタ").html();                       // 内容取得

$("セレクタ").css("background", "red"); // CSS変更



$("button").click(function(){

​    $(this).html("clicked");

​    $(this).css("background", "gray");

​    /* メソッドチェーン

​    \* 一つのセレクタに対してh複数のメソッドを連結させる書式

​    \* スクリプトが簡略化され、処理も速くなる

​    \* $(this).html("clicked").css("background", "gray");

​    */

});



/* -------------------- メソッド http://api.jquery.com/ -------------------- */



// CSSや属性に関するもの

css("属性", "値")

addClass("クラス名")

removeClass("クラス名")

hasClass("クラス名")// 真理値

width()

height()

offset().top

offset().left

scrollTop()// 要素のスクロール位置を取得

attr()

/*****/$("img").attr("src", "./images/img03.jpg")// 要素の属性を設定する

/*****/$("img").attr("src")// 属性の取得

val()

/*****/$("input").val()// value属性の取得



// HTMLに関するもの

html()

/*****/$("p").html("変更内容")// 内容変更

/*****/$("p").html()// 内容取得

prepend()

/*****/$("ul").prepend("<li>List01</li>")// 要素の挿入。冒頭に追加

/*****/$("ul").prepend($("li:last-child"))// 要素の移動。擬似クラスを利用して、最後の要素を冒頭に移動

append()

/*****/$("ul").append("<li>List01</li>")// 要素の挿入。末尾に追加

/*****/$("ul").append($("li:first-child"))// 要素の移動。擬似クラスを利用して、最初の要素を末尾に移動

remove()// 要素の削除

index()// セレクタで指定した要素が、同階層においての順番を返す。０から。



// イベントに関するもの

click()

hover()

mousemove()

scroll()



// 効果に関するもの

show()

hide()

fadeIn()

fadeOut()

slideToggle()

animate()

stop()



// 要素の検索に用いられるもの

children()

parent()

each()