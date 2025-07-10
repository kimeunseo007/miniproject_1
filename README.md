# Human Activity Recognition (AI 미니프로젝트 1차)

> 스마트폰 센서 데이터를 활용한 인간 행동 인식 모델링 프로젝트  
> 📅 기간: 2025.04.14 ~

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
  1. is_dynamic (정적 vs 동적) 이진 분_
