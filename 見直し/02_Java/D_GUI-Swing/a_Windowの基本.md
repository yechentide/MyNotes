# Windowの基本

## 基本事項

### import

```java
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
```

### windowのタイトル設定

```java
// JFrameそのまま使う場合
JFrame frame = new JFrame( "JFrame03" );
// JFrameを継承した場合、コンストラクタの中に設定
super( title );
```

### windowサイズの設定

```java
frame.setSize(400, 300);
```

### windowの可視化

```java
frame.setVisible(true);
```

### 起動時の動作

```java
// 最小化(アイコン化)
frame.setState( JFrame.ICONIFIED );
// 画面全体に最大化
frame.setExtendedState( JFrame.MAXIMIZED_BOTH );
// 垂直方向に最大化
frame.setExtendedState( JFrame.MAXIMIZED_VERT );
```

OSごとに使えるかをチェック

```java
// 最小化はサポートされていますか？
Toolkit.getDefaultToolkit().isFrameStateSupported(JFrame.ICONIFIED)
// 画面全体の最大化はサポートされていますか？
Toolkit.getDefaultToolkit().isFrameStateSupported(JFrame.MAXIMIZED_BOTH)
// 垂直方向の最大化はサポートされていますか？
Toolkit.getDefaultToolkit().isFrameStateSupported(JFrame.MAXIMIZED_VERT)
// 水平方向の最大化はサポートされていますか？
Toolkit.getDefaultToolkit().isFrameStateSupported(JFrame.MAXIMIZED_HORIZ)
```

### WindowAdapterとWindowListener

### windowを閉じる時の動作

```java
// プログラム終了にする
frame.setDefaultCloseOperation( JFrame.EXIT_ON_CLOSE );

// または、下のコードで、プログラム終了にする
frame.addWindowListener(new WindowAdapter() {
    public void windowClosing(WindowEvent e) {
        System.exit(0);
    }
});
```

または：

```java
public class JFrame04 extends JFrame {
    public static void main(String[] args) {
        new JFrame04( "JFrame04" );
    }
    public JFrame04( String title ){
        super( title );
        setDefaultCloseOperation( JFrame.DO_NOTHING_ON_CLOSE );
        addWindowListener( new WindowClosing() );
        setSize(500, 300);
        setVisible(true);
    }
    class WindowClosing extends WindowAdapter {
        public void windowClosing(WindowEvent e) {
        int ans = JOptionPane.showConfirmDialog( JFrame04.this, "ほんとうに終了しますか？" );
            if( ans == JOptionPane.YES_OPTION ){
                System.exit(0);
            }
        }
    }
}
```

### windowのイベント

```java
public static void main(String[] args) {
    new JFrame07( "JFrame07" );
}

public JFrame07( String title ){
    super( title );
    setDefaultCloseOperation( JFrame.EXIT_ON_CLOSE );
    addWindowListener( new WindowEventHandler() );
    setSize(500, 300);
    System.out.println( "ウインドウの準備が出来ました" );
    setVisible(true);
    System.out.println( "ウインドウの表示がオンになりました" );
    setVisible(false);
    setVisible(true);
}

class WindowEventHandler implements WindowListener {
    public void windowOpened( WindowEvent e ) {
        System.out.println( "ウインドウが開きました" );
    }
    public void windowClosing( WindowEvent e ) {
        System.out.println( "ウインドウが閉じようとしています" );
        System.exit(0); //ここで明示的にアプリケーション終了を指定
    }
    public void windowClosed( WindowEvent e ) {
        //*** System.exit() を明示的に呼び出している場合には、このイベントは通知されない
        System.out.println( "ウインドウが閉じました" );
    }
    public void windowIconified( WindowEvent e ) {
        System.out.println( "ウインドウがアイコン化されました" );
    }
    public void windowDeiconified( WindowEvent e ) {
        System.out.println( "ウインドウがアイコン化から復元しました" );
    }
    public void windowActivated( WindowEvent e ) {
        System.out.println( "ウインドウが活性化しました" );
    }
    public void windowDeactivated( WindowEvent e ) {
        System.out.println( "ウインドウが非活性化しました" );
    }
}
```

```java
public JFrame10( String title ){
    super( title );
    setDefaultCloseOperation( JFrame.EXIT_ON_CLOSE );
    addComponentListener( new ComponentEventHandler() );
    setLocation(100,100);   // windowの初期位置
    setSize(500, 300);
    System.out.println( "ウインドウの準備が出来ました" );
    setVisible(true);
    System.out.println( "ウインドウの表示がオンになりました" );
    setVisible(false);
    setVisible(true);
}

class ComponentEventHandler implements ComponentListener {
    public void componentMoved( ComponentEvent e ){
        System.out.println( "ウインドウが移動しました" );
        Point p = e.getComponent().getLocation();
        System.out.println( "新しい位置は "+ p.x +","+ p.y +" です。" );
    }
    public void componentResized( ComponentEvent e ){
        System.out.println( "ウインドウのサイズが変更されました" );
        Dimension d = e.getComponent().getSize();
        System.out.println( "新しい大きさは "+ d.width +","+ d.height +" です。" );
    }
    public void componentShown( ComponentEvent e ){
        System.out.println( "ウインドウが表示状態になりました" );
    }
    public void componentHidden( ComponentEvent e ){
        System.out.println( "ウインドウが非表示状態になりました" );
    }
}
```

### windowを閉じる前の処理

```java
public JFrame08( String title ){
    super( title );
    Runtime.getRuntime().addShutdownHook( new Shutdown1() );
    Runtime.getRuntime().addShutdownHook( new Shutdown2() );
    // 他は省略
}

class Shutdown1 extends Thread {
    public void run() {
        System.out.println( "シャットダウンフック１が呼び出されました" );
    }
}
class Shutdown2 extends Thread {
    public void run() {
        System.out.println( "シャットダウンフック２が呼び出されました" );
    }
}
```

### windowサイズ

```java
Dimension screenSize = Toolkit.getDefaultToolkit().getScreenSize();
int w = screenSize.width;
int h = screenSize.height;
frame.setBounds( w/4, h/4, w/2, h/2 );
frame.setMinimumSize(new Dimension(000, 100));
```

### ContentPaneに自作JPanel

```java
public JFrame11B( String title ){
    super( title );
    setDefaultCloseOperation( JFrame.EXIT_ON_CLOSE );
    setContentPane( new MyContentPane() );
    setSize( 350, 200 );
    setVisible(true);
}

class MyContentPane extends JPanel{
    MyContentPane(){
        setLayout( null );

        JLabel label = new JLabel( "自分で作ったパネルを ContentPane にしてみました" );
        label.setBounds( 0, 0, 300, 28 );
        add( label );

        JButton b1 = new JButton( "ボタン１" );
        b1.setBounds( 0, 30, 100, 28 );
        add( b1 );

        JButton b2 = new JButton( "ボタン２" );
        b2.setBounds( 0, 60, 100, 28 );
        add( b2 );
    }
}
```
