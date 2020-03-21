# UI部品



## 引数のsender

```swift
@IBAction func change(_ sender: UIStepper) {
	let num = sender.value
}
```

このメソッドを呼んだイベントの送り主であるUIStepperのインスタンスの情報が、

引数のsenderとして関数に渡している

```swift
@IBAction func change(_ sender: Any) {
	let stepper = sender as! UIStepper
   let num = stepper.value
}
```



## カスタム設定の追加

カスタムクラス設定で`@IBDesignable`、`@IBInspectable`というデコレータを利用することで、

標準のAttributesインスペクタにはない設定項目を追加できる

```swift
@IBDesignable class BorderedLabel: UILabel {
   @IBInspectable var borderColor: UIColor? {
      get {return UIColor(CGColor: layer.borderColor!)}
      set { layer.borderColor = newValue?.CGColor ?? nil}
   }
   @IBInspectable var borderWidth: CGFloat = 1.0 {
      didSet {
         // didet文はプロパティが更新されると呼ばれる
         lay.borderWidth = borderWidth
      }
   }
}
```

