# ツールバー

```java
public ToolbarTest01( String title ){
    super( title );

    JPanel pane = (JPanel)getContentPane();

    JToolBar toolbar = new JToolBar();
    pane.add( toolbar, BorderLayout.NORTH );

    JButton item;

    item = new JButton( "Open", new ImageIcon( "open.gif" ) );
    toolbar.add( item );

    item = new JButton( "Save", new ImageIcon( "save.gif" ) );
    item.setHorizontalTextPosition( JMenuItem.LEFT ); //***
    toolbar.add( item );

    toolbar.addSeparator();

    item = new JButton( "exit", new ImageIcon( "exit.gif" ) );
    toolbar.add( item );

}
```

```java
public ToolbarTest02( String title ){
    super( title );

    JPanel pane = (JPanel)getContentPane();

    JMenuBar mb = new JMenuBar();
    setJMenuBar( mb );

    JMenu file = new JMenu( "File" );
    JToolBar toolbar = new JToolBar();

    mb.add( file );
    mb.add( toolbar );

    AbstractButton item;

    item = new JButton( "Open", new ImageIcon( "open.gif" ) );
    file.add( item );
    item = new JMenuItem( "Open", new ImageIcon( "open.gif" ) );
    toolbar.add( item );

    item = new JButton( "Save", new ImageIcon( "save.gif" ) );
    file.add( item );
    item = new JMenuItem( "Save", new ImageIcon( "save.gif" ) );
    toolbar.add( item );

    file.addSeparator();
    toolbar.addSeparator();

    item = new JButton( "Exit", new ImageIcon( "exit.gif" ) );
    file.add( item );
    item = new JMenuItem( "Exit", new ImageIcon( "exit.gif" ) );
    toolbar.add( item );
}
```
