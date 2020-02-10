## Modern C++ Challenge



### 問題１

与えられた上限までの3または5で割り切れる正の数の総和

```c++
int sum = 0;
int limit = 0;
std::cout << "上限 -> ";
std::cin >> limit;
for(int i=3; i<=limit; i++){
	if(i%3==0 || i%5==0){
		sum+=i;
	}
}
std::cout << limit << "までの3または5で割り切れる正の数の総和は" << sum << "\n";
```



### 問題２

与えられた二つの正の整数の最大公約数を計算して出力

```c++
int gcd(const int a, const int b){
    return b==0 ? a : gcd(b, a%b);
}
```



### 問題３

与えられた二つ以上の正の整数の最小公倍数を計算する

```c++
int lcm(const int a, const int b){
    int h = gcd(a, b);
    std::cout << h << std::endl;
    return a*b/h;
}
```



### 問題15



































