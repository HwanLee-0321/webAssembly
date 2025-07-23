# WebAssembly C to JavaScript 예제

이 프로젝트는 C 함수를 WebAssembly(Wasm)로 컴파일하고 JavaScript를 사용하여 웹 페이지 내에서 사용하는 방법을 보여주는 간단한 예제입니다.

[관련글](https://velog.io/@hwan_lee/%EC%96%B4%EC%85%88%EB%B8%94%EB%A6%AC%EB%A1%9C-%EC%9B%B9-%EB%A7%8C%EB%93%A4%EA%B8%B0)

## 📂 파일 설명

- `index.html`: WebAssembly 모듈의 결과를 로드하고 표시하는 기본 HTML 파일입니다.
- `add.c`: 두 정수를 더하는 간단한 `add` 함수를 포함하는 C 소스 코드입니다.
- `add.wasm`: `add.c`에서 생성된 컴파일된 WebAssembly 바이너리입니다.
- `add.js`: Emscripten에 의해 생성된 JavaScript "글루" 코드로, `add.wasm` 모듈을 쉽게 로드하고 상호 작용할 수 있게 해줍니다.

## 🚀 실행 방법

이 예제를 실행하려면 브라우저의 보안 정책(CORS)으로 인해 `.wasm` 파일을 가져오기 위해 로컬 웹 서버를 사용하여 파일을 제공해야 합니다.

1. **로컬 서버 시작:**
   Python이 설치되어 있다면 프로젝트의 루트 디렉토리에서 쉽게 서버를 시작할 수 있습니다.

   ```bash
   # Python 3의 경우
   python -m http.server

   # Python 2의 경우
   python -m SimpleHTTPServer
   ```

2. **브라우저에서 열기:**
   서버가 실행되면 웹 브라우저를 열고 `http://localhost:8000`으로 이동합니다.

WebAssembly를 통해 C 함수로 계산된 `40 + 2 = 42`의 결과를 볼 수 있습니다.

## 🛠️ 빌드 방법

`add.wasm` 및 `add.js` 파일은 [Emscripten SDK](https://emscripten.org/)를 사용하여 `add.c`에서 생성되었습니다.

Emscripten이 설치 및 구성되어 있다면 다음 명령으로 파일을 다시 빌드할 수 있습니다.

```bash
emcc add.c -o add.js
```

이 명령은 C 코드를 컴파일하고, WebAssembly 바이너리(`.wasm`)를 생성하며, 브라우저에서 실행하는 데 필요한 JavaScript 글루 코드(`.js`)를 만듭니다.
