# 標準出入力

## 標準出力

### コンソールに出力

```java
System.out.print()
System.out.println()
```

### 書式を指定して出力

```java
// 書式指定(C言語のprintfみたいな感じ)
System.out.printf("%dと%dの合計は%d", 1, 2, 1+2);
```

書式文字列は、`%` `フラグ` `表示幅` `.精度` `変換文字`で構成される。`%`と`変換文字`だけは必須

* フラグ：`-` `+` `0` `,` `(`
* 表示幅：最低限の表示幅指定
* .精度：小数点以下の桁数or出力する文字数
* 変換文字：小数`f`、整数`d`、文字列`s` `S`、文字`c` `C`、論理値`b`

## 標準入力

### BufferedReaderを使う

```java
import java.io.*;

BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
try {
    System.out.print("何かを入力して --> ");
    String line = reader.readLine();
    System.out.println(line);
} catch(IOException e) {
    System.out.println(e);
}
```

### Scannerを使う

```java
import java.util.Scanner;
import java.util.InputMismatchException;

// 1行入力(空白があると２行になる)
Scanner scanner = new Scanner(System.in);
String str = scanner.next();
System.out.println(str);

// 整数を入力
try {
    int number = scanner.nextInt();
    System.out.println(number);
} catch(InputMismatchException e) {
    System.out.println("型が違います: " + e);
}

// 連続入力
while(scanner.hasNext()) {
    String line = scanner.nextLine();
    lines.add(line);
}

// 区切り文字の指定(デフォルトは空白)
scanner.useDelimiter(",");
```
