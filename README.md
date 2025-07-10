# Human Activity Recognition (AI 미니프로젝트 1차)

> 스마트폰 센서 데이터를 활용한 인간 행동 인식 모델링 프로젝트  
> 📅 기간: 2025.04.14 ~ 2025.04.15

---

## 📌 프로젝트 개요

스마트폰 센서로 수집된 데이터를 기반으로 **인간의 6가지 행동**을 분류하는 머신러닝 모델을 구축합니다.

- 데이터 출처: UCI Human Activity Recognition Using Smartphones
- 데이터 특성: 561개의 Feature, 6개의 Class
- 수행 방식: EDA → 기본 모델링 → 단계별 모델링 (2단계 구조)

---

## 📁 데이터 정보

| 항목 | 내용 |
|------|------|
| 출처 | UCI ML Repository |
| 데이터 포맷 | CSV (Row: 5881, Feature: 561, Label: Activity) |
| 센서 | 가속도계(Accelerometer), 자이로스코프(Gyroscope) |
| 행동 클래스 |
- `WALKING`
- `WALKING_UPSTAIRS`
- `WALKING_DOWNSTAIRS`
- `SITTING`
- `STANDING`
- `LAYING`

✅ 정적 행동 (0): `STANDING`, `SITTING`, `LAYING`  
✅ 동적 행동 (1): `WALKING`, `WALKING_UPSTAIRS`, `WALKING_DOWNSTAIRS`

---

## 🎯 프로젝트 목표

- 탐색적 데이터 분석(EDA)을 통해 주요 Feature 탐색
- 다양한 분류 모델을 비교하고 성능 측정
- 2단계 모델링 구조 설계:
  - 1단계: 정적/동적 행동 이진 분류
  - 2단계: 세부 동작 분류 (각 그룹 내 3-class)

---

## 🛠️ 사용 기술

- Python (Pandas, Scikit-Learn, Seaborn, Matplotlib)
- 머신러닝 모델:
  - Random Forest
  - Logistic Regression
  - KNN
  - XGBoost 등
- 모델 저장 및 로딩: `joblib`
- 데이터 전처리:
  - NaN 처리, 가변수화, StandardScaler, Train/Test Split

---

## 🔍 프로젝트 구성

### [1] 탐색적 데이터 분석 (`1. 탐색적 데이터 분석_통합_3조.ipynb`)
- 변수 중요도 기반 상위 N개 feature 선정 (Random Forest)
- 정적/동적 행동 간의 Feature 그룹 분석 (평균, std, iqr 등)
- 상관관계 및 Boxplot, KDE 시각화

### [2] 기본 모델링 (`2. 기본 모델링_통합_3조.ipynb`)
- 여러 ML 모델을 활용한 전체 6-class 분류 성능 비교
- 모델별 정확도, 정밀도, 재현율 평가

### [3] 단계별 모델링 (`3 단계별_모델링_통합_3조.ipynb`)
- 2단계 구조:
  1. is_dynamic (정적 vs 동적) 이진 분류
  2. 정적 행동 3-class 분류 모델
  3. 동적 행동 3-class 분류 모델
- 단계별 모델을 하나의 파이프라인으로 구성
- 최종 예측 함수 구현

---

## 🧠 프로젝트 전략 요약

| 단계 | 내용 |
|------|------|
| Step 1 | 561개의 Feature 중 변수 중요도 기반 주요 Feature 선별 및 EDA 수행 |
| Step 2 | 여러 ML 알고리즘 적용 → 성능 비교 및 최적 모델 선정 |
| Step 3 | 두 단계 모델로 분리하여 정확도 향상 유도 (정적/동적 → 세부 행동) |
| Pipeline | `predict_activity()` 함수로 test 데이터 예측 자동화 |

---

## 📊 결과 요약 (예시)

- Step1 RandomForest 중요도 기준 상위 Feature:  
  `tBodyAcc-mean()-X`, `tBodyGyro-std()-Y`, ...

- 기본 모델 정확도:
  - RandomForest: 93%
  - KNN: 88%
  - XGBoost: 95%

- 2단계 모델링 결과:
  - Step1 정적/동적 분류 정확도: 97%
  - Step2 세부 클래스 분류 정확도: 정적(96%), 동적(95%)

#### 📝 Learned & Reflection
- LangGraph로 **State 기반 Agent 흐름을 설계**하며, 단순한 AI 응답 생성이 아닌 **시나리오 중심 AI 시스템 구축법**을 익혔습니다.
- 답변 평가 결과의 불확실성을 보완하기 위해 **Reflection Node**와 **재평가 흐름**을 도입, **AI의 신뢰성과 품질 개선 전략**을 경험했습니다.
- Vector DB를 통해 질문 생성을 고도화하며 **RAG 구조 실습 및 프롬프트 엔지니어링 역량**을 확보했습니다.
- 단순 기능 구현을 넘어, **실제 사용자 경험까지 고려한 웹 인터페이스(Gradio) 설계 경험**이 특히 인상 깊었습니다.

---

## ✅ 종합 회고

두 프로젝트를 통해 **데이터 분석 중심의 문제 해결 역량**과 **생성형 AI를 활용한 시스템 설계 능력**을 균형 있게 강화할 수 있었습니다.  
이론이 아닌 **실제 문제 해결과 사용자 흐름을 고려한 AI 설계 경험**이 가장 큰 성장 포인트였습니다.
