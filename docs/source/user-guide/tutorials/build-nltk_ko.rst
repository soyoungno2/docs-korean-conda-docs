=================================
NLTK를 위한 콘다 패키지 빌드
=================================

자연여 처리 도구(NLTK)는 인간 언어 데이터에 통계적 자연어 처리(NLP)를 적용하는 파이썬 프로그램을 빌드하는데 사용되는 플랫폼이다.
설치가 어려울 수 있지만 이 절에서 다룰 NLTK 콘다 패키지를 빌드하면 쉽게 할 수 있을 것이다.

이 패키지는 약 8GB의 NLTK 데이터셋도 포함한다.

https://gist.github.com/danielfrg/d17ffffe0dc8ed56712a0470169ff546 에 있는 파일들을 받는다.
(우측 상단에 있는 Download ZIP 버튼을 클릭한다.)

내려받은 파일의 압축을 풀고 디렉토리 이름을 ``/nltk-with-data/``\ 로 바꾼다.

콘다 빌드(conda build)가 없다면 설치한다. ::

    conda install conda-build

``cd``\ 로 nltk-with-data 보다 하나 위의 디렉토리로 이동하다.

필요한 파이썬 버전 마다 콘다 빌드를 실행해 명령을 실행하는 플랫폼과 운영체제에 맞는 패키지를 선택한다.

.. code-block:: python

    conda build nltk-with-data --python 2.7
    conda build nltk-with-data --python 3.4
    conda build nltk-with-data --python 3.5
    conda build nltk-with-data --python 3.6

위 명령으로 빌드된 콘다 패키지는 $CONDA_ROOT/conda-bld/$ARCH/nltk-with-data.tar.bz2에 위치한다.
$CONDA_ROOT는 아나콘다 설치의 루트가 되고 $ARCH는 패키지를 빌드한 아키텍처가 된다.

콘다 패키지를 로컬 레포지토리에 업로드하거나 아나콘다 클라이언트 CLI의
`아나콘다 노트북 확장 <https://docs.continuum.io/anaconda/jupyter-notebook-extensions>`_\ 을 사용해
`아나콘다 클라우드 <https://anaconda.org>`_\ 에 업로드한다.

.. code-block:: bash

    anaconda upload $CONDA_ROOT/conda-bld/$ARCH/nltk-with-data.tar.bz2
    anaconda upload $CONDA_ROOT/conda-bld/$ARCH/nltk-with-data.tar.bz2
    anaconda upload $CONDA_ROOT/conda-bld/$ARCH/nltk-with-data.tar.bz2
    anaconda upload $CONDA_ROOT/conda-bld/$ARCH/nltk-with-data.tar.bz2

선택: 윈도우, 맥OS, 리눅스와 같은 다른 플랫폼에서 위의 단계를 반복하면 그 플랫폼을 위한 콘다 패키지를 빌드할 수 있다.
순수 파이썬 패키지라면 ``conda convert``\ 를 사용할 수도 있다.
새로운 버전의 NLTK가 배포되면 래시피를 업데이트하고 위 작업을 반복해도 된다.

콘다로 설치하기
==================

.. code-block:: bash

    conda install nltk-with-data
    ipython

.. code-block:: python

    import nltk.corpus
    nltk.corpus.treebank

이 콘다 패키지로 데이터를 가져올 수 있을 것이다.

콘다가 패키지를 설치하면 모든 데이터셋과 라이브러리를 평소와 같이 사용한다.

`NLTK 문서 <http://www.nltk.org/>`_\ 를 참고한다.
