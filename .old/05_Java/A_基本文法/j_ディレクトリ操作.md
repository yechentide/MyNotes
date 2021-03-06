# ディレクトリ操作

## ファイルを操作する

### ファイルの削除

```java
import java.io.*;

public class DeleteFile1 {
    public static void main(String[] args) {

        if(args.length != 1) {
            System.out.println("使用法：java DeleteFile1 削除ファイル");
            System.out.println("例：java DeleteFile1 trash.txt");
            System.exit(0);
        }
        String filename = args[0];
        File file = new File(filename);
        if(file.delete()) {
            System.out.println(filename + "を削除しました。");
        } else {
            System.out.println(filename + "は削除できませんでした。");
        }

    }
}
```

### ファイルの名前変更

```java
import java.io.*;

public class RenameFile1 {
    public static void main(String[] args) {

        if(args.length != 2) {
            System.out.println("使用法：java RenameFile1 現在のファイル名 新しいファイル名");
            System.out.println("例：java RenameFile1 old.txt new.txt");
            System.exit(0);
        }
        String oldfilename = args[0];
        String newfilename = args[1];
        File oldfile = new File(oldfilename);
        File newfile = new File(newfilename);
        if(oldfile.renameTo(newfile)) {
            System.out.println(oldfilename + "を" + newfilename + "に変更しました。");
        } else {
            System.out.println(oldfilename + "を" + newfilename + "に変更できませんでした。");
        }

    }
}
```

### ファイルの存在確認

```java
import java.io.*;

public class RenameFile2 {
    public static void main(String[] args) {

        if(args.length != 2) {
            System.out.println("使用法：java RenameFile2 現在のファイル名 新しいファイル名");
            System.out.println("例：java RenameFile2 old.txt new.txt");
            System.exit(0);
        }
        String oldfilename = args[0];
        String newfilename = args[1];
        File oldfile = new File(oldfilename);
        File newfile = new File(newfilename);
        if(!oldfile.exists()) {
            System.out.println(oldfilename + "が見つかりません。");
        } else if(newfile.exists()) {
            System.out.println(newfilename + "はすでに存在します。");
        } else if(oldfile.renameTo(newfile)) {
            System.out.println(oldfilename + "を" + newfilename + "に変更しました。");
        } else {
            System.out.println(oldfilename + "を" + newfilename + "に変更できませんでした。");
        }

    }
}
```

## ディレクトリを操作する

### ディレクトリの一覧を得る

```java
import java.io.*;

public class ListDir1 {
    public static void main(String[] args) {

        if (args.length != 1) {
            System.out.println("使用法：java ListDir1 ディレクトリ名");
            System.out.println("例：java ListDir1 doc");
            System.exit(0);
        }
        String dirname = args[0];
        File dir = new File(dirname);
        String[] dirlist = dir.list();
        for (int i = 0; i < dirlist.length; i++) {
            System.out.println(dirlist[i]);
        }

    }
}
```

### ディレクトリを作成する

```java
import java.io.*;

public class MakeDir1 {
    public static void main(String[] args) {

        if (args.length != 1) {
            System.out.println("使用法：java MakeDir1 ディレクトリ名");
            System.out.println("例：java MakeDir1 doc");
            System.exit(0);
        }
        String dirname = args[0];
        File dir = new File(args[0]);
        if (dir.mkdirs()) {
            System.out.println(dirname + "を作成しました。");
            System.out.println("絶対パスは" + dir.getAbsolutePath() + "です。");
        } else {
            System.out.println(dirname + "を作成できませんでした。");
        }

    }
}
```
