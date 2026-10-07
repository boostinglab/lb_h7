# 내 센터 매출 2배 만들기의 시작, 셀프 진단 키트

H7체형교정협회 무료특강(2026.09.09) 신청자 사전 자료.
원장·강사가 숫자 4개를 입력하면 어디서 매출이 새고 있는지 진단해주는 단일 HTML 페이지입니다.

- **의존성 없음** — `index.html` 하나가 전부입니다. 빌드도, npm도 필요 없습니다.
- 구글 폰트(Noto Sans KR / Poppins)만 외부에서 불러옵니다.
- 입력값은 방문자 브라우저의 `localStorage`에만 저장되며 서버로 전송되지 않습니다.

---

## 파일

| 파일 | 설명 |
|---|---|
| `index.html` | 페이지 전체 (HTML + CSS + JS 인라인) |
| `.nojekyll` | GitHub Pages의 Jekyll 처리 비활성화 |
| `og-image.png` | *(직접 추가)* 카카오톡 링크 미리보기 이미지 — 1200×630 |

---

## 배포 (GitHub Pages)

### 1. 저장소 만들기
GitHub에서 새 저장소를 만듭니다. **Public**이어야 무료 플랜에서 Pages를 쓸 수 있습니다.

- 이름 예: `h7-selfcheck`
- README·.gitignore·라이선스는 **체크하지 마세요** (빈 저장소로)

### 2. 파일 올리기

**방법 A — 웹에서 드래그 (가장 쉬움)**
빈 저장소 화면의 `uploading an existing file` 링크 → `index.html`과 `.nojekyll`을 끌어다 놓고 `Commit changes`.

> `.nojekyll`은 점으로 시작해서 파인더·탐색기에서 숨겨져 있을 수 있습니다.
> macOS는 `Cmd + Shift + .`, Windows는 탐색기 `보기 → 숨긴 항목`으로 표시하세요.
> 없어도 이 페이지는 정상 동작하니, 안 보이면 `index.html`만 올리셔도 됩니다.

**방법 B — 터미널**
```bash
cd 파일이_있는_폴더
git init
git add .
git commit -m "셀프 진단 키트"
git branch -M main
git remote add origin https://github.com/USERNAME/h7-selfcheck.git
git push -u origin main
```

### 3. Pages 켜기
저장소 → **Settings** → 왼쪽 메뉴 **Pages**

- **Source**: `Deploy from a branch`
- **Branch**: `main` / `/ (root)` → **Save**

1~2분 뒤 주소가 뜹니다.

```
https://USERNAME.github.io/h7-selfcheck/
```

### 4. 링크 미리보기 마무리
`index.html` 상단 og 태그 두 줄의 `USERNAME`/`REPO`를 실제 주소로 바꾸고, `og-image.png`(1200×630)를 저장소 루트에 올리세요. 카카오톡·문자로 공유할 때 썸네일이 뜹니다.

```html
<meta property="og:url"   content="https://USERNAME.github.io/h7-selfcheck/">
<meta property="og:image" content="https://USERNAME.github.io/h7-selfcheck/og-image.png">
```

> 카카오톡은 링크 미리보기를 캐시합니다. 이미지를 바꿔도 예전 게 보이면
> [카카오 디버거](https://developers.kakao.com/tool/debugger/sharing)에서 URL을 넣고 `초기화`를 누르세요.

---

## 수정할 만한 곳

| 무엇 | `index.html` 안에서 찾을 문자열 |
|---|---|
| 특강 날짜·시간 | `10월 21일(수) 13:00~16:00` |
| 신청 페이지 링크 | `var LIVE =` |
| 사전 질문지 링크 | `forms.gle` |
| 브랜드 컬러 | `--navy:#182C5E` |
| 벤치마크 수치 | `bench:` 로 시작하는 줄 |
| 재등록률 상한 | `var RET_CAP = 95` |

계산식은 `function calc` 안에 있습니다.

```
월 매출 = 신규 문의 × 등록률 × 평균 등록 횟수 × 객단가
평균 등록 횟수 = 1 ÷ (1 − 재등록률)
```

---

## 커스텀 도메인 (선택)

`h7-bodycenter.com` 하위에 붙이시려면:

1. 저장소 루트에 `CNAME` 파일을 만들고 안에 `check.h7-bodycenter.com` 한 줄만 적기
2. 도메인 DNS에 CNAME 레코드 추가 → `USERNAME.github.io`
3. Settings → Pages → Custom domain에 같은 주소 입력 → `Enforce HTTPS` 체크

---

*디자인: H7체형교정협회 디자인 시스템 (Brand `#182C5E` · Pretendard · radius 10/20/30)*
