# 🍽️ 오늘뭐먹지 (Oneul-Mwt-Mukji)

> AI가 당신의 기분과 상황에 맞는 메뉴를 추천해주는 웹 서비스

매일 반복되는 **"오늘 뭐 먹지?"** 고민!  
기분, 음식 종류, 인원만 선택하면  
AI가 딱 맞는 메뉴를 추천해드립니다. 🤖

<div align="center">

**🔗 배포 URL**

### [https://oneul-mwt-mukji.vercel.app](https://oneul-mwt-mukji.vercel.app)


---

## 🎯 1. 서비스 기획

### 서비스 개요
| 항목 | 내용 |
|------|------|
| **서비스명** | 오늘뭐먹지 |
| **타겟 사용자** | 매일 메뉴 고민이 귀찮은 직장인 및 학생 |
| **목표** | 간단한 선택만으로 AI 맞춤 메뉴 추천 제공 |

### 페이지 구성 (3개 이상)
🏠 메인 (index.html) → 서비스 소개 + Hero
🍽️ AI 추천 (recommend.html) → 핵심 AI 기능
❓ FAQ (faq.html) → 자주 묻는 질문


> 상단 네비게이션으로 모든 페이지 이동 가능

### AI 기능 설계
| 구분 | 내용 |
|------|------|
| **입력** | 기분 / 음식 종류 / 인원수 / 직접 입력 |
| **출력** | AI 분석 기반 맞춤 메뉴 추천 + 안내 문구 |
| **제공 가치** | 메뉴 선택 시간 절약 + 새로운 메뉴 발견 |

### 실패 처리 기준
| 상황 | 안내 메시지 |
|------|------------|
| **API 오류 (4xx/5xx)** | "😥 오류가 생겼어요. 다시 시도해주세요!" |
| **로딩 지연** | "😋 AI가 메뉴를 고민하는 중..." |

---

## ✨ 2. 주요 기능

| 기능 | 설명 |
|------|------|
| 🤖 **AI 메뉴 추천** | 기분/음식/인원 기반 맞춤 추천 (핵심 기능) |
| 🌙 **다크 모드** | 눈이 편한 야간 모드 (localStorage 저장) |
| 📱 **반응형 디자인** | 모바일/태블릿/PC 모두 최적화 |
| ❓ **FAQ** | 자주 묻는 질문 안내 |

---

## 🛠️ 3. 기술 스택

### Frontend 
![HTML](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JS](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)

- **HTML5** : 페이지 구조 및 콘텐츠 마크업
- **CSS3** : 스타일링 + 반응형 (미디어쿼리) + 다크모드
- **JavaScript** : 사용자 입력 처리 + fetch 통신 + DOM 조작

> ⚠️ React/Vue 등 프레임워크 미사용 (순수 바닐라)

### Backend
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat&logo=vercel&logoColor=white)

- **Python** : Vercel Serverless Functions
- **Google Gemini API** : AI 메뉴 추천 (`gemini-2.0-flash`)

### 배포 & 협업
- **GitHub** : 코드 저장소 및 버전 관리
- **Vercel** : GitHub 연동 자동 배포

---

## 📁 4. 프로젝트 구조


<img width="294" height="485" alt="image" src="https://github.com/user-attachments/assets/d67ab5b9-1dc0-473f-a7d7-40778b8f4825" />


---




## 🔐 5. 환경 변수 설정

프로젝트 루트에 .env 파일 생성:

GEMINI_API_KEY=여기에_본인_API_키_입력

Vercel 배포 시

Vercel 프로젝트 → Settings

Environment Variables 메뉴

GEMINI_API_KEY 추가 후 저장

## 🌐 6. 배포 방법

GitHub에 코드 push

Vercel과 GitHub 저장소 연동

Framework Preset: Other 선택

환경 변수 GEMINI_API_KEY 등록

Deploy 클릭 → 자동 배포 완료!

GitHub에 push할 때마다 Vercel이 자동으로 재배포합니다.

데이터 흐름 구조


<img width="309" height="187" alt="image" src="https://github.com/user-attachments/assets/56261acb-ff25-4491-a88f-a1d3d73d71e6" />



## 🧪 7. AI 기능 테스트

💻 데스크톱 화면

<img width="1879" height="933" alt="image" src="https://github.com/user-attachments/assets/75448a09-681a-4a4f-9187-1ab0fa2a5a97" />
<img width="1872" height="918" alt="image" src="https://github.com/user-attachments/assets/d45e302f-fc63-4171-ac52-839915761c80" />
<img width="814" height="930" alt="image" src="https://github.com/user-attachments/assets/0f906569-edda-4a2f-b77a-e8ccb821219c" />
<img width="705" height="866" alt="image" src="https://github.com/user-attachments/assets/c9c88198-9ddb-4ecf-ada8-8d97c2f7cf84" />
<img width="747" height="926" alt="image" src="https://github.com/user-attachments/assets/cb4d36f1-d390-4cc5-aae4-f01dd43a77af" />




📱 모바일 화면

<img width="585" height="1266" alt="IMG_7760" src="https://github.com/user-attachments/assets/d542605f-9e10-4b76-81e5-d5362115fd01" />
<img width="585" height="1266" alt="IMG_7761" src="https://github.com/user-attachments/assets/1750fabc-fa2a-4dd6-b4da-68b176fe6964" />
<img width="585" height="1266" alt="IMG_7762" src="https://github.com/user-attachments/assets/a166212b-b870-4a8d-bef5-6a73ebfd1a1e" />
<img width="585" height="1266" alt="IMG_7763" src="https://github.com/user-attachments/assets/4c990a6a-2f00-42bc-9108-4983890df576" />
<img width="585" height="1266" alt="IMG_7764" src="https://github.com/user-attachments/assets/305a9bfe-fcc8-4a76-b6c7-ca7857c7f4d3" />

