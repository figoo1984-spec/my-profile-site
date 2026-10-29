# 개인 개발 블로그

Notion을 CMS로 활용한 개인 기술 블로그입니다. Notion에서 글을 작성하면 자동으로 블로그에 반영됩니다.

## 🎯 주요 기능

- **Notion 연동**: Notion 데이터베이스에서 실시간으로 글 가져오기
- **동적 렌더링**: Notion 블록을 웹 페이지로 자동 변환
- **카테고리 필터링**: 카테고리별 글 목록 조회
- **검색 기능**: 글 제목 및 내용 검색
- **반응형 디자인**: 모바일, 태블릿, 데스크톱 최적화

## 🛠 기술 스택

- **Frontend**: Next.js 15, TypeScript, React 19
- **Styling**: Tailwind CSS, shadcn/ui
- **CMS**: Notion API (@notionhq/client)
- **Icons**: Lucide React
- **Deployment**: Vercel

## 📋 필수 요구사항

- Node.js 18+
- npm 또는 yarn
- Notion 계정
- Notion API 키

## 🚀 빠른 시작

### 1. 프로젝트 클론

```bash
git clone https://github.com/yourusername/notion-cms-project.git
cd notion-cms-project
```

### 2. 의존성 설치

```bash
npm install
```

### 3. 환경 변수 설정

`.env.local` 파일을 생성하고 다음 내용을 추가합니다:

```
NOTION_API_KEY=your_notion_api_key
NOTION_DATABASE_ID=your_database_id
```

**Notion API 키 발급:**
1. [Notion Developers](https://www.notion.so/my-integrations) 접속
2. "New Integration" 클릭
3. Integration 이름 설정 및 생성
4. "Internal Integration Token" 복사

**Database ID 확인:**
- Notion에서 사용할 데이터베이스의 URL 확인
- URL에서 `/database/` 뒤의 ID 복사
- 예: `https://www.notion.so/my-db-[DATABASE_ID]?v=...`

### 4. 개발 서버 실행

```bash
npm run dev
```

브라우저에서 [http://localhost:3000](http://localhost:3000)을 열어 확인합니다.

### 5. 빌드 및 배포

```bash
npm run build
npm start
```

## 📁 프로젝트 구조

```
notion-cms-project/
├── docs/
│   └── PRD.md                    # 프로젝트 요구사항 문서
├── src/
│   ├── app/                      # Next.js 앱 라우터
│   │   ├── page.tsx              # 홈 페이지
│   │   ├── layout.tsx            # 루트 레이아웃
│   │   ├── blog/
│   │   │   └── [slug]/
│   │   │       └── page.tsx      # 글 상세 페이지
│   │   ├── category/
│   │   │   └── [category]/
│   │   │       └── page.tsx      # 카테고리 페이지
│   │   └── api/                  # API 라우트
│   │       └── posts/
│   │           └── route.ts
│   ├── components/               # React 컴포넌트
│   ├── lib/                      # 유틸리티 함수
│   └── styles/                   # 스타일시트
├── public/                       # 정적 파일
├── .env.local                    # 환경 변수 (gitignore됨)
├── .gitignore
├── next.config.ts
├── tailwind.config.ts
├── tsconfig.json
└── package.json
```

## 📖 Notion 데이터베이스 설정

자세한 설정 방법은 [docs/PRD.md](./docs/PRD.md)를 참고하세요.

### 필수 필드
- **Title**: 글의 제목
- **Slug**: URL에 사용할 슬러그 (고유값)
- **Category**: 글의 카테고리
- **Published**: 글 발행일
- **Status**: 글 상태 (초안/발행됨)

### 선택 필드
- **Tags**: 글 관련 태그
- **Author**: 작성자명
- **Content**: 글 본문

## 🎨 커스터마이징

### 스타일 변경
- `tailwind.config.ts`에서 색상 및 폰트 설정
- `src/app/globals.css`에서 기본 스타일 수정

### 컴포넌트 커스터마이징
- `src/components/` 디렉토리에서 개별 컴포넌트 수정
- shadcn/ui 컴포넌트 추가: `npx shadcn-ui@latest add <component>`

## 📝 사용 가능한 스크립트

```bash
npm run dev       # 개발 서버 실행
npm run build     # 프로덕션 빌드
npm start         # 프로덕션 서버 실행
npm run lint      # 코드 린팅
```

## 🚀 배포 (Vercel)

1. [Vercel](https://vercel.com)에 로그인
2. GitHub 저장소 연결
3. 환경 변수 설정:
   - `NOTION_API_KEY`
   - `NOTION_DATABASE_ID`
4. 배포 진행

## 📚 참고 자료

- [Next.js 문서](https://nextjs.org/docs)
- [Notion API 가이드](https://developers.notion.com)
- [Tailwind CSS 문서](https://tailwindcss.com/docs)
- [shadcn/ui 컴포넌트](https://ui.shadcn.com)

## 🤝 기여

버그 리포트 및 기능 제안은 GitHub Issues를 통해 제출해주세요.

## 📄 라이선스

MIT License - [LICENSE](./LICENSE) 파일 참고

## 👨‍💻 작성자

개인 개발 블로그 프로젝트

---

**마지막 업데이트**: 2026-10-29
