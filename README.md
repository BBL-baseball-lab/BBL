# ⚾ BBL — KBO 드림팀 빌더 & 경기 시뮬레이션

실제 KBO 선수 데이터를 기반으로 나만의 드림팀을 구성하고,
몬테카를로 시뮬레이션으로 두 팀의 가상 경기를 진행해 승리 확률을 예측하는 웹사이트입니다.

---

## 📌 프로젝트 소개

KBO 선수들의 실제 타율, 홈런율, ERA 등 스탯 데이터를 활용하여:
- 포지션별로 원하는 선수를 골라 **나만의 드림팀**을 구성하고
- 두 팀을 맞붙여 **몬테카를로 시뮬레이션**으로 가상 경기를 1000번 반복해 승리 확률을 계산합니다.

---

## 🚀 주요 기능

### 핵심 기능
| 기능 | 설명 |
|------|------|
| 드림팀 빌더 | 포지션별(투수, 포수, 1~3루수, 유격수, 외야수) 선수 선택 + 레이더 차트 시각화 |
| 몬테카를로 시뮬레이션 | 투수 vs 타자 실제 기록 기반 타석별 확률 계산 → 1000번 반복 → 승리 확률 % 출력 |

### 추가 기능
| 기능 | 설명 |
|------|------|
| 선수 카드 시스템 | 트레이딩 카드 형태 UI + 스탯 기반 S/A/B/C 등급 자동 부여 |
| 시즌별 성장 그래프 | 선수의 연도별 스탯 변화 시각화 |
| 타순 최적화 추천 | 타율/출루율 기반 최적 타순 자동 배치 |
| 이닝별 중계 텍스트 | "1회 초: 홍길동 홈런! 1-0" 형태의 가상 중계 텍스트 생성 |
| 드림팀 공유 | 구성한 드림팀을 URL로 공유 가능 |

---

## 🛠️ 사용한 오픈소스 라이브러리

| 라이브러리 | 용도 | 라이선스 |
|-----------|------|---------|
| [pybaseball](https://github.com/jldbc/pybaseball) | KBO/MLB 데이터 수집 | MIT |
| [pandas](https://pandas.pydata.org/) | 데이터 처리 및 분석 | BSD |
| [plotly](https://plotly.com/python/) | 데이터 시각화 | MIT |
| [Streamlit](https://streamlit.io/) | 웹 UI 구성 | Apache 2.0 |
| [requests](https://requests.readthedocs.io/) | HTTP 요청 (크롤링) | Apache 2.0 |
| [BeautifulSoup4](https://www.crummy.com/software/BeautifulSoup/) | HTML 파싱 (크롤링) | MIT |

---

## 📦 설치 방법

### 1. 저장소 클론
```bash
git clone https://github.com/[팀장계정]/BBL.git
cd BBL
```

### 2. 가상환경 생성 및 활성화
```bash
python -m venv venv

# Mac/Linux
source venv/bin/activate

# Windows
venv\Scripts\activate
```

### 3. 의존성 설치
```bash
pip install -r requirements.txt
```

### 4. 환경변수 설정
```bash
cp .env.example .env
```

### 5. 실행
```bash
streamlit run app.py
```

---

## 📁 프로젝트 구조

```
BBL/
├── .vscode/
│   ├── settings.json         # VS Code 공통 설정
│   ├── extensions.json       # 추천 확장 프로그램
│   └── launch.json           # Streamlit 디버그 실행 설정
├── backend/
│   ├── data/
│   │   ├── collect.py        # KBO 데이터 수집 (pybaseball, BeautifulSoup)
│   │   └── preprocess.py     # 데이터 정제 및 스탯 계산 (pandas)
│   ├── simulation/
│   │   ├── montecarlo.py     # 몬테카를로 시뮬레이션 메인 로직
│   │   ├── batting.py        # 타석별 확률 계산
│   │   └── lineup.py         # 타순 최적화 알고리즘
│   └── utils/
│       └── grade.py          # 선수 등급 계산 (S/A/B/C)
├── frontend/
│   ├── pages/
│   │   ├── team_builder.py   # 드림팀 빌더 페이지
│   │   ├── simulation.py     # 시뮬레이션 결과 페이지
│   │   └── player_card.py    # 선수 카드 페이지
│   └── components/
│       ├── radar_chart.py    # 레이더 차트
│       ├── histogram.py      # 점수 분포 히스토그램
│       └── growth_graph.py   # 시즌별 성장 그래프
├── app.py                    # Streamlit 메인 진입점
├── requirements.txt
├── pyrightconfig.json        # Python 타입 체크 설정
├── .env.example
├── .gitignore
└── README.md
```

---

## 🌿 브랜치 전략

```
main                  ← 최종 배포 (직접 push 금지)
develop               ← 통합 개발 (직접 push 금지)
feature/data          ← 팀원 1: 데이터 수집
feature/simulation    ← 팀원 1: 시뮬레이션
feature/viz           ← 팀원 2: 시각화
feature/ui            ← 팀원 3: 웹 UI
```

### 협업 규칙
- 기능 개발 시 반드시 **Issue 먼저 생성** 후 작업 시작
- 작업 완료 후 **PR 올리고 팀원 최소 1명 코드 리뷰** 후 merge
- 본인 PR 본인이 merge 금지
- `.env` 파일 push 금지

### 커밋 메시지 규칙
| 태그 | 사용 상황 |
|------|----------|
| `[feat]` | 새로운 기능 추가 |
| `[fix]` | 버그 수정 |
| `[docs]` | 문서 수정 |
| `[refactor]` | 코드 리팩토링 |
| `[chore]` | 기타 작업 |

---

## 👥 팀원

| 이름 | 역할 | 담당 기능 |
|------|------|----------|
| 팀원 1 | 데이터 & 시뮬레이션 | 데이터 수집/전처리, 몬테카를로 시뮬레이션, 타순 최적화, 등급 계산 |
| 팀원 2 | 시각화 | 레이더 차트, 히스토그램, 성장 그래프 |
| 팀원 3 | 웹 UI & 통합 | Streamlit UI, 드림팀 빌더, URL 공유, 배포 |

---

## 📄 라이선스

이 프로젝트는 [MIT License](LICENSE) 하에 배포됩니다.