# 프로젝트 구조 설명

롯데렌터카 재고 관리 시스템의 전체 파일 구조와 각 파일의 역할을 설명합니다.

---

## 📁 디렉토리 구조

```
lotte-inventory/
├── index.html                      # 메인 애플리케이션 (핵심 파일)
├── README.md                       # 프로젝트 개요 및 사용법
├── QUICK_START.md                  # 5분 빠른 시작 가이드
├── DEPLOY.md                       # 상세 배포 가이드
├── PROJECT_STRUCTURE.md            # 이 파일
├── .gitignore                      # Git 무시 파일 목록
│
└── data/                           # 엑셀 데이터 폴더
    ├── .gitkeep                    # 빈 폴더 유지용
    ├── README.md                   # 데이터 폴더 설명
    ├── SAMPLE_EXCEL_FORMAT.md      # 엑셀 샘플 형식
    ├── lotte.xlsx                  # 롯데 전략재고 (업로드 필요)
    ├── hyundai.xls                 # 현대 재고 (업로드 필요)
    └── kia.xls                     # 기아 재고 (업로드 필요)
```

---

## 📄 파일별 상세 설명

### 🌟 index.html (핵심 파일)
**역할**: 전체 웹 애플리케이션

**주요 기능**:
- SheetJS를 사용한 엑셀 파일 자동 로드
- 롯데/현대/기아 데이터 통합 표시
- 제조사별 필터링
- 차종별 필터링 (한글 표시명, 중복 제거)
- 검색 기능
- 텍스트 복사 (2가지 포맷)
- 무한 스크롤

**기술 스택**:
- HTML5
- CSS3 (모던 디자인, 반응형)
- Vanilla JavaScript (ES6+)
- SheetJS (xlsx.js) - CDN

**주요 섹션**:
```javascript
// 차종명 한글 매핑
const MODEL_NAME_MAP = { ... }

// 엑셀 파싱 함수
function parseLotteExcel(workbook) { ... }
function parseCarMakerExcel(workbook, makerKey, makerName) { ... }

// 데이터 로드
async function loadAllData() { ... }

// 렌더링
function createCard(item, index) { ... }

// 복사 기능
function copyItemText(item) { ... }
```

**커스터마이징 포인트**:
1. **차종명 추가**: `MODEL_NAME_MAP` 객체
2. **색상 테마**: CSS `:root` 변수
3. **로고 변경**: `<img class="logoImg" src="...">`
4. **엑셀 컬럼명**: 파싱 함수 내부

---

### 📖 README.md
**역할**: 프로젝트 메인 문서

**내용**:
- 프로젝트 소개
- 빠른 시작 가이드
- 파일 구조
- 엑셀 업데이트 방법 (웹/Git)
- 엑셀 파일 형식 요구사항
- 주요 기능 설명
- 기술 스택
- 문제 해결

---

### ⚡ QUICK_START.md
**역할**: 최소 단계 가이드 (5분)

**내용**:
- 3단계 배포 가이드
- 매일 엑셀 업데이트 방법
- 간단한 문제 해결

**대상**: 빠르게 배포하고 싶은 사용자

---

### 🚀 DEPLOY.md
**역할**: 상세 배포 가이드

**내용**:
- 방법 1: 웹사이트에서 배포 (스크린샷 수준 상세)
- 방법 2: Git 명령어로 배포
- 매일 업데이트 방법 (2가지)
- 커스터마이징 가이드
- 문제 해결 (상세)

**대상**: 처음 GitHub Pages를 사용하는 사용자

---

### 📁 data/ 폴더

#### data/README.md
**역할**: 데이터 폴더 설명

**내용**:
- 필수 파일 3개 설명
- 각 파일별 필수/선택 컬럼
- 업데이트 방법
- 주의사항
- 문제 해결

#### data/SAMPLE_EXCEL_FORMAT.md
**역할**: 엑셀 샘플 형식

**내용**:
- 3개 파일의 샘플 테이블
- 컬럼명 정확도 요구사항
- 데이터 타입 설명
- 실제 엑셀 만들기 예시

#### data/.gitkeep
**역할**: 빈 폴더 유지

Git은 빈 폴더를 추적하지 않으므로, 이 파일로 폴더 구조 유지

#### data/*.xlsx, data/*.xls
**역할**: 실제 재고 데이터

**파일명 고정**:
- `lotte.xlsx` (롯데 전략재고)
- `hyundai.xls` (현대 재고)
- `kia.xls` (기아 재고)

---

### 🚫 .gitignore
**역할**: Git에서 무시할 파일 목록

**무시 항목**:
- OS 파일 (.DS_Store, Thumbs.db)
- 에디터 파일 (.vscode, .idea)
- 임시 엑셀 파일 (~$*.xls)

---

## 🔧 수정이 필요한 파일

### 일상적 업데이트
- `data/lotte.xlsx` - 매일
- `data/hyundai.xls` - 매일
- `data/kia.xls` - 매일

### 차종 추가시
- `index.html` → `MODEL_NAME_MAP` 수정

### 디자인 변경시
- `index.html` → CSS 섹션 수정

### 로고 변경시
- `index.html` → `<img class="logoImg">` src 수정

---

## 🔒 건드리지 말아야 할 파일

- `README.md` (프로젝트 설명)
- `QUICK_START.md` (가이드)
- `DEPLOY.md` (가이드)
- `PROJECT_STRUCTURE.md` (이 파일)
- `.gitignore`

---

## 🌐 배포 후 파일 경로

배포 후 웹에서의 파일 경로:

```
https://your-username.github.io/lotte-inventory/
├── index.html                    → 메인 페이지
├── data/lotte.xlsx              → 엑셀 (직접 접근 가능)
├── data/hyundai.xls             → 엑셀 (직접 접근 가능)
└── data/kia.xls                 → 엑셀 (직접 접근 가능)
```

---

## 📊 데이터 흐름

```
[엑셀 파일 업로드]
        ↓
[GitHub 저장소]
        ↓
[GitHub Pages 자동 빌드]
        ↓
[웹 서버에 배포]
        ↓
[사용자 브라우저에서 접속]
        ↓
[index.html 로드]
        ↓
[SheetJS로 엑셀 3개 파일 fetch]
        ↓
[JavaScript에서 파싱 및 통합]
        ↓
[화면에 렌더링]
```

---

## 🎨 커스터마이징 체크리스트

### 필수 커스터마이징
- [ ] 엑셀 3개 파일 업로드
- [ ] 차종명 한글 매핑 추가 (MODEL_NAME_MAP)

### 선택적 커스터마이징
- [ ] 로고 이미지 변경
- [ ] 색상 테마 변경
- [ ] 제목/설명 변경
- [ ] 엑셀 컬럼명 조정 (파싱 함수)

---

## 🔍 코드 찾기 가이드

### 차종명 한글 추가하고 싶어요
→ `index.html` 검색: `MODEL_NAME_MAP`

### 로고 바꾸고 싶어요
→ `index.html` 검색: `logoImg`

### 색상 바꾸고 싶어요
→ `index.html` 검색: `:root{`

### 엑셀 컬럼명 바꾸고 싶어요
→ `index.html` 검색: `parseLotteExcel` 또는 `parseCarMakerExcel`

### 복사 포맷 바꾸고 싶어요
→ `index.html` 검색: `copyItemText`

---

## 🆘 문제 해결 순서

1. **브라우저 개발자도구 (F12) → Console 탭** 확인
2. **엑셀 파일명** 정확한지 확인
3. **엑셀 컬럼명** data/SAMPLE_EXCEL_FORMAT.md와 일치하는지 확인
4. **브라우저 캐시** 강제 새로고침 (Ctrl+Shift+R)
5. **GitHub Actions** 탭에서 빌드 상태 확인

---

**최종 업데이트**: 2026-01-11
