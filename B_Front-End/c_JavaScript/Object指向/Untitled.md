### 

### クラス本体定義

```javascript
function Member(a, b, c){
    this.name = a;
    this.age = b;
    this.gender = c;
}
```



### メソッド定義

```javascript
Member.prototype.showAge = function(){
    console.log(this.age);
}
```

