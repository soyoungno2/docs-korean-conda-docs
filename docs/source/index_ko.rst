=====
콘다
=====

.. figure::  /img/conda_logo.svg
   :align: center
   :width: 50%

   ..

|

:emphasis:`파이썬, R, 루비, 루아, 스칼라, 자바, 자바스크립트, C/C++, FORTRAN 언어를 위한 패키지, 의존성 및 환경 관리 도구`


콘다(conda)는 윈도우, 맥OS, 리눅스에서 쓸 수 있는 오픈소스 패키지/환경 관리 시스템이다.
콘다는 패키지와 그 패키지의 의존 요소들을 빠르게 설치, 동작, 업데이트할 수 있다.
콘다를 사용하면 사용자의 로컬 컴퓨터에서 여러 환경을 생성, 저장, 로드하고 환경간의 전환을 쉽게 할 수 있다.
콘다는 파이썬으로 만들어졌지만 어떤 언어로 된 소프트웨어든 패키징하고 배포할 수 있다.

콘다는 사용자가 패키지를 찾고 설치하게 도와주는 패키지 관리자다.
만약 여러 버전의 파이썬이 필요한 패키지를 써야 할 때도 별도의 환경 관리자를 사용할 필요가 없다.
콘다가 환경 관리도 하기 때문이다.
몇 개의 명령만으로 보통 때 사용하는 파이썬 버전을 그대로 사용하면서 다른 버전의 파이썬이 돌아가는 완전히 별개의 환경을 만들 수 있다.

디폴트 설정에서는 콘다를 사용하여 아나콘다\ |reg|\ 사에서 관리하는 repo.continuum.io 로부터 이미 빌드된 수천개의 패키지를 설치하거나 관리할 수 있다.

콘다는 트래비스 CI(Travis CI)나 앱베이어(AppVeyor)와 같은 지속적 통합(CI) 시스템과 결합하여 빈번한 코드 테스팅을 자동화할 수 있다.

콘다 패키지/환경 관리자는 모든 버전의 :ref:`아나콘다 <anaconda-glossary>`\ |reg|,
:ref:`미니콘다 <miniconda-glossary>`, 그리고 `아나콘다 레포지토리 <https://docs.continuum.io/anaconda-repository/>`_\ 에 포함되어 있다.
콘다는 기업용 `아나콘다 엔터프라이즈 <https://www.anaconda.com/enterprise/>`_\ 에도 포함되어 있어 회사 내부에서 파이썬, R, Node.js, 자바 및 기타 어플리케이션 스택을 제공할 수 있다.
콘다를 PyPI에서 받을 수도 있지만 자주 업데이트되지는 않는다.


.. toctree::
   :hidden:
   :maxdepth: 1

   user-guide/index_ko
   help-support
   release-notes
   commands_ko
   glossary_ko
   license

.. |reg|    unicode:: U+000AE .. REGISTERED SIGN
