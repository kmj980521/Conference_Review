# Introduce Youtube Flutter Decoding

## 요약
[1. 플러터 디코딩이란?]



## 1. 플러터 디코딩이란?
- take your questions **질문을 받고** / intestigate the behind-the-scenes answers **답변을 연구하고** / unravel the code **플러터 코드의 비밀을 파헤친다** 
- Youtube 플러터 공식 채널의 시리즈 숏폼

## 10개의 문제 해결

### 1. 핫 리로드가 동작하지 않는 이유 

#### 핫 리로드?
- 동작중인 Dart Virtual Machine에 업데이트된 소스코드를 주입하여 VM을 재실행하지 않고 빠르게 업데이트된 코드를 반영하는 feature

![image](https://user-images.githubusercontent.com/61898890/156996282-4274f4fb-f7cb-4549-aa85-b106e051cfc7.png)

- 빌드 최상위부터 차례대로 build 메서드를 재실행한다 

#### 재빌드가 안 되는 것들 
- build 메서드 **밖의 static 변수**
- statefulWidget의 iniotState(), dispose() 
- statelessWidget에서 statefulWidget으로 변경한 경우
- 요약 : **Build 메서드 내부에서 변경된 값들은 hot reload 시 업데이트 된다**


### 2. 위젯의 생명주기

- 케이크를 만드듯이 수정이 쉽지 않다

- Flutter의 위젯은 생명주기가 없으며 상태(State)에 따라 3가지(build, re-build, 사용되지 않음)로 동작한다


### 3. BuildContext란?
- 위젯이 다른 위젯과의 위치 관계나 속성 정보를 가진 것


#### 다른 위젯과 관계를 어떻게 알까?
- BuildContext에 그 답이 있다. 
- Stateful, StatelessWidget은 모두 Widget 클래스를 extends 했다

##### createElement() 메서드
```Dart
@override
StatefulElement createElement() => StatefulElement(this); // override
```
- 이 메서드가 이 위젯의 트리에서 어디에 위치하는지 추적하는 역할을 한다



### 4. Asynce와 Isolate
- 비동기 작업을 하는 thread


#### Async
- Async - Wait without blocking : 블로킹 없이 작업을 수행하며 **다른 스레드를 만들지 않는다**

```Dart

```

#### Isolate
- 메모리를 공유하지 않는 독립적인 작업


### 5. Unbounded height/width error




### 6. Package와 플러그인




### 7. 노란색 밑줄이 그어진 텍스트 




### 8. ShrinkWrap과 Sliver




### 9. 위젯클래스와 헬퍼 메소드




### 10. Tear-off





[출처 유튜브 영상](https://www.youtube.com/watch?v=W6D1MqqPdXs&t=788s)
