# 🐦 BirdCLEF+ 2026 Kaggle 대회 정보

> **출처:** Kaggle 공식 페이지 직접 수집 (2026-04-29)  
> **대회 URL:** https://www.kaggle.com/competitions/birdclef-2026

---

## 1. 대회 기본 정보

| 항목 | 내용 |
|------|------|
| **대회명** | BirdCLEF+ 2026 |
| **부제** | Acoustic Species Identification in the Pantanal, South America |
| **주최(Sponsor)** | Google Research & Cornell Lab of Ornithology |
| **주최 주소** | 1600 Amphitheatre Parkway, Mountain View, CA 94043 |
| **카테고리** | Research |
| **플랫폼** | Kaggle — Code Competition (노트북 제출 필수) |
| **대회 유형** | 다중 레이블 오디오 분류 (Multi-taxa 음향 종 식별) |
| **총 상금** | $50,000 USD |
| **평가 지표** | Macro-averaged ROC-AUC (true positive 없는 클래스 제외) |
| **팀 최대 인원** | 5명 |
| **일일 최대 제출** | 5회 |
| **최종 제출 선택** | 최대 2개 선택 가능 |
| **데이터 라이선스** | CC BY-NC-SA (Attribution-NonCommercial-ShareAlike) |
| **수상작 라이선스** | Open-Source |

---

## 2. 대회 배경 및 목적

### 배경
> *"볼 수 없는 생태계를 어떻게 보호할까요? 한 가지 방법은 귀를 기울이는 것입니다."*

이 대회는 브라질 판타날 습지에서 수집된 오디오 녹음에서 야생동물 종을 자동으로 식별하는 머신러닝 모델을 구축하는 것을 목표로 합니다. 이 연구는 세계에서 가장 다양하고 위협받는 생태계 중 하나인 판타날에서의 신뢰할 수 있는 생물다양성 모니터링을 지원합니다.

**판타날(Pantanal)** 은 브라질과 인접국에 걸친 **150,000km² 이상**의 습지 생태계로 **650종 이상의 조류**와 수많은 동물이 서식합니다. 계절성 홍수·산불·농업 확장·기후변화로 인해 정기적인 현장 조사가 매우 어렵습니다.

### 녹음 위치
- **위치:** Pantanal, Mato Grosso do Sul, Brazil, South America
- **위도:** -16.5 ~ -21.6
- **경도:** -55.9 ~ -57.6
- **참고:** https://en.wikipedia.org/wiki/Pantanal

### 과제 목표
약 **1,000개의 음향 레코더**를 판타날 전역에 배포하여 야생동물 소리를 지속 수집합니다. 연속 오디오 녹음은 연구자들이 장기간에 걸쳐 다종 사운드스케이프를 포착할 수 있게 하여 생물다양성 역학에 대한 군집 수준의 관점을 제공합니다. 하지만 방대한 오디오 양은 수동 검토가 불가능합니다.

- 수동 음향 모니터링(PAM)에서 야생동물 종 자동 식별
- 다양한 서식지 환경 및 현장 데이터 노이즈 대응
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

> 모든 마감 시각은 **UTC 23:59** 기준. 주최자는 필요시 일정을 변경할 수 있습니다.

---

## 4. 상금 (Prizes)

### 순위별 상금
| 순위 | 상금 |
|------|------|
| 🥇 1위 | **$15,000** |
| 🥈 2위 | **$10,000** |
| 🥉 3위 | **$8,000** |
| 4위 | **$7,000** |
| 5위 | **$5,000** |
| **합계** | **$45,000** |

### 워킹 노트 우수상 (선택)
| 항목 | 금액 |
|------|------|
| 최우수 워킹 노트 2편 | **$2,500 × 2 = $5,000** |

- CLEF 2026 학회에 제출된 워킹 노트 중 최우수 2편에 수여
- 논문은 재현 가능한 수준의 방법론을 포함해야 함

> **총 상금 = $50,000 USD**

---

## 5. 평가 지표 (Evaluation Metric)

### Macro-averaged ROC-AUC

- 진양성(true positive) 레이블이 없는 클래스는 **점수 계산에서 제외**
- 각 `row_id`에 대해 해당 종이 존재할 **확률(0~1)** 을 예측

### 제출 형식
- 사운드스케이프 녹음의 **비겹침 5초 단위** 구간별 예측
- `row_id` 형식: `[soundscape_filename]_[end_time]`
  - 예시: 1분짜리 테스트 사운드스케이프 `BC2026_Test_0001_S05_20250227_010002.ogg`의 00:15~00:20 구간 → `BC2026_Test_0001_S05_20250227_010002_20`
- **총 컬럼 수: 235개** (row_id 1개 + 종 234개)
- 제출 파일명: **`submission.csv`** (필수)

---

## 6. 코드 제출 조건 (Code Competition)

> ⚠️ 이 대회는 **Kaggle Notebooks 전용** 코드 제출 대회입니다.

| 조건 | 내용 |
|------|------|
| **CPU 노트북** | 실행 시간 ≤ **90분** |
| **GPU 노트북** | 사실상 비활성화 (제출 가능하나 **런타임 1분** 제한) |
| **인터넷 접근** | ❌ 비활성화 |
| **외부 데이터** | ✅ 공개적으로 이용 가능한 데이터 허용 (사전 학습 모델 포함) |
| **제출 파일명** | `submission.csv` 고정 |

---

## 7. 데이터 (Data)

### 파일/폴더 구조

| 파일/폴더 | 크기 | 설명 |
|-----------|------|------|
| `train_audio/` | 대용량 | xeno-canto.org 및 iNaturalist 사용자 업로드 단종(短종) 녹음. 32kHz 리샘플링, OGG 포맷. 파일명: `[컬렉션][파일ID].ogg` |
| `train_soundscapes/` | 대용량 | test_soundscapes와 동일 녹음 위치의 추가 오디오. 일부는 전문가 어노테이션 포함 |
| `train_soundscapes_labels.csv` | - | train_soundscapes의 일부 구간에 대한 정답 레이블 (`filename`, `start`, `end`, `primary_label` 컬럼) |
| `test_soundscapes/` | - | 제출 시 자동 제공 (~600개 파일, 1분 길이, 32kHz OGG). 전체 로딩 약 5분 소요 |
| `train.csv` | 6.5 MB | 학습 데이터 메타데이터 |
| `taxonomy.csv` | 13.4 KB | 종 분류 정보 (234종) |
| `sample_submission.csv` | 16.3 KB | 유효한 제출 양식 예시 |
| `recording_location.txt` | 0.2 KB | 녹음 위치 정보 (판타날, 브라질) |

### test_soundscapes 파일명 형식
```
BC2026_Test_<file ID>_<site>_<date>_<time in UTC>.ogg
예시: BC2026_Test_0001_S05_20250227_010002.ogg
     → 파일ID: 0001, 사이트: S05, 날짜: 2025-02-27, 시각: 01:00 UTC
```

> ⚠️ train_soundscapes와 test_soundscapes는 녹음 사이트가 일부 겹치지만, **정확한 날짜와 시간은 겹치지 않습니다.**

### train.csv 주요 컬럼

| 컬럼명 | 설명 |
|--------|------|
| `primary_label` | 종 코드. 조류: eBird 코드 / 비조류: iNaturalist taxon ID |
| `secondary_labels` | 녹음자가 표시한 배경/공존 종 목록 (불완전할 수 있음) |
| `latitude`, `longitude` | 녹음 위치 좌표 (종 방언(dialect) 분석에 활용 가능) |
| `author` | 녹음 제공자 (미제공 시 Unknown) |
| `filename` | 오디오 파일 상대 경로 |
| `rating` | 음질 평점 1~5 (배경종 존재 시 0.5 감점; 0 = 미평가; iNat는 미제공) |
| `collection` | `XC` (Xeno-canto) 또는 `iNat` (iNaturalist) |

### 종(Species) 정보 — taxonomy.csv 실제 분석

**총 234종** — 조류 외 다중 분류군 포함 (대회명의 "+" 의미)

| 분류군 | 종 수 |
|--------|-------|
| 🐦 **Aves (조류)** | **162종** |
| 🐸 Amphibia (양서류) | 35종 |
| 🦟 Insecta (곤충) | 28종 (일부는 종 수준 미확인 → 소노타입으로 처리, 예: `47158son16`) |
| 🦁 Mammalia (포유류) | 8종 |
| 🐊 Reptilia (파충류) | 1종 |
| **합계** | **234종** |

> ⚠️ 일부 곤충 소노타입(sonotype)은 테스트 데이터에도 등장합니다.  
> ⚠️ train_audio에만 있는 종과 train_soundscapes에만 있는 종이 다를 수 있습니다.  
> ⚠️ 학습 데이터의 모든 종이 테스트 데이터에 등장하지는 않습니다.

---

## 8. 규칙 (Rules)

### 핵심 규칙 요약

| 항목 | 내용 |
|------|------|
| **계정** | 1인 1계정. 복수 계정 제출 시 실격 |
| **팀 최대 인원** | 5명 |
| **팀 합병** | 합산 제출 수가 허용치 이하일 때 가능 (마감: 5월 27일) |
| **일일 제출 횟수** | 최대 5회 |
| **최종 제출 선택** | 최대 2개 선택 (미선택 시 자동 선택) |
| **외부 데이터** | 모든 참가자가 동등하게 무료로 접근 가능한 공개 데이터만 허용 |
| **사전 학습 모델** | 공개된 모델 허용 |
| **코드 공유** | 팀 외 비공개 공유 금지. 공개 공유는 Kaggle 포럼/노트북에서만 허용 |
| **순위 결정** | Private Leaderboard 기준 (동점 시 먼저 제출한 팀 우선) |

### 수상자 의무사항
- 수상 모델의 **전체 소스코드(학습+추론 코드) 제출 필수**
- 컴퓨팅 환경, 아키텍처, 전처리, 손실함수, 학습 설정, 하이퍼파라미터 등 **재현 가능한 수준으로 상세 기술**
- 코드 저장소 링크 포함 필수
- 수상작 라이선스: **Open-Source Initiative 승인 라이선스** 적용

### 자격 제한
다음에 해당하는 경우 상금 수령 불가:
- 크림반도, DNR/LNR, 쿠바, 이란, 북한 거주자
- 미국 수출 통제/제재 대상자
- 만 18세 미만 (또는 해당 관할권의 성인 연령 미만)

### 준거법
- **캘리포니아 주법** 적용, 산타클라라 카운티 연방/주 법원 관할

---

## 9. 워킹 노트 우수상 심사 기준

각 노트는 **2명의 심사위원**이 검토하며 평균 점수로 평가 (최대 15점)

| 평가 항목 | 만점 | 설명 |
|-----------|------|------|
| **기여도 및 작업 품질** | 5점 | 중요한 기여(5점) ~ 과학적 기준 미달(1점) |
| **독창성 및 신규성** | 5점 | 선구적(5점) ~ 기존에 반복된 내용(1점) |
| **가독성 및 구성** | 5점 | 탁월(5점) ~ 과학적 기준 미달(1점) |

---

## 10. 현재 리더보드 TOP 10 (2026-04-29 기준)

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

## 11. 기여 기관 및 감사

데이터셋 개발은 **Bezos Earth Fund AI for Climate and Nature Grand Challenge** 지원을 받았습니다.

| 기관 | 기여자 |
|------|--------|
| Chemnitz University of Technology | Stefan Kahl, Mario Lasseck, Maximilian Eibl |
| Google DeepMind | Tom Denton |
| iNaturalist | Grant van Horn |
| Instituto Homem Pantaneiro | Wener Hugo Arruda Moreno |
| Instituto Nacional de Pesquisa do Pantanal (INPP) | Carolline Zatta Fieker, Karl-L. Schuchmann 외 |
| K. Lisa Yang Center for Conservation Bioacoustics | Stefan Kahl, Larissa Sugai, Holger Klinck |
| LifeCLEF | Alexis Joly, Henning Müller |
| Sauá Consultoria Ambiental | Carolina Martins Garcia |
| Universidade Federal de Mato Grosso do Sul (UFMS) | Alyson Vieira de Melo 외 다수 |
| Xeno-canto | Willem-Pier Vellinga, Bob Planqué |

### 공식 인용
```
Stefan Kahl, Tom Denton, Larissa Sugai, Liliana Piatti, Ryan Holbrook,
Holger Klinck, and Ashley Oldacre. BirdCLEF+ 2026.
https://kaggle.com/competitions/birdclef-2026, 2026. Kaggle.
```

---

## 12. 관련 링크

| 링크 | 설명 |
|------|------|
| [Kaggle 대회 메인](https://www.kaggle.com/competitions/birdclef-2026) | 공식 대회 페이지 |
| [Overview](https://www.kaggle.com/competitions/birdclef-2026/overview) | 대회 개요 |
| [Data](https://www.kaggle.com/competitions/birdclef-2026/data) | 데이터 다운로드 |
| [Rules](https://www.kaggle.com/competitions/birdclef-2026/rules) | 공식 규칙 전문 |
| [Leaderboard](https://www.kaggle.com/competitions/birdclef-2026/leaderboard) | 리더보드 |
| [판타날 Wikipedia](https://en.wikipedia.org/wiki/Pantanal) | 생태계 배경 정보 |

---

## 13. 접근 전략 요약

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
├── 데이터 활용 전략
│   ├── train_audio (XC + iNat) + train_soundscapes 병행 활용
│   ├── train_soundscapes_labels.csv (전문가 어노테이션) 적극 활용
│   └── 종별 데이터 불균형 처리 (희귀종 augmentation)
├── 다중 분류군 대응
│   ├── 조류(162) / 양서류(35) / 곤충(28) / 포유류(8) / 파충류(1)
│   └── 곤충 소노타입 특별 처리 필요
├── 앙상블
│   └── 여러 모델 조합으로 성능 향상
└── 후처리
    ├── ROC-AUC 최적화 → 확률 순위(ranking) 최적화가 핵심
    └── true positive 없는 클래스는 평가에서 제외됨을 고려
```

> **핵심 포인트:**
> - 평가 지표: **Macro-averaged ROC-AUC** (TP 없는 클래스 제외)
> - **GPU 사실상 비활성화** → CPU 90분 이내에 추론 완료되는 경량 모델 필수
> - `train_soundscapes` + `train_soundscapes_labels.csv` 활용이 중요한 차별화 포인트
> - 현재 리더보드 상위권 밀집 (0.949~0.955) → 후처리 전략이 핵심
> - 제출 마감: **2026년 6월 3일** (약 35일 남음)
