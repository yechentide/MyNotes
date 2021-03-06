# ファイル出入力

## ファイル出力

### PrintWriterを使う

```java
import java.io.*;

try {
    String filename = "aaa.txt";
    PrintWriter writer = new PrintWriter(new BufferedWriter(new FileWriter(filename)));
    for(int i=0; i<10; i++) {
        writer.println(i);
    }
    writer.close();
} catch(IOException e) {
    System.out.println(e);
}
```

## ファイル入力

### BufferedReaderを使う

```java
import java.io.*;

String filename = "aaa.txt";
try {
    BufferedReader reader = new BufferedReader(new FileReader(filename));
    String line;
    while((line = reader.readLine()) != null) {
        System.out.println(line);
    }
    reader.close();
} catch(FileNotFoundException e) {
    System.out.println(filename + "が見つかりません。");
} catch(IOException e) {
    System.out.println(e);
}
```

### Scannerを使う

```java
import java.util.Scanner;
import java.io.FileNotFoundException;
import java.io.File;

try{
    String filename = "aaa.txt";
    File file = new File(filename);
    Scanner scan = new Scanner(file);
    scan.useDelimiter("¥¥r¥¥n");
    int line = 1;
    while(scan.hasNext()) {
        String str = scan.next();
        System.out.println(line + ":" + str);
        line++;
    }
} catch(FileNotFoundException e) {
    System.out.println(e);
}
```
