# Socket IO로 채팅 구현하기

회사에서 기존 개발한 어플리케이션의 신규 기능으로 DM 기능을 추가하기로 하였다.

일단은 간편하게 MVP 모델로 빠르게 출시하는것을 목표로 삼은만큼 DM 처럼 보이는 http request를 이용해 채팅처럼 구현 할까도 했지만 이미 백엔드 팀에서 작업해놓은 분량도 있고 어짜피 해야하는 일이라면 하는게 낫다 싶어서 소켓을 이용한 DM 기능을 구현하면서 이곳에 공부한 기능을 남기고자 한다.

소켓 통신의 특징이라면 네트워크 링크를 열어놓고 서버와 클라이언트가 실시간으로 데이터를 주고 받을 수 있다는 것이다.
흔히 쓰이는 http request의 경우 일방향의 방법이라면 소켓은 일단 연결이 성립되면 데이터를 빠르게 주고 받을 수 있다는 장점이 있다.

개발하려는 타겟은 swift를 기반으로 작성된 iOS 어플리케이션이고 이미 소켓을 일부 사용하고 있는 중이라 기본적인 기능은 이미 사용하고 있다.
사용된 라이브러리는 swift에서 널리 쓰이는 SocketIO로 개발 중이다.

# SocketIO
## Basic of Socket

일단 통신을 하기위한 기초가 되는 **URL**이 존재한다.
그리고 그 **URL**을 관리하고 있는것이 **SocketManager**의 역할이다.

해당 **URL**로 연결시 약속된 **Namespace**가 존재하는데 **SocketClient**가 **SocketManager**에게 **Namespace**를 주면서 생성할 수 있다.
이렇게 **SocketClient**가 생성되면 연결을 시도 할 수 있다.

```
socket = self.manger.socket(forNameSpace: "/chat")
socket.connect()
socket.on("test") { dataArray, ack in
    print(dataArray)
}
socket.emit("msg", ["name" : "bongjin", ":content_type": "text", "content": "Hello World!"])
```

위의 코드는 이미 **URL**이 설정된 **SocketManager**에 **Namespace**를 부여하며 **SocketClient**를 생성해 연결을 시도한 코드이다.
3번째 라인엔 on이 있고 "test"라는 String이 있습니다.
on은 Event가 발생 시 데이터를 받는 method이고 저곳의 "test"는 그 Event를 구별하는 **EventName**에 해당합니다.
6번째 라인엔 emit이 있고 "msg"라는 String이 있고 뒤엔 Dictionary Type의 데이터가 존재합니다.
emit은 클라이언트가 서버로 메시지를 보내는 method이고 "msg"는 그 Event의 **EventName**입니다. 뒤의 Dictionary는 서버와 약속된 데이터 형태겠지요.

이것은 가장 기본적인 소켓의 방법인 메시지를 보내고 수신하는 방법 입니다. 소켓으로 작업을 하기위한 1단계에 해당합니다.

다음 단계는 DM을 개발하기 위해 필요한 중요한 부분인 보안 부분에 관련된 기능이 어떤식으로 구현하는지 체크해보겠습니다.