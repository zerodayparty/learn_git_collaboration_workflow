# 🟩 git add 명령어  

## 🟢 명령어 개요  

### 🟡 git add란 무엇인가  
작업 디렉터리(Working Directory)에서 수정하거나 새로 만든 파일을 준비 영역(Staging Area)에 추가하는 명령어이다.  
- `git` = Global Information Tracker (분산 버전 관리 시스템)  
- `add` = add (추가하다)  
- 해설: 코드를 컴퓨터에 최종 저장(Commit)하기 전, 저장할 파일들만 골라서 무대 대기실(Staging Area)에 올려놓는 역할을 한다.  

<br><br>

## 🟢 주요 사용법과 단어 풀네임  

| 명령어 | 명령어 영어 풀네임 및 단어 해석 | 해설 |  
| :--- | :--- | :--- |
| `git add <파일명>` | `git` = Global Information Tracker<br>`add` = add (추가하다) | 지정한 특정 파일 하나만 준비 영역에 올린다. |  
| `git add .` | `.` = dot (현재 폴더/디렉터리) | 현재 폴더 및 하위 폴더의 모든 변경 사항(추가, 수정, 삭제)을 한 번에 준비 영역에 올린다. |  
| `git add -p` | `-p` = patch (조각, 일부분) | 파일의 변경 사항을 줄 단위 조각으로 나누어 보면서, 스테이징 여부를 개별적으로 결정한다. |  

<br><br>

## 🟢 작동 원리 비유 설명  
`git add`는 택배를 보내는 과정에 비유할 수 있다.  
- **작업 디렉터리 (내 방)**: 물건을 만들거나 포장되지 않은 상태로 흩어놓은 공간이다.  
- **준비 영역 (택배 박스 안)**: 택배를 보내기 위해 박스 안에 담아둔 상태이다. (`git add`를 한 상태)  
- **저장소 (택배 발송)**: 박스 테이프를 붙여서 창고에 영구히 저장하는 행위이다. (`git commit`을 한 상태)  

<br><br>

## 🟢 git add -p 대화형 선택 기호 설명  
`git add -p` 실행 시 화면에 나타나는 선택 옵션 키와 그 풀네임 해설이다.  

| 선택 키 | 영어 풀네임 | 해설 |  
| :--- | :--- | :--- |
| `y` | stage this hunk | 이 변경 사항 조각(hunk)을 준비 영역에 올린다. |  
| `n` | do not stage this hunk | 이 변경 사항 조각을 준비 영역에 올리지 않는다. |  
| `q` | quit; do not stage this hunk or any of the remaining ones | 대화형 모드를 종료하고, 지금까지 결정된 것만 적용한다. |  
| `a` | stage this hunk and all later hunks in the file | 현재 조각과 이 파일 내의 이후 모든 조각을 한 번에 준비 영역에 올린다. |  
| `d` | do not stage this hunk or any of the later hunks in the file | 현재 조각과 이 파일 내의 이후 모든 조각을 준비 영역에 올리지 않는다. |  
| `s` | split the current hunk into smaller hunks | 현재 변경 사항 조각을 더 작은 크기로 쪼갠다. |  
| `?` | print help | 선택 키들의 도움말을 화면에 출력한다. |  
