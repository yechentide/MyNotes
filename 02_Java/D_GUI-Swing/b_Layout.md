# Layout

## BorderLayout

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

`.setPreferredSize( new Dimension(240, 25) )` でボタンのサイズを変更できる

## GridLayout

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

## SpringLayout

SwiftのConstraintと似ている

```java
Layout05() {
    SpringLayout layout = new SpringLayout();
    Container c =  getContentPane();
    c.setLayout( layout );
    JLabel label1 = new JLabel( "<html><h1>Java</h1>" );
    JLabel label2 = new JLabel( "Swing" );
    JLabel label3 = new JLabel( "JDK" );
    c.add( label1 );
    c.add( label2 );
    c.add( label3 );

    layout.putConstraint( NORTH, label1, 50, NORTH, c );
    layout.putConstraint( WEST, label1, 80, WEST, c );

    layout.putConstraint( NORTH, label2, 20, NORTH, c );
    layout.putConstraint( WEST, label2, 30, EAST, label1 );

    layout.putConstraint( NORTH, label3, 70, SOUTH, label2 );
    layout.putConstraint( WEST, label3, 0, WEST, label2 );

}
```

## GroupLayout

省略
