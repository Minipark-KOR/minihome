# mini home — Umbrella Repo

독립적인 웹 프로젝트들을 하나의 저장소로 관리합니다.

## 구조

```
minihome/                         ← Git Repo Root
├── apps/
│   ├── minihome/frontend/      ← Vercel: minihome (prj_scmMBu4sSrO1DesyKLO38es39sob)
│   ├── ebook/frontend/         ← Vercel: miniebook (prj_AgCf0ZgzOUJ72pn0g9sJvq3lCm9v)
│   ├── news/web/
│   ├── cashbook/frontend/
│   ├── timetable/
│   └── kuhwa/
├── docs/DEPLOYMENT.md
├── .gitignore
└── README.md
```

## 프로젝트별 배포

| Vercel 프로젝트 | Project ID | Root Directory | Framework |
|----------------|-----------|---------------|-----------|
| minihome | `prj_scmMBu4sSrO1DesyKLO38es39sob` | `apps/minihome/frontend` | Next.js |
| miniebook | `prj_AgCf0ZgzOUJ72pn0g9sJvq3lCm9v` | `apps/ebook/frontend` | Next.js |
| news | `prj_jDsE3OdG5ajEUTmgGMNKR5bW20yV` | `apps/news/web` | Next.js |
| mini-cashbook | `prj_QBezAF62BvVw4YA70I3mVIL6zEZw` | `apps/cashbook/frontend` | Static SPA |
| mini-timetable | `prj_rvPCSamTzjTeOL1iaP2KW3KYN7cH` | `apps/timetable` | Python |
| kuhwa | `prj_TBAJ1w7MsHhxBm51rwbNBYopv1ex` | `apps/kuhwa` | Next.js Static |

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
