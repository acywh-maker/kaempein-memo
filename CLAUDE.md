# CLAUDE.md — 마케터 데일리

> 팀 공통 규칙입니다. 작업 전 반드시 읽고 따르세요. 마감: 오늘 18:00

## 1. 프로젝트 개요
- 서비스: **마케터 데일리** — 마케터가 출근·점심·퇴근 전에 오늘 목표·광고비·시즌 일정·날씨 소재를 1분 만에 챙기려고 하루 3번 여는 서비스
- 기술 스택: 정적 파일만 (HTML / CSS / Vanilla JS)
  - 프레임워크·빌드 도구·서버 코드·파이썬 사용 금지
  - 외부 라이브러리 사용 금지 (단, **구글 폰트 + Pretendard CDN 링크는 허용** — DESIGN.md 8-1)
- API: **키 없는 공개 API만** 브라우저에서 직접 호출
- 배포: GitHub Pages (`main` 브랜치, 루트 폴더)
- 성공 기준: 오류 없이 돌아가는 간단한 서비스 + 과제 필수 조건 5개 충족

## 2. 역할과 소유권
| 영역 | 파일 | 담당 | 리뷰어 | 브랜치 |
| --- | --- | --- | --- | --- |
| 홈 (+ 레포·Pages·CLAUDE.md) | `index.html` | 혜정 | 서영 | `feat/home` |
| 광고비 환산 | `ad.html` | 서영 | 혜정 | `feat/ad` |
| 시즌 D-day | `season.html` | 로운 | 협성 | `feat/season` |
| 날씨 마케팅 소재 | `weather.html` | 협성 | 로운 | `feat/weather` |
| 디자인 규칙 | `DESIGN.md` | (DESIGN.md 담당) | — | — |

- **본인 담당 파일만 수정**한다. 다른 파일 수정이 필요하면 먼저 팀에 말하고 멈춘다
- `CLAUDE.md` 수정은 혜정 승인 후

## 3. 파일 구조
```
/
├── CLAUDE.md
├── DESIGN.md
├── index.html      # 홈 (혜정)
├── ad.html         # 광고비 환산 (서영)
├── season.html     # 시즌 D-day (로운)
├── weather.html    # 날씨 마케팅 소재 (협성)
└── .gitignore      # .env, .DS_Store
```
- 페이지마다 **HTML 파일 하나**. CSS·JS는 그 파일 안에 넣는다 (공통 CSS/JS 파일 없음)
- 페이지 간 링크는 상대 경로 (예: `./ad.html`)

## 4. 페이지 구성
| 페이지 | API (키 없음) | 아침 | 점심 | 저녁 | 저장 키 |
| --- | --- | --- | --- | --- | --- |
| 홈 | Open-Meteo 현재 날씨 | 날씨 + 오늘 목표 입력 | 목표 중간 점검 | 달성 체크 + 방문 요약 | `home_` |
| 광고비 환산 | Frankfurter 환율 (USD→KRW) | 오늘 예산 입력 → 원화 환산 | 쓴 금액 입력 + 소진율 | 최종 지출 + 날짜별 기록 | `ad_` |
| 시즌 D-day | Nager.Date 공휴일 (KR) | 다가오는 공휴일 5개 D-day | 캠페인 준비 체크리스트 | 완료율 + 한 줄 메모 | `season_` |
| 날씨 마케팅 소재 | Open-Meteo 시간별 예보 | 오늘 추천 소재 3개 | 오후 날씨 표 + 추천 | 내일 소재 + 저장 | `weather_` |

## 5. 공통 코드 (수정 금지)
- 4페이지 모두 `</body>` 바로 위에 **작업판의 [공통 코드]를 그대로** 붙여 넣는다. 한 글자도 수정하지 않는다
- 공통 코드가 하는 일: 상단 메뉴, 시간대 판별(`SLOT`), 방문 횟수·연속 일수, `load`/`save` 함수
- 시간대: 아침 06:00~10:59 / 점심 11:00~15:59 / 저녁 16:00~05:59
- 시간대는 공통 코드의 `SLOT`만 쓴다. 페이지에서 시간을 따로 계산하지 않는다
- 시간대별 내용은 `<section data-slot="morning">`, `data-slot="lunch"`, `data-slot="evening"`으로 나눈다
- 공통 코드에 문제가 있으면 직접 고치지 말고 혜정에게 알린다

## 6. 과제 필수 규칙
### ⏰ 시간대
- 주소 뒤 `?t=morning` / `?t=lunch` / `?t=evening` 으로 세 화면이 **서로 다르게** 보여야 한다

### 🔌 API
- 키가 필요한 API는 쓰지 않는다. API 키·`.env`·개인정보를 코드에 넣지 않는다
- API 주소는 `<script>` 맨 위 `const API = { ... }` 한 곳에 모으고, 각 줄에 `// 🔌` 주석
- 호출 실패 시 "데이터를 불러오지 못했어요" 안내를 보여 주고, 페이지는 계속 동작한다
- 화면 맨 아래 **"🔌 이 화면이 쓰는 API"** 상자: 실제 부른 주소 + 출처
- 날짜 있는 데이터는 **기준 날짜**를 같이 보여 주고 "실시간"이라고 쓰지 않는다
- 출처 표기: 날씨 `Weather data by Open-Meteo.com` / 환율 `Frankfurter` / 공휴일 `Nager.Date`

### 💾 기록
- 기록은 공통 코드의 `load` / `save` 로만 저장한다
- 저장 키 이름은 내 페이지 이름으로 시작한다 (예: `ad_budget`, `season_checks`)
- 이름·전화번호·이메일 같은 개인정보는 입력받지 않는다
- 새로고침해도 기록이 남아야 하고, 시크릿 창에서도 화면이 깨지지 않아야 한다

## 7. 디자인
- 디자인은 **`DESIGN.md`가 기준**이다. 색·글꼴·간격·모서리·컴포넌트는 DESIGN.md를 따르고, 값을 임의로 만들지 않는다
- 4페이지 모두 아래를 그대로 붙인다 (수정 금지)
  1. `<head>` 안: **DESIGN.md 8-1 폰트 불러오기**
  2. `<style>` 맨 위: **DESIGN.md 8-2 CSS 변수** (`:root`, 모바일 `@media`, `body`)
  3. 그 바로 아래: **DESIGN.md 8-3 기본 컴포넌트** (`.btn`, `.card`, `.badge`, `.heading-display`)
  4. 그 바로 아래: 아래 **[공통 메뉴 블록]**
- 색·글꼴은 DESIGN.md 변수(`var(--color-ink)` 등)만 쓴다. 색 코드를 직접 적지 않는다
- 버튼·카드·배지는 8-3 클래스를 쓰고, 페이지 전용 스타일은 그 아래에 페이지 전용 클래스로 추가한다

### [공통 메뉴 블록] — 공통 코드가 넣는 메뉴를 DESIGN.md 알약 내비로 덮어씀
```css
/* ===== 공통 메뉴 블록 (4페이지 동일, 수정 금지) ===== */
body > div:first-child > nav {
  max-width: var(--page-max-width);
  margin: var(--space-16) auto !important;
  padding: 12px var(--space-24) !important;
  background: var(--color-cream);
  border: var(--border-ink) !important;
  border-radius: var(--radius-pill);
  font-family: var(--font-body);
}
body > div:first-child > nav a {
  color: var(--color-charcoal);
  font-weight: 500;
  text-decoration: none;
}
body > div:first-child > nav a:hover { text-decoration: underline; }
body > div:first-child > p {
  max-width: var(--page-max-width);
  margin: 0 auto !important;
  padding: 0 var(--space-24) !important;
  color: var(--color-fog-dark);
  font-size: var(--text-caption);
}
/* ===== 공통 메뉴 블록 끝 ===== */
```

## 8. GitHub 협업 규칙
### 브랜치
- `main`: 배포용(GitHub Pages), 직접 push 금지
- 작업 브랜치: 2장 표의 브랜치명 사용 (영어 소문자 + 하이픈)

### 커밋 메시지
- 형식: `타입: 내용` (예: `feat: 광고비 환산 페이지 추가`)
- 타입: feat / fix / docs / style

### Issue → PR
- 페이지마다 Issue 1개, 본인 assign
- `내 브랜치 → main` 으로 PR, 본문에 `Closes #번호`
- 2장 표의 리뷰어 1명 Approve 후 merge
- PR에는 **내 담당 파일만** 포함 (`git add 내파일.html`)

### 충돌 방지
- 작업 시작 전 `git pull origin main`
- 같은 파일을 두 명이 고치지 않는다
- 충돌 나면 혼자 해결하지 말고 팀에 말한다

## 9. Claude 작업 시 지시
- 요청받은 담당 파일 외에는 수정하지 말 것
- 공통 코드·DESIGN.md에서 붙인 코드·[공통 메뉴 블록]은 읽기만 하고 절대 수정하지 말 것. 페이지 디자인은 그 아래에 페이지 전용 클래스로 추가
- 파이썬·서버 코드·키가 필요한 API로 만들지 말 것. 항상 HTML 파일 하나로
- 스타일 작업 전 `DESIGN.md`가 있으면 먼저 확인
- 다 만들면 아래 검사를 스스로 점검해서 표로 알려 줄 것
  1. `?t=morning/lunch/evening` 세 화면이 다른가
  2. API 실패 시 안내 문구가 나오고 페이지가 멈추지 않는가
  3. 화면 맨 아래 🔌 API 상자와 출처·기준 날짜가 있는가
  4. 새로고침 후 기록이 남는가
  5. 키·개인정보가 없는가
- 커밋·푸시·머지는 하지 말고, 커밋 메시지와 PR 본문(`Closes #번호`)만 제안할 것
