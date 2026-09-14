# Vercel 배포 설정

## Monorepo 구조 (업계 표준)

Vercel 표준 모노레포 구성: Git repo가 루트, 각 앱이 하위 디렉토리로 배포됨.

```
minihome/                         ← Git Repo Root (Minipark-KOR/minihome)
├── apps/
│   ├── ebook/frontend/           ← Vercel Project: minihome (prj_scmMBu4sSrO1DesyKLO38es39sob)
│   ├── news/web/                 ← Vercel Project: news (prj_jDsE3OdG5ajEUTmgGMNKR5bW20yV)
│   ├── cashbook/frontend/        ← Vercel Project: mini-cashbook (prj_QBezAF62BvVw4YA70I3mVIL6zEZw)
│   ├── timetable/                ← Vercel Project: mini-timetable (prj_rvPCSamTzjTeOL1iaP2KW3KYN7cH)
│   └── kuhwa/                    ← Vercel Project: kuhwa (prj_TBAJ1w7MsHhxBm51rwbNBYopv1ex)
├── .gitignore
└── README.md
```

> minihome = 모노레포 ROOT (저장소 이름이자 메인 Vercel 프로젝트)
> minihome4u = Vercel 팀/org 이름
> apps/ 안에 앱들이 직접 배치됨 (하위 폴더 없음)

## 프로젝트 매핑 (Vercel Root Directory)

| Vercel 프로젝트 | Project ID | Root Directory | Framework | 빌드 설정 |
|----------------|-----------|---------------|-----------|-----------|
| **minihome** | `prj_scmMBu4sSrO1DesyKLO38es39sob` | `apps/ebook/frontend` | Next.js | `npm run build` → `.next` |
| miniebook | `prj_AgCf0ZgzOUJ72pn0g9sJvq3lCm9v` | `apps/ebook/frontend` | Next.js | `npm run build` → `.next` |
| news | `prj_jDsE3OdG5ajEUTmgGMNKR5bW20yV` | `apps/news/web` | Next.js | `npm run build` → `.next` (region: hnd1) |
| mini-cashbook | `prj_QBezAF62BvVw4YA70I3mVIL6zEZw` | `apps/cashbook/frontend` | Static SPA | rewrites → index.html |
| mini-timetable | `prj_rvPCSamTzjTeOL1iaP2KW3KYN7cH` | `apps/timetable` | Python | `@vercel/python` (main.py) |
| kuhwa | `prj_TBAJ1w7MsHhxBm51rwbNBYopv1ex` | `apps/kuhwa` | Next.js Static | rewrites for API |

> **minihome** 과 **miniebook** 은 별개 Vercel 프로젝트 (같은 Root Directory, 다른 Project ID)
> minihome4u.vercel.app = minihome 프로젝트 URL

## Root Directory 설정 방법 (Vercel 대시보드)

1. Vercel 대시보드 → New Project → Import Git Repository
2. `Minipark-KOR/minihome` 선택
3. **Root Directory** 설정: 각 프로젝트별 디렉토리 지정
4. Deploy

## 주의사항

- **`apps/minihome/` 같은 하위 폴더 없음** — minihome이 모노레포 ROOT
- 환경변수 (NEXT_PUBLIC_API_URL, NEIS_API_KEY 등)는 Vercel 대시보드에서 별도 설정
- `.env` 파일은 git에 포함되지 않음
