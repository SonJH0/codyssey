
```markdown
# 🧳 국내 여행지 추천 프로그램

여행 날짜를 입력하면 **AI(Gemini)**가 여행지를 추천하고,
**카카오 지도 API**로 맛집을 검색해 **여행 리포트**를 자동 생성하는 CLI 프로그램입니다.

여러 API를 조합하여 인사이트를 만드는 흐름을 구현했습니다.
> LLM 추천 → 지도 API 맛집 검색 → 최종 리포트 생성

---

## 📌 프로그램 개요

| 항목 | 내용 |
|------|------|
| 언어 | Python 3.10+ (개발 환경: 3.14) |
| LLM API | Google Gemini (`gemini-flash-latest`) |
| 지도 API | Kakao Local (키워드 장소 검색) |
| 실행 방식 | CLI (터미널) |
| 결과물 | JSON 원본 데이터 + Markdown 리포트 |

### 처리 흐름
```
사용자 입력(날짜)
   ↓
① Gemini LLM → 여행지 추천 (JSON 구조화)
   ↓
② Kakao API → 추천 도시의 맛집 검색
   ↓
③ Gemini LLM → 최종 여행 리포트 생성 (Markdown)
   ↓
④ results/ 폴더에 JSON + MD 저장
```

---

## ⚙️ 실행 방법

### 1) 프로그램 실행

```bash
# 기본 (1개 도시 추천)
python main.py --date "2026-08-15"

# 복수 도시 추천 (보너스: 2~3개)
python main.py --date "2026-08-15" --count 3
```

### 3) 옵션 설명
| 옵션 | 필수 | 설명 |
|------|------|------|
| `--date` | ✅ 필수 | 여행 날짜 (`YYYY-MM-DD` 형식) |
| `--count` | 선택 | 추천 도시 개수 (1~3, 기본값 1) |

> ⚠️ 날짜 형식이 틀리면 사용법을 안내하고 종료됩니다.

---

## 🔑 API 키 설정 방법

### 1) API 키 발급
- **Gemini API 키**: [Google AI Studio](https://ai.google.dev/) 에서 발급
- **Kakao API 키**: [Kakao Developers](https://developers.kakao.com/) 에서 REST API 키 발급

### 2) .env 파일 생성
프로젝트 루트에 `.env` 파일을 만들고 아래처럼 작성합니다.

```
GEMINI_API_KEY=여기에_본인_Gemini_키
KAKAO_API_KEY=여기에_본인_Kakao_REST_키
```

### 3) 코드에서 키 불러오기
`python-dotenv`로 `.env`에서 키를 읽어옵니다.

```python
from dotenv import load_dotenv
import os

load_dotenv()
GEMINI_KEY = os.getenv("GEMINI_API_KEY")
KAKAO_KEY = os.getenv("KAKAO_API_KEY")
```

---


## 📁 결과물 확인 방법

프로그램 실행 후 `results/` 폴더에 파일이 생성됩니다.

| 파일 | 내용 |
|------|------|
| `data_YYYY-MM-DD.json` | 원본 데이터 (추천 결과 + 맛집 + errors) |
| `report_YYYY-MM-DD.md` | 최종 여행 리포트 (Markdown) |

### JSON 구조 예시
```json
{
  "date": "2026-08-15",
  "city_count": 3,
  "cities": [
    {
      "recommended_city": "강릉",
      "weather": "8월 중순, 덥고 습하며 해수욕 적기",
      "events": ["강릉 커피축제", "경포 여름축제"],
      "reason": "바다와 커피의 도시로...",
      "restaurants": [
        {
          "name": "○○식당",
          "address": "강원특별자치도 강릉시...",
          "category": "음식점 > 한식",
          "url": "http://place.map.kakao.com/...",
          "x": "128.910",
          "y": "37.803"
        }
      ]
    }
  ],
  "errors": []
}
```

### 리포트(MD) 포함 항목
- ✅ 추천 지역 + 추천 이유
- ✅ 날씨 요약
- ✅ 행사/축제 목록
- ✅ 맛집 리스트 (0건이면 '데이터 없음' 표기)
- ✅ 1일 일정 제안 (오전/오후/저녁)
- ✅ 처리 중 발생한 오류 요약

---

## 🛠️ 주요 기능 상세

### 1. CLI 인터페이스 (argparse)
- `--date`, `--count` 옵션 제공
- 날짜 형식 및 도시 개수 검증

### 2. LLM 연동 - 여행지 추천 (JSON 구조화)
- 반드시 JSON으로 파싱 가능한 형식으로 프롬프트 설계
- 최소 스키마: `recommended_city`, `weather`, `events`, `reason`

### 3. 지도 API 연동 - 맛집 검색
- 카카오 Local API로 도시별 맛집 5곳 검색
- 필드: `name`, `address`, `category`, `url`, 좌표(`x`, `y`)

### 4. LLM 연동 - 최종 리포트 생성
- 추천 결과 + 맛집 목록을 Markdown 리포트로 변환

### 5. 에러 처리
| 상황 | 처리 방식 |
|------|----------|
| API 키 미설정 | 즉시 종료 + 설정 방법 안내 |
| 맛집 검색 실패 | '데이터 없음' 처리, 리포트는 계속 진행 |
| 검색 결과 0건 | 중단 없이 다음 단계 진행 |
| JSON 파싱 실패 | 재시도 **최대 1회** (무한 재시도 방지) |

- 발생한 오류는 `errors` 리스트로 관리하여 리포트/JSON에 기록

---

## 🌟 보너스 과제 구현

### ✅ 보너스 1: 복수 지역 추천
- `--count` 옵션으로 2~3개 도시를 서로 다르게 추천
- **반복문(for)**으로 각 도시별 맛집을 검색
- 리포트에 지역별로 정리 + 도시 비교 추천 포함

```python
# 반복 처리로 여러 도시의 맛집을 순차 검색
for city in cities:
    city["restaurants"] = search_restaurants(city["recommended_city"])
```


---

## 📂 프로젝트 구조

```
travel_recommender/
├── main.py              # 메인 프로그램
├── .env                 # API 키 (Git 제외)
├── .gitignore           # .env, results 제외
├── README.md            # 프로젝트 문서
└── results/             # 실행 결과 저장 폴더
    ├── data_2026-08-15.json
    └── report_2026-08-15.md
```
