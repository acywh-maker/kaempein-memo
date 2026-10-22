# kaempein-memo 디자인 가이드

> **크림색 종이 위의 잉크, 그리고 어두운 방**
> 따뜻한 크림 배경에 세리프 대형 제목을 얹고, 중간중간 어두운 섹션을 둥근 "방"처럼 배치하는 편집물(신문·잡지) 스타일입니다.

이 문서는 팀원 모두가 같은 화면을 만들기 위한 **단일 기준**입니다. 색·글꼴·간격 값을 임의로 만들지 말고 여기 있는 토큰을 쓰세요. 바꿔야 할 값이 생기면 이 파일을 먼저 고치고 PR로 공유합니다.

- 레퍼런스: Wispr Flow 웹사이트의 스타일을 분석한 자료를 참고해 우리 프로젝트에 맞게 다시 정리했습니다. 로고, 문구, 일러스트는 가져오지 않고 **스타일 원칙만** 빌려 씁니다.
- 원본 자료와 달라진 부분은 [원본 대비 변경점](#9-원본-대비-변경점)에 따로 적어 두었습니다.

---

## 목차

1. [핵심 원칙 5가지](#1-핵심-원칙-5가지)
2. [컬러](#2-컬러)
3. [타이포그래피](#3-타이포그래피)
4. [간격·모서리·레이아웃](#4-간격모서리레이아웃)
5. [컴포넌트](#5-컴포넌트)
6. [Do / Don't](#6-do--dont)
7. [접근성 체크](#7-접근성-체크)
8. [코드에 바로 붙여 넣기](#8-코드에-바로-붙여-넣기)
9. [원본 대비 변경점](#9-원본-대비-변경점)

---

## 1. 핵심 원칙 5가지

| # | 원칙 | 한 줄 설명 |
|---|------|-----------|
| 1 | **종이 같은 배경** | 기본 배경은 순백이 아닌 크림색 `#ffffeb` |
| 2 | **크기로 말하는 제목** | 제목은 굵게 하지 않고(400) 크기로 위계를 만든다 |
| 3 | **2px 잉크 테두리** | 클릭 가능한 요소에는 모두 `2px solid #1a1a1a` 테두리 |
| 4 | **그림자 없음** | 깊이는 그림자 대신 면 색 교차(크림 ↔ 다크)와 큰 둥근 모서리로 표현 |
| 5 | **포인트 색은 하나** | 주요 버튼은 라벤더 `#f0d7ff` 하나. 파랑·초록 같은 다른 액션 색은 쓰지 않는다 |

---

## 2. 컬러

### 2-1. 팔레트

| 이름 | 값 | 토큰 | 용도 |
|------|----|------|------|
| Cream (배경) | `#ffffeb` | `--color-cream` | 페이지 배경, 카드 면, 다크 위 글자 |
| Ink (잉크) | `#1a1a1a` | `--color-ink` | 본문 글자, 테두리, 다크 섹션 배경 |
| Lavender (주요 액션) | `#f0d7ff` | `--color-lavender` | **주요 버튼(CTA)**, 강조 카드, 제목 밑줄 장식 |
| Forest (보조 브랜드) | `#034f46` | `--color-forest` | 상태 배지, 다크 섹션 안쪽 카드, 보조 버튼 |
| Ember (활성 상태) | `#ffa946` | `--color-ember` | 알림 점, 녹음/진행 중 표시. **장식용으로만**, 글자색 금지 |
| Stone (옅은 구분선) | `#e4e4d0` | `--color-stone` | 약한 테두리, 구분선, 내비 배경 |
| Fog (흐린 글자) | `#8a8a80` | `--color-fog` | **큰 글자(24px 이상)나 비활성 표시에만** 사용 |
| Fog Dark (보조 글자) | `#6b6b62` | `--color-fog-dark` | 캡션, 도움말 등 작은 보조 텍스트 *(우리 팀 추가)* |
| Charcoal | `#222222` | `--color-charcoal` | 보조 버튼·내비 글자 |
| White | `#ffffff` | `--color-white` | 다크 배경 위 배지 테두리, 아이콘 선 |

### 2-2. 면(Surface) 단계

| 단계 | 면 | 값 | 쓰는 곳 |
|------|----|----|--------|
| 0 | 크림 캔버스 | `#ffffeb` | 기본 페이지 |
| 1 | 다크 챔버 | `#1a1a1a` | 교차 섹션, 다크 카드 |
| 2 | 라벤더 | `#f0d7ff` | 강조 카드, 하이라이트 패널 |
| 3 | 포레스트 | `#034f46` | 배지, 다크 섹션 속 카드 |

### 2-3. 자주 쓰는 조합

| 배경 | 글자 | 비고 |
|------|------|------|
| Cream | Ink | 기본 |
| Ink | Cream | 다크 섹션 |
| Lavender | Ink | 주요 버튼 |
| Forest | Cream | 상태 배지 |

---

## 3. 타이포그래피

### 3-1. 글꼴

원본의 EB Garamond와 Figtree에는 **한글 글리프가 없습니다.** 그래서 영문 글꼴 뒤에 한글 글꼴을 이어 붙여 씁니다. 영문은 원래 글꼴로, 한글은 짝을 이루는 한글 글꼴로 자동 표시됩니다.

| 역할 | 영문 | 한글 | 굵기 |
|------|------|------|------|
| **제목(Display)** – 세리프 | EB Garamond | Noto Serif KR | **400만 사용** |
| **본문·UI** – 산세리프 | Figtree | Pretendard | 400(기본), 500(버튼·배지), 600~700(내비·강조) |

```css
--font-display: 'EB Garamond', 'Noto Serif KR', serif;
--font-body: 'Figtree', 'Pretendard', system-ui, sans-serif;
```

> 불러오기: EB Garamond, Figtree, Noto Serif KR은 Google Fonts에서, Pretendard는 [공식 CDN](https://github.com/orioncactus/pretendard)에서 불러옵니다. ([8장](#8-코드에-바로-붙여-넣기)에 코드가 있습니다.)

### 3-2. 타입 스케일

| 역할 | 글꼴 | 크기 | 줄 간격 | 자간 | 토큰 |
|------|------|------|---------|------|------|
| caption | body | 14px | 1.4 | 0 | `--text-caption` |
| body-sm | body | 16px | 1.5 | 0 | `--text-body-sm` |
| body | body | 20px | 1.5 | 0 | `--text-body` |
| subheading | body | 24px | 1.4 | 0 | `--text-subheading` |
| heading-sm | display | 32px | 1.3 | -0.03em | `--text-heading-sm` |
| heading | display | 48px | 1.15 | -0.02em | `--text-heading` |
| heading-lg | display | 64px | 1.1 | -0.03em | `--text-heading-lg` |
| display | display | 120px | 1.05 | -0.03em | `--text-display` |

**한글 때문에 조정한 점**
- 원본은 대형 제목 줄 간격을 0.85~0.95로 아주 좁게 썼지만, 한글은 글자 높이가 커서 위아래가 잘립니다. 그래서 **최소 1.05**로 올렸습니다.
- 본문 줄 간격도 원본 1.3에서 1.5로 넓혔습니다. 한글 문단은 1.3이면 빽빽해 보입니다.
- 자간은 px 대신 `em`을 써서 크기가 바뀌어도 비율이 유지되게 했습니다.
- 모바일(≤ 768px)에서는 display 120px → **56px**, heading-lg 64px → **40px**로 줄입니다.

---

## 4. 간격·모서리·레이아웃

### 4-1. 간격 (기본 단위 8px)

`8 · 16 · 24 · 32 · 40 · 48 · 56 · 64 · 80 · 96 · 128`

토큰은 `--space-8`, `--space-16` …처럼 씁니다. 이 목록에 없는 값(예: 13px, 27px)은 쓰지 않습니다.

| 용도 | 값 |
|------|----|
| 요소 사이 | 8–16px |
| 카드 사이 | 32px |
| 카드 안쪽 여백 | 32px (모바일 24px) |
| 섹션 사이 | 64–96px (모바일 48px) |

### 4-2. 모서리 반경

| 요소 | 반경 | 토큰 |
|------|------|------|
| 버튼, 입력창 | 12px | `--radius-control` |
| 사각 태그 | 8px | `--radius-tag` |
| 일반 카드 | 32px | `--radius-card` |
| 다크 섹션·큰 카드 | 40–80px (기본 64px) | `--radius-section` |
| 배지, 내비, 알약형 | 9999px | `--radius-pill` |

> 규칙: 버튼은 12px 미만, 카드는 32px 미만으로 줄이지 않습니다. (사각 태그 8px는 일부러 둔 예외입니다.)

### 4-3. 레이아웃

- **최대 너비 1200px** 중앙 정렬, 섹션 배경색은 화면 끝까지 꽉 채웁니다.
- 섹션은 **크림 → 다크 → 크림** 순서로 번갈아 놓습니다. 다크 섹션 앞뒤에는 반드시 크림 섹션이 옵니다.
- 섹션 사이에는 구분선을 넣지 않습니다. 면 색 교차와 둥근 모서리만으로 구분합니다.
- 기능 소개 섹션은 **왼쪽에 글, 오른쪽에 이미지/목업**으로 배치합니다.
- 내비게이션은 화면 끝에 붙이지 않고 떠 있는 **크림색 알약 모양**으로 둡니다.
- 푸터는 전체 너비의 다크 띠로 만듭니다.

---

## 5. 컴포넌트

모든 컴포넌트는 **그림자 없음**, 클릭 요소는 **2px 잉크 테두리**가 기본입니다.

### 버튼

| 종류 | 배경 | 글자 | 테두리 | 반경 | 여백 | 글꼴 |
|------|------|------|--------|------|------|------|
| **Primary** (페이지당 주요 액션 1개) | Lavender | Ink | 2px Ink | 12px | 16px 24px | body 500 16px |
| **Secondary** | Cream | Ink | 2px Ink | 12px | 16px 24px | body 500 16px |
| **Ghost / 텍스트 링크** | 없음 | Ink | 없음 | – | – | body 400 16px, hover 시 밑줄 |
| **다크 위 Secondary** | Cream | Ink | 2px Cream | 12px | 16px 24px | body 500 16px |

- 상태: hover 시 배경을 한 단계 진하게(라벤더 → `#e6c4fa`, 크림 → Stone `#e4e4d0`). 키보드 focus 시 `outline: 3px solid #034f46; outline-offset: 2px`.
- disabled: 배경 Stone, 글자 Fog, 테두리 Stone.

### 입력창

배경 Cream, 테두리 2px Ink, 반경 12px, 여백 12px 16px, 글꼴 body 400 16px. placeholder는 Fog Dark. focus 시 버튼과 같은 Forest 외곽선을 씁니다.

### 카드

| 종류 | 배경 | 글자 | 반경 | 여백 | 테두리 |
|------|------|------|------|------|--------|
| **크림 카드** | Cream | Ink | 32px | 32px | 2px Ink (크림 배경 위에서는 **필수**) |
| **다크 카드** | Ink | Cream | 40–80px | 56–64px | 없음 |
| **라벤더 강조 카드** | Lavender | Ink | 32px | 32px | 2px Ink |

### 배지

| 종류 | 배경 | 글자 | 테두리 | 반경 | 여백 | 글꼴 |
|------|------|------|--------|------|------|------|
| **상태 배지** (완료, 저장됨 등) | Forest | Cream | 없음 | pill | 8px 16px | body 500 14px |
| **알약 배지** (다크 섹션 위 필터·선택) | 투명 | Cream | 1–2px White | pill | 8px 16px | body 500 14px |
| **사각 태그** (카테고리 라벨) | Ink | Cream | 없음 | 8px | 8px 16px | body 500 14px |
| **활성 점** | Ember | – | – | 원 | 8×8px | – |

### 내비게이션

크림 알약 컨테이너(반경 9999px, 2px Ink 테두리), 위·좌우에서 16px 띄움. 왼쪽 로고(body 600), 가운데 메뉴(body 500 16px, Charcoal), 오른쪽에 Primary 버튼 하나를 둡니다.

### 섹션 컨테이너

배경을 Cream/Ink로 번갈아 쓰고, 다크 섹션은 바깥 모서리를 64px(모바일 32px)로 둥글게 합니다. 섹션 사이 간격은 64–96px입니다.

### 장식: 손그림 밑줄

제목에서 강조할 단어 1–2개 아래에 Lavender색 물결 SVG 선(두께 3–4px)을 긋습니다. CTA와 같은 색을 써서 "강조 = 행동"이라는 연결을 만듭니다. **한 화면에 한 번만** 씁니다.

---

## 6. Do / Don't

### ✅ Do

- 주요 액션에는 Lavender만 씁니다.
- 제목은 세리프 400 굵기로 쓰고, 크기로 위계를 만듭니다.
- 클릭 가능한 요소에는 모두 2px Ink 테두리를 둡니다.
- 크림과 다크 섹션을 번갈아 배치합니다.
- 본문과 부제는 **왼쪽 정렬**하고, 한 줄은 최대 40자(한글 기준) 정도로 맞춥니다.
- Lavender(액션)와 Forest(상태·보조)는 함께 쓰는 짝으로 생각합니다.

### ❌ Don't

- 제목을 bold(600~700)로 만들지 않습니다.
- `box-shadow`로 카드를 띄우지 않습니다.
- 그라데이션을 쓰지 않습니다. 모든 면은 단색입니다.
- 팔레트에 없는 색(파랑, 초록 등)을 링크나 버튼에 쓰지 않습니다.
- 버튼 반경을 12px 미만, 카드 반경을 32px 미만으로 쓰지 않습니다.
- 크림 배경 위에 테두리 없는 크림 카드를 올리지 않습니다. 구분이 안 됩니다.
- 본문을 가운데 정렬하지 않습니다. 가운데 정렬은 짧은 제목에만 씁니다.
- 스톡 사진이나 3D 렌더 이미지를 쓰지 않습니다. 이미지는 평면 일러스트나 실제 앱 화면으로 씁니다.

---

## 7. 접근성 체크

WCAG 2.1 AA 기준(일반 글자 4.5:1, 큰 글자 3:1)으로 계산한 명암비입니다.

| 글자 / 배경 | 명암비 | 결과 |
|-------------|--------|------|
| Ink / Cream | 약 17:1 | ✅ 모든 크기 |
| Ink / Lavender | 약 13:1 | ✅ 모든 크기 |
| Cream / Forest | 약 9.4:1 | ✅ 모든 크기 |
| Fog Dark `#6b6b62` / Cream | 약 5.3:1 | ✅ 모든 크기 |
| Fog `#8a8a80` / Cream | 약 3.4:1 | ⚠️ **24px 이상 큰 글자만** |
| Ember `#ffa946` / Cream | 약 1.9:1 | ❌ 글자로 쓰지 않음 (점·장식만) |

- 색만으로 상태를 전달하지 않습니다. 예를 들어 활성 점 옆에는 "녹음 중" 같은 텍스트나 아이콘을 함께 둡니다.
- 모든 인터랙션 요소에 키보드 focus 표시(Forest 외곽선)를 넣습니다.

---

## 8. 코드에 바로 붙여 넣기

### 8-1. 폰트 불러오기 (`<head>`)

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=EB+Garamond&family=Figtree:wght@400;500;600;700&family=Noto+Serif+KR:wght@400&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/variable/pretendardvariable-dynamic-subset.min.css">
```

### 8-2. CSS 변수

```css
:root {
  /* Colors */
  --color-cream: #ffffeb;
  --color-ink: #1a1a1a;
  --color-lavender: #f0d7ff;
  --color-lavender-hover: #e6c4fa;
  --color-forest: #034f46;
  --color-ember: #ffa946;
  --color-stone: #e4e4d0;
  --color-fog: #8a8a80;
  --color-fog-dark: #6b6b62;
  --color-charcoal: #222222;
  --color-white: #ffffff;

  /* Fonts */
  --font-display: 'EB Garamond', 'Noto Serif KR', serif;
  --font-body: 'Figtree', 'Pretendard Variable', 'Pretendard', system-ui, sans-serif;

  /* Type scale */
  --text-caption: 14px;     --leading-caption: 1.4;
  --text-body-sm: 16px;     --leading-body-sm: 1.5;
  --text-body: 20px;        --leading-body: 1.5;
  --text-subheading: 24px;  --leading-subheading: 1.4;
  --text-heading-sm: 32px;  --leading-heading-sm: 1.3;  --tracking-heading-sm: -0.03em;
  --text-heading: 48px;     --leading-heading: 1.15;    --tracking-heading: -0.02em;
  --text-heading-lg: 64px;  --leading-heading-lg: 1.1;  --tracking-heading-lg: -0.03em;
  --text-display: 120px;    --leading-display: 1.05;    --tracking-display: -0.03em;

  /* Spacing (8px base) */
  --space-8: 8px;   --space-16: 16px; --space-24: 24px; --space-32: 32px;
  --space-40: 40px; --space-48: 48px; --space-56: 56px; --space-64: 64px;
  --space-80: 80px; --space-96: 96px; --space-128: 128px;

  /* Radius */
  --radius-tag: 8px;
  --radius-control: 12px;
  --radius-card: 32px;
  --radius-section: 64px;
  --radius-pill: 9999px;

  /* Border */
  --border-ink: 2px solid var(--color-ink);

  /* Layout */
  --page-max-width: 1200px;
  --section-gap: 96px;
  --card-padding: 32px;
}

@media (max-width: 768px) {
  :root {
    --text-display: 56px;
    --text-heading-lg: 40px;
    --text-heading: 32px;
    --section-gap: 48px;
    --card-padding: 24px;
    --radius-section: 32px;
  }
}

body {
  margin: 0;
  background: var(--color-cream);
  color: var(--color-ink);
  font-family: var(--font-body);
  font-size: var(--text-body-sm);
  line-height: var(--leading-body-sm);
  word-break: keep-all; /* 한글 단어 중간에서 줄바꿈되지 않게 */
}
```

### 8-3. 기본 컴포넌트 예시

```css
.btn {
  font: 500 16px/1 var(--font-body);
  padding: 16px 24px;
  border: var(--border-ink);
  border-radius: var(--radius-control);
  color: var(--color-ink);
  cursor: pointer;
}
.btn--primary   { background: var(--color-lavender); }
.btn--primary:hover { background: var(--color-lavender-hover); }
.btn--secondary { background: var(--color-cream); }
.btn--secondary:hover { background: var(--color-stone); }
.btn:focus-visible { outline: 3px solid var(--color-forest); outline-offset: 2px; }

.card {
  background: var(--color-cream);
  border: var(--border-ink);
  border-radius: var(--radius-card);
  padding: var(--card-padding);
}
.card--dark {
  background: var(--color-ink);
  color: var(--color-cream);
  border: none;
  border-radius: var(--radius-section);
}

.badge {
  display: inline-flex; align-items: center; gap: 8px;
  font: 500 14px/1 var(--font-body);
  padding: 8px 16px;
  border-radius: var(--radius-pill);
}
.badge--status { background: var(--color-forest); color: var(--color-cream); }

.heading-display {
  font-family: var(--font-display);
  font-weight: 400;
  font-size: var(--text-display);
  line-height: var(--leading-display);
  letter-spacing: var(--tracking-display);
}
```

### 8-4. Tailwind v4를 쓴다면

```css
@import "tailwindcss";

@theme {
  --color-cream: #ffffeb;
  --color-ink: #1a1a1a;
  --color-lavender: #f0d7ff;
  --color-forest: #034f46;
  --color-ember: #ffa946;
  --color-stone: #e4e4d0;
  --color-fog: #8a8a80;
  --color-fog-dark: #6b6b62;
  --color-charcoal: #222222;

  --font-display: 'EB Garamond', 'Noto Serif KR', serif;
  --font-body: 'Figtree', 'Pretendard Variable', 'Pretendard', system-ui, sans-serif;

  --radius-tag: 8px;
  --radius-control: 12px;
  --radius-card: 32px;
  --radius-section: 64px;
}
```

사용 예: `<button class="bg-lavender text-ink border-2 border-ink rounded-control px-6 py-4 font-body font-medium">시작하기</button>`

---

## 9. 원본 대비 변경점

참고한 원본 스타일 문서에서 그대로 쓰면 문제가 되는 부분을 아래처럼 고쳤습니다.

| 항목 | 원본 | 변경 | 이유 |
|------|------|------|------|
| 한글 글꼴 | 없음 | Noto Serif KR / Pretendard 추가 | EB Garamond·Figtree에 한글 글리프가 없음 |
| 대형 제목 줄 간격 | 0.85–0.95 | 1.05–1.15 | 한글 글자 윗부분·아랫부분이 잘림 |
| 본문 줄 간격 | 1.3 | 1.5 | 한글 문단 가독성 |
| 세리프 대체 글꼴 | sans-serif로 지정됨 | serif | 원본 CSS 오류 |
| 주요 버튼 반경 | 본문 12px, 예시 프롬프트 9999px (서로 다름) | **12px로 통일** | 문서 내 충돌 |
| `--section-gap: 64-96px` | 범위 문자열 | 96px (모바일 48px) | CSS에서 동작하지 않는 값 |
| 보조 글자색 | Fog `#8a8a80` | 작은 글자는 Fog Dark `#6b6b62` | Fog는 크림 위 명암비 3.4:1로 AA 미달 |
| 반경 토큰 | 10개 (`--radius-full-3` 등) | 5개로 정리 | 이름만 보고 용도를 알 수 있게 |
| 모바일 | 언급 없음 | 반응형 축소 값 추가 | 120px 제목은 모바일에서 넘침 |
| 상태 스타일 | 없음 | hover / focus / disabled 정의 | 구현 시 팀원마다 달라지는 것 방지 |
