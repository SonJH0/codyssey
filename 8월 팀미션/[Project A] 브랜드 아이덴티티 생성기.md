
# 🎨 AI 브랜드 아이덴티티 생성기

> 브랜드 브리프(JSON) 하나로 **네이밍·슬로건·스토리·컬러 팔레트·로고 시안**까지 자동 생성하는 CLI 프로그램

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![Groq](https://img.shields.io/badge/LLM-Groq-orange)
![HuggingFace](https://img.shields.io/badge/Image-HuggingFace-yellow)

---

## 1. 🎯 미션 소개

브랜드 디자인은 네이밍, 슬로건, 스토리, 컬러, 로고 등 다양한 요소를 종합적으로 기획해야 하는 전문 작업입니다. 외주 비용이 수백만 원에서 시작하는 이유도 시간과 전문성을 요구하기 때문입니다.

이 프로젝트는 **브랜드 브리프(업종, 타겟, 키워드 등)를 입력하면 AI가 브랜드 요소를 자동 생성**하는 CLI 프로그램입니다.

- **LLM API(Groq)** → 텍스트 브랜드 요소 생성 (네이밍, 슬로건, 스토리, 컬러)
- **이미지 생성 API(HuggingFace)** → 로고 시안 생성
- 모든 결과물을 폴더에 저장

---

## 2. 📦 최종 결과물

CLI 기반 Python 프로그램 1개로 아래 기능을 모두 구현했습니다.

| 기능 | 구현 내용 |
|------|-----------|
| **브랜드 브리프** | JSON 파일로 브랜드 정보 입력 |
| **브랜드 요소 생성** | 네이밍 3개(+의미), 슬로건 3개, 스토리(300자), 컬러 팔레트 |
| **로고 시안 생성** | 이미지 생성 API로 로고 2~3개 PNG 저장 |
| **결과 저장** | 텍스트 → JSON, 컬러 팔레트 → PNG, 로고 → PNG |

---

## 3. 🖼️ 결과물 예시

**입력 브랜드**: 인스타 감성 카페 `코지그램` ☕

컬러 팔레트

<img width="921" height="331" alt="image" src="https://github.com/user-attachments/assets/78aa4ddf-573f-4c58-b499-1552d1264b0c" />

로고 시안

<img width="338" height="294" alt="image" src="https://github.com/user-attachments/assets/23b8ec46-459b-4274-9267-f8b77a4447c8" />
<img width="241" height="208" alt="image" src="https://github.com/user-attachments/assets/4956810b-3820-4e67-bfd1-0eea299f6ebe" />


* 로고를 3개 만들도록 프롬프트를 설개했으나 완성하는 도중 무료토큰의 소진으로 두 개 밖에 만들지 못했습니다. 다만 에러 처리 과정에 따라 이미 생성된 로고는 자동 저장되고 3번째 로고는 토큰부족으로 만들지 못했다는 알림이 왔습니다.
* 로고 생성 중 만들었던 네이밍과 다른 글자가 로고에 첨부되는 일이 발생하여 프롬프트에 'no word'를 추가했습니다.

<img width="748" height="55" alt="image" src="https://github.com/user-attachments/assets/a264be8b-1dcd-44c6-9016-4eeaaa524821" />



- **메인 컬러**: `#F7D2C4`
- **서브 컬러**: `#964B00`, `#C9E4CA`, `#FFC5C5`

---

## 4. ⚙️ 개발 환경

- **Python 3.10+**
- **Groq API** – 텍스트 생성 (LLM)
- **HuggingFace InferenceClient** – 이미지 생성 (FLUX 모델)

---

## 5. 📂 폴더 구조

```
brand_generator/
├── brand_generator.py     # 메인 프로그램
├── brief.json             # 브랜드 브리프 입력 파일
├── check_models.py        # 사용 가능 모델 확인용
├── requirements.txt       # 의존성 목록
├── .env                   # API 키 (git 미포함)
├── .gitignore             # 제외 파일 목록
└── output/                # 결과물 저장 폴더
    ├── brand_result.json  # 전체 텍스트 결과
    ├── color_palette.png  # 컬러 팔레트 시각화
    ├── logo_1.png         # 로고 시안 1
    └── logo_2.png         # 로고 시안 2
    
```

---

## 6. 🚀 설치 및 실행

### 1) 저장소
```bash
https://github.com/SonJH0/brand_generator
```


### 2) API 키 설정 (`.env` 파일 생성)
```env
GROQ_API_KEY=your_groq_api_key
HF_TOKEN=your_huggingface_token
```

### 3) 실행
```bash
python brand_generator.py
```

---

## 7. 📥 브랜드 브리프

```json
{
  "industry": "인스타용 카페",
  "target_audience": "20-30대 SNS에 관심 많은 직장인",
  "keywords": ["세련됨", "화제성", "편안함", "깔끔함"],
  "tone": "따뜻하고 친근한",
  "language": "ko",
  "competitors": ["투썸플레이스", "스타벅스"]
}
```

| 구분 | 필드 |
|------|------|
| **필수** | `industry`(업종), `target`(타겟), `keywords`(키워드) |
| **선택** | `tone`(톤앤매너), `competitors`(경쟁사), `language`(언어) |

---

## 8. 💻 실행 예시

<img width="774" height="805" alt="image" src="https://github.com/user-attachments/assets/e43bbaa4-bba7-4b5e-a83c-b187dfc489ad" />



---

## 9. 🔄 처리 파이프라인

```
[1] brief.json 로드
      ↓
[2] 브랜드 네이밍 생성 (Groq LLM)
      ↓
[3] 슬로건 생성 (Groq LLM)
      ↓
[4] 브랜드 스토리 생성 (Groq LLM)
      ↓
[5] 컬러 팔레트 생성 (Groq LLM) → matplotlib 시각화
      ↓
[6] 로고 시안 생성 (HuggingFace) → PNG 저장
      ↓
[7] brand_result.json 저장
```

---

## 10. 에러처리

<img width="705" height="868" alt="image" src="https://github.com/user-attachments/assets/57323cd3-7213-455b-8e08-125c44e1dda6" />

<img width="790" height="258" alt="image" src="https://github.com/user-attachments/assets/f49768f4-ed9f-4049-9834-731229aeadca" />

<img width="832" height="279" alt="image" src="https://github.com/user-attachments/assets/8aad4b36-4400-454d-a0ab-61555197a7b0" />



1. 그록의 api가 등록되지 않았을 경우 '❌ GROQ_API_KEY가 없습니다. .env 파일을 확인하세요.'라는 알림이 갑니다.

2. 어떤 이유로든 그록의 api 호출이 실패되면 '⚠️ API 호출 실패'라는 알림이 갑니다.

3. 이미지 생성 ai인 hugging face의 api가 없을 경우 '⚠️ HF_API_KEY가 없어 이미지 자동 생성을 건너뜁니다.'라는 알림이 갑니다.

4. hugging face의 로딩이 지체되면 '모델 로딩 중... 30초 대기', 오류가 발생하면 '❌ 401 인증 오류: HF_API_KEY를 확인하세요.'라는 알림이 가고 곧바로 다음으로 넘어갑니다.

---

## 12. 각 코드의 역할 및 설명

| 역할 | 담당 함수/모듈 | 제안설명 |
| :--- | :--- | :--- |
| **입력 로드** | `load_brief()` | brief.json 읽기 및 필수 필드 확인 |
| **프롬프트 생성** | `build_prompt()` | 단계별 LLM 프롬프트 생성 |
| **LLM 호출** | `call_groq()` | Groq API 호출 및 응답 수신 |
| **이미지 생성** | `generate_logo()` | HuggingFace API로 로고 생성 |
| **저장** | `save_result()` | JSON, PNG 파일 저장 |
| **에러 처리** | `record_error()` | 실패 정보를 errors 필드에 누적 |

---

## 13. 프롬프트

<img width="823" height="803" alt="image" src="https://github.com/user-attachments/assets/94cc2edc-48fc-487d-b75a-4ae2906619ce" />

* input의 브리프 파일 경로와 output의 출력 폴더 경로의 경우 아무것도 입력하지 않고 엔터만 누르면 작동하도록 코드를 짰습니다.

<img width="565" height="767" alt="image" src="https://github.com/user-attachments/assets/6691bff2-6176-44f3-899d-427a4b1ae196" />
<img width="564" height="722" alt="image" src="https://github.com/user-attachments/assets/93f0e917-f173-4be9-bd8d-ae09d07df6b4" />
<img width="793" height="640" alt="image" src="https://github.com/user-attachments/assets/b04500a5-deff-4084-9091-0bce2d6a7fe6" />
<img width="923" height="962" alt="image" src="https://github.com/user-attachments/assets/dfb649be-20e5-43f8-9d30-66b820845fb8" />
<img width="803" height="663" alt="image" src="https://github.com/user-attachments/assets/a5e86f50-16e3-4f1c-a300-8018cd0cd5ff" />

* 로고를 만들기 위한 outcome들을 만들어 냅니다.

<img width="706" height="750" alt="image" src="https://github.com/user-attachments/assets/eae8bdf6-5391-42ed-8b7b-94ee37963d5f" />

* 이미지 같은 경우는 이런 식으로 총 3개의 예시 로고를 만들도록 하였습니다.
* 만약 중간에 오류가 발생하거나 토큰이 부족하여 사진 생성에 실패하더라도 그 전에 만들어진 1,2,3,4 단계의 내용과 이미 만들어진 로고 이미지 역시 날라가지 않고 json파일에 저장되도록 했습니다.

## 🔄 공유 컨텍스트 및 상태 관리

### 1. 공유 컨텍스트 구조
모든 생성 단계는 `result`라는 단일 딕셔너리를 공유 컨텍스트로 사용합니다.
프로그램 시작 시 입력 브리프로 초기화되며, 각 단계가 결과를 누적합니다.

​```python
result = {"brief": brief}   # 공유 컨텍스트 초기화
​```

### 2. 단계별 상태 업데이트 흐름
각 단계는 완료 시 자신의 결과를 `result`에 키로 추가하여
상태를 점진적으로 누적합니다. (추적 가능)

| 순서 | 단계 | 업데이트되는 키 |
|------|------|----------------|
| 1 | 네이밍 | `result["naming"]` |
| 2 | 슬로건 | `result["slogan"]` |
| 3 | 스토리 | `result["story"]` |
| 4 | 컬러 | `result["colors"]` |
| 5 | 로고 | `result["logo_paths"]` |

### 3. 컨텍스트 데이터 재사용
입력 브리프(`brief`)는 공유 컨텍스트에 유지되며,
모든 단계의 프롬프트에서 반복 참조됩니다.
(예: 업종, 키워드, 톤앤매너, 경쟁브랜드)

### 4. 반복(루프) 처리
로고 생성 단계는 동일 프롬프트로 3회 반복하며,
각 시도는 독립적으로 성공/실패 처리됩니다.

​```python
for i in range(1, 4):        # 로고 3개 반복 생성
    try:
        image = client.text_to_image(final_prompt, model="...")
        image.save(logo_path)
        logo_paths.append(logo_path)   # 성공한 것만 누적
    except Exception as e:
        print(f"⚠️ 로고 {i} 생성 오류: {e}")
​```

### 5. 최종 상태 영속화
누적된 `result`는 최종적으로 `brand_result.json`으로 저장되어
전체 실행 상태를 추적할 수 있습니다.

​```python
json.dump(result, f, ensure_ascii=False, indent=2)
​```

## 🧩 LLM 출력 강제 및 검증 전략

### 1. 출력 형식 강제 (프롬프트 레벨)
모든 프롬프트에 "반드시 아래 형식으로만 답하세요" 지시를 포함하여
LLM이 불필요한 설명 없이 정해진 형식으로 응답하도록 유도합니다.

- 네이밍: `브랜드명 (영문): 의미 설명` 형식
- 슬로건: 문구 3줄만 출력
- 컬러: `#RRGGBB` HEX 형식만 출력

### 2. 출력 파싱 및 검증 (코드 레벨)
LLM이 형식을 벗어난 텍스트를 반환할 경우를 대비해
정규식으로 필요한 데이터만 추출·검증합니다.

​```python
hex_codes = re.findall(r"#[0-9A-Fa-f]{6}", color_text)
if hex_codes:              # 검증: 유효한 값 존재 확인
    result["colors"] = hex_codes
else:                      # 대체: 실패 안내
    print("⚠️ HEX 코드를 찾지 못했습니다.")
​```

### 3. 결과 JSON 스키마
최종 결과는 아래 스키마로 `brand_result.json`에 저장됩니다.

| 필드 | 타입 | 설명 |
|------|------|------|
| brief | object | 입력 브리프 |
| naming | string | 브랜드명 후보 |
| slogan | string | 슬로건 후보 |
| story | string | 브랜드 스토리 |
| colors | array | HEX 코드 배열 |
| logo_paths | array | 로고 이미지 경로 |

### 4. 실패 대응
각 단계는 독립적으로 처리되며, 특정 단계가 실패해도
(`if naming:` 등) 다음 단계는 정상 진행됩니다.


---

## 14. 최종 결과물

<img width="1901" height="993" alt="image" src="https://github.com/user-attachments/assets/7666ef57-4295-4eaf-8eb7-16dcfcbf5ca6" />
<img width="1903" height="1002" alt="image" src="https://github.com/user-attachments/assets/686468fd-cb93-45fc-ba52-ce312b85fe03" />
<img width="1892" height="1004" alt="image" src="https://github.com/user-attachments/assets/9b0ef6c3-cb8a-45de-a1a0-6b6e490b2be5" />
<img width="1914" height="1013" alt="image" src="https://github.com/user-attachments/assets/036b13e6-13ca-48b8-8b31-79ec726d499b" />
<img width="1906" height="1004" alt="image" src="https://github.com/user-attachments/assets/ecfad147-786d-4e87-9197-230583070841" />



---

## 15. ✅ 요구사항 대비 완료 현황

| 요구사항 | 완료 | 설명 |
|----------|:----:|------|
| 사용자 입력 (print/input 대화형) | ✅ | 브리프 경로 필수, 출력 폴더 선택(기본 `./output`) |
| 브랜드 브리프 입력 (JSON) | ✅ | 필수/선택 필드 파싱 |
| 브랜드 네이밍 생성 (3~5개+의미) | ✅ | 3개 생성 |
| 슬로건 생성 (3개) | ✅ | 톤앤매너 반영 |
| 브랜드 스토리 (300자) | ✅ | 탄생 배경·철학·비전 포함 |
| 컬러 팔레트 (메인1+서브2~3) | ✅ | HEX 코드로 생성 |
| 컬러 팔레트 시각화 (PNG) | ✅ | matplotlib 저장 |
| 로고 시안 생성 (2~3개 PNG) | ✅ | HuggingFace로 2~3개 생성 |
| 결과 저장 (JSON+PNG) | ✅ | `brand_result.json` + 개별 PNG |
| 에러 처리 | ✅ | API 실패 하더라도 다음 단계 계속 진행, 그 후 에러가 뜨지 않은 항목만 따로 저장 |
| API 키 관리 | ✅ | `.env` 환경변수 사용 |
| **[보너스]** 경쟁사 분석 | ✅ | 차별화 포인트 제안 |
