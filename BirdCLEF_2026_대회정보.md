# 🐦 BirdCLEF+ 2026 Kaggle 대회 정보

> **출처:** Kaggle 공식 API + 직접 수집 (2026-04-29)  
> **대회 URL:** https://www.kaggle.com/competitions/birdclef-2026

---

## 1. 대회 기본 정보

| 항목 | 내용 |
|------|------|
| **대회명** | BirdCLEF+ 2026 |
| **부제** | Acoustic Species Identification in the Pantanal, South America |
| **주최** | Cornell Lab of Ornithology |
| **카테고리** | Research |
| **플랫폼** | Kaggle (Kernels Only — 노트북 제출 필수) |
| **대회 유형** | 다중 레이블 오디오 분류 (Multi-taxa 음향 종 식별) |
| **상금** | $50,000 USD |
| **평가 지표** | Birdclef ROC AUC (padded cmAP 기반) |
| **팀 최대 인원** | 5명 |
| **일일 최대 제출** | 5회 |
| **대회 ID** | 129329 |

---

## 2. 대회 배경 및 목적

### 배경
**판타날(Pantanal)** 은 브라질 마투그로수두술(Mato Grosso do Sul) 주를 중심으로 한 **150,000km²** 이상의 거대한 습지 생태계입니다. 다양한 야생동물이 서식하지만, 계절성 홍수·산불·농업 확장·기후변화로 인해 정기적인 현장 모니터링이 매우 어렵습니다.

> *"볼 수 없는 생태계를 어떻게 보호할까요? 한 가지 방법은 귀를 기울이는 것입니다."*

### 녹음 위치 (실제 데이터 기반)
- **위치:** Pantanal, Mato Grosso do Sul, Brazil, South America
- **위도:** -16.5 ~ -21.6
- **경도:** -55.9 ~ -57.6
- **참고:** https://en.wikipedia.org/wiki/Pantanal

### 과제 목표
약 **1,000개의 음향 레코더**를 판타날 전역에 배포하여 지속적으로 야생동물 소리를 수집하며, 이를 자동으로 분류하는 머신러닝 모델을 구축하는 것이 목표입니다.

- 야생동물 울음소리로부터 자동으로 종(species) 식별
- 다양한 판타날 서식지 환경 대응
- 실제 현장 수집(노이즈가 많은) 오디오 처리
- 증거 기반 보전 의사결정 지원

---

## 3. 일정 (Timeline)

| 마일스톤 | 날짜 |
|----------|------|
| 대회 시작 | 2026년 3월 11일 |
| 참가 신청 마감 | **2026년 5월 27일** |
| 팀 합병 마감 | **2026년 5월 27일** |
| **최종 제출 마감** | **2026년 6월 3일 (UTC 23:59)** |

> 모든 마감 시각은 **UTC 23:59** 기준

---

## 4. 상금 (Prizes)

| 항목 | 금액 |
|------|------|
| **총 상금** | **$50,000 USD** |

---

## 5. 평가 지표 (Evaluation Metric)

### Birdclef ROC AUC (padded cmAP)

- **임계값(threshold)이 필요 없는** 순위 기반 메트릭
- 채점 전 각 제출물과 정답에 **종(species)별 5개의 진양성(true positive) 행을 패딩**
- 패딩의 목적:
  1. 테스트셋에 실제 양성 레이블이 없는 종에 대한 예측도 허용
  2. 양성 레이블이 매우 적은 희귀종의 영향 완화

### 제출 형식 (sample_submission.csv 기반)
- 사운드스케이프 녹음의 **비겹침 5초 단위** 구간별 예측
- `row_id` 형식 예시: `BC2026_Test_0001_S05_20250227_010002_5`
- 각 종(species)별 열에 **확률 점수(0~1)** 기입
- **총 컬럼 수: 235개** (row_id 1개 + 종 234개)

---

## 6. 데이터 (Data)

### 학습 데이터
| 파일/폴더 | 크기 | 설명 |
|-----------|------|------|
| `train.csv` | 6.5 MB | 학습 메타데이터 |
| `train_audio/` | 대용량 | 레이블된 오디오 (OGG, iNaturalist ID 기반 폴더 구성) |
| `taxonomy.csv` | 13.4 KB | 종 분류 정보 (234종) |

### 테스트 데이터
| 파일/폴더 | 크기 | 설명 |
|-----------|------|------|
| `test_soundscapes/` | - | 레이블 없는 현장 다종 녹음 (OGG) |
| `test_soundscapes/readme.txt` | 0.1 KB | 사운드스케이프 설명 |
| `sample_submission.csv` | 16.3 KB | 제출 양식 예시 |
| `recording_location.txt` | 0.2 KB | 녹음 위치 정보 |

### train.csv 주요 컬럼 (예상)
| 컬럼명 | 설명 |
|--------|------|
| `primary_label` | 주 종의 iNaturalist taxon ID |
| `secondary_labels` | 배경/공존 종 |
| `latitude`, `longitude` | 녹음 위치 |
| `scientific_name` | 학명 |
| `common_name` | 일반명 |
| `filename` | 오디오 파일 상대 경로 |
| `date` | 녹음 날짜 |

---

## 7. 종(Species) 정보 — taxonomy.csv 실제 분석 결과

**총 234종** (조류뿐 아니라 다중 분류군 포함 — "+" 의미)

| 분류군 (class_name) | 종 수 |
|---------------------|-------|
| **Aves (조류)** | **162종** |
| Amphibia (양서류) | 35종 |
| Insecta (곤충) | 28종 |
| Mammalia (포유류) | 8종 |
| Reptilia (파충류) | 1종 |
| **합계** | **234종** |

### 종 샘플
| primary_label | 학명 | 일반명 | 분류 |
|---------------|------|--------|------|
| 1161364 | Guyalna cuta | Guyalna cuta | 곤충 |
| 116570 | Caiman yacare | Southern Spectacled Caiman | 파충류 |
| 1176823 | Leptodactylus luctator | Wrestler Frog | 양서류 |
| 1491113 | Adenomera guarani | Guaraní leaf-litter frog | 양서류 |
| 1595929 | Lysapsus limellum | Uruguay Harlequin Frog | 양서류 |

---

## 8. 규칙 (Rules)

| 항목 | 내용 |
|------|------|
| **제출 방식** | Kaggle Notebooks Only (인터넷 접근 불가) |
| **일일 최대 제출** | 5회 |
| **팀 최대 인원** | 5명 |
| **팀 합병 마감** | 2026년 5월 27일 |
| **외부 데이터** | 공개 데이터 허용 (공개 선언 필수) |
| **사전 학습 모델** | 공개된 모델 허용 |
| **수상 조건** | 재현 가능한 코드 제출 필수 |

---

## 9. 현재 리더보드 TOP 10 (2026-04-29 기준)

| 순위 | 팀명 | 점수 |
|------|------|------|
| 🥇 1 | coolz | 0.955 |
| 🥈 2 | BirdCLEF+ 2026 Team🤗🤗🤗 | 0.955 |
| 🥉 3 | PeopleClaw👨‍🦽 | 0.954 |
| 4 | Nikita Babych | 0.952 |
| 5 | Akima | 0.951 |
| 6 | goonew | 0.950 |
| 7 | 0oO | 0.949 |
| 8 | Takoi | 0.949 |
| 9 | Kurise | 0.949 |
| 10 | Tom + Capybara | 0.949 |

> 현재 참가 팀 수: **2,710팀**

---

## 10. 관련 링크

| 링크 | 설명 |
|------|------|
| [Kaggle 대회 메인](https://www.kaggle.com/competitions/birdclef-2026) | 공식 대회 페이지 |
| [Overview](https://www.kaggle.com/competitions/birdclef-2026/overview) | 대회 개요 |
| [Data](https://www.kaggle.com/competitions/birdclef-2026/data) | 데이터 다운로드 |
| [Rules](https://www.kaggle.com/competitions/birdclef-2026/rules) | 공식 규칙 |
| [Leaderboard](https://www.kaggle.com/competitions/birdclef-2026/leaderboard) | 리더보드 |
| [판타날 Wikipedia](https://en.wikipedia.org/wiki/Pantanal) | 생태계 배경 정보 |

---

## 11. 접근 전략 요약

```
오디오 분류 접근법
├── 특징 추출
│   ├── Mel-spectrogram (주로 사용)
│   └── MFCC, CQT 등
├── 모델 아키텍처
│   ├── EfficientNet / EfficientNetV2
│   ├── BirdNET (조류 특화 사전학습)
│   ├── PANNs (오디오 신경망)
│   └── AST (Audio Spectrogram Transformer)
├── 사전 학습 활용
│   ├── BirdNET pretrained weights
│   └── AudioSet pretrained models
├── 다중 분류군 대응 전략
│   ├── 조류(162종) / 양서류(35종) / 곤충(28종) 별도 처리 고려
│   └── 종별 데이터 불균형 처리 (희귀종 augmentation)
├── 앙상블
│   └── 여러 모델 조합으로 성능 향상
└── 후처리
    ├── 종별 임계값 최적화 (ROC AUC이므로 순위 중심)
    └── 패딩(padding) 고려한 예측 전략
```

> **핵심 포인트:**
> - 평가 지표가 **ROC AUC (padded cmAP)** → 확률 점수의 **순위(ranking)** 최적화가 핵심
> - **234종 중 162종이 조류**지만 나머지 72종(양서류·곤충·포유류·파충류)도 정확히 예측 필요
> - 현재 리더보드 1위 점수: **0.955** (상위권 밀집 → 후처리 전략이 차별화 포인트)
> - 제출 마감까지 약 **35일** 남음 (2026-06-03)
