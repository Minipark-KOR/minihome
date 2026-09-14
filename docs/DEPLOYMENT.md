# Vercel 배포 설정

## Monorepo 구조 (업계 표준)

Vercel 표준 모노레포 구성: Git repo가 루트, 모든 앱이 `apps/` 하위 디렉토리로 배포됨.

```
minihome/                         ← Git Repo Root (Minipark-KOR/minihome)
├── apps/
│   ├── minihome/                 ← Vercel Project: minihome (prj_scmMBu4sSrO1DesyKLO38es39sob)
│   │   ├── app/
│   │   │   ├── page.tsx         ← 랜딩 페이지 (5개 프로젝트 링크)
│   │   │   ├── layout.tsx
│   │   │   └── globals.css
│   │   ├── package.json
│   │   ├── next.config.ts
│   │   ├── tsconfig.json
│   │   └── vercel.json
│   ├── ebook/frontend/           ← Vercel Project: miniebook (prj_AgCf0ZgzOUJ72pn0g9sJvq3lCm9v)
│   ├── news/web/                 ← Vercel Project: news (prj_jDsE3OdG5ajEUTmgGMNKR5bW20yV)
│   ├── cashbook/frontend/        ← Vercel Project: mini-cashbook (prj_QBezAF62BvVw4YA70I3mVIL6zEZw)
│   ├── timetable/                ← Vercel Project: mini-timetable (prj_rvPCSamTzjTeOL1iaP2KW3KYN7cH)
│   └── kuhwa/                    ← Vercel Project: kuhwa (prj_TBAJ1w7MsHhxBm51rwbNBYopv1ex)
├── .gitignore
└── README.md
```

> **minihome** = 모노레포 ROOT (repo 이름) + 별도 Vercel 프로젝트 (ebook과 완전히 별개)
> **miniebook** = ebook 프로젝트 (`apps/ebook/frontend`)
> minihome4u.vercel.app = minihome 프로젝트 URL

## 프로젝트 매핑 (Vercel Root Directory)

| Vercel 프로젝트 | Project ID | Root Directory | Framework | 빌드 설정 |
|----------------|-----------|---------------|-----------|-----------|
| **minihome** | `prj_scmMBu4sSrO1DesyKLO38es39sob` | `apps/minihome/` | Next.js | `npm run build` → `.next` |
| **miniebook** | `prj_AgCf0ZgzOUJ72pn0g9sJvq3lCm9v` | `apps/ebook/frontend` | Next.js | `npm run build` → `.next` |
| news | `prj_jDsE3OdG5ajEUTmgGMNKR5bW20yV` | `apps/news/web` | Next.js | `npm run build` → `.next` (region: hnd1) |
| mini-cashbook | `prj_QBezAF62BvVw4YA70I3mVIL6zEZw` | `apps/cashbook/frontend` | Static SPA | rewrites → index.html |
| mini-timetable | `prj_rvPCSamTzjTeOL1iaP2KW3KYN7cH` | `apps/timetable` | Python | `@vercel/python` (main.py) |
| kuhwa | `prj_TBAJ1w7MsHhxBm51rwbNBYopv1ex` | `apps/kuhwa` | Next.js Static | rewrites for API |

## 서버 구성 비교 (업계 표준 vs 현재)

| 프로젝트 | vercel.json | 업계 표준 | 차이점 |
|---------|------------|----------|--------|
| minihome | `framework: nextjs` | Next.js 표준 | ✅ 표준 |
| miniebook | `framework: nextjs` | Next.js 표준 | ✅ 표준 |
| news | `framework: nextjs`, `regions: [hnd1]` | Next.js 표준 | ⚠️ hnd1 (도쿄) — 한국 프로젝트에는 kr 계열 권장 |
| mini-cashbook | rewrites/headers (no framework) | Next.js 표준 | ❌ `framework` 미지정 — 정적 SPA로 취급됨 |
| mini-timetable | `@vercel/python` (main.py) | Node.js/Next.js | ❌ Python 서버리스 — 웹 표준과 다름 |
| kuhwa | `version: 2`, rewrites | Next.js 표준 | ⚠️ `version: 2` — 최신 Vercel 설정과 다름 |

## Root Directory 설정 방법 (Vercel 대시보드)

1. Vercel 대시보드 → New Project → Import Git Repository
2. `Minipark-KOR/minihome` 선택
3. **Root Directory** 설정: 각 프로젝트별 디렉토리 지정
4. Deploy

## 주의사항

- 모든 프로젝트는 `apps/` 하위에 배치 (업계 표준)
- minihome과 miniebook은 완전히 별개 프로젝트 (별도 Root Directory)
- 환경변수 (NEXT_PUBLIC_API_URL, NEIS_API_KEY 등)는 Vercel 대시보드에서 별도 설정
- `.env` 파일은 git에 포함되지 않음
