# mini home — Umbrella Repo

독립적인 웹 프로젝트들을 하나의 저장소로 관리합니다.

## 구조

```
minihome/                         ← Git Repo Root + minihome Vercel Project
├── app/                          ← minihome 랜딩 페이지 (Vercel: minihome)
├── apps/                         ← 독립 프로젝트들
│   ├── ebook/frontend/         ← Vercel: miniebook (prj_AgCf0ZgzOUJ72pn0g9sJvq3lCm9v)
│   ├── news/web/               ← Vercel: news (prj_jDsE3OdG5ajEUTmgGMNKR5bW20yV)
│   ├── cashbook/frontend/      ← Vercel: mini-cashbook (prj_QBezAF62BvVw4YA70I3mVIL6zEZw)
│   ├── timetable/              ← Vercel: mini-timetable (prj_rvPCSamTzjTeOL1iaP2KW3KYN7cH)
│   └── kuhwa/                  ← Vercel: kuhwa (prj_TBAJ1w7MsHhxBm51rwbNBYopv1ex)
├── package.json
├── next.config.ts
├── tsconfig.json
├── postcss.config.mjs
├── next-env.d.ts
├── vercel.json
├── docs/
├── .gitignore
└── README.md
```

## 프로젝트별 배포

| Vercel 프로젝트 | Project ID | Root Directory | Framework |
|----------------|-----------|---------------|-----------|
| minihome | `prj_scmMBu4sSrO1DesyKLO38es39sob` | `.` (repo root) | Next.js |
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

- minihome = ROOT (apps/ 와 동일 레벨, 별도 Vercel 프로젝트)
- apps/ 하위에 5개 독립 프로젝트 배치
- 각 프로젝트의 README를 참고하여 개별 운영
