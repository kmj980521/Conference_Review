# Flutter Korea

## 1. Flutter에 Architecture & Design Pattern 적용
<details>
 <summary> 발표자 송승현님</summary>
- BLOC Pattern, 폴더 구조

[유튜브 영상](https://www.youtube.com/watch?v=bp9AlSUsS10)
</details>
 
----


## 2. Flutter에 네이티브 모듈 연동하기

<details>
 <summary>발표자 김기범님</summary>
 
 ### 크로스 플랫폼인데 네이티브 모듈을?
 - 기존 네이티브 모듈을 꼭 서야할 때가 있다
 - 네이티브 모듈을 포팅하기 어려울 때
 - 네이티브 모듈이 더 효율적일 때
 
 ### 네이티브 모듈을 포팅하기 어려운 경우
 - 네이티브 로직이 복잡할 때
 - 네이티브 로직이 아예 공개가 안 되어 있을 때
 
 ### 네이티브 모듈이 더 효율적인 경우
 - 유지보수 비용이 덜 들어가는 경우
 - 네이티브 퍼포먼스가 더 뛰어난 경우
 
 ### 연동하기
 #### 데이터와 연동하기
 - 네이티브 모듈을 실행할 때, Flutter 쪽 데이터가 필요한 경우
 - ex) 초기 설정값, 사용자 인증 정보
 
 
 #### UI와 연동하기 
 - 네이티브 모듈을 실행할 때, Flutter 쪽 UI가 필요한 경우
 - ex) 네이티브 화면 내에서 Flutter 앱바 및 페이지 띄우기
 
 
 ### 어떻게 연동할 것인가?
 
 #### Method Channel
 - Flutter <-> Native 양방향 통신으로 데이터와 로직을 공유 
 
 ![image](https://user-images.githubusercontent.com/61898890/157690645-3a164c95-bcef-43a5-baae-b7284b4bfe95.png)
  
 #### Flutter view
 - Flutter UI + Native UI를 한 화면에 녹여낼 수 있다
 
 ![image](https://user-images.githubusercontent.com/61898890/157690910-8e3667f5-80ed-4d3a-8a74-e93d726f8243.png)

 
 ### 네이티브 모듈 연동시 질문해볼 것들
 - 네이티브를 연동하는 것이 **최선인가?**
 - Flutter 쪽 데이터에 **많이 의존적인 모듈인가?**
 - Flutter 쪽 UI에 많의 의존적인 모듈인가?
 - 메인 언어가 아닌(ex. Python, JavaScript)를 사용하는가?
 
 ### Case1: 음성영상 수업 모듈
 - 전문가와 음성 및 영상 통화 가능
 - 1:1 통화, 그룹 통화 가능
 - 실시간 채팅 및 사용자 제어 기능
 
 #### 네이티브로 개발하는 것이 더 효율적인가?
 - Dart로 포팅하기에는 부담이 크다.
 - 내부 코드를 알기 어렵다
 - 유지보수 부담도 매우 크다
 - 과연 퍼포먼스 이점이 있을지 고민이 된다. 
 - 데이터에 의존적이지 않기 때문에 네이티브 위주로 개발을 한다
 
 
 ![image](https://user-images.githubusercontent.com/61898890/157692130-9f871de1-f0da-4766-a31e-7900330f4b73.png)

 ### case2: 텍스트 에디터
 - 질문에 답변할 때 사용하는 텍스트 에디터
 - 폰트 수정, 미디어 첨부 가능한 Rich Text
 - 임시 저장, 발행 옵션 설정 기능
 
#### 네이티브로 개발하는 것이 더 효율적인가?
 - Dart로 포팅하기에는 부담이 컸다
 - 글을 불러오고, 저장하고, 등록할 때, Flutter 데이터와 로직에 많이 의존을 했다
 - MethodChannel도 글 저장, 호출 할 때 **양방향으로** 액티브하게 중계를 했다
 - Flutter Ui에 굉장히 의존적이었다
 - Flutter UI가 언제 어디서든 나올 수 있어야 했다
 
 ![image](https://user-images.githubusercontent.com/61898890/157693630-649853ce-f757-4c84-a96d-11f20bcef4f9.png)

 
 ### case3: 파이썬 모듈 연동
 - 기존에 만든 파이썬 로직을 Dart로 포팅하기 귀찮을 때
 - pub.dev에 없는 파이썬 라이브러리를 연동하고 싶을 때 (ex. SciPy, Numpy)
 
 #### Starflut
 - Python을 실행할 수 있는 Dart 패키지
 - Python 외에도 Ruby, Golang, Rust 등 실행이 가능하다
 - 그러나 Python 라이브러리 설치는 어렵다
 - 사용법이 직관적이지는 않다
 
 #### Chaquopy
 - Python을 실행할 수 있는 Dart 패키지
 - Python 라이브러리 설치 지원
 - Starflut 보다 사용법이 직관적이다.
 
 `Chaquopy.executaCode("print('helloworld')");`
 
 - 하지만 유료 라이센스가 필요하다
 - Android 환경에서만 지원이 된다
 
 
 [유튜브 영상](https://www.youtube.com/watch?v=nIqTfAeYc3Y)
 
 </details>
 



---

## 3. Introduce Youtube Flutter Decoding

<details>
 <summary>발표자 김선호님</summary>
 
 - 김선호님 
- 플러터 디코딩
- 핫 리로드가 동작하지 않는 이유
- 위젯의 생명주기
- BuildContext란?
- Async와 Isolate
- Unbounded height/width error
- Package와 플러그인
- 노란색 밑줄이 그어진 텍스트
- ShinkWrap과 Sliver
- 위젯클래스와 헬퍼 메소드
- Tear-off

[유튜브 영상](https://www.youtube.com/watch?v=W6D1MqqPdXs)
 
 </details>
 



---


## 4. [알잘딱깔쎈] Flutter Embedded

<details>
 <summary>발표자 박제창님</summary>
 
 - Raspberry Pi에 Flutter 연결하기
 
 ### Flutter Engine
 - Flutter Engine을 수정, 포팅해서 사용하여 ARM64 아키텍처 시스템에서 구동이 가능하도록 커스터마이징 작업을 진행
 
 ![image](https://user-images.githubusercontent.com/61898890/157800157-76d7c549-c054-4aec-a9f0-fe5c3354761d.png)

 - 임베디드 시스템에 대한 진입장벽이 크고 Flutter를 적용하기에는 빌드 및 포팅하는 과정이 복잡하고 Toolchain(LLVM등)에 대한 이해와 linux GUI 시스템에 대한 이해 등등이 필요하다
 
 
 ### Raspberry Pi GPIO
 
 
 
[유튜브 영상](https://www.youtube.com/watch?v=jW3pqIpQtQE&t=1s)
 
 </details>
 

---


## 5. 예비 창업자로서 플러터를 선택한 이유와 활용계획

<details>
 <summary>발표자 김진섭님</summary>
 
 
 - PMF (Product Market Fit) : 제품 시장 적합성
 
 ### 플러터를 선택한 이유
 - CTF(Company Tech Fit): 회사 기술 적합성
 - 현재 우리 회사의 스테이지, 개발 인력 등을 고려할 때 어떤 기술이 적합할까?
 - 얼리 스테이지, 모바일 1, 백엔드 1의 개발자가 필요하다고 가정
 
 #### 캐치업하기 쉬운가?
 - 러닝커브가 가파른가, 완만한가?
 - JS 기반의 리액트 네이티브의 경우 기존 JS 개발자들이 쉽게 적응 가능
 - 플러터 이전에 나온 프레임워크로서 더 많은 레퍼런스와 커뮤니티 존재
 - 플러터의 경우 비교적 생소한 다트를 사용하지만 자바와 비슷한 문법으로 쉽게 적응이 가능하다
 - 직관적이고 사용이 쉬운 기본 위젯들로 빠르게 결과물을 낼 수 있다
 
 #### 왜 RN이 아닌 플러터인가?
 - 압도적 성능
 - 현재까지의 성장세
 - 앞으로의 성장가능성
 
 ### PTF(Product Tech Fit) 측면
 - 제품 기술 적합성
 - 제품이 과연 이 기술과 잘 맞을지
 - 플러터를 써도 될지
 
 #### 광고 제작 측면
 - 페인트 및 제스처 기능이 핵심적
 - Canva처럼 기본 도형을 제공하고 제스처를 통한 도형의 이동, 확대, 축소를 구현
 - 플러터 인스펙터를 통해 정확한 위치값(화면의 offset)을 계산할 수 있다
 - 성능 측면에서 아쉬운 점이 전혀 없었다
 
 #### 광고 분석 측면
 - 트래킹하는 광고 지표들을 차트로 보여주는 기능
 - FI chart 패키지를 사용했지만 커스텀 페인트로 직접 그려도 크게 어렵지 않았다
 
 #### 도입 예정 기능 측면
 - OAuth, 결제, 지도 등 현재 도입 예정 기능에서 프러터로 구현 불가능한 것은 없다
 - 만약 생긴다고 해도 플러터 개발을 유지한 채 메서드 채널을 통해 해결할 예정이다
 
 
 ### 플러터 활용계획
 
 #### 플러터로 메인 개발
 - AOS/iOS의 이분할 팀구성보다 플러터 팀의 원팀 구성이 적어도 커뮤니케이션엔 유리하다
 - 성능 차이, 용량 이슈는 하드웨어 발전이 해결해줄 것이라는 믿음
 
 #### 디자이너용 데스크톱 앱 개발
 - 올 2월 플러터 2.10 버전 업그레이드를 통해 데스크톱 앱 지원 정식 발표
 - 현재 템플릿 업로드 방식은 디자이너가 디자인툴로 템플릿을 만들고 개발자가 일일이 템플릿을 코드로 입력하는 방식
 - 디자이너용 업로드 앱을 만든다면 디자인툴 대신 데스크톱 앱으로 템플릿을 만들고 바로 서버에 저장하며 업무 방식에 획기적인 개선을 가져올 수 있다
 
 #### 웹 서비스
 - 데스크톱 앱보다 이전부터 지원되었지만 당장 실제 도입하긴 어려움이 존재한다
 - 사내에서 쓰는 데스크톱 앱과 달리 웹의 경우 유저들이 활용하는 서비스이기 때문에 고려해야할 부분이 광범위하므로 추후 도입을 고려한다
 - 다른 프레임워크로 웹을 만들고 기능 하나하나씩 플러터로 마이그레이션하는 방향도 고려 중이다
 
 
 
 
 
 [유튜브 영상](https://www.youtube.com/watch?v=_WJMcLx6Hoo&t=2s)
 
 </details>





---

## 6. 지식인 앱 CI & CD 소개

<details>
 <summary>발표자 최유태님</summary>
 
 ### CD(Continuous Deployment/Deliver)
- 지속적 배포

#### Jenkins open source
- blue ocean & pipeline 기능

#### Jenkins pipeline
1. git checkout
2. flutter init
3. parallel execution
4. ios/android 동시에 build
5. store update

![image](https://user-images.githubusercontent.com/61898890/157449274-908469d5-f89d-4d26-b561-ea9593ca7184.png)

#### fvm(Flutter Version Management)
- Flutter SIDEKICK
- Configure version per project
- Fast switch
- Parallelism 


#### fastlane
- automate deploy
- 배포관리가 쉬워진다

#### hubot
- deploy 실행을 더 쉽게하기 위해 만듦

### CI(Continuous Integration)
- 지속적 통합
- static code analysis
- code convention
- build test

#### Github Action
- CI와 CD 모두 가능하다
- 해당 trigger는 pull request가 올라왔을 때 push, fork 했을 때로 선택할 수 있다
- self hosted

![image](https://user-images.githubusercontent.com/61898890/157455993-09740802-4ca1-4e17-9269-513239cd191d.png)

[유튜브 영상](https://www.youtube.com/watch?v=XE7arhC6tsc)
 
 </details>
 



--- 

## 7. 플러터 업데이트 모아보기

<details>
 <summary>발표자 홍종표님</summary>
 
  ### 2021 Flutter 업데이트
- Lint : 소스 코드를 분석하여 모범적인 코딩 관행을 장려하는 도구  
- Skeleton : 커뮤니티 모범 사례를 따르는 2페이지의 리스트 뷰(디테일 뷰 포함) 앱
- dart:core 패키지에 hash 관련 메소드를 override 한다
- WebView 3.0
- Flutter Favorites Packages(새로운 라우터, moor->drift, freezed, dart_code_metrics, flex_color_scheme, flutter_svg, feedback, toggle_switch, auto_size_text) 
- find.image() 메서드 추가

 ### 2022 Flutter Roadmap
 - Flutter Desktop Release
 - 개발자 경험 향상
 - 정적 메타 프로그래밍 지원 (코드 생성 없이 Data Class 만들기. ex. build_value, freezed, json_serializable) -> Kotlin의 data class처럼 그냥 만들 수 있게끔 한다
- Flutter Windows Release
- Android 관련 변경사항
- 통합 테스트(Integration Test)
- Pub.dev 검색 UI 변경
- [Chris Sells](https://medium.com/@csells_18027) 
- [Michael Thomsen](https://medium.com/@mit.mit)


[유튜브 영상](https://www.youtube.com/watch?v=fhOGL_6XGTg)
 </details>
 
 

