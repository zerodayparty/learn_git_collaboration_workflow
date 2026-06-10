# 🟩 git conflict (충돌)  

## 🟢 개념 개요  

### 🟡 git conflict란 무엇인가  
서로 다른 두 개의 버전(혹은 브랜치)을 하나로 합치려고 할 때, 동일한 파일의 동일한 줄을 서로 다르게 수정하여 Git이 자동으로 합치지 못하고 멈추는 상태를 의미한다.  
- `git` = Global Information Tracker (분산 버전 관리 시스템)  
- `conflict` = conflict (충돌)  
- 해설: Git은 어떤 버전의 소스코드가 올바른지 스스로 판단할 수 없으므로, 사용자에게 직접 충돌을 해결해달라고 요청하며 병합 과정을 중단한다.  

<br><br>

## 🟢 충돌 발생 시 표시되는 기호 해석  
충돌이 발생하면 파일 안에 아래와 같은 특수 기호들이 자동으로 삽입된다.  

### 🟡 충돌 표시 기호 구조  
```
<<<<<<< HEAD  
현재 내가 작업 중인 브랜치의 코드 내용  
=======  
병합해 가져오려고 하는 상대 브랜치의 코드 내용  
>>>>>>> 상대-브랜치-이름  
```

### 🟡 기호별 단어 풀네임 및 해설  

| 기호 | 풀네임 및 해석 | 해설 |  
| :--- | :--- | :--- |
| `<<<<<<< HEAD` | `HEAD` = HEAD (현재 위치하는 최신 커밋/브랜치의 포인터) | 현재 내가 체크아웃하여 작업 중인 브랜치에서 변경된 내용의 시작점이다. |  
| `=======` | Equal Sign (일치선/구분선) | 내 변경 사항과 상대방 변경 사항의 경계를 나누는 구분선이다. |  
| `>>>>>>> 브랜치명` | Right Angle Brackets (오른쪽 꺾쇠 표시) | 합치려고 가져온 상대방 브랜치에서 변경된 내용의 끝점이다. |  

<br><br>

## 🟢 루트의 git_conflict_practice 폴더를 활용한 충돌 실습 가이드  
루트 디렉터리에 생성된 `git_conflict_practice` 폴더와 `conflict_test.txt` 파일을 이용하여 인위적으로 충돌을 일으키고 해결하는 실습 순서이다.  

### 🟡 1단계: 실습용 폴더로 이동 후 Git 초기화  
터미널 입력:  
`cd git_conflict_practice`  
`git init`  
- `cd` = change directory (디렉터리 변경)  
- `git` = Global Information Tracker  
- `init` = initialize (초기화하다)  
- 해설: 이 폴더 전용 독립된 Git 저장소를 새로 생성하여 실습을 시작한다.  

### 🟡 2단계: 기본 파일 커밋 생성  
터미널 입력:  
`git add conflict_test.txt`  
`git commit -m "feat: add base file"`  
- 해설: 충돌 비교의 기준이 될 최초의 기본 버전을 생성한다.  

### 🟡 3단계: 1번 브랜치 생성 및 내용 수정  
터미널 입력:  
`git switch -c branch-a`  
- `switch` = switch (전환하다)  
- `-c` = create (생성하다)  
- 해설: `branch-a`라는 이름의 새로운 브랜치를 만들고 그리로 즉시 이동한다.  

`conflict_test.txt` 파일을 열어 아래와 같이 수정하고 저장한다:  
```
Base text for conflict practice.  
Line 2: Hello branch A!  
```

수정 후 터미널 입력:  
`git add conflict_test.txt`  
`git commit -m "feat: update line 2 from branch A"`  
- 해설: 1번 브랜치에서 파일 2번째 줄을 수정한 버전을 저장한다.  

### 🟡 4단계: 2번 브랜치 생성 및 내용 수정  
다시 최초의 main 브랜치로 돌아간다.  
터미널 입력:  
`git switch main`  

새로운 `branch-b`를 생성하고 이동한다.  
터미널 입력:  
`git switch -c branch-b`  

`conflict_test.txt` 파일을 열어 아래와 같이 수정하고 저장한다:  
```
Base text for conflict practice.  
Line 2: Hello branch B!  
```

수정 후 터미널 입력:  
`git add conflict_test.txt`  
`git commit -m "feat: update line 2 from branch B"`  
- 해설: 2번 브랜치에서 동일한 파일의 동일한 2번째 줄을 다르게 수정한 버전을 저장한다.  

### 🟡 5단계: 병합 시도하여 충돌 유도  
현재 `branch-b`에 머물러 있는 상태에서 `branch-a`를 합친다.  
터미널 입력:  
`git merge branch-a`  
- `merge` = merge (병합하다, 합치다)  
- 해설: 두 브랜치의 변경 사항을 병합하라고 지시한다.  

#### ⚫️ 출력되는 충돌 경고 메시지  
```
CONFLICT (content): Merge conflict in conflict_test.txt  
Automatic merge failed; fix conflicts and then commit the result.  
```
- `CONFLICT` = conflict (충돌)  
- `Automatic` = Automatic (자동의)  
- `failed` = failed (실패한)  
- `fix` = fix (수정하다, 해결하다)  
- 해설: 자동으로 병합하는 것에 실패했으니 사용자가 충돌을 직접 해결하고 커밋하라는 뜻이다.  

### 🟡 6단계: 충돌 해결 및 최종 저장  
`conflict_test.txt` 파일을 열면 다음과 같이 충돌 표시 기호가 적혀 있다:  
```
Base text for conflict practice.  
<<<<<<< HEAD  
Line 2: Hello branch B!  
=======  
Line 2: Hello branch A!  
>>>>>>> branch-a  
```

이 중 최종적으로 남길 소스 코드 한 줄만 선택하고, 나머지 기호들을 모두 깨끗이 지운다.  
예를 들어 두 내용을 모두 합쳐 아래와 같이 수정하고 저장한다:  
```
Base text for conflict practice.  
Line 2: Hello branch A and B!  
```

수정 완료 후 터미널 입력:  
`git add conflict_test.txt`  
`git commit -m "fix: resolve merge conflict"`  
- 해설: 충돌이 해결된 상태를 최종 버전으로 커밋하여 완료한다.  

<br><br>

## 🟢 충돌 관련 보조 터미널 명령어  

| 명령어 | 명령어 영어 풀네임 | 해설 |  
| :--- | :--- | :--- |
| `git merge --abort` | `merge` = merge (병합)<br>`--abort` = abort (중단하다) | 현재 발생한 충돌 해결을 취소하고 병합 작업 자체를 완전히 되돌려 이전 상태로 돌아간다. |  
| `git switch -c [브랜치명]` | `switch` = switch (전환하다)<br>`-c` = create (생성하다) | 새로운 브랜치를 생성함과 동시에 해당 브랜치로 즉시 전환한다. |  
