# Fastcampus_Solidity

# Solidity 기초 문법 실습 자료 

<p align="center">
  <a href="https://discord.gg/pFuCJcnX" target="_blank"><img src="https://ocamlpro.com/fr/blog/assets/img/logo_solidity_title.png" alt="Logo" height=170></a>
  <br />
  <br />
  <a href="https://discord.gg/pFuCJcnX" target="_blank"><img height=20 src="https://img.shields.io/discord/876711213126520882" /></a>
</p>

# 솔리디티 특징 (매번 버전 업데이트 되므로 해당 강의는 v0.8.17기준)

솔리디티(Solidity)는 계약 지향 프로그래밍 언어로 다양한 블록체인 플랫폼의 스마트계약(Smart Contract) 작성 및 구현에 사용된다. 
- 솔리디티는 정적타입(statically-typed)의 프로그래밍 언어로 EVM상에서 작동하는 스마트계약을 개발하기 위해 설계되었다
- Ethereum Virtual Machine (EVM)을 목표로 설계된 4가지 언어중 하나이다.
- (Serpent, LLL, Viper (실험용), Mutan (미사용)) 현재는 솔리디티가 이더리움의 주요 언어다.
- 이더리움과 경쟁 중인 텐더민트를 합의알고리즘으로 사용하는 Monax나 Hyperledger 등 다른 Private 블록체인 플랫폼에서도 동작한다. 
- 정적입력과 지정 및 가변적인 반환 유형이 있다. 다른 EVM 타겟팅 언어와 비교할 때 Solidity는 임의의 계층적 매핑을 포함하는 계약을 지원하기 위한 복잡한 멤버 변수가 지원됐다. 또한 계약은 상속을 지원한다. (C3 linearization 다중상속 포함)
- 하나의 계약내에서 다중 타입의 함수가 가능함. **응용이진인터페이스(application binary interface ; ABI) **(추후 Serpent에 의해 지원됨)
- 메소드호출의 진행 상태에 대해서 사용자 중심으로 명세하기 위한 문서화 시스템과 관련된 내용이 Natural Language Specification로 제안서에 포함되었다.

- 역사(1): Gavin Wood, Christian Reitwiessner, Alex Beregszaszi, Liana Husikyan, Yoichi Hirai 와 이더리움 핵심 기여자들이 이더리움과 같은 블록체인 플랫폼 상에 스마트계약을 작성 할 수 있도록 개발했다.

- 역사(2): 솔리디티는 2014년 8월에 Gavin Wood 에 의해 처음으로 제안되었으며, 제안 이후 이더리움 프로젝트의 Christian Reitwiessner 가 이끄는 솔리디티팀에 의해 개발 되었다. 


**Solidity문서**. Join [soliditylang.org](https://docs.soliditylang.org/en/v0.8.17/) 


## Install

Native: (macOS x64 & Silicon, Linux x64, Windows Subsystem for Linux)

```sh
curl -fsSL https://bun.sh/install | bash
```

npm:

```sh
npm install -g bun
```

Homebrew: (MacOS and Linux)

```sh
brew tap oven-sh/bun
brew install bun
```

Docker: (Linux x64)

```sh
docker pull jarredsumner/bun:edge
docker run --rm --init --ulimit memlock=-1:-1 jarredsumner/bun:edge
```

If using Linux, kernel version 5.6 or higher is strongly recommended, but the minimum is 5.1.

## Upgrade

To upgrade to the latest version of Bun, run:

```sh
bun upgrade
```

Bun automatically releases a canary build on every commit to `main`. To upgrade to the latest canary build, run:

```sh
bun upgrade --canary
```

[View canary build](https://github.com/oven-sh/bun/releases/tag/canary)

<sup>Canary builds are released without automated tests</sup>

## Table of Contents

- [Install](#install)
- [Using bun.js - a new JavaScript runtime environment](#using-bunjs---a-new-javascript-runtime-environment)
  - [Types for bun.js (editor autocomplete)](#types-for-bunjs-editor-autocomplete)
  - [Fast paths for Web APIs](#fast-paths-for-web-apis)
- [Using bun as a package manager](#using-bun-as-a-package-manager)
- [Using bun as a task runner](#using-bun-as-a-task-runner)
- [Creating a Discord bot with Bun](#creating-a-discord-bot-with-bun)
  - [Application Commands](#application-commands)
- [Using bun with Next.js](#using-bun-with-nextjs)
- [Using bun with single page apps](#using-bun-with-single-page-apps)
  - [Using bun with Create React App](#using-bun-with-create-react-app)
- [Using bun with TypeScript](#using-bun-with-typescript)
  - [Transpiling TypeScript with Bun](#transpiling-typescript-with-bun)
  - [Adding Type Definitions](#adding-type-definitions)
- [Not implemented yet](#not-implemented-yet)
  - [Limitations & intended usage](#limitations--intended-usage)
  - [Upcoming breaking changes](#upcoming-breaking-changes)
- [Configuration](#configuration)
  - [bunfig.toml](#bunfigtoml)
  - [Loaders](#loaders)
  - [CSS in JS](#css-in-js-bun-dev-only)
    - [When `platform` is `browser`](#when-platform-is-browser)
    - [When `platform` is `bun`](#when-platform-is-bun)
  - [CSS Loader](#css-loader)
  - [CSS runtime](#css-runtime)
  - [Frameworks](#frameworks)
- [Troubleshooting](#troubleshooting)
  - [bun not running on an M1 (or Apple Silicon)](#bun-not-running-on-an-m1-or-apple-silicon)
  - [error: Unexpected](#error-unexpected)
  - [bun install is stuck](#bun-install-is-stuck)
  - [Unzip is required](#unzip-is-required)
    - [Debian / Ubuntu / Mint](#debian--ubuntu--mint)
    - [RedHat / CentOS / Fedora](#redhat--centos--fedora)
    - [아치 / 만자로](#arch--manjaro)
    -[오픈수세](#opensuse)
-[참조](#참조)
  -[`번 설치`](#bun-install)
    -[`bunfig.toml`을 사용하여 롤빵 설치 구성](#configuring-bun-install-with-bunfigtoml)
    -[환경 변수로 구성](#configuring-with-environment-variables)
    -[플랫폼별 종속성?](#플랫폼별 종속성)
    -[피어 종속성?](#peer-dependencies)
    -[잠금 파일](#잠금 파일)
    -[왜 바이너리입니까?](#왜 바이너리인가)
    -[어떻게 검사합니까?](#How-do-i-inspect-it)
    -[잠금 파일은 무엇을 저장합니까?](#what-does-the-lockfile-store)
    -[왜 빠릅니까?](#why-is-it-fast)
    -[은닉처](#은닉처)
    -[npm 레지스트리 메타데이터](#npm-레지스트리-메타데이터)
  -['번 런'](#분런)
  -['번 만들기'](#bun-create)
    -[용법](#용법)
    -[로컬 템플릿](#로컬 템플릿)
    -[플래그](#플래그)
    -[새 템플릿 게시](#publishing-a-new-template)
    -[새 템플릿 테스트](#testing-your-new-template)
    -[구성](#config)
    -[`bun create` 작동 방식](#분류 생성 작동 방식)
  -['번 초기화'](#분초기화)
  -['빵빵'](#분분)
    -[왜 번들인가요?](#왜 번들)
    -[`.bun`은 무엇입니까?](#What-is-bun)
    -[위치 독립적 코드](#위치 독립적 코드)
    -[코드는 어디에 있습니까?](#코드는 어디에 있습니까)
    -[고급의](#고급의)
    -[모듈 ID 해시는 무엇입니까?](#what-is-the-module-id-hash)
  -['번 업그레이드'](#분업그레이드)
  -['빵완성'](#번 완성)
-[`Bun.serve` - 빠른 HTTP 서버](#bunserve---빠른-http-서버)
  -[용법](#사용법-1)
  -[HTTPS](#https-with-bunserve)
  -[웹소켓](#websockets-with-bunserve)
  -[오류 처리](#오류 처리)
-[`Bun.write` – I/O 최적화](#bunwrite--최적화-io)
-[`Bun.spawn` - 스폰 프로세스](#bunspawn--spawn-a-process)
-[`Bun.which` - 빈 경로 찾기](#bunwhich--binary에 대한 경로 찾기)
-[bun:sqlite(SQLite3 모듈)](#bunsqlite-sqlite3-모듈)
  -[bun:sqlite 벤치마크](#bunsqlite-벤치마크)
  -[bun:sqlite 시작하기](#getting-started-with-bunsqlite)
  -['데이터베이스'](#데이터 베이스)
    -[데이터베이스.프로토타입.쿼리](#databaseprototypequery)
    -[데이터베이스.프로토타입.준비](#databaseprototypeprepare)
    -[Database.prototype.exec 및 Database.prototype.run](#databaseprototypeexec--databaseprototyperun)
    -[데이터베이스.프로토타입.직렬화](#databaseprototypeserialize)
    -[Database.prototype.loadExtension](#databaseprototypeloadextension)
  -[성명](#성명)
    -[진술.모두](#statementall)
    -[문.값](#문 값)
    -[성명서.get](#statementget)
    -[문.실행](#statementrun)
    -[진술.완성](#statementfinalize)
    -[문.toString()](#statementtostring)
  -[데이터 유형](#데이터 유형)
-[`bun:ffi` (외부 함수 인터페이스)](#bunffi-외국 함수-인터페이스)
  -[낮은 오버헤드 FFI](#low-overhead-ffi)
  -[용법](#사용법-2)
  -[지원되는 FFI 유형('FFIType')](#supported-ffi-types-ffitype)
  -[문자열(`CString`)](#문자열-cstring)
    -[문자열 반환](#returning-a-string)
  -[함수 포인터(`CFunction`)](#function-pointers-CFunction)
  -[포인터](#포인터)
    -[포인터 전달](#포인터 전달)
    -[포인터 읽기](#reading-pointers)
    -[아직 구현되지 않음](#아직 구현되지 않음-1)
-[노드-API(napi)](#node-api-napi)
-[`번.트랜스파일러`](#buntranspiler)
  -[`Bun.Transpiler.transformSync`](#buntranspilertransformsync)
  -[`Bun.Transpiler.transform`](#buntranspilertransform)
  -[`Bun.Transpiler.scan`](#buntranspilerscan)
  -[`Bun.Transpiler.scanImports`](#buntranspilerscanimports)
-[`Bun.peek` - 동일한 틱 약속 읽기](#bunpeek---해결하지 않고 약속 읽기)
-[`Bun.dns` - 도메인 조회](#bundns---도메인 조회)
-[Bun의 모듈 해상도](#module-resolution-in-bun)
-[환경 변수](#환경 변수)
-[학점](#학점)
-[특허](#특허)
-[롤빵 개발](#현상판)
  -[개발자 컨테이너(Linux/Windows)](#dev-container-linuxwindows)
  -[맥 OS](#맥 OS)
    -[빌드 롤빵(macOS)](#build-bun-macos)
    -[작동하는지 확인(macOS)](#verify-it-worked-macos)
    -[문제 해결(macOS)](#문제 해결-macos)
  -[문제 해결(일반)](#문제 해결-일반)
-[vscode-지그](#vscode-zig)

## 새로운 JavaScript 런타임 환경인 bun.js 사용

bun.js는 성능, 개발자 경험 및 JavaScript 생태계와의 호환성에 중점을 둡니다.

```ts
//http.ts
내보내다 기본{
  포트:3000,
  술책(요구: 요구) {
    반품 새로운 응답("헬로 월드");
  },
};
//번 ./http.ts
```

| 초당 요청 | OS | CPU | 롤빵 버전 |
| -------------------------------------------------- -------------------- | ----- | --------------------------------------------- | ----------- |
| [260,000](https://twitter.com/jarredsumner/status/1512040623200616449) | 맥OS | 애플 실리콘 M1 맥스 | 0.0.76 |
| [160,000](https://twitter.com/jarredsumner/status/1511988933587976192) | 리눅스 | AMD Ryzen 5 3600 6코어 2.2ghz | 0.0.76 |

<상세>
<summary>다음을 실행하여 <a target="_blank" href="https://github.com/uNetworking/uSockets/blob/master/examples/http_load_test.c">http_load_test</a></summary>로 측정했습니다.

```강타
./http_load_test 20 127.0.0.1 3000
```

</세부 사항>

bun.js는 가능한 경우 새 API를 설계하는 대신 웹 API 호환성을 선호합니다. bun.js는 일부 Node.js API도 구현합니다.

-TypeScript 및 JSX 지원이 내장되어 있으며 Bun의 JavaScript 트랜스파일러로 구동됩니다.
-ESM 및 CommonJS 모듈 지원(내부적으로 bun.js는 ESM을 사용함)
-많은 npm 패키지가 bun.js와 "그냥 작동"합니다(노드 API를 거의 사용하지 않거나 전혀 사용하지 않는 경우).
-tsconfig.json`"경로"`와 함께 기본적으로 지원됩니다.`"수출"`package.json에서
- `fs`,`경로`, 그리고`프로세스`노드에서 부분적으로 구현됨
-[와 같은 웹 API`가져오기`](https://developer.mozilla.org/en-US/docs/Web/API/fetch), [`응답`](https://developer.mozilla.org/en-US/docs/Web/API/Response), [`URL`](https://developer.mozilla.org/en-US/docs/Web/API/URL) 등이 내장되어 있습니다.
-[`HTML리라이터`](https://developers.cloudflare.com/workers/runtime-apis/html-rewriter/)를 사용하면 bun.js에서 HTML을 쉽게 변환할 수 있습니다.
-시작 [노드보다 4배 빠름](https://twitter.com/jarredsumner/status/1499225725492076544) (직접 해보세요)
- `.env`파일이 자동으로 로드됨`process.env`그리고`번.env`
-최고 수준의 대기

런타임은 WebKit 및 Safari를 지원하는 JavaScript 엔진인 JavaScriptCore를 사용합니다. [와 같은 일부 웹 API'헤더'](https://developer.mozilla.org/en-US/docs/Web/API/Headers) 및 [`URL`](https://developer.mozilla.org/en-US/docs/Web/API/URL)에서 [사파리의 구현](https://github.com/oven-sh/bun/blob/HEAD/src/bun.js/bindings/webcore/JSFetchHeaders.cpp).

`고양이`실행하는 클론 [GNU cat보다 2배 빠름](https://twitter.com/jarredsumner/status/1511707890708586496) - Linux의 대용량 파일

```js
//cat.js
수입{해결하다}~에서 "길";
수입{쓰다,표준출력,파일,인수}~에서 "혈액 요소 질소";
const 길 = 해결하다(인수.~에(-1));
기다리다 쓰다(
  //stdout은 Blob입니다.
  표준 출력,
  //파일(경로)은 Blob을 반환합니다 - https://developer.mozilla.org/en-US/docs/Web/API/Blob
  파일(길),
);
//롤빵 ./cat.js ./path-to-file
```

표준 입력에서 라인 읽기:

```ts
//Bun v0.3.0부터 콘솔은 AsyncIterable입니다.
~을 위한 기다리다(const라인~의 콘솔) {
  //stdin의 텍스트 줄
  콘솔.통나무(라인);
}
```

서버 측 렌더링 반응:

```js
수입{renderToReadableStream}~에서 "react-dom/서버";
const dt = 새로운 Intl.DateTimeFormat();
내보내다 기본{
  포트: 3000,
  비동기 술책(요구: 요구) {
    반품 새로운 응답(
      기다리다 renderToReadableStream(
        <HTML>
          <머리>
            <제목>헬로 월드</제목>
          </머리>
          <신체>
            <h1>반응에서 안녕하세요!</h1>
            <피>날짜는 {dt.체재(새로운 날짜())}</피>
          </신체>
        </HTML>,
      ),
    );
  },
};
```

다음을 사용하여 stdout에 쓰기`콘솔.쓰기`:

```js
//후행 개행 없음
//문자열 및 유형이 지정된 배열과 함께 작동
콘솔.쓰다("안녕하세요 세계!");
```

[에 몇 가지 더 많은 예가 있습니다.예](./examples) 폴더.

더 많은 예제를 추가하는 PR은 매우 환영합니다!

### bun.js의 유형(편집기 자동 완성)

The best docs right now are the TypeScript types in the [`bun-types`](https://github.com/oven-sh/bun/tree/main/packages/bun-types) npm package. A docs site is coming soon.

To get autocomplete for bun.js types in your editor,

1. Install the `bun-types` npm package:

```bash
# yarn/npm/pnpm work too, "bun-types" is an ordinary npm package
bun add bun-types
```

2. Add this to your `tsconfig.json` or `jsconfig.json`:

```jsonc
{
  "compilerOptions": {
    "lib": ["ESNext"],
    "module": "esnext",
    "target": "esnext",
    "moduleResolution": "node",
    // "bun-types" is the important part
    "types": ["bun-types"]
  }
}
```

You can also [view the types here](https://github.com/oven-sh/bun/tree/main/packages/bun-types).

To contribute to the types, head over to [packages/bun-types](https://github.com/oven-sh/bun/tree/main/packages/bun-types).

### Fast paths for Web APIs

bun.js has fast paths for common use cases that make Web APIs live up to the performance demands of servers and CLIs.

`Bun.file(path)` returns a [`Blob`](https://developer.mozilla.org/en-US/docs/Web/API/Blob) that represents a lazily-loaded file.

When you pass a file blob to `Bun.write`, Bun automatically uses a faster system call:

```js
const blob = Bun.file("input.txt");
await Bun.write("output.txt", blob);
```

On Linux, this uses the [`copy_file_range`](https://man7.org/linux/man-pages/man2/copy_file_range.2.html) syscall and on macOS, this becomes `clonefile` (or [`fcopyfile`](https://developer.apple.com/library/archive/documentation/System/Conceptual/ManPages_iPhoneOS/man3/copyfile.3.html)).

`Bun.write` also supports [`Response`](https://developer.mozilla.org/en-US/docs/Web/API/Response) objects. It automatically converts to a [`Blob`](https://developer.mozilla.org/en-US/docs/Web/API/Blob).

```js
// Eventually, this will stream the response to disk but today it buffers
await Bun.write("index.html", await fetch("https://example.com"));
```

## Using bun as a package manager

On Linux, `bun install` tends to install packages 20x - 100x faster than `npm install`. On macOS, it’s more like 4x - 80x.

<img src="https://user-images.githubusercontent.com/709451/147004342-571b6123-17a9-49a2-8bfd-dcfc5204047e.png" height="200" />

To install packages from package.json:

```bash
bun install
```

To add or remove packages from package.json:

```bash
bun remove react
bun add preact
```

<details> <summary><strong>For Linux users</strong>: <code>bun install</code> needs Linux Kernel 5.6 or higher to work well</summary>

The minimum Linux Kernel version is 5.1. If you're on Linux kernel 5.1 - 5.5, `bun install` should still work, but HTTP requests will be slow due to a lack of support for io_uring's `connect()` operation.
