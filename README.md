
## uv Workspace Example
[uv github](https://github.com/astral-sh/uv)

[uv documentation](https://docs.astral.sh/uv/)

uv에서 workspace로 사용하려고 할 때

documentation을 봐도 이해가 안 가고, 
poetry같은 packaging library에 익숙하지 않은 나같은 사람들을 위한 예제.

### build command

``` powershell
uv init --lib uv-workspace
cd uv-workspace
mkdir packages
cd .\packages\

uv init --lib workspace-getter
uv init --lib workspace-setter

#if need, add optional dependencies at each packages
uv add workspace-getter
uv add workspace-setter
uv sync
```

uv add할 때, 파일 복사에 따른 Warning 뜨지만 따로 package build 하는게 아니라 workspace 단계에서는 큰 부작용 없이 돌아가는듯.

uv의 장점으로, uv sync만 해도 .venv가 자동으로 설치된다.
위의 명령어로 했을 때, main의 src/import_test.py를 실행하면, 다음과 같은 결과가 나온다 (import 성공)

```
Hello from workspace-getter!
Hello from workspace-setter!
```

packages 경로는 마음대로 해도 되지만(./packages 뿐 아니라), src등 build 구조는 정형화 되어있는 듯.

uv 엄청 빠르고 좋아요 많이 쓰세요.