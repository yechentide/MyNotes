# 例外処理



### エラーへの対処

```javascript
try{
    document.write(aaa);   // aaaは定義されていない
}catch(e){      // エラーeをキャッチする
    document.write("エラー：" + e.description);// エラー内容を出力
}finally{       // catch(){}  と  finally{}  のどっちかがあれば良い
    // .......	
}
```

```javascript
//自分で例外を発生させる・・・throwメッセージ
try{
    throw "wow";
    document.write("hello");      // hello  は出力されない
}catch(e){
    document.write(e.message);    // 出力は   wow
}
```

