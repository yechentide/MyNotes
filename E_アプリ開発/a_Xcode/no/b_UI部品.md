## UI部品



### 引数のsender

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



### UILabel

プロパティ：

* text
* textAlignment
* textColor
* backgroundColor
* isHidden

コードで作る：

```swift
override func viewDidLoad() {
	super.viewDidLoad()
	// Do any additional setup after loading the view.
	
   let myLabel = UILabel()
	myLabel.text = "コードで作った"
	// 表示領域
	myLabel.frame = CGRect(x: 50, y: 50, width: 200, height: 21)
	// 色
	myLabel.textColor = UIColor.black
	myLabel.backgroundColor = UIColor.lightGray
	view.addSubview(myLabel)
   
}
```



### UIButton

プロパティ：

* isEnabled：　ture/false。ボタンの有効・無効
* layer.masksToBounds：　ture/false。角丸にする時にtrueと設定
* layer.cornerRadius：　角丸の半径

メソッド：

* setImage()：　ラベルの横に表示する画像

   反映されるために、カスタムタイプのボタンを作る必要がある

   ```swift
   let aBUtton = UIButton(type: .custom)
   aButton.setImage(image1, for:.normal)
   aButton.setImage(image2, for:.highlighted)
   ```

コードで作る：

```swift
override func viewDidLoad() {
	super.viewDidLoad()
	// Do any additional setup after loading the view.
	
   let myButton = UIButton()
	// 表示領域
	myButton.frame = CGRect(x: 100, y: 100, width: 120, height: 120)
	// 背景画像
	let bgImg = UIImage(named: "maru")
	myButton.setBackgroundImage(bgImg, for: .normal)
	// タイトル
	myButton.setTitle("my button", for: .normal)
	myButton.setTitleColor(UIColor.black, for: .normal)
	// ボタンで実行するメソッド
	myButton.addTarget(self, action: #selector(ViewController.ok(_:)), for: UIControl.Event.touchUpInside)
	view.addSubview(myButton)
   
}
@objc func ok(_ sender:UIButton){
	// コードで関連付けるメソッド
	print("ok")
}
```



### UIStepper

`+` `-`ボタンで数値をアップダウンさせる部品

プロパティ：

* value：　Double型。
* minimumValue：　Double型。
* maximumValue：　Double型。
* stepValue：　Double型。
* autorepeat：　Bool型。長押しの時の動き



### UISwitch

On/Offを切り替えるスイッチ

プロパティ：

* isOn



### UISegmentedControl

複数の選択肢に分割された部品（ラジオボタンのような機能）

プロパティ：

* selectedSegmentIndex



### UISlider

ある範囲の値をスライドバーで指定する

プロパティ：

* value



### UITextField

キーボードからの入力を受け付ける（１行のみ）

複数行を扱うとき、Text Viewを使う

プロパティ：

* placeholder

```swift
class ViewController: UIViewController, UITextFieldDelegate {
	override func viewDidLoad() {
		super.viewDidLoad()
		// Do any additional setup after loading the view.
		tf.delegate = self
	}
	@IBOutlet weak var label: UILabel!
	@IBOutlet weak var tf: UITextField!  
	func textField(_ textField: UITextField, shouldChangeCharactersIn range: NSRange, replacementString string: String) -> Bool {
		// ...
		return true
	}
	func textFieldShouldClear(_ textField: UITextField) -> Bool {
		// ...
		return true
	}
    
	func textFieldShouldReturn(_ textField: UITextField) -> Bool {
		view.endEditing(true)
		return false
	}
	@IBAction func tapView(_ sender: UITapGestureRecognizer) {
		view.endEditing(true)
	}
}
```



### UIPickerView

複数の選択肢を回転ドラム式のコンポーネントで表示し、

コンポーネントごとに値を１つ選ぶための部品

```swift
class ViewController: UIViewController, UIPickerViewDelegate, UIPickerViewDataSource {
	override func viewDidLoad() {
		super.viewDidLoad()
		// Do any additional setup after loading the view.
		myPickerView.delegate = self
		myPickerView.dataSource = self
	}

	@IBOutlet weak var myPickerView: UIPickerView! 
	let compos = [["月","火","水","木","金","土","日"],["早朝","午前中","昼間","夜間"]]
	// 列数指定
	func numberOfComponents(in pickerView: UIPickerView) -> Int {
		return compos.count
	}
	// 行数指定
	func pickerView(_ pickerView: UIPickerView, numberOfRowsInComponent component: Int) -> Int {
		let compo = compos[component]
		return compo.count
	}
	// 幅指定
	func pickerView(_ pickerView: UIPickerView, widthForComponent component: Int) -> CGFloat {
		if component==0 {   // 1列目
			return 50
		} else {
			return 100
		}
	}
	// 項目の表示
	func pickerView(_ pickerView: UIPickerView, titleForRow row: Int, forComponent component: Int) -> String? {
		let item = compos[component][row]
		return item
	}
	// 選ばれた項目を調べる
	func pickerView(_ pickerView: UIPickerView, didSelectRow row: Int, inComponent component: Int) {
		// 選ばれた項目
		let item = compos[component][row]
		print("\(item)が選ばれた")
		// 現在選択されている行番号
		let row1 = pickerView.selectedRow(inComponent: 0)
		let row2 = pickerView.selectedRow(inComponent: 1)
		print("現在選択されている行番号\((row1,row2))")
		// 現在選択されている項目名
		let item1 = self.pickerView(pickerView, titleForRow: row1, forComponent: 0)
		let item2 = self.pickerView(pickerView, titleForRow: row2, forComponent: 1)
		print("現在選択されている項目名\((item1!,item2!))\n-------------------------------")
	}
}
```



### カスタム設定の追加

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





















