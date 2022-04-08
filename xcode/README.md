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

## UITableView의 Style

UITableView의 Style에는 세 가지가 존재한다.
```
typedef NS_ENUM(NSInteger, UITableViewStyle) {
    UITableViewStylePlain,          // regular table view
    UITableViewStyleGrouped,        // sections are grouped together
    UITableViewStyleInsetGrouped  API_AVAILABLE(ios(13.0)) API_UNAVAILABLE(tvos)  // grouped sections are inset with rounded corners
};
```

Plain의 경우 가장 흔히 사용하는 스타일이고, Grouped의 경우 테이블뷰가 스크롤링 될 때 헤더의 액션이 달라진다.
Plain의 경우엔 해당 섹션이 완전히 사라지기 전까지 섹션의 최상단에 헤더가 걸리게 되고 해당 섹션의 데이터가 전부 출력되고 다음 섹션의 데이터가 나오게 되면 헤더가 사라지게 된다.

따라서 헤더의 사용법에 따라 Plain과 Grouped를 분리하여 사용하면 좋다.. 그런데 InsetGrouped의 경우에는 iOS에서 만들어진 스타일인것 같은데 아직은 사용해 본 적이 없어서 추후에 알아보기로..

그리고 제일 중요한건 Style의 경우 TableView가 init 되고 난 뒤 바뀌지 않는 값이다. 따라서 storyboard나 xib에서 만든 UITableView를 사용할 경우 코드가 아니라 직접 바꿔줘야 한다.
