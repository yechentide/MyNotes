# TCP通信





## 説明

ObjectInout/OutputStreamとSocket通信(tcp)を用いる



### オブジェクトを通信させるには

java.io.Serializableを実装すること。
default package(src直下)で実装すること。
受けわたされるオブジェクトのクラスは外部のクラスから参照するため、

関数には必ずpublic修飾子をつけること。

```java
public class XXXX implements Serializable{}
```





## サーバー側









## クライアント側

