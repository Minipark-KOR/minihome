# Vercel 배포 설정

각 앱은 독립적인 Vercel 프로젝트로 배포됩니다.
Vercel 대시보드에서 각 프로젝트의 **Root Directory**를 아래와 같이 설정하세요.

## 프로젝트 매핑

| Vercel 프로젝트 | Root Directory | Framework | 빌드 설정 |
|----------------|---------------|-----------|-----------|
| miniebook | `apps/ebook/frontend` | Next.js | `npm run build` → `.next` |
| news | `apps/news/web` | Next.js | `npm run build` → `.next` (region: hnd1) |
| mini-cashbook | `apps/cashbook/frontend` | Static SPA | rewrites → index.html |
| mini-timetable | `apps/timetable` | Python | `@vercel/python` (main.py) |
| kuhwa | `apps/kuhwa` | Next.js Static | rewrites for API |

> **minihome4u** 가 Vercel 팀/org 이름입니다.
> **minihome** 은 모노레포 저장소(Umbrella Repo) 이름입니다. 별도 Vercel 프로젝트가 아닙니다.

## 루트 디렉토리 설정 방법

1. Vercel 대시보드 → 각 프로젝트 선택
2. Settings → Git → Root Directory 변경
3. Push하면 자동 배포

## 주의사항

- Vercel 프로젝트 `minihome` (현재 Error 상태, `prj_scmMBu4sSrO1DesyKLO38es39sob`)은 삭제 또는 miniebook으로 통합
- 환경변수 (NEXT_PUBLIC_API_URL, NEIS_API_KEY 등)는 Vercel 대시보드에서 별도 설정 필요
- `.env` 파일은 git에 포함되지 않음 — Vercel 대시보드의 Environment Variables에서 설정
