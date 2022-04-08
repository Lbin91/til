# Alamofire Tips

Alamofire 사용하면서 쉽게 검색되지 않는 사소한 팁들을 적어본다.

# NoBracket

Alamofire를 통해 서버와 http 통신을 할 때 예를 들어 클라이언트에서 POST 타입의 Request를 날리는데 Parameter중 하나를 배열로 보내야 할 경우가 있다.

보통의 Parameter 들이 

```
["name":"Gildong Hong","Age":30]
```
와 같다면 서버 요청에 따라

```
["category_ids":[3,5,9]]
```
와 같이 요청하기도 한다.

이 경우에 Alamofire의 Encoding 방식을

```
URLEncoding.Default
```

로 지정하였다면 서버에서 request를 수신 했을 때의 값이

```
["category_ids[]":[3,5,9]]
```
처럼 받아지는 경우가 생긴다.


이 경우의 대처법은 Request시 Encoding 방식을 지정해 주는데
