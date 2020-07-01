# Layout





## BorderLayout



### 例

```java
public Layout01( String title ){
    super( title );

    JPanel pane = (JPanel)getContentPane();

    JButton buttonNorth = new JButton( "North" );
    pane.add( buttonNorth, BorderLayout.NORTH );

    JButton buttonCenter  = new JButton( "Center" );
    pane.add( buttonCenter, BorderLayout.CENTER );

    JButton buttonSouth = new JButton( "South" );
    pane.add( buttonSouth, BorderLayout.SOUTH );

    JButton buttonWest  = new JButton( "West" );
    pane.add( buttonWest, BorderLayout.WEST );

    JButton buttonEast  = new JButton( "East" );
    pane.add( buttonEast, BorderLayout.EAST );
}
```

`.setPreferredSize( new Dimension(240, 25) )` でボタンのサイズを変更できる





## FlowLayout



### 例

```java
public Layout02( String title ){
    super( title );
    JPanel pane = (JPanel)getContentPane();
    pane.setLayout( new FlowLayout() );

    for( int i=0 ; i<16 ; i++ ){
		pane.add( new JButton( Integer.toString(i) ) );
    }
}
```





## GridLayout



### 例

```java
public Layout03( String title ){
    super( title );
    JPanel pane = (JPanel)getContentPane();
    pane.setLayout( new GridLayout( 4, 3 ) );

    for( int i=0 ; i<10 ; i++ ){
		pane.add( new JButton( Integer.toString(i) ) );
    }
}
```





## BoxLayout



### 例

```java
public Layout04( String title ){
    super( title );
    JPanel pane = (JPanel)getContentPane();
    pane.setLayout( new BoxLayout( pane, BoxLayout.X_AXIS ) );

    for( int i=0 ; i<10 ; i++ ){
		JButton bt = new JButton( Integer.toString(i) );
        // BoxLayout では、preferredSize は無視される
		// bt.setPreferredSize( new Dimension(240, 25) ); 
		pane.add( bt );
    }
}
```









































