# 🟩 git diff 명령어  

## 🟢 명령어 개요  

### 🟡 git diff란 무엇인가  
파일의 수정된 내용을 저장(Commit)하기 전에 구체적으로 어떤 부분이 변경되었는지 줄 단위로 비교하여 확인하는 명령어이다.  
- `git` = Global Information Tracker (분산 버전 관리 시스템)  
- `diff` = difference (차이점)  
- 해설: 수정된 소스 코드 파일들의 변경 전과 변경 후 차이를 시각적으로 보여준다.  

<br><br>

## 🟢 주요 사용 상황과 명령어 풀네임  

| 명령어 | 명령어 영어 풀네임 및 단어 해석 | 해설 |  
| :--- | :--- | :--- |
| `git diff` | `git` = Global Information Tracker<br>`diff` = difference (차이점) | 작업 폴더(Working Directory)와 준비 영역(Staging Area)의 차이를 비교한다. (즉, 수정 후 아직 `git add` 하지 않은 내용 확인) |  
| `git diff --staged` | `--staged` = staged (스테이지에 올라간) | 준비 영역(Staging Area)에 올린 파일과 마지막 저장 시점(Commit)의 차이를 비교한다. (즉, `git add` 한 후 저장하기 직전 확인) |  
| `git diff --cached` | `--cached` = cached (캐시된 것) | `git diff --staged` 명령어와 완전히 동일한 기능을 수행한다. |  
| `git diff [커밋ID1] [커밋ID2]` | `commit ID` = commit identification (커밋 식별 번호) | 지정한 두 개의 저장 시점(Commit) 사이의 소스 코드 차이를 비교한다. |  
| `git diff [브랜치1] [브랜치2]` | `branch` = branch (나뭇가지/개발 흐름) | 지정한 두 개발 흐름(Branch) 사이의 최신 소스 코드 차이를 비교한다. |  

<br><br>

## 🟢 git diff 실행 결과 화면 해설  
`git diff` 명령어를 입력했을 때 출력되는 텍스트 코드들의 의미와 풀네임을 분석한다.  

### 🟡 예시 출력 화면  
```
diff --git a/test.txt b/test.txt  
index 83db48f..31d6e59 100644  
--- a/test.txt  
+++ b/test.txt  
@@ -1 +1,2 @@  
 original text  
+added text  
```

### 🟡 줄별 상세 해석  

#### ⚫️ 1. 비교 대상 표시 줄  
- `diff --git a/test.txt b/test.txt`  
    `a/test.txt` = 수정되기 이전(a) 상태의 test.txt 파일  
    `b/test.txt` = 수정된 이후(b) 상태의 test.txt 파일  
    - 해설: Git이 test.txt 파일의 이전 상태와 현재 상태를 서로 비교하고 있음을 의미한다.  

#### ⚫️ 2. 인덱스 및 권한 표시 줄  
- `index 83db48f..31d6e59 100644`  
    - `index` = index (색인/식별 번호)  
    - `83db48f..31d6e59` = Git이 파일을 구분하기 위해 내부적으로 부여한 해시(Hash)값 앞부분  
    - `100644` = 파일의 사용 권한 모드 (일반 텍스트 파일 유형을 의미)  
    - 해설: 변경 전 파일 개체와 변경 후 파일 개체의 고유 식별 번호를 표시한다.  

#### ⚫️ 3. 이전 파일 표시 줄  
- `--- a/test.txt`  
    - `---` = 빼기 기호 (삭제되거나 변경되기 전 상태를 가리키는 기호)  
    - 해설: 이전 버전의 파일을 가리킨다.  

#### ⚫️ 4. 새 파일 표시 줄  
- `+++ b/test.txt`  
    - `+++` = 더하기 기호 (추가되거나 변경된 후 상태를 가리키는 기호)  
    - 해설: 현재 버전의 파일을 가리킨다.  

#### ⚫️ 5. 변경 위치 정보 표시 줄  
- `@@ -1 +1,2 @@`  
    - `@@` = 청크 헤더 (Chunk Header / 변경 영역 표시자)  
    - `-1` = 이전 파일의 1번째 줄부터 변경을 표시함  
    - `+1,2` = 새 파일의 1번째 줄부터 총 2줄을 표시함  
    - 해설: 파일 안에서 구체적으로 몇 번째 줄에 수정이 일어났는지 그 위치 영역을 나타낸다.  

#### ⚫️ 6. 파일 내용 표시 줄  
- ` original text`  
    - 공백으로 시작하는 줄  
    - 해설: 변경되지 않고 그대로 유지된 기존 코드 내용이다.  
- `+added text`  
    - `+` = 더하기 기호 (추가됨)  
    - 해설: 새로 추가된 소스 코드 내용이다. 녹색으로 표시된다.  
- `-deleted text`  
    - `-` = 빼기 기호 (삭제됨)  
    - 해설: 삭제된 소스 코드 내용이다. 적색으로 표시된다.  
