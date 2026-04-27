# ⚾ KBO 드림팀 빌더 & 경기 시뮬레이션

실제 KBO 선수 데이터를 기반으로 나만의 드림팀을 구성하고,  
몬테카를로 시뮬레이션으로 두 팀의 가상 경기를 진행해 승리 확률을 예측하는 웹사이트입니다.

---

## 📌 프로젝트 소개

- KBO 선수 데이터를 활용해 포지션별 드림팀을 직접 구성
- 투수/타자의 실제 기록을 기반으로 타석별 결과를 확률로 계산
- 가상 경기를 1000번 시뮬레이션하여 승리 확률 도출
- AI/ML 모델 없이 순수 통계 수식으로 구현

---

## 🚀 주요 기능

| 번호 | 기능 | 설명 |
|------|------|------|
| 1 | 드림팀 빌더 | 포지션별 선수 선택 + 레이더 차트 시각화 |
| 2 | 몬테카를로 시뮬레이션 | 타석별 확률 계산 → 1000번 반복 → 승리 확률 % |
| 3 | 선수 카드 시스템 | 트레이딩 카드 UI + S/A/B/C 등급 자동 부여 |
| 4 | 시즌별 성장 그래프 | 연도별 스탯 변화 시각화 |
| 5 | 타순 최적화 추천 | 타율/출루율 기반 최적 타순 자동 배치 |
| 6 | 이닝별 중계 텍스트 | "1회 초: 홍길동 홈런! 1-0" 형태 출력 |
| 7 | 드림팀 공유 | 구성한 팀을 URL로 공유 가능 |

---

## 🛠️ 사용한 오픈소스 라이브러리

| 라이브러리 | 용도 | 라이선스 |
|-----------|------|---------|
| [pybaseball](https://github.com/jldbc/pybaseball) | MLB/KBO 데이터 수집 | MIT |
| [pandas](https://pandas.pydata.org/) | 데이터 처리 및 정제 | BSD |
| [plotly](https://plotly.com/python/) | 데이터 시각화 | MIT |
| [Streamlit](https://streamlit.io/) | 웹 UI 구성 | Apache 2.0 |
| [requests](https://requests.readthedocs.io/) | HTTP 요청 | Apache 2.0 |
| [BeautifulSoup4](https://www.crummy.com/software/BeautifulSoup/) | KBO 데이터 크롤링 | MIT |

---

## ⚙️ 설치 방법

### 1. 저장소 클론
```bash
git clone https://github.com/your-team/kbo-dreamteam.git
cd kbo-dreamteam
```

### 2. 가상환경 생성 및 활성화
```bash
python -m venv venv
source venv/bin/activate       # macOS/Linux
venv\Scripts\activate          # Windows
```

### 3. 패키지 설치
```bash
pip install -r requirements.txt
```

### 4. 실행
```bash
streamlit run app.py
```

---

## 📁 프로젝트 구조

```
kbo-dreamteam/
├── app.py                  # Streamlit 메인 앱
├── requirements.txt        # 패키지 목록
├── README.md
├── .gitignore
├── data/
│   ├── fetch_data.py       # 데이터 수집
│   └── preprocess.py       # 데이터 전처리
├── simulation/
│   ├── monte_carlo.py      # 몬테카를로 시뮬레이션
│   └── lineup.py           # 타순 최적화
├── visualization/
│   ├── radar_chart.py      # 레이더 차트
│   ├── growth_graph.py     # 성장 그래프
│   └── histogram.py        # 점수 분포
└── ui/
    ├── team_builder.py     # 드림팀 빌더 UI
    ├── player_card.py      # 선수 카드 UI
    └── share.py            # URL 공유 기능
```

---

## 🌿 브랜치 전략

```
main          ← 최종 배포
develop       ← 통합 개발
feature/data          ← 데이터 수집 & 전처리
feature/simulation    ← 시뮬레이션 로직
feature/viz           ← 시각화
feature/ui            ← 웹 UI & 통합
```

---

## 👥 팀원

| 이름 | 역할 | 담당 기능 |
|------|------|---------|
| 팀원 1 | 데이터 & 시뮬레이션 | 데이터 수집, 몬테카를로, 타순 최적화 |
| 팀원 2 | 시각화 | 레이더 차트, 성장 그래프, 히스토그램 |
| 팀원 3 | 웹 UI & 통합 | Streamlit UI, 선수 카드, 배포 |

---

## 📄 라이선스

이 프로젝트는 [MIT License](./LICENSE)를 따릅니다.
