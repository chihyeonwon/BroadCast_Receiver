# BroadCast_Receiver
[Android] 주요 4대 컴포넌트 - Broadcast Receiver
[안드로이드 Broadcast Receiver 공식 개발 문서](https://developer.android.com/guide/components/fundamentals#ActivatingComponents)
```
배터리 정보 앱 개발
```
## Broadcast Receiver
Broadcast Receiver 라는 이름에서 알 수 있듯, Broadcast 를 수신할 수 있는 구성요소를 의미한다. 
근데 애초에 브로드캐스트가 무엇인지 모르기 때문에 뭘 수신하는 녀석인지 알 길이 없다.
간략하게 브로드캐스트의 개념부터 알아보자.

## Broadcast
브로드캐스트의 뜻은 방송이다. 안드로이드에서 브로드캐스트도 비슷한 맥락이다. 
브로드캐스트란 안드로이드 시스템이나, 기타 앱에서 특정 이벤트가 발생할 때 시스템 전역에 이를 알리는 것이다.
이를테면 폰이 부팅됐을 때, 충전이 시작됐을 때, 전화가 왔을 때와 같은 다양한 시스템 이벤트가 발생할 수 있고,
이것이 발생할 때 브로드캐스트를 뿌리는 것이다.

## Broadcast 를 수신하는 녀석
브로드캐스트는 어떤 이벤트가 발생할 때 시스템 전역에 이를 방송하는 것이라 했는데, 
그럼 몇몇 앱들은 필요에 따라 관심있는 브로드캐스트에 대해서 수신을 해서 이벤트 처리를 해볼 수 있지 않겠는가?

![image](https://github.com/chihyeonwon/BroadCast_Receiver/assets/58906858/38f1338f-a500-4b61-9999-3031d578cbfc)

TV 방송도 불특정 다수에게 방송을 송출하고, 몇몇 사람들은 필요에 따라 수신료를 내고 해당 채널을 수신하게 된다. 똑같은 원리이다. 
예를들어 충전이 시작됐을 때 브로드캐스트가 발생하고, 만약 충전 시작 시 애니메이션을 재생하는 앱을 구현한다면 해당 브로드캐스트를 수신하여 동작을 구현할 것이다.

```
이렇게 브로드캐스트를 수신하는 구성요소를 'Broadcast Receiver' 라고 한다.
앱이 특정 브로드캐스트를 수신하는 Broadcast Receiver 를 등록하면,
시스템은 해당 리시버가 수신하는 브로드캐스트가 발생할 때마다 해당 앱에 브로드캐스트를 자동으로 라우팅해준다.
이 동작은 옵저버 패턴으로 구현된다.
```
![image](https://github.com/chihyeonwon/BroadCast_Receiver/assets/58906858/599fbb2f-eef4-4cf8-a5a2-6bc6b2bb3024)

## Broadcast Receiver 활용

- ACTION_TIME_TICK
- ACTION_TIME_CHANGED
- ACTION_TIMEZONE_CHANGED
- ACTION_BOOT_COMPLETED
- ACTION_PACKAGE_ADDED
- ACTION_PACKAGE_CHANGED
- ACTION_PACKAGE_REMOVED
- ACTION_PACKAGE_RESTARTED
- ACTION_PACKAGE_DATA_CLEARED
- ACTION_PACKAGES_SUSPENDED
- ACTION_PACKAGES_UNSUSPENDED
- ACTION_UID_REMOVED
- ACTION_BATTERY_CHANGED
- ATION_POWER_CONNECTED
- ACTION_POWER_DISCONNECTED
- ACTION_SHUTDOWN

이러한 것들을 수신하면 스마트폰의 상태 변화, 각종 인터럽트 발생 등의 동작을 알아차릴 수 있고 앱에서 쉽게 이들을 대응하는 동작을 구현해볼 수 있다.      
```
또한 앱에서 브로드캐스트를 발생할 수도 있고, 다른 앱이 이를 수신받게 할 수도 있다. 다방면으로 활용가능한 컴포넌트이다.
```

## 브로드 캐스터 리시버 생성
![image](https://github.com/chihyeonwon/BroadCast_Receiver/assets/58906858/6f3b6bc9-b9fe-42d9-bce4-335aa725ecda)

## 배터리 상태 제어
![image](https://github.com/chihyeonwon/BroadCast_Receiver/assets/58906858/a55c66b9-81fd-42b5-b700-91e3fb8603a3)
```
충전량 charge level, 충전기, 배터리 상태를 조정한다.
```
![image](https://github.com/chihyeonwon/BroadCast_Receiver/assets/58906858/4bfcf3b8-005a-4f58-9309-675068a2fb63)

#### 배터리를 80%으로 변경
![image](https://github.com/chihyeonwon/BroadCast_Receiver/assets/58906858/4008e270-5280-4c81-a84b-e9efd921e1e4)

![image](https://github.com/chihyeonwon/BroadCast_Receiver/assets/58906858/b083e9e3-a30a-4eb2-b130-2f4a297d3898)
```
배터리의 상태를 감지하여 보여줍니다.
```

#### 배터리의 상태를 charging 에서 not charging으로 변경
![image](https://github.com/chihyeonwon/BroadCast_Receiver/assets/58906858/d3683879-1fe5-4242-847f-b31f61fe0a53)
![image](https://github.com/chihyeonwon/BroadCast_Receiver/assets/58906858/fbf5c4ec-d78e-43d1-9e53-e327e0612aa9)

