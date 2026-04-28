# 🐦 BirdCLEF+ 2026 Kaggle 대회 정보

> **출처:** https://www.kaggle.com/competitions/birdclef-2026  
> **정리일:** 2026-04-20

---

## 1. 대회 기본 정보

| 항목 | 내용 |
|------|------|
| **대회명** | BirdCLEF+ 2026 — Acoustic Species Identification in the Pantanal |
| **주최** | Cornell Lab of Ornithology (K. Lisa Yang 보전 생물음향학 센터) |
| **공동 주관** | TU Chemnitz, Google DeepMind, 브라질 연구기관 다수 |
| **플랫폼** | Kaggle (Featured Competition) |
| **대회 유형** | 다중 레이블 오디오 분류 (멀티 택소노미 음향 종 식별) |
| **상금 총액** | $50,000 USD |
| **관련 학회** | LifeCLEF 2026 @ CLEF 2026 Conference |

---

## 2. 대회 배경 및 목적

### 배경
**판타날(Pantanal)** 은 브라질과 인접국에 걸친 **150,000km²** 이상의 광대한 습지 생태계로, **650종 이상의 조류**를 포함한 무수한 야생동물이 서식합니다.

그러나 계절성 홍수, 산불, 농업 확장, 기후변화 등으로 인해 정기적인 현장 조사가 어렵고, 방대한 지역을 인력으로 모니터링하는 것은 비용과 물류 면에서 매우 어렵습니다.

> *"볼 수 없는 생태계를 어떻게 보호할까요? 한 가지 방법은 귀를 기울이는 것입니다."*

### 해결 방법
약 **1,000개의 음향 레코더**를 판타날 전역에 배포하여 지속적으로 야생동물 소리를 수집합니다. 이는 방대한 양의 오디오 데이터를 생성하므로, 인력 검토 한계를 넘어선 **머신러닝 자동 분류 모델**이 필요합니다.

### 과제 목표
- 야생동물 울음소리로부터 자동으로 종(species) 식별
- 다양한 판타날 서식지 환경 대응
- 실제 현장 수집 (노이즈가 많은) 오디오 데이터 처리
- 증거 기반 보전 의사결정 지원

---

## 3. 일정 (Timeline)

| 마일스톤 | 날짜 |
|----------|------|
| 대회 시작 | 2026년 3월 11일 |
| 참가 신청 마감 | 2026년 5월 27일 |
| 팀 합병 마감 | 2026년 5월 27일 |
| **최종 제출 마감** | **2026년 6월 3일** |
| 워킹 노트 제출 마감 | 2026년 6월 17일 |
| 워킹 노트 채택 통보 | 2026년 6월 24일 |
| 워킹 노트 최종본 마감 | 2026년 7월 6일 |

> 모든 마감 시각은 **UTC 23:59** 기준

---

## 4. 상금 (Prizes)

| 순위 | 상금 |
|------|------|
| 합계 | **$50,000 USD** |
| 워킹 노트 우수상 (2팀) | $5,000 USD ($2,500 × 2) |

- 워킹 노트 상: CLEF 2026 학회 논문집에 제출된 최우수 2편의 접근법 논문에 수여
- 논문에는 제출 결과를 재현 가능한 수준의 상세한 방법론이 포함되어야 함

---

## 5. 평가 지표 (Evaluation Metric)

### padded cmAP (class-averaged Mean Average Precision)

- **임계값(threshold)이 필요 없는** 순위 기반 메트릭
- 채점 전에 각 제출물과 정답에 **종(species)별 5개의 진양성(true positive) 행을 패딩**
- 패딩의 목적:
  1. 테스트셋에 실제 양성 레이블이 없는 종에 대한 예측도 허용
  2. 양성 레이블이 매우 적은 종의 영향을 줄임

### 제출 형식
- 사운드스케이프 녹음의 **비겹침 5초 단위** 구간별 예측
- 각 행: `row_id` (사운드스케이프 파일명 + 시간 구간)
- 각 종(species) 열에 **확률 점수(0~1)** 기입

---

## 6. 데이터 (Data)

### 학습 데이터
| 파일/폴더 | 설명 |
|-----------|------|
| `train_audio/` | 레이블된 오디오 녹음 (OGG 포맷, 종별 하위 폴더 구성) |
| `train_metadata.csv` | 각 학습 녹음의 메타데이터 |

### train_metadata.csv 주요 컬럼
| 컬럼명 | 설명 |
|--------|------|
| `primary_label` | 주 조류 종의 eBird 코드 |
| `secondary_labels` | 배경/공존 종 (녹음자 추가 어노테이션) |
| `type` | 울음 유형 (call, song 등) |
| `latitude`, `longitude` | 녹음 위치 |
| `scientific_name` | 학명 |
| `common_name` | 일반명 (영어) |
| `author` | eBird 녹음 제공자 |
| `filename` | 오디오 파일 상대 경로 |
| `rating` | 품질 평점 (0.0 ~ 5.0) |
| `date` | 녹음 날짜 |

### 테스트 / 사운드스케이프 데이터
| 파일/폴더 | 설명 |
|-----------|------|
| `test_soundscapes/` | 레이블 없는 현장 다종 녹음 (OGG 포맷) |

- 판타날 레코더에서 수집한 1분짜리 연속 녹음
- 모델은 **5초 비겹침 구간별** 예측을 수행해야 함

### 종(Species) 정보
- 판타날 생태계에 서식하는 종에 집중
- BirdCLEF+ 2026은 조류뿐 아니라 **다중 분류군(multi-taxa)** 포함 가능 ("+" 의미)
- 참고: BirdCLEF 2025는 206종

---

## 7. 규칙 (Rules)

### 참가 기본 규칙
- 참가자 1인당 **Kaggle 계정 1개**만 사용 가능
- 팀 최대 인원: **5명**
- 일일 최대 제출 횟수: **5회**

### 데이터 및 모델 사용
- **외부 데이터**: 공개적으로 이용 가능한 데이터 허용 (반드시 공개 선언 필요)
- **사전 학습 모델(Pre-trained models)**: 공개된 모델 허용
- **추론 환경**: Kaggle 노트북 내에서 실행 (추론 시 인터넷 접근 불가)
- Kaggle의 **추론 시간 제한** 준수 필수

### 수상 조건
- 수상자는 제출물을 재현할 수 있는 **코드 제출 필수**
- 수상 자격은 Kaggle이 인정하는 **국가의 인증된 사용자**에 한함

---

## 8. 대회 특이사항

- 2026년은 처음으로 **판타날(Pantanal)** 생태계에 초점을 맞춤
  - 이전: 2025년 콜롬비아 마그달레나 중류, 2023년 동아프리카 등
- BirdCLEF은 **2014년부터** ImageCLEF/LifeCLEF 산하에서 매년 개최
- **"+"** 표기는 조류 이외의 **다중 분류군(multi-taxa)** 포함을 의미
- 약 **3,659명 참가, 355명 활동, 340팀, 1,528건 이상 제출** (대회 규모 참고)
- 베조스 지구 기금(Bezos Earth Fund) AI for Climate and Nature 그랜드 챌린지 / iNaturalist 지원

---

## 9. 관련 링크

| 링크 | 설명 |
|------|------|
| [Kaggle 대회 메인](https://www.kaggle.com/competitions/birdclef-2026) | 공식 대회 페이지 |
| [ImageCLEF BirdCLEF 2026](https://www.imageclef.org/BirdCLEF2026) | LifeCLEF 공식 페이지 |
| [데이터 탭](https://www.kaggle.com/competitions/birdclef-2026/data) | 데이터 다운로드 |
| [규칙 탭](https://www.kaggle.com/competitions/birdclef-2026/rules) | 공식 규칙 |
| [평가 탭](https://www.kaggle.com/competitions/birdclef-2026/overview/evaluation) | 평가 지표 상세 |
| [K. Lisa Yang 센터](https://www.birds.cornell.edu/ccb/) | 주최 기관 |

---

## 10. 접근 전략 요약 (참고)

```
오디오 분류 접근법
├── 특징 추출: Mel-spectrogram, MFCC 등
├── 모델: EfficientNet, BirdNET, PANNs, AST 등
├── 사전 학습: BirdNET, AudioSet 사전학습 모델 활용
├── 앙상블: 여러 모델 조합
└── 후처리: 종별 임계값 조정, 패딩 고려
```

> **핵심**: 평가 지표가 `padded cmAP`이므로 종별 순위(ranking) 최적화가 중요하며, 희귀종에 대한 recall 확보도 전략적으로 고려 필요.
