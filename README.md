# 롯데렌터카 재고 관리 시스템

롯데렌터카 전략재고 및 현대자동차/기아 재고를 통합 관리하는 웹 기반 시스템입니다.

## 📚 문서 가이드

| 문서 | 설명 | 대상 |
|------|------|------|
| **[시작하기.md](시작하기.md)** | 전체 개요 및 시작 가이드 | 모든 사용자 ⭐ |
| **[QUICK_START.md](QUICK_START.md)** | 5분 빠른 시작 | 급한 사용자 🚀 |
| **[DEPLOY.md](DEPLOY.md)** | 상세 배포 가이드 | 처음 사용자 📖 |
| **[PROJECT_STRUCTURE.md](PROJECT_STRUCTURE.md)** | 파일 구조 설명 | 개발자 🔧 |
| **[data/README.md](data/README.md)** | 데이터 폴더 가이드 | 데이터 관리자 📊 |
| **[data/SAMPLE_EXCEL_FORMAT.md](data/SAMPLE_EXCEL_FORMAT.md)** | 엑셀 샘플 형식 | 엑셀 작성자 📝 |

## 🚀 빠른 시작

### GitHub Pages 배포 방법

1. **저장소 생성**
   - GitHub에 새 저장소를 만듭니다 (예: `lotte-inventory`)
   - Public 저장소로 설정합니다

2. **파일 업로드**
   ```bash
   git clone https://github.com/your-username/lotte-inventory.git
   cd lotte-inventory
   # 모든 파일을 복사한 후
   git add .
   git commit -m "Initial commit"
   git push origin main
   ```

3. **GitHub Pages 활성화**
   - 저장소 설정(Settings) → Pages
   - Source: `Deploy from a branch`
   - Branch: `main` / `/ (root)` 선택
   - Save 클릭

4. **완료!**
   - 약 1-2분 후 `https://your-username.github.io/lotte-inventory/` 에서 접속 가능

## 📁 프로젝트 구조

```
lotte-inventory/
├── index.html              # 메인 페이지
├── data/                   # 엑셀 파일 저장 폴더
│   ├── lotte.xlsx         # 롯데 전략재고 (매일 업데이트)
│   ├── hyundai.xls        # 현대 재고 (매일 업데이트)
│   └── kia.xls            # 기아 재고 (매일 업데이트)
└── README.md              # 이 파일
```

## 🔄 매일 엑셀 파일 업데이트 방법

### 방법 1: GitHub 웹 인터페이스 (추천 - 가장 쉬움)

1. GitHub 저장소에서 `data` 폴더 클릭
2. 업데이트할 파일 클릭 (예: `lotte.xlsx`)
3. 우측 상단 **휴지통 아이콘** 클릭하여 기존 파일 삭제
4. Commit changes 클릭
5. `data` 폴더로 돌아가서 **Add file** → **Upload files**
6. 새 엑셀 파일을 드래그 앤 드롭
7. Commit changes 클릭

**중요**: 파일명은 반드시 동일하게 유지해야 합니다
- `lotte.xlsx` (롯데 전략재고)
- `hyundai.xls` (현대 재고)
- `kia.xls` (기아 재고)

### 방법 2: Git 명령어 (고급 사용자)

```bash
# 저장소 클론 (최초 1회만)
git clone https://github.com/your-username/lotte-inventory.git
cd lotte-inventory

# 엑셀 파일 교체
# 새 파일을 data/ 폴더에 복사 (기존 파일 덮어쓰기)

# 변경사항 커밋 및 푸시
git add data/*.xlsx data/*.xls
git commit -m "Update inventory data - 2026-01-11"
git push origin main
```

**자동 반영**: 푸시 후 1-2분 내에 웹사이트에 자동으로 반영됩니다!

## 📊 엑셀 파일 형식 요구사항

### 롯데 전략재고 (lotte.xlsx)
필수 컬럼:
- 차종
- 옵션 (트림)
- 외장색상
- 내장색상
- 가격
- 판매가능재고 (즉시)
- 입고재고 (미출고)
- 정상재고
- 전기차 보조금 (선택)

### 현대/기아 재고 (hyundai.xls, kia.xls)
필수 컬럼:
- 차종명
- 차종코드 (Sales Code)
- 옵션코드
- 옵션명
- 외장색상코드
- 외장색상명
- 내장색상코드 (선택)
- 내장색상명 (선택)
- 출고지
- 정상재고 수량
- 가격

## ✨ 주요 기능

1. **통합 재고 조회**
   - 롯데/현대/기아 재고를 하나의 리스트로 통합 표시
   - 제조사별 필터링

2. **차종 필터**
   - 한글 표시명으로 통일 (예: AVANTE → 아반떼)
   - 중복 차종은 1개로 통합 표시

3. **재고 상태 표시**
   - 롯데: 판매가능/입고/정상 재고 구분 표시
   - 현대/기아: 정상재고만 표시

4. **텍스트 복사**
   - 포맷 1: `카메이커, 차종코드, 옵션코드, 외장코드, 내장코드, 출하장`
   - 포맷 2: `차종: [차종명] 옵션: [옵션명] 외장색상/내장색상: [색상]`

5. **검색 기능**
   - 차종, 옵션, 색상으로 실시간 검색

## 🛠️ 기술 스택

- **프론트엔드**: HTML5, CSS3, JavaScript (ES6+)
- **엑셀 파싱**: SheetJS (xlsx.js)
- **배포**: GitHub Pages (정적 호스팅)

## 📝 문제 해결

### 엑셀 파일이 로드되지 않아요
- 파일명이 정확한지 확인 (`lotte.xlsx`, `hyundai.xls`, `kia.xls`)
- 파일이 `data/` 폴더 안에 있는지 확인
- 브라우저 개발자 도구(F12) → Console 탭에서 에러 메시지 확인

### 업데이트가 반영되지 않아요
- GitHub Actions 탭에서 빌드 상태 확인
- 브라우저 캐시 강제 새로고침 (Ctrl+Shift+R / Cmd+Shift+R)
- 5분 정도 기다린 후 재시도

### 차종명이 영어로 나와요
- `index.html`의 `MODEL_NAME_MAP` 객체에 매핑 추가
- 예: `"CARNIVAL": "카니발"` 형식으로 추가

## 📞 지원

문제가 발생하면 GitHub Issues에 등록해주세요.

## 📄 라이선스

MIT License - 자유롭게 사용, 수정, 배포 가능합니다.

---

**최종 업데이트**: 2026-01-11  
**버전**: 1.0.0
