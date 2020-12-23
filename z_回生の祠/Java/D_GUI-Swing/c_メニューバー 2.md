# メニューバー

## 基本

### メニューバーの設定

```java
public JFrame11( String title ){
    super( title );
    setDefaultCloseOperation( JFrame.EXIT_ON_CLOSE );

    JMenuBar menuBar = new JMenuBar();
    setJMenuBar( menuBar );
    menuBar.setToolTipText( "ここはメニューバーです" );

    JMenu file = new JMenu( "File" );
    JMenu edit = new JMenu( "Edit" );
    JMenu help = new JMenu( "Help" );
    menuBar.add( file );
    menuBar.add( edit );
    menuBar.add( help );

    contentPane = (JPanel)getContentPane();
    contentPane.setToolTipText( "ContentPane は Swing コンポーネントです" );

    setSize(400, 300);
    setVisible(true);
}
```

```java
public MenuTest01( String title ){
    super( title );

    JMenuBar menuBar = new JMenuBar();
    setJMenuBar( menuBar );

    JMenu file = new JMenu( "File" );
    menuBar.add( file );

    JMenuItem item;
    item = new JMenuItem( "Open" );
    file.add( item );

    item = new JMenuItem( "Save" );
    // item = new JMenuItem( "Save", new ImageIcon( "save.gif" ) );
    // item.setHorizontalTextPosition( JMenuItem.LEFT );
    item.setToolTipText( "保存" );
    file.add( item );

    file.addSeparator();
    item = new JMenuItem( "Exit" );
    file.add( item );
}
```

## ラジオボタン＆チェックボックス

```java
public MenuTest04( String title ){
    super( title );

    JMenuBar menuBar = new JMenuBar();
    setJMenuBar( menuBar );

    JMenu menu1 = new JMenu( "メニュー1" );
    menuBar.add( menu1 );
    JMenu menu2 = new JMenu( "メニュー2" );
    menuBar.add( menu2 );

    JMenuItem item;  

    ButtonGroup bg1 = new ButtonGroup();  
    item = new JRadioButtonMenuItem( "和食" );
    menu1.add( item );
    bg1.add( item );
    item = new JRadioButtonMenuItem( "中華" );
    menu1.add( item );
    bg1.add( item );
    item = new JRadioButtonMenuItem( "洋食" );
    menu1.add( item );
    bg1.add( item );

    item = new JCheckBoxMenuItem( "和食" );
    menu2.add( item );
    item = new JCheckBoxMenuItem( "中華" );
    menu2.add( item );
    item = new JCheckBoxMenuItem( "洋食" );
    menu2.add( item );

    JButton btn = new JButton("クリア");
    btn.addActionListener( new ActionListener() {
        public void actionPerformed( ActionEvent event ) {
            bg1.clearSelection();
        }
    });
    JPanel pane = (JPanel)getContentPane();
    pane.setLayout( new FlowLayout() );
    pane.add(btn);
}
```

## popメニュー(右クリック)

```java
public MenuTest05( String title ){
    super( title );

    JPopupMenu popup = new JPopupMenu();
    JMenuItem item;

    item = new JMenuItem( "Open", new ImageIcon( "open.gif" ) );
    popup.add( item );
    item = new JMenuItem( "Save", new ImageIcon( "save.gif" ) );
    popup.add( item );
    popup.addSeparator();
    item = new JMenuItem( "Exit", new ImageIcon( "exit.gif" ) );
    popup.add( item );

    enableEvents( AWTEvent.MOUSE_EVENT_MASK );
}

protected void processMouseEvent( MouseEvent e ){
    //System.out.println( e );
    if( e.isPopupTrigger() ){
        popup.show( e.getComponent(), e.getX(), e.getY() );
    }
    super.processMouseEvent( e );
}
```
