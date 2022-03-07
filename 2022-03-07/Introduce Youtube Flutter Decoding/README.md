# Introduce Youtube Flutter Decoding

## 요약
[1. 플러터 디코딩이란?](https://github.com/kmj980521/Conference_Review/blob/main/2022-03-07/Introduce%20Youtube%20Flutter%20Decoding/README.md#1-%ED%94%8C%EB%9F%AC%ED%84%B0-%EB%94%94%EC%BD%94%EB%94%A9%EC%9D%B4%EB%9E%80)

[2. 핫 리로드가 동작하지 않는 이유](https://github.com/kmj980521/Conference_Review/blob/main/2022-03-07/Introduce%20Youtube%20Flutter%20Decoding/README.md#2-%EC%9C%84%EC%A0%AF%EC%9D%98-%EC%83%9D%EB%AA%85%EC%A3%BC%EA%B8%B0)

[3. 위젯의 생명주기](https://github.com/kmj980521/Conference_Review/blob/main/2022-03-07/Introduce%20Youtube%20Flutter%20Decoding/README.md#3-buildcontext%EB%9E%80)

[4. BuildContext란?](https://github.com/kmj980521/Conference_Review/blob/main/2022-03-07/Introduce%20Youtube%20Flutter%20Decoding/README.md#4-async%EC%99%80-isolate)

[5. Async와 Isolate]()

[6. Unbounded height/width error]()

[7. Package와 플러그인]()

[8. 노란색 밑줄이 그어진 텍스트]()

[9. ShrinkWrap과 Sliver]()

[10. Tear-off]()


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


---

### 2. 위젯의 생명주기

- 케이크를 만드듯이 수정이 쉽지 않다

- Flutter의 위젯은 생명주기가 없으며 상태(State)에 따라 3가지(build, re-build, 사용되지 않음)로 동작한다


---


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



---


### 4. Async와 Isolate
- 비동기 작업을 하는 thread


#### Async
- Wait without blocking : 블로킹 없이 작업을 수행하며 **다른 스레드를 만들지 않는다**

```Dart
void _refresh() async {
  var url = _assembleUrl(options);
  var content = await http.get(url);
  var articles = _parse(content); // _parse를 Isolate로 구현할 수 있다
  _update(articles);

}
```
- 한 작업이 끝날 때까지 기다릴 때 사용한다
- 대부분의 작업은 Async만으로도 가능하지만 무거운 작업인 경우에는 어떻게 해야할까?

#### Isolate
- Run in Parallel : 병렬로 작업을 실행한다
- Isolate는 다른 Isolate에 **전혀 영향을 미치지 않으며**, **동시에 최고속도로 수행**된다
- 메모리를 공유하지 않는 독립적인 작업


---


### 5. Unbounded height/width error
- Column에 Listview를 넣게 되는 경우 자주 발생한다. (주로 Listveiw의 ShrinkWrap 속성을 true로 해서만 해결하는 경우가 있다. 그러나 그 이유는 왜일까?)
- Flutter의 layout 퍼포먼스를 높이기 위한 알고리즘에서 파생되는 에러이다

#### 위젯의 알고리즘을 배치하는 기술 
- Single Pass
- Constraints go down : Container의 최대 크기값을 하위로 전달
- Geometry goes up : 위치와 크기 정보를 상위로 전달

#### 해결법
- 에러는 없지만 원하지 않는 결과 
- Column이 서로 상호작용하며 정보를 전달
- Unbounded height error (Size 같은 제한된 크기의 위젯을 사용하거나 expand(), flexible()로 감싼다)

---

### 6. Package와 플러그인
- 앱의 기능 구현을 위해 필요하다
- ex. url_launcher : url을 실행하기 위한 플러그인

#### Package
- 순수한 dart 코드로 만들어진 것

#### 플러그인
- 자바, 코틀린, 스위프트, 자바스크립트 코드가 포함된 것. 
- 즉 **다른 코드가 포함된 것**


---

### 7. 노란색 밑줄이 그어진 텍스트 
- Text 위젯은 위젯 트리를 올라가다 DefaultTextStyle을 발견하고 이를 적용한다
- Scaffold : 건물 외벽에 인부들이 이동하는 지지대라는 뜻에서 파생

#### DefaultTextStyle은 Scaffold에 정의되어 있었다

![image](https://user-images.githubusercontent.com/61898890/157015499-cbbe732a-1876-4b43-9a4a-62102ce04347.png)

#### 해결 방법
- DefaultTextStyle을 가진 위젯을 추가한다
- Scaffold를 상단에 추가한다

---

### 8. ShrinkWrap과 Sliver
- ShrinkWrap이 true인 경우 스크롤바의 크기를 결정하기 위해 ListView의 모든 위젯을 강제로 만든다 (만약 타일에 아이콘이 많이 들어가거나 애니메이션이 들어간다면 성능 저하로 이어질 수 있다)
![image](https://user-images.githubusercontent.com/61898890/157015939-e5a1ce05-7e9b-4bb0-829d-80df8c4ceafc.png)

#### 그렇다면 shrinkWrap을 안 쓰고 어떻게 성능을 개선할 수 있을까?
- outerList를 감싸는 ListView를 **CustomScrollView**로 바꾼다
- outerListChildren을 **SliverList**로 바꾼다
- outerListChildren의 내부 아이템을 **delegate가 필요한 SliverList**로 바꾼다

##### Before

![image](https://user-images.githubusercontent.com/61898890/157016514-ec115152-2c65-49c7-bd52-8f24f3341aac.png)

##### After

![image](https://user-images.githubusercontent.com/61898890/157016545-b3ed5cd2-2fc0-4227-a9b9-ab7411ff483f.png)

#### 해결 방법
- shrinkWrap:true가 보이면 **SliverList로 바꾸자!**



---

### 9. 위젯클래스와 헬퍼 메소드
#### 헬퍼 메서드
- 입력 변수가 오픈되어 있어, 변수 전달이 상대적으로 쉽다 
- 또한, 코드량이 적다는 장점이 있다
- 직관적이지가 않고, Widget이라 명시하지 않는다면 내부 내용을 확인해야 한다
- 내부에 setState가 있다면, 이 헬퍼메서드를 포함한 모든 위젯은 리빌드 된다 (만약 애니메이션 위젰이 있으면 성능 저하의 요인이 된다)**


```dart
Widget someWidget() {
  return Container();
}
```

#### 위젯 클래스
- const 생성자가 있으면 위젯을 재사용함으로써 위젯의 재생성하는 불필요한 작업들을 줄일 수 있다
- 내부에서 buildContext를 사용하는 경우 잘못된 buildContext 사용으로 인한 bug를 사전에 예방할 수 있다


```dart
class SomeWidget extends StatelessWidget{
  ...
}
```

> Classes have a better default behavior. The only benefit of methods is having to write a tiny bit less code. There's no functional benefit

#### 결론

- 불필요한 빌드를 방지하기 위해 **최대한 위젯 클래스를 사용**하자
- **Const 생성자를 이용**하자


---

### 10. Tear-off
- 불필요한 익명 함수를 사용하지 않고, **함수시그니쳐를 제공하는 방법**

##### tear-off 전
```dart
ElevatedButton(
  onPressed: () {
    myHandler();
  },
  child:: ...,
)
```

##### tear-off 후
```dart
ElevatedButton(
  onPressed:myHandler();
  child:: ...,
)
```
- 익명람다함수의 사용을 줄이고 Tear-off를 잘 활용하자

[출처 유튜브 영상](https://www.youtube.com/watch?v=W6D1MqqPdXs&t=788s)

## Going forward (그 외 시리즈 채널)
- Begin learning Flutter
- Further your Flutter skills!
- Flutter Widget of the Week
- Flutter Apprentice Book Club
- Events
- Flutter in Focus
- The Boring Flutter Development Show
