# A/B Testing Project

사용자 행동 퍼널 전반에서 A/B 테스트 효과를 검증하고, 연령·성별·날짜에 따라 실험 효과가 어떻게 달라지는지 분석한 프로젝트입니다.  
CTR, CVR, AOV, ARPU 등 주요 KPI 모니터링과 세그먼트별 A/B 테스트를 위한 Tableau 대시보드를 구축하여, 실험안 적용이 유효한 사용자 집단과 추가 검증이 필요한 영역을 도출했습니다.

---

## Project Links

- [Google Colab Notebook 열기](https://colab.research.google.com/drive/1_DS48PIWWIUy5n91Y5utejMmfK6plaQj?usp=sharing)
- [Tableau Dashboard 보기](https://public.tableau.com/app/profile/seoyeon.park.ds/viz/ABTestingPerformanceDashboard/KPIAnalysisABTestingReport)
- [프로젝트 슬라이드 보기](https://docs.google.com/presentation/d/19iYnmh2KrfUgZfgv2RSrVi3eC2_tJWx3t-4H8Em49UQ/edit?usp=sharing)

---

## Workflow

### 1. 원천 데이터 적재 및 스키마 구축 (SQL)
Amazon S3에서 사용자·실험 배정·이벤트 데이터를 수집하고 EDA를 수행한 뒤, 분석에 활용할 수 있도록 관계형 원천 데이터 스키마를 구축했습니다.

### 2. A/A 그룹 배정 균형 검증 (Python)
Hash 기반으로 구성된 Test / Control 그룹의 배정 비율을 검증하고, A/B 테스트 수행 전 통계적으로 유의한 배정 불균형이 없는지 확인했습니다.

### 3. 전체 사용자 수준 A/B 테스트 (Python)
사용자 행동 데이터를 사용자-일 단위로 집계하고, Impression, Click, Purchase, Revenue에 대해 독립표본 t-검정을 수행하여 Test와 Control 간 평균 차이를 검증했습니다.

### 4. 세그먼트별 집계 테이블 구축 (SQL)
날짜·연령·성별 세그먼트별 반복 A/B 테스트를 위해 `n`, `sum`, `sum2` 통계량을 포함한 OLAP형 집계 테이블을 구축했습니다.

### 5. KPI 모니터링 및 A/B 테스트 대시보드 구축 (Tableau)
CTR, CVR, AOV, ARPU를 모니터링하고, 세그먼트별 퍼널 단계의 Test–Control 효과와 통계적 유의성을 비교할 수 있는 Tableau 대시보드를 구축했습니다.

### 6. 세그먼트 인사이트 및 Drill-down
연령·성별에 따라 서로 다른 실험 반응을 확인했으며, 날짜별 분석을 통해 1월 16일의 부정적 이상 신호가 특히 20–49세 사용자에게 집중된 것을 확인했습니다.

---

## 비즈니스 전략 제안

실험안을 전체 사용자에게 일괄 적용하기보다, 세그먼트별 효과를 고려한 차등 적용 전략이 필요하다고 판단했습니다.

- **1월 16일 이상 신호 우선 검증**  
  시스템·운영 이슈 또는 실험 요소의 영향 여부를 확인한 뒤 실험 결과를 재검증합니다.

- **0–19세**  
  Click, Purchase, Revenue에서 긍정적인 효과가 확인되어 일부 트래픽에 우선 적용하고 성과 재현 여부를 모니터링합니다.

- **20–49세**  
  Purchase와 Revenue가 감소했으므로 기존안을 유지하고, 실험 요소를 분리하여 원인을 추가 검증합니다.

- **50세 이상**  
  주요 지표에서 유의한 변화가 확인되지 않아 기존안을 유지합니다.

- **성별 후속 실험**  
  남성의 노출·클릭 증가가 구매로 이어지지 않은 원인과 여성의 구매 감소에 영향을 준 실험 요소를 추가 A/B 테스트를 통해 확인합니다.

---

## Tools Used

- SQL
- Python
- Google Colab
- Tableau
- Claude
- 통계적 가설 검정
- 세그먼트 / 퍼널 분석
