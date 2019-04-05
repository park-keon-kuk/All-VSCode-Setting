# python

python을 통한 개발 때 사용했던 설정입니다.


## 가상 환경 설정

python 가상환경입니다. 프로젝트별 python 패키지를 갖는 것이 배포나 관리에 있어서 편리합니다.
다음 속성 값을 통해 프로젝트에서 사용하는 가상환경을 설정합니다.

```json
    "python.pythonPath": "env\\Scripts\\python.exe",
```


## linting

python 소스 코드에서 문제가 있을 경우 이를 찾아 경고 또는 오류를 보고해 줍니다.
아래의 설정을 통해 활성화해줍니다. 기본은 pylint를 사용합니다.
그리고 linting은 저장시에만 확인하며 최대 100개까지만 보고하도록 합니다.

```json
    "python.linting.enabled": true,
    "python.linting.lintOnSave": true,
    "python.linting.maxNumberOfProblems": 100,
```


사용한 프로그램은 PyLint와 Flake8 입니다.
PyLint는 기본값이 true이지만 명시적으로 표현합니다.

```json
    "python.linting.pylintEnabled": true,
    "python.linting.flake8Enabled": true,
```


원하지 않은 경고를 표현할 경우 파라미터를 통해 설정해 줄 수 있습니다.
설정 방식은 linting 프로그램 별로 다릅니다.

```json
    "python.linting.pylintArgs": [
        "--disable=no-member", // 이런 맴버는 없는데?
        "--disable=missing-docstring", // 설명문이 빠지지 않았냐?
        "--disable=invalid-name", // 상수를 왜 대문자로 쓰지 않냐?
        "--disable=unused-import", // 안 쓰는데 왜 import 하냐?
        "--disable=wrong-import-position", // import 위치 왜 그러냐?
        "--disable=no-name-in-module", // 그런 이름 모듈에 없는데?
        "--disable=import-error", // import 할 수 없는데?
    ],

    "python.linting.flake8Args": [
        "--ignore=F401", // 안 쓰는데 왜 import 하냐?
    ],
```

## format

python 소스 코드를 가독성이 좋도록 공백, 줄 바꾸기를 조정해줍니다.
사용한 프로그램으로는 autopep8를 사용합니다.

```json
    "python.formatting.provider": "autopep8",
```


위의 설정 후 python 파일에 대한 editor 설정을 해주어야 format이 작동합니다.
파일을 저장할 때 자동으로 format을 실행시킵니다.

```json
    "[python]": {
        "editor.formatOnSave": true,
        "editor.formatOnType": false,
        "editor.formatOnSaveTimeout": 750,
    },
```


혹, 컴퓨터가 좋지 않을 경우 format 하는데 충분한 시간을 주지 않으면 
format을 못 할 수 있습니다. 위의 formatOnSAveTimeout 설정 값을 높여줍니다.

```json
    "[python]": {
        "editor.formatOnSave": true,
        "editor.formatOnType": false,
        "editor.formatOnSaveTimeout": 5000,
    },
```


## 작업 중 불필요한 파일/폴더 탐색기에서 노출하지 않기

python 개발 중 \_\_pycache\_\_/ 폴더 등 캐시 폴더가 만들어 지는데
아래의 설정을 통해 탐색기에서 보이지 않도록 할 수 있습니다. 
필요하다면 가상환경(env/)도 보이지 않게 할 수 있습니다.

```json
    "files.exclude": {
        "**/__pycache__": true, // python 캐시 폴더
        "**/env":true, // 내 python 가상환경
    }
```