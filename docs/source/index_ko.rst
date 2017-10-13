.. 콘다 문서 마스터 파일
   Sat Nov  3 16:08:12 2012 에 sphinx-quickstart 로 생성.
   이 파일을 사용자의 선호에 따라 수정해도 되지만 최소한 루트 `toctree` 명령어는 포함해야 한다.

.. =====
.. 콘다
.. =====

.. figure::  images/conda_logo.svg
   :align:   center

**패키지, 하위 요소, 환경 관리를 어떤 언어에서도:Python, R, Scala, Java, Javascript, C/ C++, FORTRAN**

콘다는 오픈소스 패키지 관리 시스템과 환경 관리 시스템으로 여러 버전의 패키지와 구성요소들을 설치하거나 설치된 환경간의 전환을 가능하게 한다.
리눅스, OS X, 윈도우에서 작동하고 파이썬 프로그램을 위해 제작되었지만 어떤 소프트웨어도 가능하다.

콘다는 아나콘다와 미니콘다에 포함되어 있다. Continuum 아나콘다 `서브스크립션 <https://www.continuum.io/anaconda-subscriptions>`_\ 에도 포함된다.
아나콘다 서브스키립션에는 파이썬, R, Node.js, 자바, 그 외 다른 어플리케이션을 위한 기업용 실무 패키지와 환경 관리 도구가 포함된다.
pypi를 통해서도 콘다를 사용할 수도 있지만 이 경우에는 최신 버전이 아닐 수 있다.

**미니콘다**\ 는 콘다, 파이썬 그리고 이들이 의존하는 패키지들을 포함하는 초간단 버전이다.
conda install 커맨드를 사용해 720 여개의 과학 연구용 패키지와 그 하위 요소들을 Continuum 저장소로부터 개별적으로 설치할 수 있다.

**아나콘다**\ 는 콘다, 콘다 빌드, 파이썬 및 150 여개의 자동 설치되는 과학 연구용 패키지와 구성요소를 포함한다.
미니콘다와 마찬가지로 conda install 커맨드를 사용해 250 여개의 추가적인 과학 연구용 패키지를 설치할 수 있다.

`conda`\ 는 `아나콘다 <http://docs.continuum.io/anaconda/index.html>`_ 설치를 관리하기 위한 명령어다.
아나콘다 패키지 인덱스와 현재 아나콘다 설치 상황을 검색할 수 있고 새로운 환경을 생성하거나 기존 환경에 패키지를 추가 설치 또는 업데이트 할 수 있다.



.. toctree::
   :hidden:

   get-started_ko
   using/index_ko
   building/build_ko
   help/help_ko
   get-involved_ko

프레젠테이션 & 블로그 포스트
----------------------------------

`콘다로 패키지화 하고 배포하기 - Travis Oliphant <https://speakerdeck.com/teoliphant/packaging-and-deployment-with-conda>`_

`아나콘다의 파이썬 3 지원 - Ilan Schnell <https://www.continuum.io/content/python-3-support-anaconda>`_

`콘다 진전 사항 - Ilan Schnell <https://www.continuum.io/blog/developer/new-advances-conda>`_

`콘다의 파이선 패키지와 환경 - Bryan Van de Ven <https://www.continuum.io/content/python-packages-and-environments-conda>`_

`콘다 고급 기능, 파트 1 - Aaron Meurer <https://www.continuum.io/blog/developer/advanced-features-conda-part-1>`_

`콘다 고급 기능, 파트 2 - Aaron Meurer <https://www.continuum.io/blog/developer/advanced-features-conda-part-2>`_

요구사항
------------

* 파이썬 2.7, 3.4, 3.5, or 3.6
* pycosat
* pyyaml
* requests
