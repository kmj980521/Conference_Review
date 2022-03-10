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
 

[유튜브 영상](https://www.youtube.com/watch?v=jW3pqIpQtQE&t=1s)
 
 </details>
 

---


## 5. 예비 창업자로서 플러터를 선택한 이유와 활용계획

<details>
 <summary>발표자 김진섭님</summary>
 
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
 
 

