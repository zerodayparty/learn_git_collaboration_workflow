# 🟩 git commit 명령어  

## 🟢 명령어 개요  

### 🟡 git commit이란 무엇인가  
준비 영역(Staging Area)에 올라와 있는 파일의 변경 사항들을 영구히 기록하여 하나의 '버전'으로 저장소(Repository)에 등록하는 명령어이다.  
- `git` = Global Information Tracker (분산 버전 관리 시스템)  
- `commit` = commit (제출하다, 확정하다, 약속하다)  
- 해설: 변경 내용을 스냅숏(특정 시점의 스크린샷 이미지) 형태로 기록하여 보관하며, 나중에 언제든지 이 시점으로 코드를 되돌릴 수 있다.  

<br><br>

## 🟢 주요 사용법과 단어 풀네임  

| 명령어 | 명령어 영어 풀네임 및 단어 해석 | 해설 |  
| :--- | :--- | :--- |
| `git commit` | `git` = Global Information Tracker<br>`commit` = commit (제출/확정) | 기본 텍스트 에디터를 열어 여러 줄짜리 상세한 커밋 메시지를 적고 저장한다. |  
| `git commit -m "메시지"` | `-m` = message (메시지) | 에디터를 열지 않고 쌍따옴표 안에 적은 짧은 메시지와 함께 바로 버전을 저장한다. |  
| `git commit -am "메시지"` | `-a` = all (모든 변경 파일)<br>`-m` = message (메시지) | `git add`와 `git commit`을 동시에 처리한다. (단, 기존에 한 번이라도 커밋된 적이 있는 **Tracked** 파일만 적용된다.) |  
| `git commit --amend` | `--amend` = amend (수정하다, 개선하다) | 직전에 만든 가장 최신 커밋의 메시지를 수정하거나, 빠트린 파일을 추가하여 덮어쓴다. |  

<br><br>

## 🟢 작동 원리 비유 설명  
`git commit`은 물건 포장을 마치고 창고에 쌓는 행위와 같다.  
- **준비 영역 (Staging Area)**: 포장 상자 안에 보낼 물건들을 모아둔 공간이다.  
- **커밋 완료 (Commit)**: 상자 입구를 테이프로 밀봉하고 상자 겉면에 포장 라벨(Commit Message)을 붙인 다음, 보관 창고(Repository)의 선반에 안전하게 보관하는 행위이다.  

<br><br>

## 🟢 커밋 생성 시 터미널 출력 메시지 해석  
커밋을 정상적으로 완료했을 때 화면에 출력되는 예시 메시지 해설이다.  

### 🟡 예시 출력 화면  
```
[main 7f2d4e1] feat: add login feature  
 2 files changed, 25 insertions(+), 3 deletions(-)  
 create mode 100644 src/login.js  
```

### 🟡 메시지 해석 및 영어 풀네임  

| 영어 메시지 | 단어별 풀네임 및 해석 | 해설 |  
| :--- | :--- | :--- |
| `[main 7f2d4e1]` | `main` = main (기본 브랜치 명)<br>`7f2d4e1` = commit hash (커밋 해시값 앞자리) | 'main' 브랜치에 고유번호 '7f2d4e1'번으로 버전을 저장했다는 뜻이다. |  
| `feat: add login feature` | `feat` = feature (기능)<br>`add` = add (추가하다)<br>`login` = login (로그인)<br>`feature` = feature (기능) | 작성한 커밋 메시지 내용이다. |  
| `2 files changed` | `files` = files (파일들)<br>`changed` = changed (변경된) | 총 2개의 파일에 변경 사항이 생겼다는 뜻이다. |  
| `25 insertions(+)` | `insertions` = insertions (추가된 줄 수) | 코드 내용이 25줄 새로 추가되었다는 뜻이다. |  
| `3 deletions(-)` | `deletions` = deletions (삭제된 줄 수) | 기존 코드 내용이 3줄 삭제되었다는 뜻이다. |  
| `create mode 100644` | `create` = create (생성하다)<br>`mode` = mode (파일 유형 모드) | 'src/login.js'라는 새 파일이 생성되어 저장소에 등록되었다는 뜻이다. |  
