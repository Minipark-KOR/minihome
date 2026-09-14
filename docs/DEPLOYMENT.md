# Vercel 배포 설정

각 앱은 독립적인 Vercel 프로젝트로 배포됩니다.
Vercel 대시보드에서 각 프로젝트의 **Root Directory**를 아래와 같이 설정하세요.

## 프로젝트 매핑

| Vercel 프로젝트 | Root Directory | Framework | 빌드 설정 |
|----------------|---------------|-----------|-----------|
| minihome | **분리 필요** — minihome은 ebook과 별개 프로젝트 | — | — |
| news | `apps/news/web` | Next.js | `npm run build` → `.next` (region: hnd1) |
| mini-cashbook | `apps/cashbook/frontend` | Static SPA | rewrites → index.html |
| mini-timetable | `apps/timetable` | Python | `@vercel/python` (main.py) |
| kuhwa | `apps/kuhwa` | Next.js Static | rewrites for API |

## 루트 디렉토리 설정 방법

1. Vercel 대시보드 → 각 프로젝트 선택
2. Settings → Git → Root Directory 변경
3. Push하면 자동 배포

## 주의사항

- minihome 프로젝트는 **separate project**로 분리 필요 (현재 ebook 프론트엔드와 혼합됨)
- 환경변수 (NEXT_PUBLIC_API_URL, NEIS_API_KEY 등)는 Vercel 대시보드에서 별도 설정 필요
- `.env` 파일은 git에 포함되지 않음 — Vercel 대시보드의 Environment Variables에서 설정
