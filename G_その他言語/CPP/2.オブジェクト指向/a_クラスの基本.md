## クラスの基本



### クラス宣言

アクセス指定子を省略したら、全て`private`となる

```c++
class クラス名 {
   アクセス指定子:
   	変数宣言;
   	メンバ関数宣言;
};
```

メンバ関数の定義：

クラス宣言の中に定義するメンバ関数は、inline関数となる

```c++
戻り値の型 クラス名::メンバ関数名(型 仮引数名, 型 仮引数名, ...){
   // ...
   return 戻り値;
}
```

例：

```c++
class Car {
   public:
   	int num;
   	double gas;
   	void show();
};
void Car::show(){
   cout << "車のナンバーは" << num << "です\n"
}
```



### 使い方

```c++
Car car1;
car1.num = 1234;
car1.gas = 20.5;
car1.show();
```

オブジェクトを動的に生成する

```c++
Car *pCar = new Car;
pCar->num = 1234;
pCar->gas = 20.5;
delete pCar;
```



### カプセル化

デフォルトで`private`となる

**同じクラスの異なるインスタンスであれば、互いのprivateメンバにアクセスできる**

```c++
class Car {
   private:
   	int num;
   	double gas;
   public:
   	void show();
   	void setNumGas(int n, double g);
};
```





### クラスのポインタ＆参照

```c++
Car *pCar = &car1;
cout << pCar->num;
```

```c++
Car &rCar = car1;
cout << rCar.num;
```



### コンストラクタ

コンストラクタの定義

デフォルト引数も使えるぞ〜

```c++
クラス名::クラス名(型 仮引数名, 型 仮引数名, ...){
   // ...
}
```

```c++
Car::Car(){
   num = 0;
   gas = 0.0;
}
Car::Car(int n, double g){
   num = n;
   gas = g;
}

Car car1;					// num=0, gas=0.0
Car car2(1234, 20.5);	// num=1234, gas=20.5
Car cars[6];
```



### 静的メンバ

`static`をつける

```c++
クラス名::変数
クラス名::関数
```























