# mini home — Umbrella Repo

독립적인 웹 프로젝트들을 하나의 저장소(umbrella repo)로 관리합니다.
각 프로젝트는 `apps/` 하위에 위치하며, 독립적으로 배포 및 운영됩니다.

## 구조

```
minihome/                    ← Monorepo root (umbrella)
├── apps/
│   ├── ebook/              ← 웹소설 리더 (Next.js + FastAPI)
│   ├── news/               ← AI 뉴스 수집/번역 (Python http.server + Next.js)
│   ├── cashbook/           ← 가계부 (FastAPI + HTMX/SPA)
│   ├── timetable/          ← 시간표 구독 (FastAPI + Google Calendar Sync)
│   └── kuhwa/              ← 한국구화학교 학사일정 (Next.js 정적 사이트)
├── docs/
├── .gitignore
└── README.md
```

## 프로젝트별 배포

| 프로젝트 | 프론트엔드 | 백엔드 | 배포 |
|---------|-----------|--------|------|
| ebook | Next.js (Vercel) | FastAPI (OCI devforge) | Vercel + OCI |
| news | Next.js (Vercel) | stdlib http.server (systemd) | Vercel + OCI |
| cashbook | HTMX/SPA (Vercel) | FastAPI (systemd) | Vercel + OCI |
| timetable | Jinja2 (Vercel Python) | FastAPI (Vercel Python) | Vercel |
| kuhwa | 정적 HTML (Vercel) | 없음 (서버리스) | Vercel |

## 프로젝트 독립성

각 프로젝트는 완전히 독립적으로 동작합니다:
- 독립적인 디렉토리 구조
- 독립적인 빌드/배포 파이프라인
- 독립적인 의존성 관리
- 독립적인 런타임 환경

## 공통 규칙

- `apps/` 하위에만 프로젝트 배치
- 루트 레벨에는 프로젝트 코드 없음 (설정 파일만)
- 각 프로젝트의 README를 참고하여 개별 운영
