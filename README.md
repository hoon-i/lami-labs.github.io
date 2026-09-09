# LaMI Lab 홈페이지

Language-driven Multimodal Intelligence Lab (LaMI Lab, 한양대학교) 공식 홈페이지 소스입니다. [Hugo](https://gohugo.io/) + [Hugo Blox](https://hugoblox.com/) (Tailwind CSS v4) 기반의 정적 사이트이며, `main` 브랜치에 푸시하면 GitHub Actions가 자동으로 빌드해서 GitHub Pages에 배포합니다.

이 문서는 **인수인계 문서**를 겸합니다. 처음 맡는 사람이 이 README만 읽고도 "어떤 파일을 고치면 어디가 바뀌는지"를 알 수 있도록 작성했습니다.

---

> 아래 각 섹션 제목을 클릭하면 내용이 펼쳐집니다.

---

<details>
<summary><h2>1. 한눈에 보기</h2></summary>

| 항목 | 내용 |
|---|---|
| 프레임워크 | Hugo `0.160.1` (extended) + Hugo Blox `blox-tailwind` 모듈 |
| 스타일 | Tailwind CSS v4 + `assets/css/custom.css` |
| 콘텐츠 방식 | **페이지 뼈대**는 `content/`, **실제 데이터**는 `data/` YAML |
| 배포 | GitHub Actions → GitHub Pages (`.github/workflows/deploy.yml`) |
| 사이트 주소 | https://lami-labs.github.io/ |
| 원본 레포 | `LaMI-Labs/lami-labs.github.io` (upstream) |

핵심 원칙: **일상적인 콘텐츠 수정(멤버 추가, 논문 추가, 뉴스 추가 등)은 `data/` 폴더의 YAML 파일과 `static/media/`의 이미지만 건드리면 됩니다.** `layouts/`나 `content/`는 페이지 레이아웃 자체를 바꿀 때만 수정합니다.

</details>

<details>
<summary><h2>2. 로컬 실행 방법</h2></summary>

### 필요한 도구

- Hugo extended (버전은 `hugoblox.yaml`에 고정되어 있음. 로컬은 최신 버전이어도 무방)
- Go 1.19 이상 (Hugo 모듈 다운로드용)
- Node.js 20 + pnpm 또는 npm (Tailwind 빌드용)

macOS 기준 설치:

```bash
brew install hugo go node pnpm
```

### 실행

```bash
git clone https://github.com/LaMI-Labs/lami-labs.github.io.git
cd lami-labs.github.io
pnpm install          # 또는 npm install
hugo server --disableFastRender
```

브라우저에서 `http://localhost:1313` 접속. 파일을 저장하면 자동으로 새로고침됩니다.

프로덕션 빌드 확인:

```bash
hugo --minify          # public/ 폴더에 결과물 생성
```

> 로컬에서 Tailwind가 `node`를 실행할 수 있도록 `config/_default/hugo.yaml`의 `security.exec.allow`에 허용 목록이 들어 있습니다. 이 설정이 없으면 최신 Hugo에서 빌드가 실패합니다.

</details>

<details>
<summary><h2>3. 배포 흐름</h2></summary>

1. `main` 브랜치에 푸시 (또는 PR 머지)
2. `.github/workflows/deploy.yml`이 자동 실행
   - `hugoblox.yaml`에서 Hugo 버전을 읽어 설치
   - `pnpm install` → `hugo --minify` 빌드
   - `public/`을 GitHub Pages에 업로드
3. 수 분 내 사이트 반영

GitHub 저장소 **Settings → Pages**에서 Source가 **GitHub Actions**로 설정되어 있어야 합니다.

### 포크해서 작업하는 경우

1. 원본 레포를 본인 계정으로 Fork
2. 로컬에서 수정 후 본인 포크에 푸시
3. 원본 레포(`LaMI-Labs/lami-labs.github.io`)로 Pull Request 생성
4. 관리자가 리뷰 후 머지하면 배포됨

> 푸시만으로는 원본에 반영되지 않습니다. 반드시 PR을 만들어야 합니다.

### 배포 직후 429 (Rate limit exceeded)가 보일 때

GitHub Pages는 짧은 시간에 배포가 반복되거나 새로고침이 몰리면 몇 분간 429를 돌려줍니다. 장애가 아니니 10분 정도 뒤에 다시 열면 됩니다.

</details>

<details>
<summary><h2>4. 디렉터리 구조</h2></summary>

```
lami-labs.github.io/
├── .github/workflows/deploy.yml   # GitHub Pages 자동 배포 워크플로
├── hugoblox.yaml                  # Hugo 버전 고정, 템플릿 ID
├── go.mod / go.sum                # Hugo 모듈(테마) 의존성
├── package.json                   # Tailwind, preact 의존성
│
├── config/_default/               # 사이트 전역 설정
│   ├── hugo.yaml                  #   사이트 제목, baseURL, security.exec 등
│   ├── params.yaml                #   테마 색상, 헤더/푸터, SEO, 분석 도구 등
│   └── menus.yaml                 #   상단 네비게이션 메뉴
│
├── content/                       # 페이지 뼈대 (각 페이지에 어떤 섹션을 넣을지)
│   ├── _index.md                  #   홈
│   ├── members/_index.md          #   Members (전체 목록, 메뉴에는 없음)
│   ├── members/professor/_index.md #  Members > Professor (교수 사진 + 소개/학력/경력)
│   ├── members/students/_index.md #   Members > Students (박사, 석박통합, 석사, 인턴)
│   ├── members/alumni/_index.md   #   Members > Alumni (졸업생)
│   ├── news/_index.md             #   News
│   ├── publications/_index.md     #   Publications
│   ├── gallery/_index.md          #   Gallery
│   ├── contact/_index.md          #   Contact (주소, 이메일, Office Hours)
│   ├── join/_index.md             #   Join LaMI (모집 안내, 지원 폼 링크)
│   ├── research/_index.md         #   Research (메뉴에는 없음, /research/ 직접 접속)
│   ├── project/_index.md          #   Project (메뉴에는 없음)
│   └── calendar/_index.md         #   Calendar (메뉴에는 없음)
│
├── data/                          # ★ 실제 콘텐츠 데이터 (가장 자주 수정)
│   ├── authors/                   #   멤버 (카테고리별 폴더, 한 명당 YAML 하나)
│   │   ├── professor/  postdoc/  phd/  integrated/  master/  undergrad/  Alumni/
│   ├── research/                  #   연구 주제 (Research 페이지용, 현재 비어 있음)
│   ├── publications/publications.yaml
│   ├── project/projects.yaml
│   ├── news/news.yaml
│   ├── gallery/albums.yaml
│   ├── info/contact.yaml          #   Contact 페이지 주소/이메일/Office Hours
│   ├── info/resources.yaml        #   (장비 카드 데이터, 현재 미사용)
│   ├── info/contact_info.yaml     #   (구 연락처 카드 데이터, 현재 미사용)
│   └── application/notice.yaml    #   Join LaMI 페이지 안내문
│
├── docs/examples/                 # 멤버/연구 YAML 예시 파일 (.example)
│
├── layouts/                       # 커스텀 템플릿 (HTML + Hugo 템플릿 문법)
│   ├── shortcodes/                #   content/에서 {{< ... >}}로 호출하는 컴포넌트
│   │   ├── members-pi.html        #     교수 카드
│   │   ├── members-postdoc.html   #     포닥 카드
│   │   ├── members-phd.html       #     박사과정 카드
│   │   ├── members-integrated.html #    석박통합과정 카드
│   │   ├── members-master.html    #     석사과정 카드
│   │   ├── members-interns.html   #     학부생/인턴 카드
│   │   ├── members-alumni.html    #     졸업생 목록
│   │   ├── members-cards.html     #     (범용 멤버 카드, 현재 미사용)
│   │   ├── research-cards.html    #     연구 주제 카드 (Research 페이지)
│   │   ├── home-research-topic.html #   (홈용 연구 캐러셀, 현재 미사용)
│   │   ├── publication-cards.html #     논문 목록 + 검색/필터
│   │   ├── project-cards.html     #     과제 목록
│   │   ├── news-cards.html        #     뉴스 카드 (홈/뉴스 페이지 공용)
│   │   ├── gallery-albums.html    #     갤러리 앨범 + 라이트박스
│   │   ├── resource-cards.html    #     장비/서버 카드 (현재 미사용)
│   │   ├── contact-panel.html     #     연락처 2단 패널 (주소 / 이메일·Office Hours 카드)
│   │   ├── contact-info-cards.html #    (구 연락처 카드, 현재 미사용)
│   │   └── application-notice.html #    지원 안내
│   ├── partials/authors/
│   │   ├── author-image.html      #   멤버 사진 경로 결정 로직
│   │   └── author-hover-image.html #  멤버 hover 사진 경로 결정 로직
│   ├── partials/body_end.html     #   파비콘 강제 교체 스크립트
│   └── _partials/hooks/body-end/  #   페이지 하단에 삽입되는 JS
│       ├── favicon-static.html    #     파비콘 교체
│       ├── nav-underline.html     #     메뉴 밑줄 애니메이션
│       └── people-hover-image.html #    멤버 사진 hover 전환
│
├── assets/                        # Hugo 파이프라인으로 처리되는 자산
│   ├── css/custom.css             #   전역 커스텀 CSS (메뉴 간격, 컨테이너 폭 등)
│   ├── js/preact-built/hero.js    #   히어로 섹션 preact 번들 (빌드 결과물)
│   └── media/
│       ├── home.png               #   홈 히어로 배경 이미지
│       └── logo.png               #   헤더 로고
│
├── static/                        # 그대로 복사되는 정적 파일 (URL: /media/...)
│   ├── favicon.png
│   └── media/
│       ├── icon/*.svg             #   연락처/논문 링크용 아이콘
│       ├── authors/               #   멤버 사진 (카테고리별 하위 폴더)
│       ├── research/              #   연구 주제 이미지
│       ├── news/                  #   뉴스 이미지
│       ├── gallery/<앨범폴더>/     #   갤러리 사진
│       └── resource/              #   장비 사진
│
└── blog/                          # 템플릿 잔여물. hugo.yaml에서 렌더링 비활성화됨
```

</details>

<details>
<summary><h2>5. 페이지별 수정 가이드</h2></summary>

각 페이지는 `content/<페이지>/_index.md`에 정의되어 있고, `sections:` 아래 `block: markdown` 안에서 shortcode를 호출하는 구조입니다. 실제 내용은 shortcode가 `data/`에서 읽어옵니다.

| 페이지 | URL | content 파일 | 데이터 소스 | 이미지 위치 |
|---|---|---|---|---|
| Home | `/` | `content/_index.md` | `data/news/news.yaml` | `assets/media/home.png` (배경) |
| Members > Professor | `/members/professor/` | `content/members/professor/_index.md` | 페이지 파일 안 HTML | `static/media/authors/<카테고리>/` |
| Members > Students | `/members/students/` | `content/members/students/_index.md` | `data/authors/**/*.yaml` (PhD, Integrated, Master, Interns) |
| Members > Alumni | `/members/alumni/` | `content/members/alumni/_index.md` | `data/authors/Alumni/*.yaml` | 없음 | `static/media/authors/<카테고리>/` |
| Members (전체) | `/members/` | `content/members/_index.md` | 위 전체 | 메뉴에 노출되지 않음 |
| News | `/news/` | `content/news/_index.md` | `data/news/news.yaml` | `static/media/news/` |
| Publications | `/publications/` | `content/publications/_index.md` | `data/publications/publications.yaml` | 없음 (아이콘만) |
| Gallery | `/gallery/` | `content/gallery/_index.md` | `data/gallery/albums.yaml` | `static/media/gallery/<folder>/` |
| Contact | `/contact/` | `content/contact/_index.md` | `data/info/contact.yaml` | 없음 |
| Research (메뉴 없음) | `/research/` | `content/research/_index.md` | `data/research/*.yaml` | `static/media/research/` |
| Project (메뉴 없음) | `/project/` | `content/project/_index.md` | `data/project/projects.yaml` | 없음 |
| Join LaMI | `/join/` | `content/join/_index.md` | `data/application/notice.yaml` | 없음 |
| Calendar (메뉴 없음) | `/calendar/` | `content/calendar/_index.md` | 파일 안에 iframe 직접 작성 | 없음 |

### 홈 (`content/_index.md`)

- **히어로**: `sections[0]` (`block: hero`)의 `title`, `text`, `announcement`를 수정. 배경은 `assets/media/home.png`.
- **지원 링크**: 히어로의 Apply 버튼과 소개 문단의 `Join us →` 링크는 `/join/` (Join LaMI 페이지)로 갑니다. 구글 폼 주소는 `data/application/notice.yaml`의 `buttons`에만 있습니다.
- **연구실 소개 문단**: `id: intro` 블록의 HTML을 직접 수정.
- **Research Areas 3단 카드**: `id: research-areas` 블록의 HTML에 직접 작성되어 있음. 연구 분야 제목/설명을 바꾸려면 여기를 수정.
- **Latest News**: `{{< news-cards >}}` → `data/news/news.yaml`에서 최신 12개.

### Members > Professor (`content/members/professor/_index.md`)

- 이 페이지는 멤버 카드 shortcode를 쓰지 않고 `id: pi` 블록의 HTML로 직접 구성되어 있습니다. 왼쪽 사진, 오른쪽 소개글, 아래에 Education / Professional Experience / Academic Service / Invited Talks 4개 섹션입니다.
- 사진은 `static/media/authors/professor/jisoo-mok.jpg`를 읽습니다. 소개글, CV 링크, 경력이 바뀌면 이 파일의 HTML을 수정하세요.
- 교수 YAML(`data/authors/professor/jisoo-mok.yaml`)은 전체 Members 페이지(`/members/`)에서만 쓰입니다.

### Contact (`content/contact/_index.md`)

- 2단 연락처 패널 한 블록으로 구성됩니다. (장비 카드 `resource-cards`는 제거했습니다. 다시 넣으려면 `data/info/resources.yaml`과 shortcode가 남아 있습니다.)
- 연락처 패널의 텍스트는 전부 `data/info/contact.yaml`에서 읽습니다 (6.7 참고). 페이지 파일은 건드릴 필요가 없습니다.
- 지도는 넣지 않았습니다. 주소 텍스트만 표시합니다.
- 데이터 파일은 페이지 이름과 달리 `data/info/`에 있습니다 (shortcode가 `site.Data.info`를 읽음).

### Calendar (`content/calendar/_index.md`)

- Google Calendar 예약 페이지 iframe과 일반 캘린더 iframe이 들어 있음. 이전 템플릿의 링크가 그대로라 사용하려면 `src` URL을 교체해야 합니다. 메뉴에는 없습니다.

</details>

<details>
<summary><h2>6. 데이터 파일 스키마 (YAML)</h2></summary>

> 각 YAML 파일 상단에 주석으로 예시가 들어 있습니다. `docs/examples/`에도 예시 파일이 있습니다.

### 6.1 멤버 — `data/authors/<카테고리폴더>/<slug>.yaml`

**멤버 한 명당 YAML 파일 하나**입니다. 폴더는 정리용이며, 실제 분류는 파일 안의 `category` 값으로 결정됩니다.

`category`에 들어갈 수 있는 값 (shortcode 필터 기준, 대소문자 정확히):

| category 값 | 표시 페이지 / 섹션 | 사진 폴더 (`static/media/authors/`) |
|---|---|---|
| `PI` | Professor 페이지 / Professor | `professor/` |
| `Postdoc` | (현재 어느 페이지에도 표시 안 함) | `postdoc/` |
| `PhD Students` | Students 페이지 / Ph.D. Students | `phd/` |
| `Integrated Students` | Students 페이지 / Integrated M.S./Ph.D. Students | `integrated/` |
| `Master Students` | Students 페이지 / M.S. Students | `master/` |
| `Interns` | Students 페이지 / Interns | `undergrad/` |
| `Alumni` | Alumni 페이지 | (사진 없음) |

> Alumni는 예외적으로 **폴더 이름이 `Alumni`인 것**을 기준으로 수집합니다. 반드시 `data/authors/Alumni/` 안에 두세요.
> `docs/examples/`의 예시 파일에는 `Post Doc`, `Undergraduate Students` 같은 값이 적혀 있는데, 실제 shortcode는 위 표의 값만 인식합니다.

일반 멤버 예시 (`data/authors/undergrad/jaehoon-jang.yaml`):

```yaml
schema: hugoblox/author/v1
slug: jaehoon-jang          # 사진 파일명과 동일해야 함 (jaehoon-jang.jpg)
is_owner: false
category: Interns
order: 1                    # 섹션 내 정렬 순서 (작을수록 앞)
name:
  display: Jaehoon Jang
  given: Jaehoon
  family: Jang
role: |-                    # 여러 줄 가능. 첫 줄 과정, 둘째 줄 출신 학교. "Lab Representative" 문구는 자동 강조됨
  Undergraduate Intern
  HUFS
tags:                       # 연구 분야 배지
  - LLM Fundamentals
hidden_image: jaehoon-jang-2.jpg   # (선택) hover 시 보일 사진, static/media/authors/hidden/ 에 위치
links:                      # 아이콘 링크 줄. 없으면 표시되지 않음. at-symbol은 아이콘 옆에 주소가 함께 표시됨
  - icon: at-symbol
    url: mailto:name@example.edu
    label: E-mail
  - icon: brands/github
    url: https://github.com/username
    label: GitHub
  - icon: academicons/google-scholar
    url: https://scholar.google.com/...
    label: Google Scholar
  - icon: brands/linkedin
    url: https://linkedin.com/in/...
    label: LinkedIn
  - icon: homepage
    url: https://example.com
    label: Homepage
```

`links[].icon`에 지원되는 값: `at-symbol`, `brands/github`, `brands/linkedin`, `academicons/google-scholar`, `homepage` (또는 `brands/x`). `url`을 비워두면 아이콘이 비활성 상태로 표시됩니다.

교수 예시 (`data/authors/professor/jisoo-mok.yaml`): 위와 동일하되 `is_owner: true`, `category: PI`, `role: Assistant Professor`. 추가로 `bio`, `affiliations` 필드를 넣을 수 있습니다.

Alumni 예시 (`data/authors/Alumni/<slug>.yaml`):

```yaml
schema: hugoblox/author/v1
slug: kim-alumni
category: Alumni
order: 1
name:
  display: Firstname Lastname
course: M.S. Student        # 재학 당시 과정 (없으면 role 사용)
next: "Samsung Electronics" # 진로
graduated: "2025 Fall"      # 졸업 시기
```

**사진 규칙** (`layouts/partials/authors/author-image.html` 로직):

1. `image:` 필드가 있으면 그 값을 사용 (URL, `/`로 시작하는 절대경로, 또는 카테고리 폴더 내 파일명)
2. 없으면 `static/media/authors/<카테고리폴더>/<slug>.jpg`를 자동으로 찾음
3. 그것도 없으면 `static/media/authors/me.jpg`로 대체 (기본 이미지, 필요 시 추가)

### 6.2 연구 주제 — `data/research/<slug>.yaml`

**주제 하나당 YAML 파일 하나**. Research 페이지(메뉴 미노출)에 사용됩니다. 홈의 Research Areas는 `content/_index.md`에 직접 작성된 HTML이라 이 파일과 무관합니다.

```yaml
slug: world-models
title: World Models for Physical AI
category: Physical AI       # 배지. "Intelligent Systems" / "Physical AI" 는 전용 색상, 그 외는 회색
description: One or two sentences describing this research direction.
image: world-models.gif     # static/media/research/ 기준 파일명. 생략 시 <slug>.jpg 자동 탐색
# image:                    # 두 장을 나란히 보여주려면 리스트로
#   - world-models-a.png
#   - world-models-b.png
# captions:                 # (선택) 이미지별 캡션
# pair_gap: 24              # (선택) 두 이미지 사이 간격(px)
url: https://...            # (선택) "Read more" 버튼
order: 1                    # 정렬 순서
```

### 6.3 논문 — `data/publications/publications.yaml`

리스트 형태. 최신 `date`순으로 자동 정렬되며, `category`로 필터 버튼이, `method` / `domain` / `task`가 있으면 키워드 배지가 생성됩니다. 검색창은 제목/저자/학회명을 대상으로 합니다.

```yaml
- slug: C17
  title: "Paper Title"
  authors:
    - "Firstname Lastname*"   # * 는 공동 1저자, † 는 교신저자 표기 관례
    - "Jisoo Mok†"
  venue: "ICLR 2026"
  category: conference      # conference | journal | workshop | preprint
  date: 2026-04-01          # 정렬용. 정확한 날짜를 모르면 학회 개최 월로
  note: "NVIDIA Academic Grant"   # (선택) 협업/지원 표기
  method: Method Area       # (선택) 키워드 배지
  domain: Application Domain
  task: Task Name
  links:                    # 모두 선택. 있는 것만 아이콘으로 표시
    paper: https://.../paper.pdf
    supp: https://.../supp.pdf
    page: https://project-page
    code: https://github.com/...
    link: https://...
```

> Google Scholar 자동 연동은 하지 않습니다. Scholar는 공식 API가 없어 크롤링밖에 방법이 없고 수시로 차단됩니다. 논문이 나오면 이 파일에 한 블록 추가하세요.

### 6.4 과제 — `data/project/projects.yaml`

`start` 기준 최신순 정렬.

```yaml
- title: "Project title"
  duration: "01/2026 - 12/2027 (2 years)"
  program: "Program name"
  funding: "Funding agency"
  organization: "Managing organization"
  infra: "GPU resources"    # (선택)
  status: "Ongoing"         # Ongoing | Completed
  category: research        # research | gpu
  start: "2026-01"
```

### 6.5 뉴스 — `data/news/news.yaml`

`date` 기준 최신순 정렬. 홈에는 최신 12개, News 페이지에는 전체(12개씩 더 보기).

```yaml
- date: 2026-01             # YYYY-MM 또는 YYYY-MM-DD
  type: Publication         # Honor | Project | Events | Publication (그 외는 Events로 표시)
  title: "One paper accepted to ICLR 2026"
  description: |-
    One or two sentences. [Link](https://...) 형식의 마크다운 링크 사용 가능.
  image: "media/news/example.png"   # (선택) static/ 기준 경로. 없으면 텍스트만 표시되고 이미지 영역은 생기지 않음
  url: https://...          # (선택) description 안의 [Link] 텍스트가 이 URL로 연결됨
```

### 6.6 갤러리 — `data/gallery/albums.yaml`

앨범 하나당 항목 하나. 사진은 `static/media/gallery/<folder>/`에 넣으면 **폴더 안 이미지 전체를 자동으로 읽어** 라이트박스에 표시합니다. 파일명 앞 숫자(`1.jpg`, `2.jpg`…) 순으로 정렬됩니다.

```yaml
- slug: "workshop-2026"
  title: "Lab Workshop 2026"
  folder: "workshop_2026"   # static/media/gallery/workshop_2026/
  cover: "1.jpg"            # (선택) 생략 시 첫 번째 이미지
  category: "Events"        # 필터 버튼 그룹
  date: "2026-01-15"
  location: "Seoul"
```

### 6.7 Contact — `data/info/contact.yaml`

`contact.yaml` (연락처 패널):

```yaml
address:
  eyebrow: Address           # 작은 상단 라벨
  title: Visit Us
  places:                    # 왼쪽 세로선 블록. 여러 개 가능
    - title: Professor's Office
      lines:                 # 첫 줄은 굵게 표시
        - "Prof. Jisoo Mok"
        - "#1001 구자겸기계관"
  footer:                    # 구분선 아래 주소 문단. 마지막 줄은 회색
    - "Hanyang University"
    - "222, Wangsimni-ro, Seongdong-gu, Seoul"

cards:                       # 오른쪽 카드. 순서대로 표시
  - title: Email
    value: name@hanyang.ac.kr
    href: mailto:name@hanyang.ac.kr   # (선택) 있으면 링크
    note: 설명 문장 (마크다운 가능)
  - title: Office Hours
    lines:                   # value 대신 lines를 주면 표 형태로 표시
      - "**Mon** 09:00–12:00 | 13:00–18:00"
```

`resources.yaml` (장비 카드, 현재 미사용): `sections` 형식(텍스트 목록) 또는 `robots` 형식(사진 그리드) 둘 중 하나.

```yaml
- title: "Server"
  sections:
    - title: "In-House Resources"
      items:
        - "RTX A6000 (4 ea) / 256GB RAM / 20TB"
- title: "Robot"
  robots:
    - name: "Robot name"
      image: "robot.jpg"    # static/media/resource/
```

### 6.8 Join LaMI — `data/application/notice.yaml`

```yaml
intro: |
  소개 문단 (마크다운)
buttons:
  - label: "Apply 🚀"
    url: "https://forms.gle/..."
    variant: "primary"
    new_tab: true
tracks:
  - title: "Undergraduate Intern"
    badge: "Rolling admission"
    content: |
      마크다운 본문. ### 소제목, - 목록 사용 가능
```

</details>

<details>
<summary><h2>7. 이미지 / 미디어 파일 위치</h2></summary>

| 용도 | 경로 | 비고 |
|---|---|---|
| 헤더 로고 | `assets/media/logo.png` | `params.yaml`의 `identity.logo`, `header.logo`에서 참조 |
| 홈 히어로 배경 | `assets/media/home.png` | `content/_index.md`의 `background.image.filename` |
| 파비콘 | `static/favicon.png` | JS로 강제 교체하므로 이 파일만 바꾸면 됨 |
| 멤버 사진 | `static/media/authors/{professor,postdoc,phd,integrated,master,undergrad}/<slug>.jpg` | 3:4 비율 권장 |
| 멤버 hover 사진 | `static/media/authors/hidden/<파일명>` | YAML의 `hidden_image` |
| 멤버 기본 사진 | `static/media/authors/me.jpg` | 사진 없을 때 대체 이미지 (현재 없음, 추가 권장) |
| 연구 주제 이미지 | `static/media/research/` | jpg/png/gif |
| 뉴스 이미지 | `static/media/news/` | |
| 갤러리 사진 | `static/media/gallery/<folder>/` | 폴더 통째로 자동 인식 |
| 장비 사진 | `static/media/resource/` | |
| 아이콘 | `static/media/icon/*.svg` | 연락처, 논문 링크용 |

`static/` 안의 파일은 사이트에서 `/media/...` 경로로 접근됩니다. `assets/`는 Hugo가 처리(리사이즈, 해시)하는 파일용입니다.

</details>

<details>
<summary><h2>8. 사이트 전역 설정</h2></summary>

### `config/_default/hugo.yaml`

- `title`: 사이트 제목 (브라우저 탭)
- `baseURL`: 배포 URL. GitHub Actions에서는 자동으로 덮어쓰므로 로컬 개발 시에만 영향
- `cascade`: `blog/` 렌더링 비활성화 설정 (템플릿 잔여물 숨김)
- `security.exec.allow`: 로컬 빌드 시 Tailwind가 `node`를 실행할 수 있도록 허용

### `config/_default/params.yaml`

- `identity`: 연구실 이름, 로고, 설명 (SEO/OG 태그에 사용)
- `theme.mode`: `system` / `light` / `dark`
- `theme.colors.primary`: 주 색상. 현재 `neutral`(무채색)로 설정해 블랙 앤 화이트 테마입니다. 강조색은 `custom.css`의 `--nav-accent`와 각 shortcode의 `#111827` 계열 값입니다.
- `header`: 로고, 정렬, 테마 토글 여부 등
- `footer`, `copyright`: 하단 문구
- `analytics.google.measurement_id`: GA4 ID를 넣으면 분석 활성화

### `config/_default/menus.yaml`

상단 메뉴 목록. `weight`가 작을수록 왼쪽. 새 페이지를 만들면 여기에도 추가해야 메뉴에 보입니다.

현재 메뉴는 Home, Members(Professor / Students / Alumni), News, Publications, Gallery, Contact, Join LaMI 7개입니다. Research, Project, Calendar 페이지는 존재하지만 메뉴에는 노출하지 않습니다.

드롭다운 메뉴는 부모 항목에 `hasChildren: true`를 주고, 자식 항목에 `parent: <부모 name>`을 지정합니다. Members 메뉴가 이 방식으로 Professor / Students / Alumni 세 개의 하위 메뉴를 가집니다.

### `assets/css/custom.css`

전역 CSS 오버라이드. Hugo Blox 기본 컨테이너 폭 제한을 풀거나, 드롭다운 메뉴 간격을 다른 메뉴와 맞추는 등의 조정이 들어 있습니다. shortcode 파일 안에도 `<style>` 블록이 있으니, 특정 컴포넌트 스타일은 해당 shortcode를 먼저 확인하세요.

</details>

<details>
<summary><h2>9. 자주 하는 작업 체크리스트</h2></summary>

**새 멤버 추가**
1. `data/authors/<카테고리폴더>/<slug>.yaml` 생성 (6.1 참고)
2. 사진을 `static/media/authors/<카테고리폴더>/<slug>.jpg`로 저장
3. `order` 값으로 순서 조정

**멤버 졸업 처리**
1. 기존 YAML을 `data/authors/Alumni/`로 이동
2. `category: Alumni`로 바꾸고 `course`, `next`, `graduated` 추가
3. 불필요한 `links`, `tags` 등은 제거해도 됨 (Alumni 카드는 표시하지 않음)

**논문 추가**
1. `data/publications/publications.yaml` 맨 위에 항목 추가 (정렬은 자동)
2. 필요하면 `data/news/news.yaml`에 `type: Publication` 뉴스도 추가

**뉴스 추가**
1. `data/news/news.yaml`에 항목 추가
2. 이미지가 있으면 `static/media/news/`에 저장

**갤러리 앨범 추가**
1. `static/media/gallery/<folder>/`에 사진 저장 (`1.jpg`, `2.jpg`… 순번 권장)
2. `data/gallery/albums.yaml`에 항목 추가

**연락처 / Office Hours 변경**
1. `data/info/contact.yaml` 수정

**지원 폼 링크 변경**
1. `data/application/notice.yaml`의 `buttons[].url`

**새 페이지 추가**
1. `content/<이름>/_index.md` 생성 (기존 페이지 복사 권장)
2. 필요하면 `layouts/shortcodes/`에 컴포넌트 작성, `data/`에 데이터 파일 추가
3. `config/_default/menus.yaml`에 메뉴 항목 추가

</details>

<details>
<summary><h2>10. 주의사항 및 알려진 이슈</h2></summary>

- **멤버 사진이 아직 없습니다.** `static/media/authors/<카테고리>/<slug>.jpg`에 사진을 넣으면 카드에 표시됩니다. 사진 없는 멤버의 대체 이미지 `static/media/authors/me.jpg`도 없으니 하나 넣어두는 것을 권장합니다.
- **로고, 파비콘, 홈 배경이 임시 이미지입니다.** `assets/media/logo.png`와 `static/favicon.png`는 검은 네모에 흰 L, `assets/media/home.png`는 검은 단색입니다. 정식 로고와 히어로 이미지가 생기면 같은 파일명으로 교체하면 됩니다.
- **교수 YAML의 Google Scholar 링크와 논문별 원문/코드 링크가 비어 있습니다.**
- **멤버 `category` 값은 shortcode 필터와 정확히 일치해야 합니다.** 6.1의 표를 따르세요.
- 멤버가 없는 섹션은 숨기지 않고 "Coming soon." 문구를 표시합니다. 문구는 각 `members-*.html`의 `members-empty` 요소에서 바꿀 수 있습니다.
- `data/research/`가 비어 있습니다. Research 페이지(메뉴 미노출)는 YAML을 넣기 전까지 빈 상태입니다.
- `layouts/shortcodes/members-cards.html`, `home-research-topic.html`, `contact-info-cards.html`은 현재 어떤 페이지에서도 호출하지 않는 예비 컴포넌트입니다.
- `blog/` 폴더는 Hugo Blox 템플릿 잔여물이며 `hugo.yaml`에서 렌더링을 꺼두었습니다. 삭제해도 무방합니다.
- `assets/js/preact-built/hero.js`는 빌드된 번들입니다. 직접 수정하지 마세요.
- Members 하위 페이지에서 상단 메뉴 밑줄이 Home 아래에 그려집니다. `nav-underline.html`이 드롭다운 항목을 매칭하지 않아서 생기는 사소한 문제입니다.
- YAML 들여쓰기 오류가 가장 흔한 빌드 실패 원인입니다. 푸시 전에 `hugo --minify`로 로컬 빌드를 한 번 돌려보세요.

</details>
