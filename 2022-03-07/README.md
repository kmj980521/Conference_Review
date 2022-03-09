# Flutter Korea

## 1. Flutter에 Architecture & Design Pattern 적용
- 송승현님
- BLOC Pattern, 폴더 구조

[유튜브 영상](https://www.youtube.com/watch?v=bp9AlSUsS10)

----

## 2. Flutter에 네이티브 모듈 연동하기
- 김기범님


[유튜브 영상](https://www.youtube.com/watch?v=nIqTfAeYc3Y)

---

## 3. Introduce Youtube Flutter Decoding
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


---


## 4. [알잘딱깔쎈] Flutter Embedded
- 박제창님


[유튜브 영상](https://www.youtube.com/watch?v=jW3pqIpQtQE&t=1s)

---


## 5. 예비 창업자로서 플러터를 선택한 이유와 활용계획
- 김진섭님 


[유튜브 영상](https://www.youtube.com/watch?v=_WJMcLx6Hoo&t=2s)

---

## 6. 지식인 앱 CI & CD 소개
- yutae님
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


--- 

## 7. 플러터 업데이트 모아보기
- 홍종표님
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
