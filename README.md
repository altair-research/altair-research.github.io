# altair-research.github.io

> 갱신: 2026-10-22
> 상태: 첫 화면 = 앱 8개 허브·포트폴리오(한/영). 10-22 앱별 'AI 의존도' 추가.
> 다음: 포트폴리오로 키우기 — 공개 연락처·받을 일의 범위는 사용자 결정 대기(컨트롤 타워 보드 ⏸ HUB-PORTFOLIO).
> 막힘: 없음
> 더 볼 곳: 이 문서 '첫 화면' 절 · `index.html` · 컨트롤 타워 `README.md`

조직의 GitHub Pages 사용자 사이트(도메인 루트). 하는 일이 둘이다 — **첫 화면(앱 허브)** 과 **`assetlinks.json`**.

- **`.well-known/assetlinks.json`** — 안드로이드 앱과 이 도메인이 같은 주인임을 증명하는 파일(Digital Asset Links).
  안드로이드는 이 파일을 **도메인 루트에서만** 찾는다. 프로젝트 저장소(`/drape/`) 안에 두면 무시된다.
  이게 없으면 TWA 앱 위에 브라우저 주소창이 뜬다.

## 지금 등록된 앱

| 앱 | 패키지 | 사이트 |
|---|---|---|
| Personal Color Mirror | `com.altairresearchlab.colormirror` | https://altair-research.github.io/drape/ |
| Sprout Frame | `com.altairresearchlab.sproutframe` | https://altair-research.github.io/sprout-frame/ |

## 지문을 고칠 때

`sha256_cert_fingerprints` 는 여러 개를 넣을 수 있고, **하나라도 맞으면** 통과한다.
넣어야 하는 값은 둘이다:

1. **업로드 키** 지문 — 내 PC 에서 서명한 apk 를 직접 설치해 볼 때 필요.
2. **Play 앱 서명 키** 지문 — Play 가 배포용으로 다시 서명하므로 **스토어로 설치한 앱에는 이게 쓰인다.**
   Play Console > 앱 > 테스트 및 출시 > 설정 > 앱 서명(App integrity) 에서 복사한다.

확인: https://altair-research.github.io/.well-known/assetlinks.json 이 JSON 으로 열려야 하고,
구글 검증기로도 볼 수 있다:

```
https://digitalassetlinks.googleapis.com/v1/statements:list?source.web.site=https://altair-research.github.io&relation=delegate_permission/common.handle_all_urls
```

절차 전체는 `altair-research/drape` 의 `PLAY-STORE.md` §4 에 있다.

## 첫 화면 (`index.html`) — 앱 허브 · 포트폴리오

2026-10-15 에 만들고 10-17 에 다시 짰다. **우리가 만든 것과, 각각 어디까지 왔는지**를 한 화면에 보여 준다.
앞으로는 앱 개발 의뢰를 받을 때 "어디까지 만들 수 있는지" 보여 주는 포트폴리오로 키운다(연락처·의뢰 안내는 아직 없음).

**구성:** 할 수 있는 것(기술 요약) → 카테고리 바로가기 → 카테고리별 카드.
카드 하나 = 화면 캡처 + 한 줄 설명 + **지금**(어디까지 왔나) + 태그(종류·테스트 여부·언어) + 그 앱이 보여 주는 기술.

**카테고리:** 🌱 식물 · 👗 스타일 · 🧠 집중·학습 · 🧭 생활 도구.
10-17 에 카테고리 → 앱을 잇는 가지 그림(SVG)을 넣었다가 **같은 날 뺐다.** 사용자가 "너무 인위적"이라 했고, 따져 보니
섹션 제목이 이미 같은 묶음을 보여 줘서 그림만의 정보는 점선 하나뿐이었다. 폰에서는 글자가 8px 로 작았다.
대신 카테고리 바로가기 한 줄을 둔다.

**한/영:** 문구마다 `data-ko` / `data-en` 이 짝으로 있고, 처음엔 브라우저 언어로 고른다. HTML 기본값은 영어(자바스크립트가 꺼져도 읽힌다).

**지켜 온 기준:**
- **넣는 것:** 공개 주소로 열리는 앱·사이트. **안 넣는 것:** 블로그(ABAD·AEE·GDS), 비공개·진행 중·접은 프로젝트.
  전체 현황은 비공개 `altair0622/control-tower` 의 `PROJECTS.md` 가 맡는다.
- **종류는 "자기 도메인의 웹사이트가 있느냐"로 가른다** (10-17 사용자 기준):
  `웹사이트 · 도메인` — FocusTone Lab(focustonelab.com) · PriceAfter(priceafter.com) · ShadeSpot(shadespot.app) · Uncommon Plant(uncommonplant.com).
  `웹 앱` — 사이트 없이 앱만 배포한 것: PeachPlay · Personal Color Mirror · Sprout Frame · WearCast (전부 이 도메인 밑 `/이름/`).
  처음엔 전부 "Web" 으로 뭉뚱그렸고, 다음엔 "주소가 곧 앱이냐"로 나눴다가 이 기준으로 다시 고쳤다.
  ShadeSpot 은 한국어 지인 테스트 안내(`/shadespot-intro/`)에 걸었었는데, 실제 사이트는 `shadespot.app`(영어)이다.
- **언어는 앱을 열어서 확인한다.** 소개 문구 언어로 짐작하지 않는다 — 처음에 FocusTone Lab·PriceAfter·Personal Color Mirror 를
  "한국어"로 잘못 달았다. 셋 다 한/영이다(Personal Color Mirror 는 브라우저 언어를 보고 자동 선택).
- **설명은 각 앱 사이트의 문구를 따른다.** 허브가 앱보다 센 주장을 하지 않는다.

**새 앱 추가:** 폰 크기(375×812)로 첫 화면을 캡처해 `assets/hub/<이름>.jpg`(가로 300px), 해당 카테고리 `<ul class="grid">` 에 카드
`<li>` 하나. 바로가기의 개수도 고친다. 문구는 `data-ko`·`data-en` 둘 다.
**`index.html` 을 고칠 때 `.well-known/` 은 건드리지 않는다.**

## AI 의존도 (2026-10-22 추가)

**결정이 바뀌었다.** 전에는 AI 의존도를 최대한 낮추고 제한적으로만 쓰려 했다.
이제는 **의존도가 커도 사업성이 있으면 밀고 나간다.** 그래서 숨기지 않고 앱마다 투명하게 보여 준다.

**재는 기준: "앱을 쓸 때 AI가 필요한가."** 코드를 AI 도구로 함께 짰는지는 넣지 않았다 — 모든 앱이 해당해 구분이 안 된다.
이 축을 고른 이유는 **이용당 비용과 끊길 위험**(AI 서비스 값이 오르거나 막히면 그 기능이 멈춘다)이 여기서 갈리기 때문이다.

| 단계 | 뜻 |
|---|---|
| ▱▱▱ 없음 | AI 없이 동작 |
| ▰▱▱ 기기 안 · 만들 때만 | 폰 안에서 도는 인식(서버·이용료 없음), 또는 앱 속 이미지 등을 AI로 만들었지만 실행엔 불필요 |
| ▰▰▱ 일부 기능 | 일부 기능이 실행 중 AI 서비스를 부른다 — 그 기능은 이용당 비용이 들고, 없으면 그 기능만 빠진다 |
| ▰▰▰ 핵심 | AI 없으면 앱이 동작하지 않는다 |

**10-22 판정** — 각 저장소 코드를 직접 검색해 확인했다(AI API 호출·모델 파일·외부 전송 여부):

| 앱 | 단계 | 근거 |
|---|---|---|
| PriceAfter | 일부 기능 | '사진으로 찾기'가 워커를 거쳐 이미지 인식 AI(Anthropic 등)로 사진을 보낸다. 바코드·직접 입력은 AI 없음 |
| Sprout Frame | 기기 안 | `app/labelread.js` + tesseract(wasm) — 서버로 보내는 코드 없음 |
| WearCast | 만들 때만 | 코디 이미지를 이미지 생성 도구로 만들었다(`tool/make_prompts.dart`, 디자인 문서). 앱 코드엔 AI 없음 |
| PeachPlay | 없음 | 읽어주기는 브라우저 내장 `speechSynthesis` |
| FocusTone Lab · Uncommon Plant · Personal Color Mirror · ShadeSpot | 없음 | AI 호출·모델 없음 |

**판정이 바뀌는 때:** 앱이 AI 기능을 새로 넣거나 빼면 카드의 `<span class="ai lvN">` 를 고친다. 0~3 이 위 단계다.

## 앱 개인정보처리방침 (2026-10-27 추가)

Play 스토어가 요구하는 공개 개인정보처리방침을 `privacy/<앱>/` 한 장으로 둔다(사용자 10-27 결정: 앱마다 새 공개 저장소를 만들지 않고 허브에 둔다).
첫 화면 카드에는 걸지 않는다 — 스토어 등록 정보에서만 링크한다.

| 앱 | 주소 | 원본 |
|---|---|---|
| Battery One | https://altair-research.github.io/privacy/battery-one/ | `altair-research/battery-one-app` 의 `docs/privacy.md`·`docs/privacy.html` |

문구를 고칠 때는 원본 저장소를 먼저 고치고 여기로 옮긴다. 시행일도 함께 바꾼다.
