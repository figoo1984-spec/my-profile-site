# 개인 개발 블로그 - PRD

## 프로젝트 개요

### 프로젝트명
**개인 개발 블로그** (Personal Tech Blog)

### 목적
Notion을 CMS로 활용한 개인 기술 블로그. Notion에서 글을 작성하면 자동으로 블로그에 반영되어, 별도의 배포 프로세스 없이 콘텐츠 관리 가능.

### CMS 선택 이유
- **간편한 콘텐츠 관리**: Notion에서 글을 작성하면 자동으로 블로그에 반영
- **추가 관리 UI 불필요**: Notion 인터페이스 그대로 활용
- **유지보수 용이**: 블로그 호스팅만 관리하면 됨
- **풍부한 포매팅**: Notion의 다양한 블록 타입 활용

---

## 주요 기능

### 1. Notion 데이터베이스에서 블로그 글 목록 가져오기
- Notion API를 통해 실시간 글 목록 조회
- 발행된 상태의 글만 필터링
- 캐싱 전략으로 성능 최적화
- 정기적인 데이터 동기화

### 2. 개별 글 상세 페이지 표시
- 제목, 작성일, 카테고리, 태그 표시
- Notion 블록 콘텐츠 렌더링 (텍스트, 코드, 이미지, 링크 등)
- 마크다운 지원
- TOC(목차) 자동 생성

### 3. 카테고리별 필터링
- 카테고리 목록 표시
- 선택한 카테고리의 글만 표시
- 카테고리별 동적 라우팅

### 4. 검색 기능
- 제목 및 내용 기반 검색
- 실시간 검색 결과
- 태그 기반 필터링

### 5. 반응형 디자인
- 모바일, 태블릿, 데스크톱 최적화
- 터치 친화적 UI
- 접근성 고려

---

## 기술 스택

| 계층 | 기술 |
|------|------|
| **Frontend Framework** | Next.js 15 |
| **Language** | TypeScript |
| **CMS API** | Notion API (@notionhq/client) |
| **Styling** | Tailwind CSS |
| **UI Components** | shadcn/ui |
| **Icons** | Lucide React |
| **Deployment** | Vercel |
| **Database** | Notion |

---

## Notion 데이터베이스 구조

### Posts 데이터베이스 스키마

| 필드명 | 타입 | 설명 | 필수여부 |
|--------|------|------|---------|
| Title | Title | 글의 제목 | ✅ |
| Slug | Text | URL에 사용할 슬러그 (고유값) | ✅ |
| Category | Select | 글의 카테고리 (React, Next.js, JavaScript 등) | ✅ |
| Tags | Multi-select | 글 관련 태그 | ❌ |
| Published | Date | 글 발행일 | ✅ |
| Status | Select | 글 상태 (초안/발행됨) | ✅ |
| Content | Block (Rich Text) | 글의 본문 내용 | ✅ |
| Author | Text | 작성자명 (기본값: 본인) | ❌ |
| Updated | Last edited time | 마지막 수정 일시 | (자동) |

### Select 옵션 예시
- **Category**: React, Next.js, JavaScript, TypeScript, CSS, Tools, Career
- **Status**: 초안 (Draft), 발행됨 (Published)

---

## 화면 구성

### 1. 홈 페이지 (/)
**최근 글 목록**
- 최신 발행일순으로 정렬된 글 목록
- 글 카드 (제목, 요약, 카테고리, 발행일)
- 페이지네이션 또는 무한 스크롤
- 카테고리 필터 탭
- 검색 바

**레이아웃**: 헤더 > 홈 제목 > 카테고리 탭 > 글 목록

### 2. 글 상세 페이지 (/blog/[slug])
**개별 글 내용 표시**
- 글 제목, 작성자, 발행일, 수정일
- 카테고리 및 태그 배지
- Notion 블록 콘텐츠 렌더링
- 목차 (TOC)
- 이전/다음 글 네비게이션
- 공유 버튼 (선택사항)

**레이아웃**: 헤더 > 글 제목 영역 > 본문 > 관련 정보 > 네비게이션

### 3. 카테고리 페이지 (/category/[category])
**카테고리별 글 목록**
- 해당 카테고리의 모든 발행된 글
- 카테고리명 표시
- 글 개수 표시
- 발행일순 정렬
- 페이지네이션

**레이아웃**: 헤더 > 카테고리명 > 글 목록

---

## MVP 범위

### 포함할 최소 기능
- ✅ Notion API 패키지 설치 및 환경 설정
- ✅ Notion 데이터베이스 생성 및 API 키 발급
- ✅ 글 목록 페이지 구현 (홈)
- ✅ 글 상세 페이지 구현
- ✅ Notion 블록 렌더링 (paragraph, heading, code, image, bulleted_list 등)
- ✅ 카테고리별 필터링
- ✅ 기본 검색 기능
- ✅ 반응형 디자인 (Mobile, Tablet, Desktop)
- ✅ SEO 최적화 (메타 태그)

### 향후 추가 기능
- 댓글 시스템 (Giscus, Utterances 등)
- 조회수 추적
- 소셜 공유 (Twitter, LinkedIn 등)
- 다크 모드
- RSS 피드 생성
- 구독 뉴스레터
- 관련 글 추천

---

## 구현 단계

### 1단계: Notion API 패키지 설치 및 환경 설정 (2-3시간)
- Next.js 15 + TypeScript 프로젝트 생성
- `@notionhq/client` 패키지 설치
- Tailwind CSS, shadcn/ui 설치
- 환경 변수 설정 (.env.local)
  - `NOTION_API_KEY`: Notion API 키
  - `NOTION_DATABASE_ID`: 블로그 데이터베이스 ID

### 2단계: Notion 데이터베이스 생성 및 API 키 설정 (1-2시간)
- Notion에 Posts 데이터베이스 생성
- 필드 구조 설정 (Title, Category, Tags, Published, Status 등)
- Notion Integrations에서 API 키 생성
- 데이터베이스에 Integration 연결
- 테스트 데이터 입력

### 3단계: 글 목록 페이지 구현 (4-5시간)
- API 라우트 생성 (`/api/posts`)
  - Notion 데이터베이스 쿼리
  - 필터링 (Status = "발행됨")
  - 정렬 (Published 역순)
- 홈 페이지 (`/`) 구현
  - 글 목록 렌더링
  - 글 카드 컴포넌트
  - 페이지네이션
- 카테고리 필터 구현
- 검색 기능 구현

### 4단계: 글 상세 페이지 구현 (6-7시간)
- 동적 라우트 생성 (`/blog/[slug]`)
- API 라우트 생성 (`/api/posts/[slug]`)
  - 개별 글 조회
  - Notion 블록 데이터 가져오기
- 글 상세 페이지 컴포넌트
- Notion 블록 렌더러 구현
  - 텍스트 (paragraph, heading)
  - 코드 블록
  - 이미지
  - 링크
  - 리스트 (bullet, numbered)
  - 인용
- TOC(목차) 자동 생성
- 이전/다음 글 네비게이션

### 5단계: 스타일링 및 최적화 (3-4시간)
- 헤더, 푸터 컴포넌트 구현
- 전체 레이아웃 스타일링
- 반응형 디자인 테스트 및 개선
- 이미지 최적화 (Next.js Image)
- 메타 태그 및 SEO 최적화
- 성능 최적화 (캐싱, ISR 등)
- Vercel 배포

---

## 기술 상세

### Notion API 연동
```typescript
// 환경 변수
NOTION_API_KEY=ntion_...
NOTION_DATABASE_ID=abcd1234...

// 클라이언트 초기화
import { Client } from "@notionhq/client";

const notion = new Client({
  auth: process.env.NOTION_API_KEY,
});
```

### 데이터 흐름
1. 클라이언트 (Next.js) → API 라우트 요청
2. API 라우트 → Notion API 쿼리
3. 데이터 변환 및 포맷팅
4. 클라이언트에게 JSON 응답
5. 페이지 렌더링

### 캐싱 전략
- **ISR (Incremental Static Regeneration)**
  - 글 목록: 1시간마다 재검증
  - 글 상세: 24시간마다 재검증
- **클라이언트 캐싱**: 메타데이터 캐싱

### 에러 처리
- Notion API 연결 실패 시 폴백 UI
- 존재하지 않는 글: 404 페이지
- 발행되지 않은 글: 접근 제한

---

## 프로젝트 구조

```
notion-cms-project/
├── docs/
│   └── PRD.md
├── src/
│   ├── app/
│   │   ├── layout.tsx
│   │   ├── page.tsx              # 홈 페이지
│   │   ├── blog/
│   │   │   └── [slug]/
│   │   │       └── page.tsx      # 글 상세 페이지
│   │   ├── category/
│   │   │   └── [category]/
│   │   │       └── page.tsx      # 카테고리 페이지
│   │   ├── api/
│   │   │   └── posts/
│   │   │       ├── route.ts      # 글 목록 API
│   │   │       └── [slug]/
│   │   │           └── route.ts  # 글 상세 API
│   │   └── globals.css
│   ├── components/
│   │   ├── Header.tsx
│   │   ├── Footer.tsx
│   │   ├── PostCard.tsx
│   │   ├── PostList.tsx
│   │   └── NotionRenderer.tsx
│   ├── lib/
│   │   ├── notion.ts             # Notion API 클라이언트
│   │   ├── types.ts              # TypeScript 타입 정의
│   │   └── utils.ts              # 유틸리티 함수
│   └── hooks/
│       ├── usePosts.ts
│       └── useSearch.ts
├── public/
│   └── (이미지, 파비콘 등)
├── .env.local                    # 환경 변수 (gitignore)
├── next.config.ts
├── tailwind.config.ts
├── tsconfig.json
└── package.json
```

---

## 성공 지표

- ⚡ **페이지 로드 시간**: 2초 이내
- 📱 **모바일 반응성**: Lighthouse 85점 이상
- 🔍 **SEO**: 구글 검색 가능 및 색인화
- 🎯 **기능 완성도**: 모든 MVP 기능 구현
- 🚀 **배포 성공**: Vercel에 정상 배포

---

## 마일스톤

| 단계 | 예상 시간 | 상태 |
|------|---------|------|
| 1. 환경 설정 | 2-3시간 | - |
| 2. DB 생성 및 API 키 | 1-2시간 | - |
| 3. 글 목록 페이지 | 4-5시간 | - |
| 4. 글 상세 페이지 | 6-7시간 | - |
| 5. 스타일링 및 배포 | 3-4시간 | - |
| **총 예상 시간** | **16-21시간** | - |

---

## 참고사항

### Notion API 주의사항
- **레이트 제한**: 3 requests/second
- **페이지 크기**: 최대 100개 항목 (페이지네이션 필요)
- **블록 제한**: 페이지당 최대 100개 블록

### 성능 최적화
- Notion 쿼리 필터링으로 불필요한 데이터 최소화
- 이미지 최적화 (Next.js Image 컴포넌트)
- 코드 스플리팅으로 번들 크기 감소
- ISR로 정적 생성과 동적 업데이트 균형

### 보안
- API 키는 환경 변수로 관리 (절대 코드에 노출 금지)
- API 라우트를 통한 간접 접근으로 보안 강화
- 발행되지 않은 글 접근 제한

---

## 배포 (Vercel)

```bash
# 1. GitHub 저장소 생성
# 2. Vercel에서 프로젝트 연결
# 3. 환경 변수 설정
#    - NOTION_API_KEY
#    - NOTION_DATABASE_ID
# 4. 배포 진행
```

---

**작성일**: 2026-10-29  
**버전**: 1.0  
**상태**: 초안
