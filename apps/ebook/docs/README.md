# mini home — 문서

웹소설 리더 전용 서비스 문서

## 빠른 참조

```
minihome = Next.js (Vercel CDN) → /api/* catch-all → devforge FastAPI → JSON 파일 DB
```

### 핵심 파일
- `frontend/app/page.tsx` — 메인 페이지 (소설 하이라이트 + 카테고리)
- `frontend/app/library/page.tsx` — 소설 목록 (ISR)
- `frontend/app/novel/[id]/` — 소설 상세 + 회차 읽기 (ISR)
- `backend/main.py` — FastAPI 엔트리포인트
- `scripts/pipeline.py` — 파이프라인 (수집/저장/인덱싱)

### 핵심 데이터 위치
- `/opt/ai_data/flaresolverr/novels/{소설ID}/` — 챕터 JSON + 인덱스 캐시
- `/opt/ai_data/flaresolverr/epub/` — EPUB 캐시

### 외부 의존성
- **FlareSolverr** — Cloudflare 우회 (북토끼)
- **Playwright + DataImpulse** — 뉴토끼 우회
- **namu.wiki** — 메타데이터 + 표지
- **Vercel** — ISR 호스팅

## 주의: ebooklib과의 관계

ebook은 모노레포 `apps/ebook/`에 포함된 독립 프로젝트입니다.
이전에는 ebooklib과 심볼릭 링크로 참조했지만, 현재는 실제 코드가 포함됩니다.

### 구조
- `backend/` — FastAPI 엔트리포인트 + 라우터 + 서비스 + lib
- `frontend/` — Next.js 16 App Router 프론트엔드
- `scripts/` — 파이프라인 + EPUB 변환기
- `docs/` — 시스템 문서
