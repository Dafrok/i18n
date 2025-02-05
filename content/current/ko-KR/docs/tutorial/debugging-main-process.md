# 메인 프로세스 디버깅하기

Electron 브라우저 창의 개발자 도구는 윈도우(i.e 웹 페이지) 같은 창에서 실행된 스크립트만 디버깅이 가능합니다. 메인 프로세스에서 실행된 자바스크립트를 디버깅 하기 위해 외부 디버거가 필요하며, Electron 실행시 `--debug` 또는 `--debug-brk` 스위치가 필요합니다.

## 커맨드 라인 스위치(command line switches)

다음 커맨드 라인 스위치들을 사용하여 메인 프로세스를 디버깅 할 수 있습니다:

### `--inspect=[port]`

Electron will listen for V8 inspector protocol messages on the specified `port`, an external debugger will need to connect on this port. The default `port` is `5858`.

```shell
electron --inspect=5858 your/app
```

### `--inspect-brk=[port]`

`--inspect`와 같지만 Javascript 첫번째 line에서 실행을 중단합니다.

## 외부 디버거

V8 디버거 프로토콜을 지원하는 디버거가 필요합니다. 다음 가이드들이 도움이 됩니다:

- 크롬의 `chrome://inspect` 를 방문하고, 현재의  거기에 있는  Electron app 을 찾아보고 선정하여 설치하기
- [Debugging in VSCode](debugging-vscode.md)
