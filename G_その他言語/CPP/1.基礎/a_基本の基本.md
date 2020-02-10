## 基本の基本



### コメント

```c++
// コメント
/*
	コメント
*/
```



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



### main関数

最後の`return 0;`は省略しても良い

暗黙的に 0 を返しているなのだ























