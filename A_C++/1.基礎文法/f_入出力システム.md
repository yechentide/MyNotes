# 入出力システム





### 出力

```c++
#include <iostream>
using namespace std;

int main(){
   cout << "Hello, World!\n";
   cout << "Hello, World!" << endl;
   cout << "Hello" << ", " << "World" << "!" << endl;
   
   cout << "変数numの値は" << num << "です\n";
}
```



### 入力

```c++
#include <iostream>
using namespace std;

int main(){
   int num1, num2;
   cin >> num1;
   cin >> num1 >> num2;
   
   string s;
   cin >> s;
   // 入力された１行を丸ごと受け取る
   getline(cin, s);
}
```





## 出入力の基礎



### C++の入出力の基礎

1. 標準入力：`std::cin`
2. 標準出力：`std::cout`
3. 標準エラー出力：`std::cerr`
4. バッファー付き標準エラー出力：`std::clog`、特殊な用途でしか使わない

cinやcoutなどは、全てiostreamヘッダーの中のテンプレートクラスの実体である。

* `std::basic_istream`   -->.  `std::cin`
* `std::basic_ostream`   -->.  `std::cout` `std::cerr` `std::clog`
* `std::basic_iostream`  入力＆出力のどちらもできる



### 書式設定された出力

#### 

* フラグを設定して表示方法を変える

  ```c++
  cout.flags()				// セットされているフラグを取得
  std::cout.unsetf(  std::ios::フラグ名  )	// セットしてあるフラグを外す
  std::cout.setf(  std::ios::フラグ名  )		// フラグをセット
  ```

  |       フラグ名       |                             効果                             |
  | :------------------: | :----------------------------------------------------------: |
  | std::ios::boolalpha  |         bool型を出力するときにtrueとfalseで出力する          |
  |    std::ios::oct     |                    数値を8進数で出力する                     |
  |    std::ios::dec     |                    数値を10進数で出力する                    |
  |    std::ios::hex     |                    数値を16進数で出力する                    |
  |  std::ios::showbase  | 数値を出力するとき、8進数なら0を、16進数なら0xを先頭につける |
  |   std::ios::fixed    |         浮動小数点数を固定表記(123.456000)で出力する         |
  | std::ios::scientific |               浮動小数点数を科学表記で出力する               |
  |    std::ios::left    |                       左詰めで出力する                       |
  |  std::ios::internal  |     中央揃え（何桁の中央に揃えるかは別の方法で指定する）     |
  |   std::ios::right    |                       右詰めで出力する                       |

* flags()関数とsetf()関数のオーバーロード

  ```c++
  flags(フラグの組み合わせ)
  setf(フラグ, フラグの組み合わせ)
  ```

  `flags(フラグ)`は、全てのフラグを、引数のフラグの組み合わせ通りに変更する

  `setf(フラグ, マスクの組み合わせ)`は、第２引数で指定したものを全部クリアして、２つの引数の和集合でフラグ設定する

  | よく使うフラグの組み合わせ |               概要                |
  | :------------------------: | :-------------------------------: |
  |  `std::ios::adjustfield`   | left, internal, rightの組み合わせ |
  |   `std::ios::basefield`    |     dec, hex, octの組み合わせ     |
  |   `std::ios::floatfield`   |   scientific, fixedの組み合わせ   |

  ```c++
  auto defaultFlag = std::cout.flags();
  
  std::cout.setf(std::ios::scientific);						// 科学表記に
  std::cout.setf(std::ios::hex, std::ios::basefield);	// フラグクリア後、16進数フラグをセット
  
  std::cout.flags(defaultFlag);		// デフォルトにリセット
  ```

* 幅、精度、充填文字の指定

  ```c++
  std::streamsize   width() const;
  std::streamsize   width(std::streamsize wide);		// デフォルトは右詰め
  std::streamsize   precision() const;
  std::streamsize   precision(std::streamsize prec);	// デフォルトは有効桁数６桁、整数部分優先
  char   fill() const;
  char   fill(char ch);							// デフォルトは空白が使用される
  ```




### 他のテキスト入出力関数

```c++
std::istream&   get(char* buf, std::streamsize num);
std::istream&   get(char* buf, std::streamsize num, char delim);

std::istream&   getline(char* buf, std::streamsize num);
std::istream&   get(char* buf, std::streamsize num, char delim);
```

* ２引数の`get()`：

  bufに最大num-1文字を保存、必ず最後にヌル文字を付け加える

  改行文字をストリームに残すため、連続に使うと次は空となる

* ３引数の`get()`：

  第３引数で区切り文字を指定できる以外、２引数のと同じ

* ２引数の`getline()`：

  ２引数の`get()`とほとんど同じ

  改行文字をストリームから取り除く

* ３引数の`getline()`：

  第３引数で区切り文字を指定できる以外、２引数のと同じ



### 入出力 マニピュレーターの使用

一部のマニピュレーターは、`#include<iomanip>`する必要がある

```c++
std::cout << std::hex << 1234;		// 16進数に
std::cout.setf(std::ios::boolalpha);
std::cout << std::noboolalpha << true;		// 1
```

|             マニピュレーター             |            効果            |                           補足                            |
| :--------------------------------------: | :------------------------: | :-------------------------------------------------------: |
|              std::boolalpha              | 対応するフラグをセットする |         フラグをクリアするstd::noboolalphaもある          |
|     std::oct,   std::dec,   std::hex     | 対応するフラグをセットする |     oct, dec, hexのうちセットしなかったものは外される     |
| std::left,   std::internal,   std::right | 対応するフラグをセットする | left, internal, rightのうちセットしなかったものは外される |
|      std::fixed,   std::scientific       | 対応するフラグをセットする |   fixed, scientificのうちセットしなかったものは外される   |
|              std::hexfloat               | 浮動小数点数を16進数で表記 |                             -                             |
|              std::showbase               | 対応するフラグをセットする |          フラグをクリアするstd::noshowbaseもある          |
|           std::setfill(char c)           |     充填文字をcにする      |                             -                             |
|         std::setprecision(int p)         |       精度をpにする        |                             -                             |
|             std::setw(int w)             |      幅(桁)をw似する       |                             -                             |



### ファイルの入出力

* ファイルストリーム

  1. `std::ifstream in`：入力用
  2. `std::ofstream out`：出力用
  3. `std::fstream inout`：両用

* ファイルを開くには、コンストラクタにファイル名を渡すか、オブジェクト作成後`open()`を使う

  閉じるには`close()`を使う

  ```c++
  #include <fstream>
  int main(){
     std::ofstream out;
     out.open("aaa.txt");
     out << "Line 1" << std::endl;
     out.close();
     
     std::ifstream in{"aaa.txt"};
     std::string line;
     std::getline(in, line);	// ファイルから１行入力
     in >> line;		// ファイルから１行入力
     in.close();
  }
  ```

* ファイルオープンのモードフラグ

  モードはどのような用途・状態でオープンするかを表す

  `open()`の第２引数、またはコンストラクタの第２引数で渡す。

  or演算子 `|` で複数組み合わせることができる

  途中でモードを変えたいとき、開き直す必要がある

  |   モードフラグ   |                   意味                   |
  | :--------------: | :--------------------------------------: |
  |   std::ios::in   |           入力可能なように開く           |
  |  std::ios::out   |           出力可能なように開く           |
  |  std::ios::app   |  **常に**出力がファイルの末尾に追加する  |
  |  std::ios::ate   | **開くときに**ファイルの末尾にシークする |
  | std::ios::trunc  |        ファイルを空にしてから開く        |
  | std::ios::binary |           バイナリモードで開く           |

* ファイルオープンの失敗

  `is_open()`で確認できる。真理値を返す

* ファイルの終端

  ファイルの終わり＝終端(EOF)。

  ファイルに出力する時に自動的に伸びていくので気にしなくて良い。

  ファイルから入力する時に、`eof()`で確認すべき。`eof()`は真理値を返す

* 書式不定のバイナリ入出力

  バイナリモードで開くことをおすすめ。

  様々な方法で書式を持たないファイル出入力があるが、その中一番低水準なものは`get()` `put()`。

  １バイトだけ入力/出力できる

  `get()`は変数に代入するのに対して、`peek()`は戻り値として返す

  `get()`や`peek()`はint型の値を返すのに、なぜchar型を使うのか？

  それはこの２つの関数では`eof()`関数を使えないので、char型では収まらないEOFとして返すことで判別している

  ```c++
  std::ofstream out{"aaa.bin", std::ios::binary};
  out.put(1);
  out.put(2).put(3);
  out.close()
  
  char a, b, c;
  std::ifstream in{"aaa.bin", std::ios::binary};
  in.get(&a);
  in.get(&b).get(&c);
  a = in.peek();
  ```

  １引数の`get()`と引数なしの`get()`

  ```c++
  // ファイルの中身は１行：　Hello, EOF
  std::ifstream in{"aaa.txt"};
  
  char c;
  if(!in.get(c).eof()){  }
  
  int ci = in.get();
  if(ci!=EOF){  }
  ```

* ブロックのバイナリ入出力

  ```c++
  std::istream&   read(char* buf, std::streamsize num);
  std::ostream&   write(const char* buf, std::streamsize num);
  
  // 読み込んだサイズを調べる
  std::streamsize gcount() const;
  ```

* ランダムアクセス

  現在の位置を知る

  ```c++
  std::ios::pos_type tellg() const;	// 入力ストリームの位置
  std::ios::pos_type tellp() const;	// 出力ストリームの位置
  ```

  現在の位置を変更する

  ```c++
  std::istream&   seekg(std::ios::pos_type position);	// 入力ストリームの位置変更
  std::ostream&   seekp(std::ios::pos_type position);	// 出力ストリームの位置変更
  
  in.seekg(  in.tellg()+std::streamoff{12}  );	// 現在の位置から12バイト後ろに
  
  std::istream&   seekg(std::ios::off_type offset, std::ios::seekdir origin); // 相対位置
  std::ostream&   seekp(std::ios::off_type offset, std::ios::seekdir origin); // 相対位置
  ```

  originに指定できる値：

  1. `std::ios::beg`：ファイルの先頭
  2. `std::ios::cur`：現在の位置
  3. `std::ios::end`：ファイルの最後

* 入出力状態のチェック

  エラーなどの状態に関する情報を`std::ios::iostate`型という値で保存している

  | `std::ios::iostate`の値 |                    意味                    |
  | :---------------------: | :----------------------------------------: |
  |    std::ios::goodbit    |            エラーが起きなかった            |
  |    std::ios::eofbit     |          ファイルの終端に到達した          |
  |    std::ios::failbit    |        致命的ではないエラーが起きた        |
  |    std::ios::badbit     | (復旧できないような)致命的なエラーが起きた |

  現在の情報の取得

  ```c++
  // 全ての情報を取得できるため、ビット演算で結果を分析する必要がある
  std::ios::iostate   rdstate() const;
  // 特定な状態を調べる
  bool good() const;
  bool eof() const;
  bool fail() const;
  bool bad() const;
  ```

  エラーフラグは通常自動的にクリアされない。

  もしエラーを解決できたら、エラーフラグもクリアする必要がある

  ```c++
  void clear(std::ios::iostate flags = std::ios::goodbit);
  // 例：
  std::ifstream in{"aaa.txt"};
  in.clear(std::ios::badbit | std::ios::failbit);	// フラグのセット
  in.clear();													// フラグのリセット
  ```

  



































