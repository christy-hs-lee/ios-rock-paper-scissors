# ✊🏻✌🏻✋🏻묵찌빠 게임
1. 프로젝트 인원: [Brody](https://github.com/seunghyunCheon), [Christy](https://github.com/christy-hs-lee)
2. 프로젝트 기간: 2022.12.26~2022.12.29
3. Grouped Rules
    - 스크럼
        - 시작시간: 9:30
        - 식시시간: 1시간 30분 
    - 계획
        - 프로젝트 진행보다는 공식문서 학습에 초점
        - 모르는 개념에 대해선 즉시 파고들기
4. 폴더 구조

```
├── main
├── UserInputFunction
├── MukjippaFunction
├── Type
└── RockScissorPaperFunction
    
```

### 목차
- [프로젝트 소개](#프로젝트-소개)
- [타임라인](#타임라인)
- [순서도](#순서도)
- [기능 설명](#기능-설명)
- [트러블 슈팅](#고민했던-점과-트러블-슈팅)
- [참고 자료](#참고-자료)
- [키워드](#키워드)
- [팀회고](#팀회고)
## <span style="color: #007bff"/>프로젝트 소개</span>
```
사용자의 입력값을 받아 컴퓨터와 가위바위보 게임을 실시합니다!
가위바위보 게임의 결과에 따라 선공을 정하고 묵찌빠 게임을 진행하게 됩니다.
묵찌빠 게임에서 사용자와 컴퓨터가 동일한 패를 선택할 경우 해당 턴의 선공 플레이어가 승리하게 됩니다!
```

## <span style="color: #007bff"/>타임라인</span>

**22.12.26 (월): 참고자료를 읽는다.**
**22.12.27 (화): 전체적인 흐름을 담은 슈도코드를 작성하고 STEP1 코드작성 후 PR 요청**
**22.12.28 (수): STEP1 수정사항을 main에 merge 후 STEP2 브랜치를 만들어 코드 작성 후 PR 요청**
**22.12.29 (목): STEP2 수정사항 반영**


## <span style="color: #007bff"/>순서도</span>
<img src="https://i.imgur.com/x6MtZQX.png" width="600" height="1100"/>






## <span style="color: #007bff"/>기능 설명</span>

* #### 가위바위보 게임 실행 화면
가위바위보 게임의 실행 화면입니다. 사용자에게 가위, 바위, 보에 해당하는 값을 입력받을 수 있습니다. 0을 입력 받으면 종료됩니다. 

<img src="https://i.imgur.com/UmA7Lip.png" width="400"/>

---

* #### 가위바위보 입력값 오류 화면
가위바위보 게임의 입력값 오류 화면입니다. 0~3를 벗어난 다른 값이 들어온다면 에러 메세지를 출력하고 메뉴를 재출력합니다.

<img src="https://i.imgur.com/cT7HefJ.png" width="400"/>

---

* #### 가위바위보 게임 종료 화면
가위바위보 게임을 종료하는 화면입니다. 사용자가 0을 입력할 겨우 게임은 종료됩니다.

<img src="https://i.imgur.com/ZYSM3sV.png" width="400"/>

---

* #### 묵찌빠 게임 실행 화면
가위바위보 게임에서 승패가 정해지면 묵찌빠 게임이 진행됩니다. 가위바위보 게임의 승자가 선공을 가지며, 사용자는 묵, 짜, 빠 중 하나의 값을 입력하여 게임을 진행합니다.

<img src="https://i.imgur.com/dJNt3as.png" width="400"/>

---

* #### 묵찌빠 입력값 오류 화면
묵찌빠 게임에서 사용자가 선공일 때, 범위를 벗어나는 값을 입력할 경우 컴퓨터의 공격으로 변경됩니다. 컴퓨터의 선공일 경우 그래도 컴퓨터의 공격으로 유지됩니다.

<img src="https://i.imgur.com/AkwBRV8.png" width="400"/>

---






## <span style="color: #007bff"/>고민했던 점과 트러블 슈팅</span>
### 🤔 변수 네이밍
가위바위보는 게임 내에서의 핵심 로직이자 자주 사용되는 용어이기 때문에 RockScissorsPaper를 포함하여 변수 네이밍을 했다. 하지만 choiceRockScissorsPaper과같이 너무 길어지는 변수명이 가독성을 저하시키는 것 같아 이대로 사용해도되는지 의문점이 들었다.

### ⚒️ 트러블 슈팅 
리뷰어 인호의 의견으로 축약표현은 지양되기도하고 가위바위보의 경우 자주 쓰이는 표현이기 떄문에 길게 작성되어도 가독성이 떨어지지 않는다고 하셔서 궁금증을 해결했다.

-----

### 🤔 옵셔널 처리
```swift
func createRandomRockScissorsPaper() -> RockScissorsPaperType? {
    let choice = RockScissorsPaperType(rawValue: Int.random(in: 1...3))
    guard let randomChoice = choice else {
        return nil
    }
    return randomChoice
}
```
- 위의 코드에서는 randomChoice가 값을 가지고 있지 않을때 nil을 호출함으로써 옵셔널을 리턴하고 있다. 하지만 이 경우에서는 확정적으로 1~3이라는 값이 나오는 것을 알기 때문에 옵셔널을 리턴하는 것이 아닌 기본타입을 리턴하고 싶었다. 강제 언래핑을 사용하지 않고 기본값으로 만들어 리턴하는 방법이 무엇이 있을까 고민하게 되었다.

### ⚒️ 트러블 슈팅
- else문에 현재함수를 다시 한번 호출함으로써 문제를 해결했다.
```swift
func createRandomRockScissorsPaper() -> RockScissorsPaperType {
    let choice = RockScissorsPaperType(rawValue: Int.random(in: 1...3))
    guard let randomChoice = choice else {
        return createRandomRockScissorsPaper()
    }
    return randomChoice
}
```
- 모종의 이유로 choice변수에 값이 들어가지 않았다고 하더라도 다시 createRandomRockScissorsPaper함수를 호출하기 때문에 random한 값을 받을 수 있게 된다. 그리고 이 방식이 재귀함수의 형태라는 것을 알게되었다.

------

###  🤔 재귀함수, 반복문 그리고 꼬리 재귀함수
- 프로젝트의 내용으로 재귀함수와 반복문은 어떤 차이가 있고 또 꼬리 재귀함수라는 것은 무엇인지 궁금해졌다.

### ⚒️ 트러블 슈팅 
- 반복문, 재귀함수, 꼬리 재귀함수 각각의 특징들을 알기위해 Xcode 디버그를 이용했다. 
- 실행 속도를 비교하기 위해서 `Foundation`을 임포트하고 TimeInterval과 CFAbsoluteTimeGetCurrent를 사용해서 비교했다. 사용법은 progressTime함수 아규먼트 안에 실행시간을 확인해볼 함수를 넣으면 된다.
```swift
    func progressTime(_ closure: () -> ()) -> TimeInterval {
        let start = CFAbsoluteTimeGetCurrent()
        closure()
        let diff = CFAbsoluteTimeGetCurrent() - start
        return (diff)
    }

    print(progressTime {
        print()
    })
```

- 먼저 반복문과 재귀함수를 정의하고 그 안에 breakPoint를 찍어 serial-queue안에 어떻게 호출되는지와 실행시간을 알아봤다.
```swift
func 재귀함수(_ n: Int) -> Int {
    guard n > 0 else { return 0 }
    return n + 재귀함수(n-1)
}

func 반복문(_ n: Int) -> Int {
    var num = 0
    for i in stride(from: n, through: 0, by: -1) {
        num += i
    }
    return num
}
```



||재귀함수|반복문|
|:------:|:---:|:---:|
|Serial-Queue|<img src="https://i.imgur.com/viwOviS.png" width = "300"/>|<img src="https://i.imgur.com/cAWnN2i.png" width = "300"/>|

### 재귀함수 반복문 실행시간 (10,000입력 기준)
<img src="https://i.imgur.com/6NZ9f5Y.png" width="300"/><br>
위가 재귀함수 아래가 반복문

### 꼬리재귀함수 재귀함수 실행시간 (10,000,000입력 기준)
<img src="https://i.imgur.com/PBELAC8.png" width="300"/><br>

위가 꼬리재귀함수, 아래가 재귀함수

### 비교

||반복문|재귀함수|꼬리 재귀함수|
|:------:|:---:|:---:|:------------:|
|속도|빠름|느림|매우 빠름|
|실행|명령을 반복적으로 실행| 함수를 호출 | 함수를 호출 |
|스택메모리|사용하지 않음|함수 호출 될때마다 사용|스택프레임 하나만 사용|
|가독성|코드 길이가 많아져 떨어짐|코드 길이가 줄어 높아짐|코드 길이가 줄어 높아짐
|무한반복| CPU 사이클을 반복적으로 사용 | 스택 오버플로우 발생 | 한번만 실행되기 떄문에 스택오버플로우 미발생| 



## <span style="color: #007bff"/>키워드</span>
- `Optional`, `guard`, `switch`, `inout`, `~=`, `rawValue`,`Result`
- `반복문`, `재귀함수`, `꼬리재귀함수`
- `기능 분리`
- `git`
    - `커밋 단위`
    - `커밋 규칙`
- `컨벤션`, `네이밍`
- `magic literal`, `enum`, `namespace`, `static`
- `Debug`, `breakpoint`, `watch`, `TimeInterval`


## <span style="color: #007bff"/>참고 자료</span>
- [공식문서](https://www.swift.org/)
- [커밋 규칙](http://karma-runner.github.io/latest/dev/git-commit-msg.html)
- [Debug](https://meetup.nhncloud.com/posts/315)
- [컨벤션, 네이밍](https://www.swift.org/documentation/api-design-guidelines/)
- [Enumerations](https://docs.swift.org/swift-book/LanguageGuide/Enumerations.html)





## <span style="color: #007bff"/>팀회고</span>

### 우리팀이 잘한 점
- 사전참고 자료를 중요하게 생각해 미리미리 학습한 점
- 의문점에 대해 깊게 파고든 점
- 학습 시간과 쉬는 시간의 균형을 잘 맞춤 점

### 우리팀 개선할 점
- 학습을 하며 핵심 키워드를 파악하지 못 한점


### 팀원 서로 칭찬하기

Christy -> Brody : 
- 학습을 진행하며 허를 찌르는 질문을 많이 해주셨습니다! 가볍게 읽고 넘어갔던 부분을 Brody의 핵심을 관통하는 질문을 통해 깊은 학습이 가능했습니다.
- 설명 능력이 몹시 뛰어납니다! 이해가 안되는 부분에 대해 질문을 하면 왜 그런지 부터 차근차근 설명을 해주셨습니다.
- 원하는 부분에 대해 자료를 찾는 능력이 뛰어났습니다! 구글링을 하며 저는 찾아내지 못 한 좋은 정보를 잘 찾으셨습니다.

Brody -> Christy
- 문제해결능력이 뛰어납니다. 의문점이 생기고 질문을 하게되면 필요한 자료들을 잘 선별하여 올바르게 해석해서 잘 알려주었습니다. 
- 의견을 피력할 때와 받아들일 때 항상 배려하려고 하시는 모습을 보였습니다. 덕분에 제 의견에 대해 망설임없이 표현할 수 있었습니다.
- 영어 해석을 정말 잘하십니다. 단순히 번역을 하는 것이 아닌 문장의 의미를 파악하는 능력이 뛰어납니다.


