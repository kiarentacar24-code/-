# 빠른 시작 가이드 ⚡

5분 안에 GitHub Pages에 배포하는 최소 단계 가이드입니다.

---

## 🎯 3단계로 끝내기

### 1️⃣ GitHub 저장소 생성 (1분)

1. [github.com](https://github.com) 접속 후 로그인
2. 우측 상단 **"+"** → **"New repository"**
3. 저장소 이름 입력 (예: `lotte-inventory`)
4. **Public** 선택
5. **"Create repository"** 클릭

### 2️⃣ 파일 업로드 (2분)

1. 생성된 페이지에서 **"uploading an existing file"** 클릭
2. 다음 파일들을 드래그 앤 드롭:
   - `index.html`
   - `README.md`
   - `.gitignore`
3. **"Commit changes"** 클릭
4. **"Add file"** → **"Create new file"** 클릭
5. 파일명에 `data/.gitkeep` 입력 후 **"Commit"** 클릭
6. `data/` 폴더에서 엑셀 3개 업로드:
   - `lotte.xlsx`
   - `hyundai.xls`
   - `kia.xls`

### 3️⃣ GitHub Pages 활성화 (1분)

1. 저장소 **"Settings"** → 좌측 **"Pages"** 클릭
2. **Branch**: `main` 선택 → **Save**
3. 1-2분 후 페이지 새로고침
4. 초록색 박스의 URL 클릭! 🎉

---

## 📱 완료!

이제 다음 URL에서 접속 가능합니다:
```
https://your-username.github.io/lotte-inventory/
```

---

## 🔄 매일 엑셀 업데이트 (30초)

1. GitHub 저장소 → `data/` 폴더
2. 기존 파일 클릭 → 휴지통 아이콘 → Commit
3. **"Add file"** → **"Upload files"**
4. 새 엑셀 드래그 앤 드롭 → Commit
5. 1분 후 자동 반영 ✅

---

## ❓ 문제 발생시

### 데이터가 안 보여요
→ 엑셀 파일명 확인: `lotte.xlsx`, `hyundai.xls`, `kia.xls` 정확히 일치?

### 404 에러가 나요
→ Settings → Pages에서 Source가 `main` 브랜치로 설정되었는지 확인

### 업데이트가 반영 안돼요
→ 브라우저 강제 새로고침 (Ctrl+Shift+R / Cmd+Shift+R)

---

## 📚 자세한 가이드

- 전체 배포 가이드: [DEPLOY.md](DEPLOY.md)
- 엑셀 형식 가이드: [data/SAMPLE_EXCEL_FORMAT.md](data/SAMPLE_EXCEL_FORMAT.md)
- 프로젝트 개요: [README.md](README.md)

---

**축하합니다! 🎊 이제 롯데렌터카 재고 관리 시스템이 온라인으로 운영됩니다!**
