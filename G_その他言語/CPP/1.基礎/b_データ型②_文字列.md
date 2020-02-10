## String型



### 文字列と配列の関係

文字列を「char型の配列」で扱うことができる

```c++
// 配列で初期化
char str01[] = {'H', 'e', 'l', 'l', 'o', '\0'};
char str01[6] = {'H', 'e', 'l', 'l', 'o', '\0'};

// ""で初期化
char str02[] = "World";
char str02[6] = "World";
```

注意：　char配列において、`" "`は初期化の時にのみ使える。後から`" "`で代入できない

```c++
cout << str01 << "\n";
```



### 文字列とポインタ

文字列を「char型のポインタ」で扱うことができる

```c++
char *str03 = "Hello";
str03 = "Goodbye";

cout << str03 << "\n";
```

上のと違って、この場合は`" "`で初期化できるし、再代入もできる

（ポインタの指すアドレスにある文字列が変わる）

```c++
char *p;
    
p = "hello";
cout << p << "\n";      // hello
cout << *p << "\n";     // h
cout << &p << "\n";     // 0x7ffeea816940

p = "bye";
cout << p << "\n";      // bye
cout << *p << "\n";     // b
cout << &p << "\n";     // 0x7ffeea816940
```



### 文字列関連の標準ライブラリー

```c++
#include <string>
```

* `strlen(const char* s)`

   文字列sのNULL文字を除く長さを返す

* `strcpy(char* s1, const char* s2)`

   文字列s2を配列s1にコピーしてs1を返す

* `strcat(char* s1, const char* s2)`

   文字列s2を文字列s1も末尾に追加してs1を返す

* `strcmp(const char* s1, const char* s2)`

   文字列s1とs2を比較し、負の値(s1<s2)、0(s1=s2)、正の値(s1>s2)を返す























