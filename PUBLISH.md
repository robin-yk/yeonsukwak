# 개인 웹사이트 공개 방법

2026년 7월 31일자 CV 하나만 가지고 만든 개인 학술 웹사이트입니다. 빌드 도구도, 프레임워크도,
의존성도 없습니다. HTML 한 장과 CSS 한 장, JS 한 장이 전부라서 GitHub Pages에 그대로 올리면
바로 동작합니다.

먼저 `index.html`을 브라우저에서 더블클릭해서 열어보세요. 그게 공개될 화면과 같습니다.

---

## 1. 공개 전에 꼭 확인할 것

### 개인정보 두 군데

1. **`cv/Kwak_Yeonsu_CV.pdf` 첫 줄에 집 주소와 휴대폰 번호가 있습니다.**
   `512 Scotland Dr, Newark, DE | fiske@udel.edu | +1 (302) 661-5002`
   이 PDF를 그대로 올리면 두 정보가 검색엔진에 영구히 남습니다. 웹용으로는 헤더를 이메일과
   LinkedIn만 남긴 버전을 따로 export해서 같은 파일 이름으로 덮어쓰는 방식을 권합니다.
   파일 이름만 유지하면 HTML은 고칠 필요가 없습니다.
2. **CV 마지막 REFERENCES 섹션에 추천인 다섯 분의 개인 이메일이 있습니다.**
   웹페이지 본문에는 넣지 않았지만 PDF에는 남아 있습니다. 웹용 CV에서는 빼는 편이 안전합니다.

웹페이지 본문에는 학과 주소와 UD 이메일만 넣었고, 집 주소와 전화번호, 추천인 정보는 없습니다.

### 사진

`assets/img/headshot.jpg` 자리가 비어 있어서 지금은 회색 placeholder가 보입니다. 세로로 긴
4대5 비율 사진을 그 경로에 `headshot.jpg`라는 이름으로 넣으면 자동으로 바뀝니다. 800 × 1000
픽셀 정도면 충분합니다. HTML은 건드리지 않아도 됩니다.

### 링크

Contact 항목에 CV, Google Scholar, LinkedIn 세 개가 들어 있습니다. UD ChBE 프로필이나 Vlachos
그룹 페이지, ORCID가 있으면 `index.html` 아래쪽 `contact__links` 목록에 한 줄씩 추가하면 됩니다.

---

## 2. GitHub Pages에 올리기

GitHub 계정 이름이 예를 들어 `yeonsukwak`이라면, 저장소 이름을 `yeonsukwak.github.io`로
만들어야 주소가 `https://yeonsukwak.github.io`가 됩니다. 계정 이름과 저장소 이름이 정확히
같아야 하고, Public이어야 합니다.

1. github.com에서 **New repository**를 누릅니다.
2. 이름에 `<본인계정이름>.github.io`를 넣고, Public을 선택합니다. README나 .gitignore를 추가하는
   체크박스는 모두 비워둡니다.
3. Create repository를 누릅니다.

### 방법 A. 웹에서 끌어다 놓기 (터미널 없이)

만들어진 저장소 화면에서 **uploading an existing file**을 누르고, 이 폴더 안의 파일과 폴더를
통째로 끌어다 놓은 뒤 Commit changes를 누릅니다. `.nojekyll` 파일이 빠지지 않게 주의하세요.
숨김 파일이라 Finder에서 `Cmd + Shift + .`를 눌러야 보입니다. 이 파일이 없으면 GitHub이 사이트를
Jekyll로 처리하려다 일부 파일을 무시합니다.

### 방법 B. 터미널

```
cd <이 폴더>
git init -b main
git add -A
git commit -m "Initial site"
git remote add origin https://github.com/<본인계정이름>/<본인계정이름>.github.io.git
git push -u origin main
```

어느 쪽이든 1분쯤 뒤 `https://<본인계정이름>.github.io`에서 열립니다. 저장소의 Settings 안
Pages 항목에서 Source가 `main` 브랜치로 되어 있는지 한 번 확인하면 됩니다.

---

## 3. 내용 고치기

모든 문구는 `index.html` 한 파일 안에 있습니다. 원하는 문장을 텍스트 편집기에서 찾아 고치고
저장한 뒤 다시 push하면 끝입니다.

색과 여백, 글자 크기는 `assets/css/style.css` 맨 위 `:root` 블록에 변수로 모아뒀습니다. 예를
들어 `--accent`를 바꾸면 링크, 강조선, 버튼 색이 한 번에 바뀝니다. 지금은 네이비입니다.

로컬에서 확인하려면 이 폴더에서 아래를 실행하고 `http://localhost:8000`을 여세요.

```
python3 -m http.server 8000
```

---

## 4. 내용이 어디서 왔는지

전부 CV에서 그대로 옮겼습니다. 다만 아래는 옮기면서 판단이 들어간 부분이라 확인이 필요합니다.

- **Research 4갈래.** CV에 없는 구분입니다. 마이크로파 촉매, 펄스 줄 가열 반응기, 수소 저장과
  방출, 저탄소 연료 공정 개발로 나눴습니다. 표현이 마음에 안 들면 그 문단만 고치면 됩니다.
- **논문 링크.** CV PDF에 걸려 있던 링크만 사용했고 추적용 토큰만 잘라냈습니다. 없는 DOI를
  임의로 만들어 넣지 않았습니다. 예외는 US 11,674,068 B2의 Google Patents 주소 하나인데 이건
  특허번호로부터 형식이 고정되어 있습니다. 나머지 한국 특허 세 건은 링크 없이 번호만 있습니다.
- **About의 논문 수.** 1저자 10편과 CV의 "10 out of 16" 표기를 합쳐 26편으로 적었습니다.
- **심사 중 논문.** CV가 "et al."로만 적고 있어서 공저자를 비워뒀습니다. 확정되면 채우면 됩니다.
- **Awards 두 열.** 연구 관련 상과 장학금으로 나눈 것은 두 열 길이를 맞추기 위한 편의입니다.
