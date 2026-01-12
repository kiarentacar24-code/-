# GitHub Pages 배포 가이드

이 문서는 롯데렌터카 재고 관리 시스템을 GitHub Pages에 배포하는 전체 과정을 단계별로 안내합니다.

## 📋 배포 전 체크리스트

- [ ] GitHub 계정이 있음
- [ ] Git이 설치되어 있음 (선택사항)
- [ ] 프로젝트 파일이 준비됨

---

## 🚀 방법 1: GitHub 웹사이트에서 배포 (가장 쉬움)

### Step 1: GitHub 저장소 생성

1. [GitHub](https://github.com)에 로그인
2. 우측 상단 **"+"** 클릭 → **"New repository"** 선택
3. 저장소 설정:
   - **Repository name**: `lotte-inventory` (원하는 이름)
   - **Description**: `롯데렌터카 재고 관리 시스템`
   - **Public** 선택 (GitHub Pages는 Public 저장소 필요)
   - **Add a README file** 체크 해제 (우리가 직접 업로드할 것)
   - **Add .gitignore** 선택 안 함
4. **"Create repository"** 클릭

### Step 2: 파일 업로드

1. 생성된 저장소 페이지에서 **"uploading an existing file"** 링크 클릭
2. 다음 파일들을 드래그 앤 드롭:
   ```
   index.html
   README.md
   .gitignore
   ```
3. 하단에 커밋 메시지 입력: `Initial commit`
4. **"Commit changes"** 클릭

### Step 3: data 폴더 생성 및 파일 업로드

1. 저장소 메인 페이지에서 **"Add file"** → **"Create new file"** 클릭
2. 파일명에 `data/.gitkeep` 입력 (폴더가 자동 생성됨)
3. 파일 내용은 비워둠
4. **"Commit new file"** 클릭
5. `data/` 폴더로 이동
6. **"Add file"** → **"Upload files"** 클릭
7. 엑셀 파일 3개 업로드:
   - `lotte.xlsx`
   - `hyundai.xls`
   - `kia.xls`
8. **"Commit changes"** 클릭

### Step 4: GitHub Pages 활성화

1. 저장소 페이지 상단의 **"Settings"** 탭 클릭
2. 좌측 메뉴에서 **"Pages"** 클릭
3. **Source** 섹션에서:
   - **Branch**: `main` 선택
   - **Folder**: `/ (root)` 선택
4. **"Save"** 버튼 클릭

### Step 5: 배포 완료 확인

1. 1-2분 정도 기다립니다
2. 페이지를 새로고침하면 상단에 초록색 박스가 나타남:
   ```
   ✅ Your site is live at https://your-username.github.io/lotte-inventory/
   ```
3. 링크를 클릭하여 사이트 접속!

---

## 🚀 방법 2: Git 명령어로 배포 (고급 사용자)

### Step 1: Git 저장소 초기화

```bash
# 프로젝트 폴더로 이동
cd lotte-inventory

# Git 초기화
git init

# 모든 파일 추가
git add .

# 첫 커밋
git commit -m "Initial commit"
```

### Step 2: GitHub 저장소 연결

```bash
# GitHub에서 생성한 저장소 URL로 연결
git remote add origin https://github.com/your-username/lotte-inventory.git

# 브랜치 이름 main으로 변경 (필요시)
git branch -M main

# 푸시
git push -u origin main
```

### Step 3: GitHub Pages 활성화

위의 "방법 1 - Step 4" 참조

---

## 🔄 매일 엑셀 파일 업데이트

### 웹사이트에서 (추천)

1. GitHub 저장소의 `data/` 폴더 접속
2. 업데이트할 파일 클릭 (예: `lotte.xlsx`)
3. 우측 상단 **휴지통 아이콘** 클릭
4. **"Commit changes"** 클릭 (기존 파일 삭제)
5. `data/` 폴더로 돌아가서 **"Add file"** → **"Upload files"** 클릭
6. 새 엑셀 파일 드래그 앤 드롭
7. **"Commit changes"** 클릭

**자동 반영**: 1-2분 후 웹사이트에 자동으로 반영됩니다!

### Git 명령어로

```bash
# 저장소 클론 (최초 1회만)
git clone https://github.com/your-username/lotte-inventory.git
cd lotte-inventory

# 엑셀 파일 교체
# 새 파일을 data/ 폴더에 복사 (기존 파일 덮어쓰기)

# 변경사항 커밋
git add data/*.xlsx data/*.xls
git commit -m "Update inventory - $(date +%Y-%m-%d)"
git push origin main
```

---

## 🎨 커스터마이징

### 차종명 한글 매핑 추가

`index.html` 파일의 `MODEL_NAME_MAP` 객체를 수정:

```javascript
const MODEL_NAME_MAP = {
  'AVANTE': '아반떼',
  'SONATA': '쏘나타',
  // 새 차종 추가
  'NEW_MODEL': '새차종명',
  // ...
};
```

### 로고 변경

`index.html`에서 로고 이미지 URL 변경:

```html
<img class="logoImg" src="새로운이미지URL" alt="롯데렌터카 로고" />
```

### 색상 테마 변경

`index.html`의 CSS `:root` 섹션 수정:

```css
:root{
  --accent:#e60012;      /* 포인트 색상 (롯데 레드) */
  --accent2:#2563eb;     /* 보조 색상 (블루) */
  --success:#10b981;     /* 성공 색상 (그린) */
  /* ... */
}
```

---

## 🛠️ 문제 해결

### 사이트가 404 에러를 보여요
- Settings → Pages에서 Source가 올바르게 설정되었는지 확인
- 5-10분 정도 기다린 후 재시도
- 브라우저 시크릿 모드로 접속 시도

### 엑셀 파일이 로드되지 않아요
- 파일명이 정확한지 확인 (`lotte.xlsx`, `hyundai.xls`, `kia.xls`)
- 파일이 `data/` 폴더 안에 있는지 확인
- 브라우저 개발자도구(F12) → Console 탭에서 에러 확인
- CORS 에러인 경우: GitHub Pages는 CORS를 지원하므로 다른 원인 확인

### 업데이트가 반영되지 않아요
- GitHub Actions 탭에서 최근 워크플로우 상태 확인
- 브라우저 캐시 강제 새로고침 (Ctrl+Shift+R / Cmd+Shift+R)
- 2-5분 정도 기다린 후 재시도

### 데이터가 이상하게 파싱돼요
- `data/README.md`의 컬럼명 요구사항 확인
- 엑셀 파일의 첫 번째 행이 헤더인지 확인
- 숫자 필드에 텍스트가 들어가지 않았는지 확인

---

## 📞 추가 지원

- **GitHub 문서**: https://docs.github.com/pages
- **이슈 등록**: 저장소의 Issues 탭에서 문제 보고

---

## 🎉 축하합니다!

이제 롯데렌터카 재고 관리 시스템이 온라인에서 실행됩니다! 

**다음 단계**:
1. 팀원들과 URL 공유
2. 매일 엑셀 파일 업데이트
3. 필요시 차종명 매핑 추가

**최종 업데이트**: 2026-01-11
