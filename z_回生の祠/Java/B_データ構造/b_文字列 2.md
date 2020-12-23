# 文字列

## Stringの変換

### 数値から文字列

```java
//int型
int intvalue=10;
String s1=String.valueOf(intvalue);

//short型
short shortvalue=10;
s1=String.valueOf(shortvalue);

//byte型
byte bytevalue=10;
s1=String.valueOf(bytevalue);

//long型
long longvalue=10;
s1=String.valueOf(longvalue);

//float型
float floatvalue=10.5f;
s1=String.valueOf(floatvalue);

//double型
double doublevalue=10.5;
s1=String.valueOf(doublevalue);
```

### 文字列から数値

```java
String str="10";

//int型
int a_int=Integer.parseInt(str);
//short型
short a_shrot=Short.parseShort(str);
//byte型
byte a_byte =Byte.parseByte(str);
//long型
long l_a=Long.parseLong(str);
//float型
str="10.5";
float f_a=Float.parseFloat(str);
//double型
str="10.5";
double d_a=Double.parseDouble(str);
```

### StringBufferから変換

```java
s1.toString(stringbuffer)
```

## Stringのよく使う操作

### 文字列のコピー

```java
String s1="ねこ", s2="こねこ";
/*①*/s2=new String(s1);
/*②*/s2=s1.toString();
```

### 文字列の比較

```java
s1.equals(s2);
s1.compareTo(c1)    // ???
```

### 文字列の結合

```java
/*①*/s1=s1.concat(s2);
/*②*/s1=s2+"abc";
```

### 文字列の長さ

```java
s1.length();
```

### 部分文字列の取得

```java
s1.charAt(3);       // 1文字のみ
s1.substring(3,5);
```

### 文字列の置換

```java
s1.replace(c1,c2)
```

### 指定文字(列)の出現位置

```java
s1.indexOf(c1)      // 最初の出現位置
s1.lastIndexOf(c1)  // 最後の出現位置
```

### 文字列の分割

```java
s1.split(",")       // ","を区切りで分割
```

## Stringの他のメソッド

### 大小文字を無視して比較

```java
s1.equalsIgnoreCase(s2);
```

### 文字列の先頭＆末尾をチェック

```java
s1.startsWith(s1)
s1.startsWith(s1,offset)    // オフセットからの文字列をチェック
s1.endsWith(s1)
```

### 前後のスペースの削除

```java
s1.trim()
```

### 大・小文字への変換

```java
s1.toUpperCase()
s1.toLowerCase()
```

### 配列要素の連結

```java
String.join("_", 配列);
```

## StringBufferクラス

### なぜ使うか

Javaでは変数の宣言はヒープ(保存スペース)をVMと呼ばれる仕組みの中に確保します。
ループ処理でString等の値がセットされる度にこの保存スペースが新しく作り直されます。
処理速度の低下につながるという問題が起こります。

### 速さ対決

Stringより、StringBufferの方が速いらしい

```java
public class StringSpeedTest {

    public static void main(String[] args) {
        final int count = 100000;

        String str0 = "";
        String appendStr = "@";

        long time1 = System.currentTimeMillis();
        for(int i=0; i<count; i++){
            str0 += appendStr;
        }
        long time2 = System.currentTimeMillis();
        System.out.println("duration1 = "+(time2-time1));
        //System.out.println(str0);


        StringBuffer str1 = new StringBuffer();
        time1 = System.currentTimeMillis();
        for(int i=0; i<count; i++){
            str1.append("@");
        }
        time2 = System.currentTimeMillis();
        System.out.println("duration2 = "+(time2-time1));
        //System.out.println(str1.toString());


    }

}
```

### 利用例

for文内では数値を文字列に変換し生成し、
StringBuilderのインスタン変数valにappendメソッドを使って追加します。
高速になります。

```java
public class StringBuilderTestSample {
    public static void main(String[ ] args) {

        StringBuilder strb = new StringBuilder();
        StringBuffer buff = new StringBuffer();

        long t0= System.currentTimeMillis();
        String str0="";
        for(int count = 0; count < 10000; count++) {

            String str_c = Integer.toString(count);
            //strb.append("値は" + str_c+",");
            buff.append("値は" + str_c+",");
            //str0+=str_c;
        }

        long t1= System.currentTimeMillis();
        //System.out.println(new String(strb).toString());
        System.out.println(new StringBuffer(buff));
        //System.out.println(new String(str0));
        System.out.println("dur time is"+(t1-t0)+"ms");
    }
}
```
