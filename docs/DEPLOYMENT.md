# Vercel 배포 설정

각 앱은 독립적인 Vercel 프로젝트로 배포됩니다.
Vercel 대시보드에서 각 프로젝트의 **Root Directory**를 아래와 같이 설정하세요.

## 프로젝트 매핑

| Vercel 프로젝트 | Project ID | Root Directory | Framework | 빌드 설정 |
|----------------|-----------|---------------|-----------|-----------|
| **minihome** | `prj_scmMBu4sSrO1DesyKLO38es39sob` | `apps/ebook/frontend` | Next.js | `npm run build` → `.next` |
| miniebook | `prj_AgCf0ZgzOUJ72pn0g9sJvq3lCm9v` | `apps/ebook/frontend` | Next.js | `npm run build` → `.next` |
| news | `prj_jDsE3OdG5ajEUTmgGMNKR5bW20yV` | `apps/news/web` | Next.js | `npm run build` → `.next` (region: hnd1) |
| mini-cashbook | `prj_QBezAF62BvVw4YA70I3mVIL6zEZw` | `apps/cashbook/frontend` | Static SPA | rewrites → index.html |
| mini-timetable | `prj_rvPCSamTzjTeOL1iaP2KW3KYN7cH` | `apps/timetable` | Python | `@vercel/python` (main.py) |
| kuhwa | `prj_TBAJ1w7MsHhxBm51rwbNBYopv1ex` | `apps/kuhwa` | Next.js Static | rewrites for API |

> **minihome4u** = Vercel 팀/org 이름
> **minihome** = 모노레포 저장소 이름 + 별도 Vercel 프로젝트 (umbrella/최상위)
> **minihome** 과 **miniebook** 은 별개 프로젝트

## 루트 디렉토리 설정 방법

1. Vercel 대시보드 → 각 프로젝트 선택
2. Settings → Git → Root Directory 변경
3. Push하면 자동 배포

## 주의사항

- Vercel 프로젝트 `minihome` (`prj_scmMBu4sSrO1DesyKLO38es39sob`) 은 **miniebook과 별개**로 유지
- 환경변수 (NEXT_PUBLIC_API_URL, NEIS_API_KEY 등)는 Vercel 대시보드에서 별도 설정 필요
- `.env` 파일은 git에 포함되지 않음 — Vercel 대시보드의 Environment Variables에서 설정
