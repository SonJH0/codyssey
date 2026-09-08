
#  공부 시간 기록 AI 비서

> 내 공부 데이터를 이해하고 맞춤형 조언을 해주는 AI 학습 비서 웹서비스

일반 ChatGPT는 내 데이터를 모릅니다.  
이 서비스는 **내 공부 기록을 분석**하고, 그 데이터를 바탕으로  
AI가 "너 요즘 공부 늘었어!" 같은 **맞춤형 답변**을 제공합니다.

---

##  서비스 소개

- **무엇을 해결하나요?**  
  단순히 공부 시간을 기록하는 것을 넘어,  
  AI가 내 학습 데이터를 분석해 **개인화된 피드백**을 제공합니다.

- **핵심 기능**
  -  공부 시간 기록 (CRUD)
  -  데이터 시각화 (막대 그래프)
  -  데이터 기반 AI 채팅 (컨텍스트 주입)
  -  대화 기록 저장 / 불러오기 / 삭제

---

## 🛠 기술 스택

| 구분 | 기술 |
|------|------|
| **백엔드** | FastAPI, Uvicorn |
| **프론트엔드** | HTML, CSS, JavaScript (바닐라) |
| **데이터베이스** | Firebase Firestore |
| **AI** | OpenAI GPT API |
| **시각화** | Chart.js |
| **배포** | Render (백엔드), Vercel (프론트) |

---

##  배포 URL

| 구분 | 링크 |
|------|------|
| **프론트엔드** | https://vercel.com/son-jh/aisup/ALq854hC3Kh3XaihjjEbpj6yo46T |
| **백엔드 API** | https://aisup-auxx.onrender.com |
| **Swagger 문서** | https://aisup-auxx.onrender.com/docs |

>  **콜드 스타트 안내**  
> Render 무료 플랜은 15분간 요청이 없으면 서버가 잠듭니다.  
> 첫 요청 시 **최대 1분** 정도 응답이 지연될 수 있습니다. (정상)

---

##  프로젝트 구조

<img width="204" height="436" alt="image" src="https://github.com/user-attachments/assets/54c25675-36d3-4c80-8225-b43ea91b8569" />


---

##  데이터 소개

- **주제**: 공부 시간 기록 (시계열 데이터)
- **데이터 형태**: `{ date, value(분), memo }`
- **데이터 개수**: 100개 이상
- **요약 정보**: 기간, 개수, 평균/최대/최소, 최근 추세(증가/감소/유지)

---

##  API 명세

###  데이터 관리 (CRUD)
| 메서드 | 경로 | 설명 |
|--------|------|------|
| `POST` | `/records` | 새 데이터 추가 |
| `GET` | `/records` | 데이터 목록 조회 |
| `PUT` | `/records/{id}` | 데이터 수정 |
| `DELETE` | `/records/{id}` | 데이터 삭제 |
| `GET` | `/data/summary` | 데이터 요약 (프롬프트 주입용) |

###  AI 채팅
| 메서드 | 경로 | 설명 |
|--------|------|------|
| `POST` | `/chat` | 데이터 요약 반영 AI 답변 + 자동 저장 |

###  대화 기록
| 메서드 | 경로 | 설명 |
|--------|------|------|
| `POST` | `/api/conversations` | 대화 저장 |
| `GET` | `/api/conversations` | 대화 목록 조회 |
| `GET` | `/api/conversations/{id}` | 특정 대화 전체 메시지 조회 |
| `DELETE` | `/api/conversations/{id}` | 대화 삭제 |

---

##  AI 컨텍스트 주입 원리

```
1️⃣ 사용자 질문 입력 (예: "나 요즘 공부 잘하고 있어?")
2️⃣ /data/summary 로 데이터 요약 조회
3️⃣ 요약을 시스템 프롬프트에 삽입
   → "이 사용자의 평균 공부 시간은 90분, 최근 추세는 증가입니다..."
4️⃣ OpenAI GPT API 호출
5️⃣ 데이터를 반영한 맞춤형 답변 생성
6️⃣ 대화 내용을 conversations에 자동 저장
```

>  이렇게 하면 GPT가 "내 데이터"를 알고 답변합니다!

---

##  로컬 실행 방법

### 1. 저장소 클론
```bash
https://github.com/SonJH0/aisup
```

### 2. 가상환경 생성 및 활성화
```bash
python -m venv venv

# Windows
venv\Scripts\activate

# Mac/Linux
source venv/bin/activate
```

### 3. 패키지 설치
```bash
pip install fastapi uvicorn firebase-admin openai python-dotenv
```

### 4. 환경 변수 설정 (`.env` 파일 생성)
아래 [환경 변수 목록](#-환경-변수-목록) 참고

### 5. 백엔드 실행
```bash
uvicorn main:app --reload
```


### 6. 프론트엔드 실행
`index.html` 파일을 브라우저로 열거나  
Live Server 확장으로 실행

https://aisup.vercel.app/

---

##  환경 변수 목록

| 변수명 | 설명 |
|--------|------|
| `OPENAI_API_KEY` | OpenAI API 키 |
| `FIREBASE_SERVICE_ACCOUNT_JSON` | Firebase 서비스 계정 키 (JSON) |
| `API_BASE_URL` | 프론트에서 사용할 백엔드 주소 |
| `ALLOWED_ORIGINS` | CORS 허용 도메인 목록 |

>  **보안 주의**  
> API 키와 서비스 계정 키는 **절대 코드에 하드코딩하지 않으며**,  
> `.gitignore`에 `.env`를 추가해 GitHub에 노출되지 않도록 합니다.

---

##  제출 스크린샷

### 1. 데이터 요약 기반 AI 채팅 (질문 + 답변)

<img width="984" height="823" alt="image" src="https://github.com/user-attachments/assets/805efe4d-a90c-424d-9db8-d47ebf1cbd01" />


<img width="780" height="874" alt="image" src="https://github.com/user-attachments/assets/23ab8f62-3d7a-443d-bc6f-8436a446de0b" />



### 2. 데이터 관리 화면 (CRUD 동작)

<img width="721" height="233" alt="image" src="https://github.com/user-attachments/assets/ec9fa7a2-12ba-47cf-82c2-3fb30fe44a20" />



### 3. 대화 기록 화면 (불러오기 동작)
<img width="743" height="593" alt="image" src="https://github.com/user-attachments/assets/b17cd841-cf80-40f8-b315-d29ca09e3800" />


---

##  요구사항 체크리스트

- [x] Python 3.10+ / 가상환경 구성
- [x] FastAPI + CORS 설정
- [x] Firestore 연동 (환경변수 관리)
- [x] 데이터 CRUD API 5개
- [x] 데이터 요약 API
- [x] AI 채팅 API (컨텍스트 주입 + 자동 저장)
- [x] 대화 기록 API (저장/조회/불러오기/삭제)
- [x] 100개 이상 시계열 데이터
- [x] 바닐라 프론트엔드 (채팅/데이터/기록)
- [x] Chart.js 데이터 시각화 (보너스)
- [x] Render 백엔드 배포
- [x] Vercel 프론트 배포

