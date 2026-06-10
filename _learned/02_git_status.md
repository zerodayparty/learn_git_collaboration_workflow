# 🟩 git status 명령어  

## 🟢 명령어 개요  

### 🟡 git status란 무엇인가  
현재 작업 디렉터리(Working Directory)와 스테이징 영역(Staging Area)의 상태를 확인하는 명령어이다.  
- `git` = Global Information Tracker (분산 버전 관리 시스템)  
- `status` = status (상태)  
- 해설: 현재 어떤 파일이 수정되었고, 어떤 파일이 새로 추가되었으며, 어떤 파일이 커밋할 준비가 되었는지 등의 상태를 보여준다.  


<br><br>

## 🟢 파일의 상태 구분  
Git이 관리하는 파일은 아래 표와 같이 상태를 분류한다.  

| 상태 | 풀네임 (Full Name) | 해설 |  
| :--- | :--- | :--- |
| Untracked | Untracked (추적되지 않는) | Git이 아직 관리를 시작하지 않은 새로 만든 파일. |  
| Tracked | Tracked (추적되는) | Git이 이미 버전 관리를 하고 있는 파일. |  
| Unmodified | Unmodified (수정되지 않은) | 마지막 저장(Commit) 이후 아무것도 변경되지 않은 파일. |  
| Modified | Modified (수정된) | 마지막 저장(Commit) 이후 내용이 수정된 파일. |  
| Staged | Staged (스테이지에 올라간) | 커밋하기 위해 준비 영역(Staging Area)에 올라간 파일. |  

<br><br>

## 🟢 git status 실행 결과 분석  
터미널에서 명령어를 실행했을 때 나타나는 상황별 출력 메시지와 해설이다.  

### 🟡 1. 변경 사항이 없을 때  
#### ⚫️ 터미널 입력 명령어  
- `git status`  
    - `git` = Global Information Tracker  
    - `status` = status (상태)  
    - 해설: 현재 프로젝트 폴더의 상태를 출력한다.  

#### ⚫️ 출력 메시지  
```
On branch main  
nothing to commit, working tree clean  
```

#### ⚫️ 메시지 해석 및 영어 풀네임  

| 영어 메시지 | 단어별 풀네임 및 해석 | 해설 |  
| :--- | :--- | :--- |
| On branch main | `On` = On (~위에)<br>`branch` = branch (나뭇가지/브랜치)<br>`main` = main (주요한) | 현재 'main' 브랜치 위에서 작업 중이다. |  
| nothing to commit | `nothing` = nothing (아무것도 없음)<br>`to` = to (~하기 위한)<br>`commit` = commit (제출/저장) | 새로 저장(Commit)할 변경 사항이 없다. |  
| working tree clean | `working` = working (작업 중인)<br>`tree` = tree (나무/폴더 구조)<br>`clean` = clean (깨끗한) | 작업 디렉터리에 수정 중인 파일이 없다. |  

<br><br>

### 🟡 2. 추적되지 않는 파일(Untracked)이 존재할 때  
#### ⚫️ 터미널 입력 명령어  
- `git status`  

#### ⚫️ 출력 메시지  
```
On branch main  
Untracked files:  
  (use "git add <file>..." to include in what will be committed)  
	new_file.txt  

nothing added to commit but untracked files present (use "git add" to track)  
```

#### ⚫️ 메시지 해석 및 영어 풀네임  

| 영어 메시지 | 단어별 풀네임 및 해석 | 해설 |  
| :--- | :--- | :--- |
| Untracked files: | `Untracked` = Untracked (추적되지 않는)<br>`files` = files (파일들) | Git이 추적하지 않고 있는 파일 목록이다. |  
| (use "git add <file>..." to include in what will be committed) | `use` = use (사용하다)<br>`git add` = Git Add (깃 추가)<br>`include` = include (포함하다)<br>`what` = what (~하는 것)<br>`will be` = will be (~이 될 것이다)<br>`committed` = committed (저장된) | "git add <파일명>" 명령어를 실행하여 해당 파일을 커밋할 대상에 포함하라는 뜻이다. |  
| nothing added to commit but untracked files present | `nothing` = nothing (아무것도 없음)<br>`added` = added (추가된)<br>`but` = but (그러나)<br>`present` = present (존재하는) | 커밋을 위해 추가된 파일은 없지만 추적되지 않은 새 파일이 존재한다는 뜻이다. |  
| (use "git add" to track) | `track` = track (추적하다) | 추적을 시작하기 위해 "git add" 명령어를 사용하라는 권장 사항이다. |  

<br><br>

### 🟡 3. 수정된 파일(Modified)이 존재할 때  
#### ⚫️ 터미널 입력 명령어  
- `git status`  

#### ⚫️ 출력 메시지  
```
On branch main  
Changes not staged for commit:  
  (use "git add <file>..." to update what will be committed)  
  (use "git restore <file>..." to discard changes in working directory)  
	modified:   existing_file.txt  

no changes added to commit (use "git add" and/or "git commit -a")  
```

#### ⚫️ 메시지 해석 및 영어 풀네임  

| 영어 메시지 | 단어별 풀네임 및 해석 | 해설 |  
| :--- | :--- | :--- |
| Changes not staged for commit: | `Changes` = Changes (변경 사항들)<br>`not` = not (~가 아닌)<br>`staged` = staged (스테이지에 올라간)<br>`for` = for (~를 위한) | 커밋을 위해 준비 영역(Staging Area)에 올라가지 않은 변경 사항들이다. |  
| (use "git restore <file>..." to discard changes in working directory) | `restore` = restore (복원하다)<br>`discard` = discard (버리다/취소하다)<br>`working directory` = working directory (작업 디렉터리) | "git restore <파일명>" 명령어를 사용하여 작업 중인 폴더의 변경 사항을 취소하고 이전 상태로 되돌리라는 뜻이다. |  
| modified: existing_file.txt | `modified` = modified (수정된) | existing_file.txt 파일의 내용이 수정되었다는 뜻이다. |  

<br><br>

### 🟡 4. 스테이징 영역에 올라간 파일(Staged)이 존재할 때  
#### ⚫️ 터미널 입력 명령어  
- `git status`  

#### ⚫️ 출력 메시지  
```
On branch main  
Changes to be committed:  
  (use "git rm --cached <file>..." to unstage)  
	new file:   new_file.txt  
```

#### ⚫️ 메시지 해석 및 영어 풀네임  

| 영어 메시지 | 단어별 풀네임 및 해석 | 해설 |  
| :--- | :--- | :--- |
| Changes to be committed: | `to be` = to be (~가 될)<br>`committed` = committed (저장된) | 곧 커밋(저장)될 예정인 변경 사항들이다. |  
| (use "git rm --cached <file>..." to unstage) | `rm` = remove (제거하다)<br>`cached` = cached (캐시된/저장된)<br>`unstage` = unstage (스테이지에서 내리는) | "git rm --cached <파일명>" 명령어를 사용하여 스테이징 영역에서 해당 파일을 제외(unstage)하라는 뜻이다. |  

<br><br>

## 🟢 Git 상태 관련 터미널 명령어 모음  

| 명령어 | 명령어 영어 풀네임 | 명령어 기능 해설 |  
| :--- | :--- | :--- |
| `git status` | `git` = Global Information Tracker<br>`status` = status (상태) | 현재 작업 폴더와 준비 영역(Staging Area)에 있는 파일들의 상태를 보여준다. |  
| `git status -s` | `git` = Global Information Tracker<br>`status` = status (상태)<br>`-s` = short (짧은, 간결한) | 파일 상태 정보를 아주 간결하고 짧게 요약해서 보여준다. |  
| `git add <파일명>` | `git` = Global Information Tracker<br>`add` = add (추가하다) | 지정한 파일을 준비 영역(Staging Area)에 추가하여 다음 커밋에 포함되게 한다. |  
| `git restore <파일명>` | `git` = Global Information Tracker<br>`restore` = restore (복원하다) | 작업 폴더 내 파일의 수정 내용을 취소하고 마지막 커밋 상태로 복구한다. |  
| `git rm --cached <파일명>` | `git` = Global Information Tracker<br>`rm` = remove (제거하다)<br>`--cached` = cached (캐시된 것만) | 로컬 컴퓨터의 실물 파일은 그대로 두고, Git의 관리 대상(Staging Area)에서만 제외한다. |  
