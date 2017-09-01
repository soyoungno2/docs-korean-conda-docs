# 콘다 문서


이 저장소는 콘다에 대한 모든 문서를 포함한다. 콘다 빌드 문서도 포함한다.

웹사이트는 https://conda.io/ 이고 문서들은 https://conda.io/docs/ 에서 볼 수 있다.

이 저장소에 수정을 제안하기 위해 자유롭게 pull request 하기 바란다.
오타수정부터 리펙터링까지 모든 수정을 환영한다.

## 웹사이트

다음 커맨드를 입력한다.

    conda create -n conda-website -c asmeurer sphinxjp.themes.basicstrap cloud_sptheme

아래와 같이 입력해 웹사이트를 빌드한다.

    source activate conda-website
    cd web
    make html

결과는 web/build/html 경로에 저장된다.

링크가 유효한지 확인하려면 다음 커맨드를 사용한다.

    make linkcheck

## 문서

문서는 여러 하위 요소를 갖는다. 다음 커맨드로 하위 요소를 모두 설치할 수 있다.

    conda create -n conda-docs python=3 sphinx sphinx_rtd_theme numpydoc
    source activate conda-docs
    conda install -c asmeurer help2man man2html

추가로 콘다 빌드가 설치되어 있어야 콘다 빌드 커맨드의 도움말 페이지를 만들 수 있다.

    conda install -n root conda-build pycrypto

다음을 실행한다.

    source activate conda-docs
    cd docs
    make html

결과는 docs/build/html 에 저장된다.

커맨드 문서 생성을 생략해 더 빠르게 진행하려면 다음을 입력한다.

    make just-html

## 배포

마스터가 커밋을 푸시하면 웹사이트와 문서는 GitHub 페이지에 Travis CI로 자동 배포된다.
Travis 는 풀 리퀘스트 상의 문서들을 빌드하고 빌드 경고나 에러가 없는지 확인한다.
Travis 는 마스터에게만 배포한다.

https://conda.io 에서 현 저장소의 GitHub 페이지로 갈 수 있다.