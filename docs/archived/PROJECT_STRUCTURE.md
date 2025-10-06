# 📁 프로젝트 폴더 구조

## 🎬 ECG (Easy Caption Generator) Frontend

Next.js 기반의 자막 편집 도구 프로젝트입니다.

## 📂 전체 구조

```
ecg-front/
├── 📦 node_modules/          # npm 패키지들
├── 📁 public/                 # 정적 파일들 (이미지, 폰트 등)
├── 📁 scripts/                # 빌드 및 배포 스크립트
│   └── build-static.sh        # S3 정적 배포용 빌드 스크립트
├── 📁 src/                    # 소스 코드
│   ├── 📁 app/                # Next.js App Router
│   ├── 📁 components/         # 재사용 가능한 컴포넌트
│   ├── 📁 hooks/              # 커스텀 React 훅
│   ├── 📁 lib/                # 유틸리티 함수들
│   ├── 📁 styles/             # 전역 스타일
│   └── 📁 utils/              # 헬퍼 함수들
├── 📄 .gitignore              # Git 무시 파일 설정
├── 📄 next.config.ts          # Next.js 설정
├── 📄 package.json            # 프로젝트 의존성 및 스크립트
├── 📄 tailwind.config.ts      # TailwindCSS 설정
└── 📄 tsconfig.json           # TypeScript 설정
```

## 🗂️ 주요 폴더 상세 설명

### 📁 src/app/ (페이지 라우팅)

```
app/
├── 📁 (route)/                # 라우트 그룹 (URL에 영향 없음)
│   ├── 📁 editor/             # 에디터 페이지 (/editor)
│   │   ├── 📁 components/     # 에디터 전용 컴포넌트
│   │   │   ├── ClipComponent/ # 자막 클립 컴포넌트
│   │   │   ├── SelectionBox/  # 선택 영역 표시
│   │   │   └── VideoSection/  # 비디오 플레이어 섹션
│   │   ├── 📁 hooks/          # 에디터 전용 훅
│   │   ├── 📁 store/          # Zustand 상태 관리
│   │   │   └── slices/        # 상태 관리 슬라이스
│   │   ├── 📁 types/          # TypeScript 타입 정의
│   │   └── 📄 page.tsx        # 에디터 메인 페이지
│   └── 📁 transcriptions/     # 음성 변환 페이지 (/transcriptions)
├── 📁 api/                    # API 라우트
│   ├── 📁 health/             # 헬스체크 API
│   ├── 📁 projects/           # 프로젝트 관련 API
│   │   ├── [id]/              # 프로젝트 조회/삭제
│   │   ├── export/            # 프로젝트 내보내기
│   │   └── save/              # 프로젝트 저장
│   └── 📁 transcription/      # 음성 변환 API
├── 📁 components/             # 페이지 레벨 컴포넌트
├── 📄 layout.tsx              # 루트 레이아웃
├── 📄 page.tsx                # 홈페이지 (/)
└── 📄 globals.css             # 전역 CSS
```

### 📁 src/components/ (컴포넌트)

```
components/
├── 📁 ui/                     # UI 컴포넌트 라이브러리
│   ├── AlertBanner.tsx        # 알림 배너
│   ├── AlertDialog.tsx        # 모달 다이얼로그
│   ├── Badge.tsx              # 상태 배지
│   ├── Button.tsx             # 버튼 컴포넌트
│   ├── Checkbox.tsx           # 체크박스
│   ├── Dropdown.tsx           # 드롭다운 메뉴
│   ├── HelpText.tsx           # 도움말 텍스트
│   ├── ProgressBar.tsx        # 진행 표시줄
│   ├── RadioGroup.tsx         # 라디오 버튼 그룹
│   ├── StatusLight.tsx        # 상태 표시등
│   ├── Tab.tsx                # 탭 네비게이션
│   ├── TextField.tsx          # 텍스트 입력 필드
│   ├── Toolbar.tsx            # 툴바
│   └── Tooltip.tsx            # 툴팁
├── 📁 icons/                  # 아이콘 컴포넌트
├── 📁 DnD/                    # 드래그 앤 드롭 컴포넌트
│   ├── DndContext.tsx         # DnD 컨텍스트 제공자
│   ├── Draggable.tsx          # 드래그 가능 항목
│   └── SortableContext.tsx   # 정렬 가능 컨텍스트
└── 📁 HomePage/               # 홈페이지 컴포넌트
```

### 📁 src/utils/ (유틸리티)

```
utils/
├── 📁 editor/                 # 에디터 관련 유틸리티
│   ├── clipManagement.ts      # 클립 관리 함수
│   ├── editorHistory.ts       # 실행 취소/다시 실행
│   └── keywordHighlight.ts   # 키워드 강조
├── 📁 storage/                # 저장소 관련
│   ├── localProjectStorage.ts # 로컬 저장소
│   └── serverProjectStorage.ts # 서버 저장소
└── 📁 color/                  # 색상 관련
    └── colorUtils.ts          # 색상 유틸리티
```

## 🛠️ 주요 기능별 위치

### 자막 편집 기능

- **메인 에디터**: `src/app/(route)/editor/page.tsx`
- **클립 컴포넌트**: `src/app/(route)/editor/components/ClipComponent/`
- **드래그 앤 드롭**: `src/components/DnD/`
- **상태 관리**: `src/app/(route)/editor/store/`

### 프로젝트 저장/불러오기

- **API 라우트**: `src/app/api/projects/`
- **저장소 유틸**: `src/utils/storage/`

### UI 컴포넌트

- **디자인 시스템**: `src/components/ui/`
- **아이콘**: `src/components/icons/`
- **색상 시스템**: `src/lib/utils/colors.ts`

### 음성 변환

- **페이지**: `src/app/(route)/transcriptions/`
- **API**: `src/app/api/transcription/`

## 🚀 개발 명령어

```bash
# 개발 서버 실행
npm run dev

# 프로덕션 빌드
npm run build

# 정적 빌드 (S3 배포용)
npm run build:static

# 린트 검사
npm run lint

# 타입 체크
npm run type-check

# 코드 포맷팅
npm run format
```

## 📝 참고사항

1. **API 라우트**: 정적 배포 시 `build:static` 스크립트를 사용하여 API 폴더를 임시로 이동
2. **상태 관리**: Zustand를 사용한 전역 상태 관리
3. **스타일링**: TailwindCSS v4 + PostCSS 사용
4. **타입 안전성**: TypeScript strict 모드 활성화
5. **코드 품질**: ESLint, Prettier, Husky 사전 커밋 훅 설정

## 🔧 기술 스택

- **프레임워크**: Next.js 15.5.2 (App Router)
- **언어**: TypeScript 5
- **UI 라이브러리**: React 19.1.1
- **스타일링**: TailwindCSS v4
- **상태 관리**: Zustand 5.0.8
- **드래그 앤 드롭**: @dnd-kit
- **아이콘**: react-icons (Lucide)
