# acapz.dev

`acapz.dev`는 [Astro](https://astro.build) 기반 정적 블로그입니다. [Fuwari](https://github.com/saicaca/fuwari) 테마를 바탕으로 개인 블로그 용도에 맞게 커스터마이즈했습니다.

개발 기록, 프로젝트 회고, 에세이, 나중에 다시 읽고 싶은 글을 남기기 위한 저장소입니다.

## 기술 스택

- [Astro](https://astro.build)
- [Svelte](https://svelte.dev)
- [Tailwind CSS](https://tailwindcss.com)
- [Pagefind](https://pagefind.app)
- [Biome](https://biomejs.dev)
- [pnpm](https://pnpm.io)

## 요구 사항

- Node.js 20 이상
- pnpm 9 이상

이 저장소는 `preinstall` 스크립트로 pnpm 사용을 강제합니다.

## 로컬 실행

```sh
pnpm install
pnpm dev
```

기본 개발 서버 주소는 `http://localhost:4321`입니다.

## 글 작성

새 글은 다음 명령어로 생성합니다.

```sh
pnpm new-post <filename>
```

글 파일은 `src/content/posts/` 아래에 생성됩니다. 기본 frontmatter 형식은 다음과 같습니다.

```yaml
---
title: My Post
published: 2026-07-06
description: Short description
image: ''
tags: [Essay]
category: Essay
draft: false
lang: ''
---
```

공개하지 않을 글은 `draft: true`로 설정합니다.

## 명령어

| 명령어 | 설명 |
|:--|:--|
| `pnpm dev` | 로컬 개발 서버를 실행합니다 |
| `pnpm build` | 프로덕션 사이트와 Pagefind 검색 인덱스를 빌드합니다 |
| `pnpm preview` | 프로덕션 빌드를 로컬에서 미리 봅니다 |
| `pnpm check` | Astro 검사를 실행합니다 |
| `pnpm type-check` | TypeScript 타입 검사를 실행합니다 |
| `pnpm format` | Biome으로 `src`를 포맷합니다 |
| `pnpm lint` | Biome 검사를 실행하고 `src`에 수정 가능한 변경을 적용합니다 |
| `pnpm new-post <filename>` | 새 글 파일을 생성합니다 |

## 프로젝트 구조

```text
src/
  components/       UI 컴포넌트
  content/
    posts/          블로그 글
    spec/           정적 콘텐츠 페이지
  i18n/             다국어 문구
  layouts/          페이지 레이아웃
  pages/            Astro 라우트
  styles/           전역 스타일
  config.ts         사이트, 프로필, 내비게이션, 라이선스 설정
public/             정적 공개 파일
scripts/            유틸리티 스크립트
```

## 배포

사이트 주소는 `astro.config.mjs`에 다음과 같이 설정되어 있습니다.

```js
site: "https://acapz.dev/"
```

프로덕션 빌드는 다음 명령어로 생성합니다.

```sh
pnpm build
```

빌드 결과물은 `dist/`에 생성됩니다.

## 라이선스

소스 코드는 upstream Fuwari와 동일하게 MIT 라이선스를 따릅니다. 블로그 글과 작성 콘텐츠는 사이트 설정상 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)을 사용합니다.
