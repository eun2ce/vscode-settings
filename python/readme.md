# python

## 개발환경 설정

- python 설치
- python project set up in vscode
- uv 가상환경 설치

### python 설치

#### [uv](https://github.com/astral-sh/uv) 설치

`uv`는 가상환경 생성, 패키지 설치, 의존성 관리까지 통합한 python 도구

```bash
$ curl -Ls https://astral.sh/uv/install.sh | sh
$ uv --version
```

#### 가상환경 생성

2. `uv`는 python이 시스템에 설치되어 있지 않아도 자동으로 필요한 버전을 다운로드하여 가상환경을 구성

```bash
$ mkdir project && cd project
$ uv venv -p 3.12
$ source .venv/bin/actiavate
```

### python project set up in vscode

#### vs-code에서 interpreter & linter 선택 & 설치

1. 생성한 `project` 폴더를 vscode 에서 연다.
2. `shift + command + p` --> `python : select interpreter` --> 생성한 가상환경 선택
3. `shift + command + p` --> `python : select linter` --> flake8 선택&설치
   - linter은 작성한 코드에 에러가 생길 부분을 미리 감지한다.
   - 해당 폴더에 `.vscode` 폴더가 생성된 것을 확인할 수 있다.

#### formatter-black

1. 코드를 보기 좋게 format

```bash
$ uv pip install back --dev
```

2. `.vscode`안에 `settings.json` 파일에 아래와 같은 내용 포함

```json
{
  "python.linting.pylintEnabled": false,
  "python.linting.flake8Enabled": true,
  "python.linting.enabled": true,
  "python.formatting.provider": "black",
  "python.linting.flake8Args": ["--max-line-length=88"]
}
```

### python project set up in pycharm

1. interpreter 설정 후 프로젝트 열기

2. `black formatter` 설정

```bash
$ uv pip install black
```

3. 아래와 같이 설정

   - `which black`으로 **black** 패키지의 경로를 체크하고 복사
   - Pycharm에서 `command + ,` (`ctrl + ,`) 단축키로 설정창 열고 `Tools` 탭에서 `File Watchers`에 들어가서 `+`버튼을 클릭한 후 `<custom>` template를 선택
   - `Program` -> `/Users/eun2ce/opt/anaconda3/bin/black`, `Arguments` -> `$FilePath$`, `Output paths to refresh` -> `$FilePath$`

4. prettier 설정
   1. `node`, `yarn` 설치
   2. `yarn global add prettier`으로 prettier 패키지 설치
   3. `which prettier`으로 prettier 패키지 경로 체크 후 복사
   4. pycharm에서 `command + ,` (`ctrl + ,`) 단축키로 설정창 열고 `Tools` 탭에서 `File Watchers`에 들어가서 `+`버튼을 클릭한 후 `<custom>` template를 선택
   5. 아래와 같이 설정
      - `/usr/local/bin/prettier`
      - `--write $FilePathRelativeToProjectRoot$`
      - `$FilePathRelativeToProjectRoot$`
      - `$ProjectFileDir$`
