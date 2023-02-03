# Fastcampus_Solidity

# Solidity 기초 문법 실습 자료 

강의는 최신 v0.8.17기준이나, 계속 업데이트 되는 특성에따라 <br>
pragma solidity >=0.7.0 < 0.9.0;

<p align="center">
  <a href="https://discord.gg/pFuCJcnX" target="_blank"><img src="https://ocamlpro.com/fr/blog/assets/img/logo_solidity_title.png" alt="Logo" height=170></a>
  <br />
  <br />
  <a href="https://discord.gg/pFuCJcnX" target="_blank"><img height=20 src="https://img.shields.io/discord/876711213126520882" /></a>
</p>

## 솔리디티 문법 기초 커리큘럼 
- 변수와 자료, 연산자와 상수
- 가시성 지정자
- 모디파이어
- 함수와 참조타입
- 함수와 변수
- 함수와 가시성 지정자
- 조건문의 구조
- 반복문과 응용
- 매핑
- 배열
- 구조체
- 참조타입의 데이터 저장영역

# 솔리디티 특징 
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


**Solidity문서**. [soliditylang.org](https://docs.soliditylang.org/en/v0.8.17/) 

## 리믹스IDE 사용해서 실습
지원 매체: 웹,앱,데스크톱, VSCode확장 제공 <br>

<li> online https://remix.ethereum.org/ </li>
<li> online
https://ethereum.github.io/browser-solidity/</li>
<li> offline
https://github.com/ethereum/remix-ide </li>

## Install

크롬, 엣지, 사파리 등 다양한 브라우저 '리믹스'접속 가능 <br>
<strong> 강의는 크롬 사용 / 맥OS </strong>


## nvm을 이용하여 node.js 설치하기

nvm 이란?<br>
nvm은 nodejs version manager로 시스템에 여러 개의 nodejs 를 설치하고, 사용할 버전을 쉽게 전환할 수 있도록 도와주는 shell script이다. rvm(Ruby Version Manager)와 비슷한 역할을 수행한다고 생각하면 됨

NVM 설치하기  https://nodejs.org/ko/download/

home brew설치하기(Homebrew: (MacOS and Linux)https://brew.sh/index_ko
```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
homebrew를 설치했으면, brew 명령어를 사용할 수 있다. 
만약 command not found: brew 와 같은 오류가 발생한다면, 환경변수에 brew가 설치된 경로를 추가해준다.

brew를 이용하여 nvm을 설치해보자
```sh
$ vim ~/.zshenv
```

```sh
# HOMEBREW
export PATH="/opt/homebrew/bin:$PATH"
```

```sh
$ brew update
$ brew install nvm
```
nvm 환경변수 설정
```sh
$ vim ~/.zshenv
```

```sh
export NVM_DIR="$HOME/.nvm"
[ -s "/opt/homebrew/opt/nvm/nvm.sh" ] && \. "/opt/homebrew/opt/nvm/nvm.sh"  # This loads nvm
[ -s "/opt/homebrew/opt/nvm/etc/bash_completion.d/nvm" ] && \. "/opt/homebrew/opt/nvm/etc/bash_completion.d/nvm"  # This loads nvm bash_completion
```
nvm 설치 확인
```sh
$ nvm -v
0.39.0
```

Node.js 설치하기  https://nodejs.org/ko/download/
ls-remote 명령어로 설치할 수 있는 node.js 버전을 확인할 수 있다.
```sh
$ nvm ls-remote
```
설치하고 싶은 node.js의 버전을 선택하여 install 명령어로 node.js를 설치할 수 있다.
```sh
$ nvm install 17.2.0
```
node 설치 확인
```sh
$ node --version
```
npm 설치 확인
```sh
$ npm --version
```

## Upgrade
Solidity의 가장 최신버전은 v0.8.18(23년 2월)
```sh
pragma solidity >=0.7.0 < 0.9.0; 
이렇게쓰면 0.7버전이상 0.9버전미만의 모든 버전 컴파일가능)

1) 업데이트 변경 사항 블로그: https://blog.soliditylang.org/2020/12/16/solidity-v0.8.0-release-announcement/
2) 업데이트 변경 사항 문서: https://docs.soliditylang.org/en/v0.8.18/080-breaking-changes.html

주요 변경 사항:
코드 생성기: 기본적으로 모든 산술이 검사됩니다. 이러한 검사는 를 사용하여 비활성화할 수 있습니다 unchecked { ... }.
코드 생성기: 길이가 잘못 인코딩된 저장소의 바이트 배열에 액세스하면 패닉이 발생합니다.
코드 생성기: 어설션 실패 시 잘못된 opcode 대신 revert오류 서명 및 오류 코드와 함께 사용합니다.Panic(uint256)
명령줄 인터페이스: JSON 필드 abi, devdoc및 는 이제 문자열 userdoc이 storage-layout아닌 하위 개체입니다.
명령줄 인터페이스: --old-reporter옵션을 제거합니다.
명령줄 인터페이스: 레거시 --ast-json옵션을 제거합니다. --ast-compact-json현재 옵션 만 지원됩니다.
일반: 기본적으로 ABI 코더 v2를 활성화합니다.
일반: 전역 함수 log0, log1, log2및 log3을 제거 log4합니다.
파서: 지수화는 올바른 결합입니다. a**b**c로 파싱됩니다 a**(b**c).
스캐너: , 및 이스케이프 시퀀스에 대한 지원을 \b제거 \f합니다 \v.
표준 JSON: legacyAST옵션을 제거합니다.
타입 검사기: 함수 호출 옵션은 한 번만 주어질 수 있습니다.
형식 시스템: 및 라는 이름 this의 선언 은 공용 함수 및 이벤트를 제외하고 허용되지 않습니다.super_
유형 시스템: 기능 msg.data에서 허용 receive()하지 않습니다.
유형 시스템: 금지 type(super).
유형 시스템: 256개 이상의 구성원이 있는 열거형을 허용하지 않습니다.
유형 시스템: 음수 리터럴 및 유형보다 큰 리터럴에서 명시적 변환을 허용하지 type(uint160).max않습니다 address.
유형 시스템: 유형을 허용하지 byte않습니다. 에 대한 별칭이었습니다 bytes1.
유형 시스템: 유형으로의 명시적 변환은 address항상 지불할 수 없는 유형을 반환합니다 address. 특히 , address(u)및 는 ( 여기서 , address(b)및 는 각각 유형 및 계약 유형 의 임의 변수입니다 .)address(c)address(this)addressaddress payableubcuint160bytes20
유형 시스템: 기호, 너비 또는 종류 중 둘 이상을 동시에 변경하는 경우 두 유형 간의 명시적 변환이 허용되지 않습니다.
형식 시스템: 리터럴에서 열거형으로의 명시적 변환은 값이 열거형에 맞는 경우에만 허용됩니다.
유형 시스템: 리터럴에서 정수 유형으로의 명시적 변환은 암시적 변환만큼 엄격합니다.
유형 시스템: address(...).code코드를 bytes memory. 크기는 를 통해 얻을 수 address(...).code.length있지만 현재는 항상 코드 복사가 포함됩니다.
Type System: block.chainid현재 체인 ID를 검색하기 위해 도입합니다.
유형 시스템: address(...).codehash계정의 코드해시 검색을 지원합니다.
유형 시스템: 전역 변수 tx.origin에는 . 대신 msg.sender유형 이 있습니다.addressaddress payable
유형 시스템: 단항 부정은 부호 없는 정수가 아닌 부호 있는 정수에서만 사용할 수 있습니다.
Pure Checker 보기: chainid보기로 표시합니다.
Yul: 지정된 방언/EVM 버전에서 사용할 수 없는 경우에도 EVM 명령어와 같은 예약된 식별자의 사용을 허용하지 않습니다.
Yul: assignimmutable"EVM with objects" 방언의 내장 기능은 추가 인수로 수정할 코드의 기본 오프셋을 사용합니다.
언어 기능:
슈퍼 생성자는 이제 멤버 표기법(예: )을 사용하여 호출할 수 있습니다 M.C(123).
버그 수정:
유형 검사기: 배열 길이 표현식에서 상수를 사용할 때 적절한 절단 정수 산술을 수행합니다.
AST 변경 사항:
많은 IdentifierPath곳에서 UserDefinedTypeName.
. _ UncheckedBlock_unchecked { ... }



