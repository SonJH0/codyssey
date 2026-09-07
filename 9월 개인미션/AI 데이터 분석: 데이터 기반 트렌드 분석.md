# SK하이닉스 주가 시계열 분석 프로젝트

SK하이닉스 주가 데이터를 수집·분석하고,
머신러닝으로 미래 주가를 예측하는 **인터랙티브 대시보드**입니다.

---

## 프로젝트 개요

- **분석 대상**: SK하이닉스 주가 (2025 ~ 2026)
- **데이터 규모**: 407일치 (5개 컬럼)
- **주요 기능**: 시각화, 이동평균 분석, 주가 예측
- **결과물**: Streamlit 웹 대시보드

---

## 사용 기술

| 분류 | 기술 |
|------|------|
| 언어 | Python 3.13 |
| 데이터 수집 | yfinance |
| 데이터 처리 | pandas |
| 시각화 | matplotlib |
| 머신러닝 | scikit-learn (선형회귀) |
| 웹 대시보드 | Streamlit |

---

## 주요 기능

### 1️⃣ 주가 시각화
- 종가 추이 그래프
- 거래량 분석
- 이동평균선 (사용자 조절 가능)

### 2️⃣ 인터랙티브 대시보드
- 이동평균 기간 슬라이더 조절
- 예측 기간 슬라이더 조절
- 실시간 그래프 업데이트

### 3️⃣ 주가 예측
- 선형회귀 기반 추세선
- N일 후 예상 주가 계산
---

## analysis.ipynb

<img width="999" height="687" alt="image" src="https://github.com/user-attachments/assets/f22a9e63-6314-4637-b48c-94f22ea64e05" />

<img width="985" height="750" alt="image" src="https://github.com/user-attachments/assets/28941619-a3cc-443d-9f46-cbee1d0de222" />

<img width="982" height="716" alt="image" src="https://github.com/user-attachments/assets/36e51e1b-8b25-4bd8-bd18-267284dd683d" />

<img width="950" height="825" alt="image" src="https://github.com/user-attachments/assets/9f942b83-9d58-4b57-8d09-d26035472ade" />

<img width="971" height="608" alt="image" src="https://github.com/user-attachments/assets/1db061d8-048a-4949-bd69-67ed2758abf4" />

<img width="973" height="425" alt="image" src="https://github.com/user-attachments/assets/e33409a0-87a8-471f-8692-2052c8e42ab6" />

## 리포트

### 📈 SK하이닉스 주가 시계열 분석 리포트

#### 1. 분석 주제
SK하이닉스의 주가 데이터를 활용한 시계열 분석

#### 2. 데이터 설명
- **출처**: yfinance (Yahoo Finance)
- **종목**: SK하이닉스
- **기간**: 2025-01-02 ~ 2026-09 (약 407일)
- **컬럼**: Close, High, Low, Open, Volume (5개)

#### 3. 분석 질문
1. SK하이닉스 주가는 전체적으로 어떤 흐름을 보이는가?
2. 주가가 크게 움직인 시점에 거래량은 어떻게 변했는가?
3. 이동평균선(MA20, MA60)으로 볼 때 매매 신호(골든크로스 등)가 있었는가?


#### 4. 시각화

##### 4-1. 종가 추이
<img width="1001" height="469" alt="image" src="https://github.com/user-attachments/assets/a4355bbd-719a-44b3-aa93-ada3c6f3824a" />


SK하이닉스의 종가는 2025년부터 우상향하다가 2026년 중반 고점 이후 조정 국면에 진입했다.

##### 4-2. 거래량 추이
<img width="1001" height="469" alt="image" src="https://github.com/user-attachments/assets/4a2e5900-f426-4626-be02-4c8380e21294" />


특정 시점에 거래량이 폭발적으로 증가하는 구간이 관찰된다.

##### 4-3. 종가 + 이동평균선 (MA20, MA60)
<img width="1001" height="469" alt="image" src="https://github.com/user-attachments/assets/8bd35ac4-9e38-4463-a6a0-73efd31f7c2e" />


MA20이 MA60을 상향 돌파하는 골든크로스 이후 상승세를 보였으나, 이후 하락 전환되었다.

#### 5. 인사이트
1. **강력한 상승 후 조정**: 주가는 2025년 하반기부터 급등하여 2026년 7월 최고점(약 300만원) 도달, 이후 하락 조정 중.
2. **최고가 시점 거래량 폭발**: 주가 급등 구간에서 거래량이 평소보다 크게 증가 → 시장 관심 집중.
3. **골든크로스 후 하락 전환**: 2025년 하반기 골든크로스(MA20>MA60)로 상승세, 2026년 7월 이후 종가가 MA20 아래로 내려가며 하락 전환.

#### 6. 결론 및 한계점
- **결론**: SK하이닉스는 분석 기간 동안 강한 상승 추세를 보였으나 최고점 이후 조정 국면에 진입함. 이동평균선과 거래량이 추세 판단에 유용함.
- **한계점**:
  - 과거 데이터 기반 분석으로 미래 예측을 보장하지 않음.
  - 외부 요인(반도체 업황, 환율, 글로벌 이슈 등)은 반영하지 않음.

#### 7. AI 사용 로그
- **사용 작업**: 코드 작성, 시각화, 인사이트 해석
- **사용 이유**: 시간 절감, 개념 학습, 오류 해결
- **검증 방법**: 그래프 직접 확인, 데이터 재확인, 결과 재현

## 웹 대시보드

실행 방법 : streamlit run app.py

링크 : http://localhost:8501/

<img width="1881" height="934" alt="image" src="https://github.com/user-attachments/assets/31675c01-a5c7-4d5a-bbee-6a4387a42a7b" />

<img width="1908" height="929" alt="image" src="https://github.com/user-attachments/assets/c4874ae7-528d-4ce0-af14-d1acd0720400" />










## 📁 프로젝트 구조
<img width="275" height="284" alt="image" src="https://github.com/user-attachments/assets/2781f591-1556-42f2-bdef-855dac205946" />



