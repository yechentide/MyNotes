# JFrame





## 基本構造



### 枠組み

```java
import javax.swing.*;
import java.awt.*;

public class MyAPP extends JFrame {

    public static void main(String[] args){
        MyAPP window = new MyAPP("GUIアプリ復習");
        window.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        Dimension screenSize = Toolkit.getDefaultToolkit().getScreenSize();
        // setSize( 350, 200 );
        window.setBounds( screenSize.width/4, screenSize.height/4, screenSize.width/2, screenSize.height/2 );
        window.setMinimumSize(new Dimension(300, 200));
        window.setVisible(true);
    }

    public MyAPP(String title){
        super(title);

		// 何もない真っ白な画面

    }


}
```



### メニューバー

```java
import javax.swing.*;
import java.awt.*;

public class MyAPP extends JFrame {

    public static void main(String[] args){
        // 省略
    }

    public MyAPP(String title){
        super(title);

        /* ---------- ---------- ---------- メニューバー ---------- ---------- ---------- */
        JMenuBar menuBar = new JMenuBar();
        menuBar.setToolTipText("ここはメニューバーです");
        setJMenuBar(menuBar);

        JMenuItem item;
        ButtonGroup bg1 = new ButtonGroup();
        
        // メニューA
        JMenu m1 = new JMenu("メニューA");
        menuBar.add(m1);
        
        item = new JRadioButtonMenuItem("ラジオボタン01");
            m1.add(item);
            bg1.add(item);
		item = new JRadioButtonMenuItem("ラジオボタン02");
            m1.add(item);
            bg1.add(item);
        item = new JRadioButtonMenuItem("ラジオボタン02");
            m1.add(item);
            bg1.add(item);
        
        // メニューB
        JMenu m2 = new JMenu("メニューB");
        menuBar.add(m2);
        
        item = new JMenuItem( new ImageIcon( "open.gif" ) );
            item.setToolTipText( "開く" );
            m2.add( item );
        file.addSeparator();	// 分割線
		item = new JMenuItem( new ImageIcon( "save.gif" ) );
			item.setToolTipText( "保存" );
			m2.add( item );
        
        // メニューC
        JMenu m3 = new JMenu("メニューC");
        menuBar.add(m3);

    }


}
```



### 内容

```java
import javax.swing.*;
import java.awt.*;

public class MyAPP extends JFrame {

    public static void main(String[] args){
        // 省略
    }

    public MyAPP(String title){
        super(title);

        /* ---------- ---------- ---------- 内容 ---------- ---------- ---------- */
        JPanel p = (JPanel) getContentPane();
        p.setToolTipText("ContentPane は Swing コンポーネントです");
        p.setLayout(new BorderLayout());

        JPanel leftButtonPanel = new JPanel();
        leftButtonPanel.setLayout(new GridLayout(5, 1));
        for (int i = 1; i <= 5; i++) {
            leftButtonPanel.add(new JButton(Integer.toString(i)));
        }
        p.add(leftButtonPanel, BorderLayout.WEST);

    }


}
```







































