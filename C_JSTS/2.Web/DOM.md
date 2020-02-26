# DOM



/* ------------------------ DOM(Document Object Model) ------------------------ */

​    /* windowは省略可 */

​    window.document.getElementById( "id" )

​    window.document.getElementsByName( )

​    window.document.getElementsByTagName( )

​    window.document.getElementsByClassName( )

​    window.document.querySelector( )

​    window.document.querySelectorAll( )



​    window.document.write()

​    window.document.getElementById().innerHTML = ""

​    window.document.getElementById().style.属性 = ""

​    window.document.getElementById().className = ""     // cssのクラスの指定

​    // 例：

​        var target = document.getElementById( "aaa" );

​        target.style.backgroundColor = "red";



/* ------------------------ 要素の取得 ------------------------ */

var a1 = document.getElementById("a_id");               // １個の要素を返す

var a2 = document.getElementsByTagName("a_tag");        // 複数の要素の配列を返す

var a3 = document.getElementsByClassName("a_class");    // 複数の要素の配列を返す

var a4 =document.getElementsByClassName("aa bb");       // 複数のクラスを持つタグを探す



/* ------------------------ 要素の属性の取得＆変更 ------------------------ */

var b1 = a1.getAttribute(属性名);       // 属性は、HTMLを記述した時の属性

a1.setAttribute(属性名, 値);

var b2 = a1.プロパティ名;                // プロパティは、オブジェクトの現在の属性

a1.プロパティ名 = 値;



/* ------------------------ HTMLを書き換える ------------------------ */

// テキストを書き換える

window.onload = function(){

​    var button01 = document.getElementById("button");

​    button01.onclick = function(){

​        var elem = document.getElementById("Sample");   // <p id="Sample">

​        elem.textContent = "ここは書き換える内容";

​    }

}

// HTMLを書き換える

window.onload = function(){

​    var button01 = document.getElementById("button");

​    button01.onclick = function(){

​        var elem = document.getElementById("Sample");   // <div id="Sample">

​        var html = '変更したもの<br><img src="images/aaa.jpg">';

​        elem.innerHTML = html;                          // innerHTMLプロパティを利用して、HTMLを書き換える

​    }

}

/* innerHTMLとtextContentの違い

​    htmlタグが含まれるかどうかで、どれを使うかを決める

*/





/* ------------------------ HTML要素の追加＆削除 ------------------------ */

window.onload = function(){

​    var button01 = document.getElementById("button");

​    button01.onclick = function(){

​        var img = document.createElement("img");

​        img.src = "images/bbb.jpg";

​        document.body.appendChild(img);         // bodyの一番下にimg要素を追加

​    }

}

window.onload = function(){

​    var button0２ = document.getElementById("button");

​    button0２.onclick = function(){

​        var elem = document.getElementById("aaa");

​        document.body.removeChild(elem);

​    }

}



// アンカー＆リンク

​    //*アンカー：　<a name="アンカー名">文字列a</a>

​    //*リンク：　　<a href="#アンカー名">文字列b</a>

​    // アンカーを設定

​        var str = "文字列a";

​        var aaa = str.anchor("アンカー名");

​        document.write("<p>" + aaa + "</p>");

​    // リンクを設定

​        var link1 = "文字列b".link("xxx.html#アンカー名");

​        document.write("<p>" + link1 + "</p>");



// テーブルを作る

var ttt = document.getElementById("table01");

var row01 = ttt.insertRow(-1);

var cell01 = row01.insertCell(-1);

cell01.textContent = "abc";



/* ------------------------ CSSを操作する ------------------------ */

// エレメント.style.プロパティ　　で操作する

​    img.style.left = event.clientX + "px";      // クリックしたところのx座標で画像の座標を変更