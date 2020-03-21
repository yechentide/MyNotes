# UIPickerView



## 説明

複数の選択肢を回転ドラム式のコンポーネントで表示し、

コンポーネントごとに値を１つ選ぶための部品



## コードで生成

```swift
import UIKit

class ViewController: UIViewController, UIPickerViewDelegate, UIPickerViewDataSource {
    
    private var myUIPicker: UIPickerView!
    private let myValues: NSArray = ["その一","その二","その三","その四"]

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        
        // UIPickerViewを生成.
        myUIPicker = UIPickerView()
        // サイズを指定する.
        myUIPicker.frame = CGRect(x: 0, y: 0, width: self.view.bounds.width, height: 180.0)

        // Delegateを設定する.
        myUIPicker.delegate = self
        // DataSourceを設定する.
        myUIPicker.dataSource = self

        // Viewに追加する.
        self.view.addSubview(myUIPicker)
        
        
    }
    
    func numberOfComponents(in pickerView: UIPickerView) -> Int {
        return 1
    }

    /* pickerに表示する行数を返すデータソースメソッド. (実装必須) */
    func pickerView(_ pickerView: UIPickerView, numberOfRowsInComponent component: Int) -> Int {
        return myValues.count
    }

    /* pickerに表示する値を返すデリゲートメソッド. */
    func pickerView(_ pickerView: UIPickerView, titleForRow row: Int, forComponent component: Int) -> String? {
        return myValues[row] as? String
    }

    /* pickerが選択された際に呼ばれるデリゲートメソッド. */
    func pickerView(_ pickerView: UIPickerView, didSelectRow row: Int, inComponent component: Int) {
        print("row: \(row)")
        print("value: \(myValues[row])")
    }

    

    
}

```



## 複数列

### 

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

