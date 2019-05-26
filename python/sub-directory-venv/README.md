# Sub Directory Virtual Environment

project/env/.. 같은 경우와 달리 가상환경이 하위 디렉터리에 있을 경우 project/server/env/ 는 자동ㅇ,로 Select Python Interpreter 명령으로 찾을 수가 없다. 그런 경우 설정파일과 같이 직접 path를 설정해주어야한다.

## 가상 환경

```json
"python.pythonPath": "server\\env\\Scripts\\python.exe",
```

## Linting

pylint 와 pep8 를 사용할 경우

```json
"python.linting.enabled": true,
"python.linting.lintOnSave": true,
"python.linting.pylintEnabled": true,
"python.linting.pylintPath": "server\\env\\Scripts\\pylint.exe",
"python.linting.pylintArgs": [
    "--disable=no-member", // 이런 맴버는 없는데?
    "--disable=missing-docstring", // 설명하는 문장이 빠졌는데?
    "--disable=invalid-name", // 상수를 왜 대문자로 쓰지 않냐?
    "--disable=unused-import", // 안 쓰는데 왜 import 하냐?
    // "--disable=wrong-import-position", // import 위치 왜 그러냐?
    "--disable=no-name-in-module", // 그런 이름은 모듈에 없는데?
    // "--disable=import-error", // import 할 수 없는데?
],
"python.linting.pep8Enabled": true,
"python.linting.pep8Path": "server\\env\\Scripts\\pep8.exe",
```

## Format

autopep8 를 사용할 경우

```json
"python.formatting.provider": "autopep8",
"python.formatting.autopep8Path": "server\\env\\Scripts\\autopep8.exe",
"[python]": {
    "editor.formatOnSave": true,
    "editor.formatOnSaveTimeout": 750,
}
```
