#swift study record

##2022

## 함수의 리턴을 튜플로 하기
어떤 목적을 가지고 함수를 만들다 보면 
>리턴값을 하나 이상 받고 싶은데...

이런 생각이 들 때가 있다.

이 경우에 유용한 방법이 바로 튜플이다.

```
func makeStringLonger(originalString : String) -> (string,int) {
    let newString = originalString + originalString
    let stringLength = newString.count
    
    return (newString , stringLength)
}

func viewDidLoad() {
    let result = makeStringLonger(originalString : "swift")
    
    let resultString = result.0
    let resultLength = result.1
    
    // resultString = "swiftswift" , resultLength = 10
}
```

이런 리턴 값으로써 튜플의 사용은 가급적 2개로 제한하는걸 권장하고 그 이상의 리턴값이 필요하면 별도의 struct를 만들어서 하는걸 권장한다.
(어느 이름모를 블로그에서 스쳐지나가 본듯..^^)

다만 이런 형태의 경우 0,1 과 같이 뽑아내는 방식 보다는 가독성이 훨씬 높도록 Labeling 해주는 방법을 좀 더 권장함.

```
func makeStringLonger(originalString : String) -> (twiceString : string, stringLength : int) {
    let newString = originalString + originalString
    let stringLength = newString.count
    
    return (newString , stringLength)
}

func viewDidLoad() {
    let result = makeStringLonger(originalString : "swift")
    
    let resultString = result.twiceString
    let resultLength = result.stringLength
    
    // resultString = "swiftswift" , resultLength = 10
}
```

**리턴 값으로의 튜플.. 끝**