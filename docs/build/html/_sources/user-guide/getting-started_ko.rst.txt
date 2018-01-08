================
시작 안내서
================

이 시작 안내서는 다음과 같은 연습들로 구성되며 30분이 소요된다.

* :ref:`콘다 관리 <managing-conda>`\ 에서는 아나콘다/미니콘다가 설치되었는지 확인하고
  :doc:`콘다 <../index_ko>`\ 가 최신 버전인지 체크한다. 3분이 걸린다.

* :ref:`환경 관리 <managing-envs>`\ 에서는 몇 개의 :ref:`환경 <concept-conda-env>`\ 을
  생성하고 환경을 전환하는 법을 배운다. 현재 활성화된 환경을 확인하고 백업을 위해 그 환경의 카피를 생성한다.
  10분이 걸린다.

* :ref:`파이썬 관리 <managing-python>`\ 에서는 설치 가능한 파이썬 버전을 확인한다.
  다른 버전의 파이썬을 설치하고 버전 간에 전환을 해본다. 4분이 걸린다.

* :ref:`패키지 관리<managing-pkgs>`\ 에서는 :ref:`패키지 <concept-conda-package>`\ 를 다룬다. 
  10분이 걸린다.

  * 사용자의 컴퓨터에 설치된 패키지를 나열한다.

  * 설치 가능한 패키지를 나열한다.

  * ``conda install`` 명령으로 패키지를 설치한다.

  * ``conda install`` 명령으로 설치할 수 없는 패키지는 `Anaconda.org <http://Anaconda.org>`_\ 를 검색한다.

  * 위의 두 방법을 모두 사용할 수 없는 패키지는 pip 패키지 관리자로 설치한다.
    아나콘다의 상용 패키지인 IOPro의 30일 체험판을 설치한다. 
    
  10분이 걸린다.

* :ref:`패키지, 환경, 콘다 삭제 <remove-pkgs-envs-conda>`\ 에서는 하나 이상의 테스트 패키지, 환경, 콘다를 삭제한다. 3분이 걸린다.

총 소요 시간: 30분

팁: 어떤 명령에 대한 전체 문서를 보려면 :doc:`명령줄 도움말 보기 <tasks/view-command-line-help>`\ 를 이용한다.



.. _managing-conda:

콘다 관리
===============

콘다 버전을 관리하려면 터미널이나 아나콘다 프롬프트에서 다음 단계를 따라 진행한다.

#. 콘다가 설치되었는지 확인한다.

   .. code::

      conda --version

   사용자가 설치한 콘다 버전이 나타난다.

   예시: ``conda 3.11.0``

   주의: 에러 메세지가 나타나면 현재 사용자 계정이 아나콘다/미니콘다가 설치된 계정인지 확인하고
   설치 후 터미널을 종료하고 다시 열었는지 확인한다.

#. 콘다를 최신 버전으로 업데이트한다.

   .. code::

      conda update conda

   각 패키지의 버전을 비교해 설치 가능한 콘다 버전을 보여준다.
   콘다 업데이트 시 자동으로 업데이트되거나 변경되는 패키지도 함께 나타난다.

#. 업데이트 가능한 콘다 버전이 있다면 ``y``\ 를 입력해 업데이트한다.

   .. code::

      Proceed ([y]/n)? y


.. _managing-envs:

환경 관리
=========================

복수의 환경을 생성하고 환경 간에 전환을 하려면 터미널이나 아나콘다 프롬프트에서 다음 단계를 따라 진행한다.

#. ``conda create`` 커맨드로 환경을 생성한다.

   .. code::

      conda create --name snowflakes biopython

   "snowflakes"라는 이름으로 환경이 생성되고 이 환경에 Biopython 프로그램이 설치된다.

   팁: 자주 사용하는 여러 옵션을 하나의 대시와 옵션의 첫글자로 축약할 수 있다.
   예를 들어, ``--name``\ 은 ``-n``\ 과 같고 ``--envs``\ 는 ``-e``\ 와 같다.
   ``conda --help``, ``conda -h`` 커맨드로 축약 목록을 볼 수 있다.

#. 운영체제에 맞는 커맨드를 실행해 생성된 환경을 활성화한다.

   * 리눅스, 맥OS: ``source activate snowflakes``
   * 윈도우:  ``activate snowflakes``

   팁: 기본으로 ``conda`` 디렉토리의 ``envs`` 디렉토리에 환경이 생성된다.
   다른 경로를 지정하고 싶다면 ``conda create --help``\ 를 참고한다.

   팁: 파이썬 버전을 지정하지 않았기 때문에 콘다를 다운로드, 설치할 때 사용한 버전과 같은
   버전의 파이썬을 설치한다.

#. 환경을 생성하고 다른 버전의 파이썬과 아스트로이드(Astroid), 바벨(Babel) 패키지를 설치한다.

   .. code::

      conda create --name bunnies python=3.5 astroid babel

   ``/envs`` 디렉토리에 "bunnies"라는 이름의 환경이 만들어지고 이 환경에
   파이썬 3, 아스트로이드, 바벨이 설치된다.

   팁: 환경에 설치하고자 하는 모든 프로그램을 한번에 설치한다.
   프로그램을 하나씩 설치하면 의존 요소 충돌이 일어날 수 있다.

   팁: ``conda create`` 커맨드에 더 많은 옵션을 추가할 수 있다.
   ``conda create --help``\ 에서 세부사항을 확인한다.
   
#. 지금까지 설치한 환경을 띄운다.

   .. code::

      conda info --envs

   다음과 비슷하게 환경 목록이 나타난다.

   .. code::

      conda environments:

          snowflakes   * /home/username/miniconda/envs/snowflakes
          bunnies        /home/username/miniconda/envs/bunnies
          root           /home/username/miniconda

   현재 활성화된 환경 앞에 별표(*)가 나타난다.

#. 현재 환경을 확인한다.

   .. code::

      conda info --envs

   모든 환경의 목록에 표시된다. 현재 환경의 이름은 프롬프트 앞의 (소괄호) 또는 [대괄호] 안에 나타난다.

   .. code::

      (snowflakes) $

#. 다른 환경으로 전환한다.

   * 리눅스, 맥OS: ``source activate bunnies``
   * 윈도우:  ``activate bunnies``

#. 현재 환경에서 루트 환경으로 되돌아간다.

   * 리눅스, 맥OS: ``source deactivate``
   * 윈도우:  ``deactivate``

   팁: 환경이 비활성화되면 그 환경의 이름은 더 이상 프롬프트에 나타나지 않는다.

#. "flowers"라는 이름으로 snowflakes 환경을 복사한 복사본을 만든다.

   .. code::

      conda create --name flowers --clone snowflakes

#. 복사본이 만들어졌는지 확인한다.

   .. code::

      conda info --envs

   flowers, bunnies, snowflakes 환경이 목록에 나타난다.

#. flowers 환경을 삭제한다.

   .. code::

      conda remove --name flowers --all

#. flowers 환경이 삭제되었는지 확인한다.

   .. code::

      conda info --envs

   flowers 환경이 목록에 나타나지 않으면 삭제된 것이다.


.. _managing-python:

파이썬 관리
====================

콘다는 파이썬을 다른 패키지와 똑같이 취급한다. 따라서 여러 버전의 파이썬을 쉽게 설치 관리하고 업데이트할 수 있다.

터미널이나 아나콘다 프롬프트에서 다음을 실행해 설치 가능한 파이썬 버전을 확인한다.

.. code::

   conda search --full-name python

``--full-name`` 옵션은 패키지의 전체 명칭이 정확히 "python"인 패키지만을 보여준다.
명칭에 "python"이 포함된 모든 패키지를 검색하고 싶다면 ``conda search python``\ 를 사용한다.

파이썬 2.7 환경을 덮어쓰지 않고 파이썬 3를 설치하려면 터미널이나 아나콘다 프롬프트에서 다음 단계를 따라 진행한다.

#. "snakes"라는 이름으로 환경을 생성하고 파이썬 3의 최신 버전을 설치한다.

   .. code::

      conda create --name snakes python=3

#. 생성된 환경을 활성화한다.

   * 리눅스, 맥OS: ``source activate snakes``
   * 윈도우:  ``activate snakes``

#. snakes 환경이 추가되었는지 확인한다.

   .. code::

      conda info --envs

   모든 환경이 목록에 나타난다. 현재 환경의 이름은 프롬프트 앞에 (소괄호)나 [대괄호] 안에 나타난다.

   .. code::

     (snakes) $

#. snakes 환경이 파이썬 3를 사용하는지 확인한다.

   .. code::

      python --version

#. 기본으로 설치된 파이썬 2.7 환경으로 돌아온다.

   * 리눅스, 맥OS: ``source activate snowflakes``
   * 윈도우:  ``activate snowflakes``

#. snowflakes 환경이 콘다를 설치할 때 사용한 것과 동일한 파이썬 버전을 사용하는지 확인한다.

   .. code::

      python --version

#. snowflakes 환경을 비활성화하고 경로를 이전 상태로 되돌린다.

   * 리눅스, 맥OS: ``source deactivate``
   * 윈도우: ``deactivate``


.. _managing-pkgs:

패키지 관리
======================

앞서 환경을 생성하면서 특정 버전의 파이썬과 아스트로이드, 바벨 패키지를 설치해 보았다.
이 절에서는 설치되어 있는 패키지와 설치 가능한 패키지를 확인하고 특정 패키지를 검색하여 설치해 본다.

우선 Anaconda.org 레포지토리에서 특정 패키지를 검색하고 
Anaconda.org 로부터 패키지를 설치한다.
``conda install`` 대신 ``pip`` 설치를 사용해 패키지를 더 설치해본다.
상용 패키지도 설치해본다.


패키지를 검색하려면 터미널이나 아나콘다 프롬프트에서 다음 단계를 따라 진행한다.

#. 패키지가 추가, 삭제되었는지 확인하기 위해 환경에 설치된 패키지와 버전 목록을 본다.

   .. code::

      conda list

#. ``conda install`` 커맨드로 설치 가능한 패키지 목록을 본다.
   각 파이썬 버전에 따른 패키지 목록은 http://docs.continuum.io/anaconda/pkg-docs.html\ 에서 볼 수 있다.

#. "beautifulsoup4" 패키지를 콘다로 설치할 수 있는지 확인한다.

   .. code::

      conda search beautifulsoup4

   패키지가 보이면 설치할 수 있다.

패키지를 설치하려면 터미널이나 아나콘다 프롬프트에서 다음 단계를 따라 진행한다.

#. beautifulsoup4를 현재 환경에 설치한다.

   .. code::

      conda install --name bunnies beautifulsoup4

   주의: ``--name bunnies``\ 와 같이 환경을 지정하지 않으면 현재 환경에 패키지가 설치된다.

#. bunnies 환경을 활성화한다.

   * 리눅스, 맥OS: ``source activate bunnies``
   * 윈도우:  ``activate bunnies``

#. 새로 설치된 프로그램을 나열한다.

   .. code::

      conda list


Anaconda.org에서 패키지를 받아서 설치하기
-----------------------------------------------------------------

``conda install``\ 로 설치할 수 없는 패키지는 Anaconda.org를 확인한다.
Anaconda.org는 공공/개인 패키지 레포지토리를 위한 패키지 관리 서비스로
아나콘다나 미니콘다와 같이 아나콘다사의 제품이다.

팁: Anaconda.org 에 등록하지 않아도 파일을 다운로드할 수 있다.

Anaconda.org에서 현재 환경으로 패키지를 다운로드하려면
원하는 패키지의 전체 URL을 입력해 Anaconda.org를 채널로 지정해야 한다.
이 URL는 다음과 같이 찾는다.

#. 브라우저에서 http://anaconda.org\ 로 들어간다.

#. "bottleneck" 패키지를 검색한다.

   #. 화면 좌측 상단의 Search Anaconda Cloud 박스에 ``bottleneck``\ 을 입력한다.

   #. Search 버튼을 누른다.

   Anaconda.org 에서 설치 가능한 bottleneck 패키지 카피는 십여개가 있지만
   가장 많이 다운로드 된 카피를 선호할 것이다.

#. Downloads 열 제목을 클릭 검색 결과를 다운로드순으로 정렬한다.

#. 가장 많이 다운로드된 버전의 패키지 이름을 클릭한다.

   Anaconda.org의 세부사항 페이지가 나타나면 패키지 다운로드에 사용할 커맨드를 볼 수 있다.

   .. code::

      conda install --channel https://conda.anaconda.org/pandas bottleneck

#. 표시된 커맨드를 실행한다.

#. 터미널이나 아나콘다 프롬프트에서 다음을 실행해 패키지가 다운로드 되었는지 확인한다.

   .. code::

      conda list



pip를 사용한 패키지 설치
-----------------------------

콘다나 Anaconda.org에서 제공하지 않는 패키지는 대부분 pip로 설치할 수 있다.
pip는 "pip installs packages"의 약자이다.

팁: Pip는 패키지 관리자일 뿐 환경 관리는 할 수 없다.
콘다와 달리 pip는 파이썬을 패키지로 취급하지 않기 때문에 파이썬 업데이트도 할 수 없다.
하지만 pip를 사용하면 콘다로 설치할 수 없는 패키지도 설치할 수 있다.
pip와 conda 모두 아나콘다/미니콘다에 포함되어 있다.

터미널이나 아나콘다 프롬프트에서 다음 단계를 따라 진행한다.

#. 프로그램을 설치할 환경을 활성화한다. 여기에서는 bunnies를 활성화한다.

   * 리눅스, 맥OS---``source activate bunnies``
   * 윈도---``activate bunnies``

#. "see" 프로그램을 설치한다.

   .. code::

      pip install see

#. see가 설치되었는지 확인한다.

   .. code::

      conda list



상용 패키지 설치
------------------------------

상용 패키지도 다른 콘다 패키지와 동일한 방법으로 설치한다.

예시: 아나콘다의 상용 패키지 IOPro의 체험판을 설치하면 파이썬 처리속도를 향상시킬 수 있다.
터미널이나 아나콘다 프롬프트에서 다음을 실행한다.

.. code::

   conda install iopro

팁: 학술적 목적이 아닌 경우, 이 체험판은 30일 후에 만료된다.


.. _remove-pkgs-envs-conda:

패키지, 환경, 콘다 삭제
===============================================

하나 이상의 테스트 패키지, 환경, 콘다를 삭제하는 법은 다음과 같다.


#. 터미널이나 아나콘다 프롬프트에서 다음을 실행해 bunnies 환경에 설치된 상용 패키지 IOPro를 삭제한다.

   .. code::

      conda remove --name bunnies iopro

#. 다음을 실행해 IOPro가 삭제되었는지 확인한다.

   .. code::

      conda list

#. 터미널이나 아나콘다 프롬프트에서 다음을 실행해 snakes 환경을 삭제한다.

   .. code::

      conda remove --name snakes --all

#. 다음을 실행해 snakes 환경이 삭제되었는지 확인한다.

   .. code::

      conda info --envs

   환경 목록에 snakes가 나타나지 않으면 삭제된 것이다.

#. 콘다를 삭제한다.

   * 리눅스, 맥OS: 아나콘다/미니콘다의 설치 디렉토리를 삭제한다.

     .. code::

        rm -rf ~/miniconda

     또는

     .. code::

        rm -rf ~/anaconda

   * 윈도우: 제어판의 프로그램 추가 제거에서 Python X.X (Anaconda) 또는
     Python X.X (Miniconda)를 선택하고 프로그램 제거를 클릭한다.

     주의: X.X는 사용자의 파이썬 버전이다.

     주의: 윈도우10에서는 다른 방법으로 삭제한다.



추가 정보
================

* 전체 문서---`<https://veranostech.github.io/docs-korean-conda-docs/docs/build/html/index_ko.html>`_.
* 요약집---:doc:`cheatsheet`.
* 자주 하는 질문---`<http://docs.continuum.io/anaconda/faq.html>`_.
* 무료 커뮤니티 지원---`<https://groups.google.com/a/anaconda.com/forum/#!forum/anaconda>`_.
* 유료 지원 옵션---`<https://www.anaconda.com/support/>`_.
* 교육훈련---`<https://www.anaconda.com/training/>`_.
* 컨설팅---`<https://www.anaconda.com/consulting/>`_.
