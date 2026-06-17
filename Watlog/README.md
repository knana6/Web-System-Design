# Watlog (Watch + Log)

> 나만의 비공개 영화 감상 기록 웹사이트 + AI 영화 추천 챗봇

---

## 프로젝트 소개

**Watlog**는 영화를 좋아하는 사람들을 위한 개인 영화 기록 플랫폼입니다.  
기존 서비스(왓챠피디아, 레터박스드 등)는 리뷰가 기본 공개되고 타인의 평가가 먼저 노출되는 구조입니다.  
Watlog는 **오직 나만 보는 공간**으로, 솔직한 감상을 기록하고 AI 챗봇에게 취향 기반 추천을 받을 수 있습니다.

---

## 주요 기능

| 기능 | 설명 |
|------|------|
| 영화 목록 조회 | TMDB 인기 영화 200개 + 내 리뷰를 카드 그리드로 표시 |
| 영화 추가 (Create) | TMDB 데이터 자동 수집 또는 직접 입력으로 영화 등록 |
| 영화 상세 조회 (Read) | 포스터, 제목, 장르, 감독, 별점, 내 리뷰, 감상 날짜 표시 |
| 리뷰 수정 (Update) | 기존 리뷰·별점 수정 가능 |
| 리뷰 삭제 (Delete) | 작성한 리뷰 삭제 후 목록으로 이동 |
| 영화 검색 | 제목·감독·배우 기준 OR 검색 |
| 영화 정렬 | 최신순·별점순·제목순·개봉순 |
| 페이지네이션 | 24개씩 페이지 단위 표시 (JS 기반) |
| TMDB API 연동 | 인기 영화 200개 자동 수집, 중복 방지 |
| WatBot (RAG 챗봇) | DB 영화 데이터 기반 OpenAI 연동 추천 챗봇 |

---

## 기술 스택

| 구분 | 기술 |
|------|------|
| Backend | Python, Django |
| Frontend | HTML, CSS, JavaScript, Bootstrap 5 |
| Database | SQLite3 |
| API | TMDB API (영화 데이터), OpenAI API (챗봇) |
| 환경 관리 | python-dotenv, .env, .gitignore |

---

## 프로젝트 구조

```
Watlog/
├── config/
│   ├── settings.py       # Django 전체 설정
│   ├── urls.py           # 전체 URL 연결
│   └── wsgi.py
├── reviews/
│   ├── models.py         # Review 모델 (영화 + 리뷰 통합)
│   ├── views.py          # CRUD, 검색, 정렬, 챗봇 API
│   ├── urls.py           # reviews 앱 URL 경로
│   ├── services/
│   │   ├── tmdb_service.py     # TMDB API 호출 및 데이터 처리
│   │   └── chatbot_service.py  # RAG 기반 OpenAI 챗봇
│   ├── templates/
│   │   ├── base.html
│   │   └── reviews/
│   │       ├── review_list.html    # 영화 목록 (필터·정렬·페이지네이션)
│   │       ├── review_detail.html  # 영화 상세 + 내 리뷰
│   │       ├── review_form.html    # 영화 추가 / 수정 폼
│   │       ├── search_results.html # 검색 결과
│   │       └── chatbot.html        # WatBot 챗봇 화면
│   └── migrations/
├── media/posters/        # 사용자 업로드 포스터 이미지
├── db.sqlite3
├── .env
└── manage.py
```

---

## 설치 및 실행

### 1. 가상환경 활성화

```bash
cd Watlog
source venv/bin/activate
```

### 2. 의존 패키지 설치

```bash
pip install -r requirements.txt
```

### 3. 환경변수 설정

`.env` 파일에 아래 키를 입력합니다.

```
TMDB_API_KEY=your_tmdb_api_key
OPENAI_API_KEY=your_openai_api_key
DJANGO_SECRET_KEY=your_secret_key
```

### 4. 마이그레이션

```bash
python manage.py migrate
```

### 5. 서버 실행

```bash
python manage.py runserver
```

브라우저에서 `http://127.0.0.1:8000` 접속

---

## 주요 화면

- **메인 (영화 목록)** — TMDB 인기 영화 + 내 리뷰 카드 그리드, 필터/정렬/페이지네이션
- **리뷰 작성** — TMDB에서 자동 데이터 가져오기 또는 직접 입력, 포스터 이미지 업로드
- **영화 상세** — 내 별점·리뷰·감상 날짜 표시, 수정·삭제 버튼
- **검색** — 제목·감독·배우 키워드로 My 리뷰 + TMDB 동시 검색
- **WatBot** — "SF 영화 추천해줘" 같은 자연어로 AI에게 영화 추천 요청

---

## 차별점

- **비공개 리뷰** — 내가 쓴 리뷰는 나만 볼 수 있음 (소셜 노출 없음)
- **타인 평가 비노출** — TMDB 별점은 카드에만 표시, 상세 페이지는 내 별점 중심
- **RAG 기반 챗봇** — 단순 GPT 답변이 아니라 내 DB에 저장된 영화 데이터를 근거로 추천

---

## 개발자

- 김민하 (2514864)
- 웹시스템설계 기말 프로젝트
