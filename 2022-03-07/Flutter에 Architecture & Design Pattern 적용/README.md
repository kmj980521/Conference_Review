# Flutter에 Architecture & Design Pattern 적용하기

## 요약
[1. 소프트웨어 엔지니어링이란?](https://github.com/kmj980521/Conference_Review/blob/main/2022-03-07/Flutter%EC%97%90%20Architecture%20&%20Design%20Pattern%20%EC%A0%81%EC%9A%A9/README.md#1-%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4-%EC%97%94%EC%A7%80%EB%8B%88%EC%96%B4%EB%A7%81%EC%9D%B4%EB%9E%80)

[2. Pattern이란?](https://github.com/kmj980521/Conference_Review/blob/main/2022-03-07/Flutter%EC%97%90%20Architecture%20&%20Design%20Pattern%20%EC%A0%81%EC%9A%A9/README.md#2-pattern%EC%9D%B4%EB%9E%80)

[3. Architecture & Design Pattern](https://github.com/kmj980521/Conference_Review/blob/main/2022-03-07/Flutter%EC%97%90%20Architecture%20&%20Design%20Pattern%20%EC%A0%81%EC%9A%A9/README.md#3-architecture--design-pattern)

[4. Flutter와 Pattern](https://github.com/kmj980521/Conference_Review/blob/main/2022-03-07/Flutter%EC%97%90%20Architecture%20&%20Design%20Pattern%20%EC%A0%81%EC%9A%A9/README.md#4-flutter%EC%99%80-pattern)

[5. Pattern 적용방법 - BLOC](https://github.com/kmj980521/Conference_Review/blob/main/2022-03-07/Flutter%EC%97%90%20Architecture%20&%20Design%20Pattern%20%EC%A0%81%EC%9A%A9/README.md#5-pattern-%EC%A0%81%EC%9A%A9%EB%B0%A9%EB%B2%95---bloc)

[6. Pattern을 선택하는 가이드라인](https://github.com/kmj980521/Conference_Review/blob/main/2022-03-07/Flutter%EC%97%90%20Architecture%20&%20Design%20Pattern%20%EC%A0%81%EC%9A%A9/README.md#6-pattern%EC%9D%84-%EC%84%A0%ED%83%9D%ED%95%98%EB%8A%94-%EA%B0%80%EC%9D%B4%EB%93%9C%EB%9D%BC%EC%9D%B8)

[7. Flutter 개발자에게 소프트웨어 공학도가 하고 싶은 말 ](https://github.com/kmj980521/Conference_Review/blob/main/2022-03-07/Flutter%EC%97%90%20Architecture%20&%20Design%20Pattern%20%EC%A0%81%EC%9A%A9/README.md#7-flutter-%EA%B0%9C%EB%B0%9C%EC%9E%90%EC%97%90%EA%B2%8C-%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4-%EA%B3%B5%ED%95%99%EB%8F%84%EA%B0%80-%ED%95%98%EA%B3%A0-%EC%8B%B6%EC%9D%80-%EB%A7%90)


---
## 1. 소프트웨어 엔지니어링이란?
- 소프트웨어 생산의 모든 부분과 관련된 공학분야

## 2. Pattern이란?
- 재사용 가능하며, 필요한 목적에 맞는 가장 단순한 형태 

- 소프트웨어 개발 3원칙 
1. 중복을 피하고 **DRY(Don't Repeat Yourself)**
2. 단순하게 **KISS(Keep it simple. stupid)**
3. 필요한 것만 **YAGNI(You Ain't Gonna Need it)**

- ex. 싱글톤, MVVM, Proxy, MVP, Facade, 옵저버, MVC, 프로토 타입 Pattern

## 3. Architecture & Design Pattern

### Architecture Pattern
- 소프트웨어 아키텍처(구조) 관점에서 활용 가능한 패턴
- ex. MVC Pattern, DTO(Data Transfer Object) Pattern

### Design Pattern
- 소프트웨어 디자인(설계) 관점에서 활용 가능한 패턴
`아키텍처가 설계단계의 좀 더 넓은 개념에서 활용 가능하다면, 디자인 패턴은 그 보다 더 작은, 실제 코드 단위(컴포넌트) 단위에서 발생하는 문제들을 해결하기 위해서 사용된다


## 4. Flutter와 Pattern
- 대다수의 개발자가 같은 문제를 겪고 있다
- Architecture Pattern은 작성한 코드의 책임을 명확하게 해준다
- 특히 Flutter에서 Pattern은 앱의 상태를 어디서 변경할지, 언제부터 관측할지 명확하게 해준다
- Flutter에는 다양한 Pattern 선택지가 있다 (ex. MVVM, MVC, Redux, Mobx, Bloc, Provider ....)


## 5. Pattern 적용방법 - BLOC
### Overview
#### BLOC Pattern
- BLOC Pattern은 google의 개발자 Felix Angelo가 제안한 상태 관리 패턴

#### 주요 목적
- Business Logic과 UI의 완전한 분리
- 개발자의 효율적인 코드 재사용
- UI와 Business Logic을 분리하여 테스트

#### 핵심 컨셉
- **Stream** : Business Logic을 구현하는 BLOC 혹은 Cubit에 Dart : Stream이 사용된다. Stream은 비동기 데이터를 받기 위해 사용된다.
- Cubit, BLOC : Presentation Layer가 Business Logic을 구독할 수 있게 해주는 요소

#### 구조적 특징
- Presentation Layer(UI) : Business에서 받은 상태정보를 어떻게 다음 화면에서 보여줄까?
- Business Layer : Data Layer에서 받은 정보를 어떻게 상태정보에 반영할까?
- Data Layer : 비즈니스 로직에 어디서(api, db, etc..)온 정보를 어떤(Data type)으로 가공해서 전달할까? 

![image](https://user-images.githubusercontent.com/61898890/156984018-4300d4ed-42b3-4097-ab3c-e61b1e9578f2.png)

### 설계 방법
1. 프로젝트 폴더 구조 잡기

![image](https://user-images.githubusercontent.com/61898890/156984485-6299e7a8-5711-4e4b-bfdc-807bd90cac0c.png)

[출처:BLOC architecture Samples](https://github.com/brianegan/flutter_architecture_samples/tree/master/bloc_library)

2. 프로젝트 폴더 별 구성, 코드 요약
### blocks 폴더 

#### logic_block.dart  
- Block<Event, State>를 extend 받고, 내부적으로 Stream을 가진다
- Event는 수신할 사용자의 이벤트, State는 Stream으로 넘겨줄 Stream


#### logic_event.dart
- 사용자가 어떤 이벤트를 하고자 하는지를 판단해서 사용자에게 stream 정보를 전송
- **Equatable**을 extends 하고 같은 객체인지를 판단한다 

#### logic_status.dart
- 사용자의 UI가 어떤 Status일 때 어떤 행동을 할 것인지 판별
- **Equatable**을 extends 한다

- Equatable 클래스를 extends 한 경우, get에서 BLOC이 가진 모든 프로퍼티를 넘겨주는데, 정해진 프로퍼티들을 다 넘겨주지 않으면 상태를 Stream으로 계속해서 전송하지 못하는 일들이 발생한다


![image](https://user-images.githubusercontent.com/61898890/156985004-1a91fda4-d7a0-4fd6-a27b-cbb6817e6f82.png)

### model 폴더
- 외부에서 받아오는 데이터는 Dart와 맞지 않을 수 있으니, 모델을 구현하여 Flutter에 어떻게 넘겨줄지 담당하는 코드를 구현한다
![image](https://user-images.githubusercontent.com/61898890/156986660-8dd42fef-d705-4b33-894d-a4b029f5679a.png)

### provides 폴더 
- 특정 서버, 특정 데이터베이스로부터 정보를 받아와서 Decode 후 넘겨준다. 


![image](https://user-images.githubusercontent.com/61898890/156986851-24121b89-cf25-46aa-ba2a-d0b87377a6a9.png)

### Conclusion
- Architecture Pattern으로 재사용 가능한 코드, 코드의 책임 구분, 분명한 테스트 단위의 효과를 볼 수 있다

## 6. Pattern을 선택하는 가이드라인

![image](https://user-images.githubusercontent.com/61898890/156987457-b1ae1faa-dbb0-4716-9bc6-d6088896fbc0.png)

### 전체적인 Process
1. 앱의 특징 확인
- UI와 로직의 분리가 필요할까? 
- Native와의 소통이 필요한가?

2. 상태관리 패키지 선택
- 내가 알고 있는 상태관리는?
- 패키지 의존적인가? 
- 커스텀 가능한가? 
- 상태관리 이외의 기능을 포함하는가? 

3. 테스팅 단위 선택
- 최소한의 테스팅 단위는? 
- 테스팅 기준은?

### Pattern reference
1. State management 
- ex. BLOC, getX, Redux, Provider

2. Testing
- ex. Clean Architecture, BLOC Clean


## 7. Flutter 개발자에게 소프트웨어 공학도가 하고 싶은 말

- `Architecture, Testing, Code review, 개발 문서는 정말 개발 시간을 더 느리게 할까?`에 대한 고민이 필수이다









[출처 유튜브 영상](https://www.youtube.com/watch?v=bp9AlSUsS10)
