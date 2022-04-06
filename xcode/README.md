# xcode 공부 내용들

## IBOutlet의 Optional object의 이유

화면이 존재하는 class의 경우
```sh
@IBOutlet var viewMain : UIView!
@IBOutlet var buttonConfirm : UIButton?
```
과 같이 추가하는 경우가 있다.

이 경우 뒤에 !가 붙는 경우와 ?가 붙는 경우가 있다.

보통 !가 붙는 경우 Optinal 처리가 없어서 간편하긴 하지만 무조건 !로 object를 선언해서는 안된다.

* xib나 storyboard의 실제 객체와 연결되지 않았을 경우
* 상속 받은 자식 class가 있는데 해당 객체와 연결되어 있지 않는 경우

이 경우에 !로 객체 선언 시 오류가 발생 할 수 있다.

동일하게 상속받아서 객체를 연결해 줄 수 있다면 !로 강제로 선언해 주어도 좋지만 그렇지 않다면 옵셔널로 받는것이 좋다.
