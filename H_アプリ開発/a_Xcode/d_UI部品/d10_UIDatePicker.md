# UIDatePicker



## コードで生成

```swift
import UIKit

class ViewController: UIViewController, UIPickerViewDelegate {
    
    private var myTextField: UITextField!
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        self.view.backgroundColor = UIColor.white

        // DatePickerを生成する.
        let myDatePicker: UIDatePicker = UIDatePicker()

        // datePickerを設定（デフォルトでは位置は画面上部）する.
        myDatePicker.frame = CGRect(x:0, y:50, width:self.view.frame.width, height:200)
        myDatePicker.timeZone = NSTimeZone.local
        myDatePicker.backgroundColor = UIColor.white
        myDatePicker.layer.cornerRadius = 5.0
        myDatePicker.layer.shadowOpacity = 0.5

        // 値が変わった際のイベントを登録する.
        myDatePicker.addTarget(self, action: #selector(ViewController.onDidChangeDate(sender:)), for: .valueChanged)

        // DataPickerをViewに追加する.
        self.view.addSubview(myDatePicker)

        // UITextFieldを作成する.
        myTextField = UITextField(frame: CGRect(x:0,y:0,width:200,height:30))
        myTextField.text = ""
        myTextField.borderStyle = .roundedRect
        myTextField.layer.position = CGPoint(x: self.view.bounds.width/2,y: self.view.bounds.height - 100);

        // UITextFieldをViewに追加する.
        self.view.addSubview(myTextField)
        
        
    }
    
    /* DatePickerが選ばれた際に呼ばれる. */
    @objc internal func onDidChangeDate(sender: UIDatePicker){

        // フォーマットを生成.
        let myDateFormatter: DateFormatter = DateFormatter()
        myDateFormatter.dateFormat = "yyyy/MM/dd hh:mm"

        // 日付をフォーマットに則って取得.
        let mySelectedDate = myDateFormatter.string(from: sender.date)
        myTextField.text = mySelectedDate
    }
    

    
}

```

