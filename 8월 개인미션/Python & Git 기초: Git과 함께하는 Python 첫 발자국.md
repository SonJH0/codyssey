# Python & Git 기초 미션 보고서  
## Git과 함께하는 Python 첫 발자국 - 프롬프트 관리 프로그램

---

## 1. 프로젝트 개요

본 프로젝트는 Python 기초 문법과 Git/GitHub 사용법을 함께 학습하기 위해 제작한 콘솔 기반 프롬프트 관리 프로그램입니다.

생성형 AI 학습 과정에서 작성한 여러 프롬프트를 한 곳에 모아 관리할 수 있도록, 프롬프트 추가, 목록 조회, 카테고리별 조회, 검색, 상세 보기, 즐겨찾기 기능을 구현했습니다.

또한 Git을 사용하여 기능 단위로 커밋을 남기고, 브랜치를 생성하여 기능을 개발한 뒤 main 브랜치로 병합하는 과정을 수행했습니다. 최종 코드는 GitHub 저장소에 업로드했습니다.

---

## 2. GitHub 저장소

- GitHub 저장소 URL:  
  https://github.com/SonJH0/prompt-manager

---

## 3. 개발 환경

| 항목 | 내용 |
|---|---|
| 에디터 | Visual Studio Code |
| 언어 | Python |
| Python 버전 | Python 3.10 이상 |
| 버전 관리 | Git |
| 원격 저장소 | GitHub |
| 실행 방식 | 터미널 콘솔 실행 |

개발 환경에서 다음 항목을 확인했습니다.

```bash
python --version
git --version
git config user.name
git config user.email
```


Python 3.14.6

git version 2.55.0.windows.2


또한 VSCode에서 Python 확장을 설치하고, GitHub 계정 연동 및 터미널을 통한 Git 명령어 사용 환경을 설정했습니다.

---

## 4. 프로젝트 목표

이 프로젝트의 목표는 다음과 같습니다.

1. Python 기본 문법을 활용하여 실제 동작하는 콘솔 프로그램을 제작한다.
2. 조건문, 반복문, 함수 분리를 통해 프로그램 흐름을 구성한다.
3. 사용자가 메뉴를 선택하여 여러 기능을 실행할 수 있게 한다.
4. Git을 사용하여 코드 변경 이력을 관리한다.
5. GitHub에 프로젝트를 업로드하여 원격 저장소를 관리한다.
6. 브랜치 생성 및 병합 과정을 경험한다.

---

## 5. 주요 기능

### 5.1 메인 메뉴 출력

프로그램 실행 시 사용자가 선택할 수 있는 메뉴가 출력됩니다.

사용자는 번호를 입력하여 원하는 기능을 실행할 수 있으며, 잘못된 번호를 입력하면 안내 메시지가 출력되고 다시 메뉴로 돌아갑니다.

---


### 5.2 프롬프트 추가

사용자가 새로운 프롬프트를 등록할 수 있습니다.

입력 항목은 다음과 같습니다.

- 제목
- 내용
- 카테고리



---

### 5.3 프롬프트 목록 보기

저장된 모든 프롬프트를 번호와 함께 출력합니다.

목록에서는 다음 정보를 확인할 수 있습니다.

- 번호
- 제목
- 카테고리
- 즐겨찾기 여부

프롬프트가 없을 경우 안내 메시지를 출력합니다.

---

### 5.4 카테고리별 조회

사용자가 카테고리를 선택하면 해당 카테고리에 속한 프롬프트만 출력합니다.

해당 카테고리에 등록된 프롬프트가 없으면 안내 메시지를 출력합니다.

---

### 5.5 프롬프트 검색

키워드를 입력하면 프롬프트의 제목 또는 내용에 해당 키워드가 포함되어 있는지 검색합니다.

검색 결과가 있으면 목록 형태로 출력하고, 결과가 없으면 안내 메시지를 출력합니다.

---

### 5.6 프롬프트 상세 보기

프롬프트 번호를 입력하면 해당 프롬프트의 상세 정보를 출력합니다.

상세 보기에서 확인할 수 있는 정보는 다음과 같습니다.

- 제목
- 카테고리
- 즐겨찾기 여부
- 조회수
- 내용 전체

잘못된 번호를 입력하면 오류 안내 메시지를 출력합니다.

---

### 5.7 즐겨찾기 관리

프롬프트 번호를 입력하여 즐겨찾기를 추가하거나 해제할 수 있습니다.

즐겨찾기된 프롬프트만 따로 모아서 확인할 수도 있습니다.

---

### 5.8 즐겨찾기 목록 보기

즐겨찾기된 프롬프트만 따로 모아서 볼 수 있는 기능을 구현했습니다.

## 6. 보너스 기능



### 6.1 프롬프트 수정

등록된 프롬프트의 제목, 내용, 카테고리를 수정할 수 있습니다.

---

### 6.2 프롬프트 삭제

사용자가 선택한 프롬프트를 삭제할 수 있습니다.

삭제 전 번호를 확인하여 잘못된 항목이 삭제되지 않도록 처리했습니다.

---

### 6.3 조회수 기록

프롬프트 상세 보기를 실행할 때마다 해당 프롬프트의 조회수가 증가하도록 구현했습니다.

---

### 6.4 조회수 TOP 목록

조회수가 높은 프롬프트를 기준으로 정렬하여 자주 확인한 프롬프트를 볼 수 있도록 구현했습니다.


---

## 7. 프로그램 구조

코드는 하나의 큰 함수에 몰아넣지 않고 기능별 함수로 분리했습니다.

주요 함수 예시는 다음과 같습니다.

```python
show_menu()
add_prompt()
show_list()
search_prompt()
show_favorites()
```



---

## 8. 사용한 Python 개념

이 프로젝트에서 사용한 Python 개념은 다음과 같습니다.

| 개념 | 사용 내용 |
|---|---|
| 변수 | 사용자 입력값, 메뉴 번호, 프롬프트 데이터 저장 |
| 리스트 | 여러 개의 프롬프트를 저장 |
| 조건문 | 메뉴 선택, 잘못된 입력 처리 |
| 반복문 | 프로그램 메뉴 반복 실행 |
| 함수 | 기능별 코드 분리 |
| 문자열 처리 | 검색, 입력값 검증 |
| 예외 처리 | 잘못된 입력에 대한 안정적 처리 |

---

## 9. 실행 방법



```bash
python main.py
```


---

## 10. Git 사용 기록

프로젝트는 Git을 사용하여 버전 관리를 수행했습니다.

사용한 주요 Git 명령어는 다음과 같습니다.

```bash
git init
git add .
git commit -m "커밋 메시지"
git branch
git checkout
git merge
git remote add origin
git push -u origin main
git pull origin main
git log --oneline --graph --all
```

---

## 11. GitHub 업로드 과정

로컬 저장소에서 작업한 프로젝트를 GitHub 원격 저장소와 연결한 뒤 push를 수행했습니다.

```bash
git remote set-url origin https://github.com/SonJH0/prompt-manager.git
git push -u origin main
```

최종적으로 main 브랜치가 GitHub 원격 저장소에 정상 업로드되었습니다.

---

## 12. 브랜치 작업 및 병합

프롬프트 목록 보기 기능은 main 브랜치가 아닌 별도의 feature 브랜치에서 작업했습니다.

작업 흐름은 다음과 같습니다.

1. main 브랜치에서 새로운 기능 브랜치 생성
2. 기능 구현
3. 기능 단위 커밋
4. main 브랜치로 이동
5. feature 브랜치를 main에 병합
6. GitHub에 push

명령어:

```bash
git checkout -b feature/list
git add .
git commit -m "프롬프트 목록 보기 기능 추가"
git checkout main
git merge feature/list
git push origin main
```

이를 통해 브랜치 생성과 병합 과정을 직접 수행했습니다.

---

## 13. 커밋 관리

프로젝트 진행 중 기능 단위로 커밋을 작성했습니다.

커밋은 최소 요구사항인 10개 이상을 충족하며, 각 커밋은 기능 추가 또는 개선 단위로 작성했습니다.

커밋 내용:

- 프로젝트 초기 설정
- 기본 프롬프트 데이터 추가
- 메뉴 출력 기능 구현
- 프롬프트 추가 기능 구현
- 프롬프트 목록 보기 기능 구현
- 카테고리별 조회 기능 구현
- 검색 기능 구현
- 상세 보기 기능 구현
- 즐겨찾기 기능 구현
- 수정 및 삭제 기능 구현
- 조회수 기능 구현


커밋 기록은 다음 명령어로 확인했습니다.

```bash
git log --oneline --graph --all
```

---

## 14. 폴더 구조

프로젝트의 기본 폴더 구조는 다음과 같습니다.

```text
prompt-manager/
│
├── main.py
├── README.md
├── .gitignore
└── prompts.json
```

파일 설명:

| 파일명 | 설명 |
|---|---|
| main.py | 프롬프트 관리 프로그램 실행 파일 |
| README.md | 프로젝트 설명 및 실행 방법 문서 |
| .gitignore | Git에서 제외할 파일 설정 |
| prompts.json | 프롬프트 데이터 저장 파일 |

---

## 15. 실행 결과 예시

프로그램 실행 시 다음과 같은 메뉴가 출력됩니다.

```text
===== 프롬프트 관리 프로그램 =====
1. 프롬프트 추가
2. 프롬프트 목록 보기
3. 카테고리별 조회
4. 프롬프트 검색
5. 프롬프트 상세 보기
6. 즐겨찾기 추가/해제
7. 프롬프트 삭제
8. 프롬프트 수정
9. 조회수 TOP 목록
10. 즐겨찾기 목록 보기
0. 종료
메뉴를 선택하세요:
```

사용자는 번호를 입력하여 원하는 기능을 실행할 수 있습니다.

---

## 16. 제출용 스크린샷 목록

과제 제출을 위해 다음 스크린샷을 준비했습니다.


### 16.1 개발 환경 설정

포함 내용:

- VSCode 실행 화면
- Python 버전 확인
- Git 버전 확인
- Git 사용자 정보 확인
- GitHub 계정 연동 확인

명령어:

```bash
python --version
git --version
git config user.name
git config user.email
```

<img width="926" height="232" alt="스크린샷 2026-08-07 110957" src="https://github.com/user-attachments/assets/6e1ae0b6-c129-4d77-b36a-3172ae6920ca" />


---

### 16.2 프로그램 실행 결과 스크린샷


<img width="350" height="396" alt="스크린샷 2026-08-07 113454" src="https://github.com/user-attachments/assets/70a5775a-3507-41ad-ae9d-e2dc7285dcd5" />
<img width="455" height="385" alt="스크린샷 2026-08-07 113510" src="https://github.com/user-attachments/assets/9da678f6-99e0-46f1-beb6-07e47cad6eaa" />
<img width="454" height="378" alt="스크린샷 2026-08-07 113538" src="https://github.com/user-attachments/assets/dc429afd-b01c-42ec-8033-5bdc921273b8" />
<img width="362" height="370" alt="스크린샷 2026-08-07 113558" src="https://github.com/user-attachments/assets/65143998-f8d5-4406-b90b-3282e34bbeb1" />
<img width="380" height="556" alt="스크린샷 2026-08-07 113620" src="https://github.com/user-attachments/assets/1ca0b505-4448-424a-a630-c0290088306f" />
<img width="319" height="405" alt="스크린샷 2026-08-07 113637" src="https://github.com/user-attachments/assets/68a27b95-7269-4e61-8ce8-4a74d1fca337" />
<img width="454" height="342" alt="스크린샷 2026-08-07 113649" src="https://github.com/user-attachments/assets/77bc0ce9-59f2-45c3-98b0-127ea1891e9c" />
<img width="378" height="400" alt="스크린샷 2026-08-07 113703" src="https://github.com/user-attachments/assets/496bf170-671c-4035-aa0c-45673695a187" />
<img width="342" height="403" alt="스크린샷 2026-08-07 113714" src="https://github.com/user-attachments/assets/3e964a51-c281-4cd6-8b64-a734579f1707" />
<img width="450" height="390" alt="스크린샷 2026-08-07 113729" src="https://github.com/user-attachments/assets/808af817-6300-407a-8fd7-d6d78701ad47" />







---

### 16.3 Git 로그 스크린샷

포함 내용:

- 커밋 10개 이상
- 브랜치 생성 및 병합 기록

사용 명령어:

```bash
git log --oneline --graph --all
```

<img width="924" height="377" alt="스크린샷 2026-08-07 111038" src="https://github.com/user-attachments/assets/37ca24c4-9bfa-465b-855e-703d1d23f58e" />
<img width="923" height="114" alt="스크린샷 2026-08-07 111046" src="https://github.com/user-attachments/assets/99d57aec-aa49-4c2f-be93-3b466f798417" />



---

### 16.4 GitHub 저장소 화면 스크린샷


<img width="299" height="310" alt="image" src="https://github.com/user-attachments/assets/1d7c4032-bd08-4d84-aaad-d54f2b403339" />
<img width="969" height="840" alt="스크린샷 2026-08-07 111650" src="https://github.com/user-attachments/assets/1cb73d94-a4de-4dd1-9dab-68eefea1cbd6" />
<img width="970" height="934" alt="스크린샷 2026-08-07 111657" src="https://github.com/user-attachments/assets/ed37f4ea-6b89-4c10-8123-a4d89fc39b98" />
<img width="974" height="851" alt="스크린샷 2026-08-07 111709" src="https://github.com/user-attachments/assets/f350b9ab-2732-4a51-824a-79c9ba6b6779" />
<img width="1316" height="721" alt="image" src="https://github.com/user-attachments/assets/8805c541-d208-4cdb-b3ff-4042a9559ea6" />




---

## 17. 요구사항 충족 여부

| 요구사항 | 충족 여부 |
|---|---|
| Python 3.10 이상 사용 | 충족 |
| VSCode 사용 | 충족 |
| Git 설치 및 설정 | 충족 |
| GitHub 저장소 생성 | 충족 |
| 원격 저장소 연결 | 충족 |
| GitHub push | 충족 |
| README.md 작성 | 충족 |
| .gitignore 작성 | 충족 |
| 기본 프롬프트 3개 이상 등록 | 충족 |
| 프롬프트 추가 | 충족 |
| 프롬프트 목록 보기 | 충족 |
| 카테고리별 조회 | 충족 |
| 프롬프트 검색 | 충족 |
| 프롬프트 상세 보기 | 충족 |
| 즐겨찾기 추가/해제 | 충족 |
| 즐겨찾기 목록 보기 | 충족 |
| 커밋 10개 이상 | 충족 |
| 수정/삭제 기능 | 충족 |
| 조회수 기능 | 충족 |

