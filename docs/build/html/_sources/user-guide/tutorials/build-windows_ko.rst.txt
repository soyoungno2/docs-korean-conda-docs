==================================
윈도우에서 콘다 패키지 빌드
==================================

.. contents::
   :local:
   :depth: 2


이 튜토리얼은 윈도우에서 콘다 빌드(conda build)를 사용해 콘다 패키지를 생성하는 방법을 설명한다.
예제로 SEP와 pySLALIB 패키지를 사용한다.

이 튜토리얼에서 최종적으로 빌드된 패키지는 `아나콘다 클라우드 <https://anaconda.org>`_\ 에 있다.

* `SEP <https://anaconda.org/wwarner/sep/files>`_.

* `pySLALIB <https://anaconda.org/wwarner/pyslalib/files>`_.

이 튜토리얼은 래시피를 작성하는 방법도 다룬다.
최종 `SEP 래시피 <https://github.com/conda/conda-docs/tree/master/docs/source/user-guide/tutorials/sep>`_\ 와
`pySLALIB 래시피 <https://github.com/conda/conda-docs/tree/master/docs/source/user-guide/tutorials/pyslalib>`_\ 를
깃헙(Github)의 `콘다 문서 레포지토리 <https://github.com/conda/conda-docs>`_\ 에서 볼 수 있다.


시작에 앞서
=================

튜토리얼을 시작하기 전에 :doc:`요구 사항 <index_ko>`\ 을 확인한다.


도구
=========

마이크로소프트 비주얼 스튜디오
------------------------

콘다 개발자 표준 예제에 각기 다른 버전의 파이썬을 위한 콘다 패키지가 빌드되어 있다.
다음은 파이썬 버전에 대응하는 비주얼 스튜디오(Visual Studio) 버전이다.

* 파이썬 2.7 패키지: 비주얼 스튜디오(VS) 2008
* 파이썬 3.4 패키지: VS 2010
* 파이썬 3.5 패키지: VS 2015
* 파이썬 3.6 패키지: VS 2015

위에 나열한 버전의 VS를 사용해 각 버전의 파이썬 패키지를 빌드하는 것은 python.org의 공식 파이썬 빌드에도 사용되는 방식이다.
VS 2015는 마이크로소프트로부터 구매할 수 있고 VS 2008, VS 2010은 리셀러에게 구매해야 한다.


비주얼 스튜디오 대안
----------------------------------------

다음은 각 버전의 비쥬얼 스튜디오(VS) 컴파일러의 무료 대안이다.

* VS 2008 대신
  `파이썬2.7을 위한 무료 마이크로소프트 C++ 컴파일러 <https://www.microsoft.com/en-us/download/details.aspx?id=44266>`_\
  가 자주 사용된다.

* VS 2010 대신
  `윈도우7과 .Net Framework4를 위한 무료 마이크로소프트 윈도우 SDK <https://www.microsoft.com/en-us/download/details.aspx?id=8279>`_\
  가 자주 사용된다.

* `VS 2010 서비스팩 1 (SP1) <https://www.microsoft.com/en-us/download/details.aspx?id=23691>`_\ 을 설치했는지 확인한다.

* VS 2010 SP1 인스톨러의 버그로 인해 설치 과정에서 컴파일러 도구가 삭제될 수 있다.
  `윈도우 SDK 7.1을 위한 마이크로소프트 비주얼 C++ 2010 SP1 컴파일러 업데이트 <https://www.microsoft.com/en-us/download/details.aspx?id=4422>`_\
  의 안내를 따르면 삭제된 컴파일러 도구를 복구할 수 있다.

* VS 2015는 학술적 목적, 오픈 소스 프로젝트, 이외에 특정 사용 사례을 위한
  `모든 기능이 포함된 무료 커뮤니티 에디션 <https://www.visualstudio.com/en-us/products/visual-studio-community-vs.aspx>`_\
  을 지원한다.


파이썬2.7을 위한 마이크로소프트 비주얼 C++ 컴파일러와 윈도우7,.NET Framework4를 위한 마이크로 소프트 SDK는 모두 합리적인 테스트를 거쳤다.
콘다 빌드는 이 설정을 지원하기 위해 세심하게 테스트되었지만 CMake 빌드 도구나 VS 2008, VS 2010의 무료 대안들과 관련된 알려진 문제들이 있다.
이러한 문제가 발생했을 때 비주얼 스튜디오 솔루션 생성기 대신 "NMake Makefile" 생성기를 권장한다.


윈도우 버전
-----------------

최근 버전의 윈도우는 모두 사용할 수 있다. 여기에서는 윈도우8.1을 사용한다.

다른 도구
------------

어떤 환경에는 처음부터 bzip2나 깃(Git)과 같이 몇몇 빌드 작업 방식에 필요한 도구들이 없을 수 있다.

``conda install git`` 명령으로 콘다를 통해 깃을 설치할 수 있다.

bzip2도 같은 방식으로 얻을 수 있다. 콘다 bzip2 패키지는 bzip2 라이브러리만 포함하고 bzip2 실행 파일은 포함하지 않는다.
bzip2 실행 파일은 http://gnuwin32.sourceforge.net/packages/bzip2.htm 과 같은 다른 소스로부터 받아야 한다.
실행 파일을 PATH 어딘가에 둔다. 미니콘다(Miniconda)/아나콘다(Anaconda) 설치 경로의 ``Library/bin`` 폴더에 두는 것이 좋다.


빌드 전략 세우기
============================

콘다 래시피(conda recipe)는 일반적으로 시행 착오를 거쳐 빌드된다.
보통 패키지 빌드의 첫번째 시도는 의존 요소 손실로 인한 컴파일러,링크 에러로 실패한다.
래시피를 작성하는 개발자는 발생한 에러를 살피고 ``meta.yaml`` 파일을 수정해 손실된 의존 요소를 포함시킨다.
다시 빌드를 시도한다. 이러한 시행 착오 과정을 거쳐 패키지를 성공적으로 빌드한다.


미니콘다 설치의 다른 버전 파이썬으로 빌드하기
Building with a Python version different from your Miniconda installation
==========================================================================

미니콘다2와 미니콘다3는 원하는 버전을 지정하면 파이썬2나 파이썬3를 위한 패키지를 간단히 빌드할 수 있다.
미니콘다2는 파이썬2만을 포함하고 미니콘다3는 파이썬3만을 포함한다.

하나의 미니콘다만을 설치하면 빌드 추적이 더 쉬워지지만 두개의 미니콘다를 하나의 시스템에 동시에 설치할 수도 있다.
두개를 모두 설치했다면 ``where`` 명령으로 어떤 버전이 PATH에 먼저 설정되어 있는지 확인한다.
이 버전이 사용자가 사용하게 될 파이썬 버전이다. ::

  where python

미니콘다 설치와 다른 파이썬 버전을 위한 패키지를 빌드하려면 파이썬 버전을 위한 ``conda-build`` 명령에 ``--python`` 옵션을 추가한다.
``conda-build`` command.

예시: 미니콘다2로 파이썬3.5 패키지를 빌드한다. ::

    conda-build recipeDirectory --python=3.5

주의: (위 명령에서) ``recipeDirectory``\ 를 래시피 디릭토리의 이름과 경로로 바꾼다.


테스트 자동화
==================

래시피 디렉토리가 테스트 파일 ``run_test.bat``(윈도우),``run_test.sh``(맥OS,리눅스),``run_test.py``(모든 운영체제)를 포함하면
빌드 후에 파일이 실행되어 패키지를 테스트하고 에러가 보고된다.

주의: 테스트가 실행될 때 :ref:`meta.yaml 파일의 테스트 섹션 <meta-test>`\ 을 사용해
데이터 파일을 래시피 디렉토리에서 테스트 디렉토리로 옮긴다


콘다와 파이썬2/파이썬3로 SEP 패키지 빌드하기
=====================================================

`SEP 문서 <https://sep.readthedocs.io>`_\ 에 따르면 SEP는 파이썬2와 파이썬3에서 작동하고 넘파이(NumPy)에만 의존한다.
PyPI와 SEP를 검색해 보면 이미 `SEP를 위한 PyPI 패키지 <https://pypi.python.org/pypi/sep>`_\ 가 있는 것을 알 수 있다.

SEP를 위한 PyPI 패키지가 이미 있기 때문에 ``conda skeleton`` 명령으로 PyPI 패키지에 기반한 스켈레톤이나 콘다 래시피 개요를 만들 수 있다.
래시피 개요를 수동으로 마무리하면 콘다는 완전한 래시피로부터 콘다 패키지를 빌드 할 수 있다.


비주얼 스튜디오 설치하기
----------------------

아직 비주얼 스튜디오가 없다면 적절한 버전의 비주얼 스튜디오를 설치한다.

* 파이썬3: 비주얼 스튜디오 2015

  #. 사용자 지정 설치를 선택한다.

  #. 프로그램 언어에서 비주얼 C++를 선택해 설치한다.

* 파이썬2: 비주얼 스튜디오 2008

  #. 사용자 지정 설치를 선택한다.

  #. X64 컴파일러와 도구를 선택해 설치한다. 서비스팩1을 설치한다.


스켈레톤 래시피 만들기
-----------------------------

#. 스켈레톤(skeleton) 명령을 실행한다. ::

       conda skeleton pypi sep

   ``skeleton`` 명령은 ``sep``\ 라는 이름으로 생성된 디렉토리에 파일을 설치한다.

#. ``sep`` 디렉토리로 가서 생성된 파일을 본다. ::

       cd sep

   다음과 같이 세개의 스켈레톤 파일이 생성된다.

   * ``bld.bat``: 윈도우를 위한 스켈레톤 파일이다.
   * ``build.sh``: 맥OS,리눅스를 위한 스켈레톤 파일이다.
   * ``meta.yaml``: 모든 플랫폼을 위한 스켈레톤 파일이다..


스켈레톤 파일 편집하기
------------------------

이 예제에서 빌드하는 패키지는 ``bld.bat`` 파일과 ``build.sh`` 파일은 수정하지 않아도 된다.
``meta.yaml`` 파일을 수정해 의존 요소 넘파이를 추가하고 빌드한 패키지를 가져오는 방식의 선택적 테스트를 추가한다.

#. ``meta.yaml`` 파일의 requirements 섹션에 넘파이를 패키지 빌드 요구 사항으로 하는 행을 추가한다.

#. 넘파이를 패키지 실행 요구 사항으로 하는 행을 추가한다.

넘파이 버전은 문자 ``x.x``\ 로 설정한다.

추가한 행이 바로 위에 ``- python``\ 과 정렬되었는지 확인한다.

예시:

.. code-block:: yaml

    requirements:
      build:
        - python
        - numpy     x.x

      run:
        - python
        - numpy     x.x

주의: ``1.11``\ 과 같은 특정 버전 대신 ``x.x``\ 로 버전을 지정하면 넘파이 버전이 유동적으로 지정되어
빌드 명령에서 실제 넘파이 버전을 가져오게 된다. 현재는 넘파이만 버전을 유동적으로 지정할 수 있다.
SEP는 Cython을 통한 넘파이의 C API를 사용하기 때문에 버전 지정이 중요하다.
C API는 넘파이 버전에 따라 달라지므로 실행 시에 빌드했을 때 사용한 것과 동일한 버전의 넘파이를 사용하는 것이 중요하다.

선택---빌드된 패키지를 위한 테스트 추가하기
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

다음 선택 테스트를 추가하면 빌드 마지막에 파이썬 선언 ``import sep``\ 가 잘실행되는지 확인하는 방식으로 패키지를 테스트한다.

#. 테스트 섹션에서 ``test:``, ``imports:`` 행의 주석에 사용된 ``#``\ 을 제거한다.

#. ``- sep``\ 을 추가한다. 들여쓰기가 파일의 다른 코드와 일치하는지 확인한다.

예시:

.. code-block:: yaml

    test:
      # Python imports
      imports:
        - sep


테스트 파일 생성
-------------------

``run_test.py``\ 라는 이름으로 새 테스트 파일을 만들고
`Background estimation and source detection <https://sep.readthedocs.org/en/v0.5.x/detection.html>`_\
에서 가져온 코드를 입력해 ``sep`` 디렉토리에 저장한다.

.. code-block:: python

    import numpy as np
    import sep

    data = np.random.random((256, 256))

    # Measure a spatially variable background of some image data
    # (a numpy array)
    bkg = sep.Background(data)

    # ... or with some optional parameters
    # bkg = sep.Background(data, mask=mask, bw=64, bh=64, fw=3, fh=3)


빌드 후에 새로 빌드된 패키지를 테스트 하기 위해 이 파일이 실행된다.

이제 래시피 작성이 끝났다.


패키지 빌드하기
-----------------

생성한 래피시로 패키지를 빌드한다. ::

    conda-build . --numpy=1.11


출력 확인하기
----------------

#. 빌드가 성공적으로 끝났는지 확인하기 위해 출력을 확인한다.
   출력에는 최종 패키지 파일의 위치와 아나콘다 클라우드(Anaconda Cloud)로 패키지를 업로드하는 명령이 나타난다.

#. 링크나 컴파일러 에러가 나타나면 래시피를 수정하고 다시 빌드한다.


콘다와 파이썬2/파이썬3로 pySLALIB 패키지 빌드하기
=========================================================

이 과정은 파이썬2나 파이썬3로 패키지를 빌드하는 방법을 설명한다.
빌드하고자 하는 파이썬 버전에 맞는 설명을 따라 진행한다.

pySLALIB는 포트란(Fortran)을 포함하므로 빌드를 위해 포트란 컴파일러가 필요하다.
pySLALIB의 PyPI 패키지가 없기 때문에 ``conda skeleton``\ 로 생성되는 스켈레톤 래시피를 사용할 수 없다.
래시피를 처음부터 만들어야 한다. pySLALIB를 빌드하는 과정은 SEP 빌드와 유사하지만
포트란 컴파일러 설치, PyPI 대신 깃헙(GitHub)으로부터 가져오는 ``meta.yaml`` 파일 작성, 포트란 코드에 맞는 패치 적용이 포함된다.

다음 단계를 따라 pySLALIB을 빌드한다.

#. 비주얼 스튜디오를 설치한다.

   * 파이썬3: 비주얼 스튜디오 2015를 설치한다. 사용자 지정 설치의 프로그램 언어에서 비주얼 C++을 선택한다.

   * 파이썬2: 비주얼 스튜디오 2008을 설치한다. 사용자 지정 설치에서 X64 컴파일러와 도구를 선택한다. 비주얼 스튜디오 2008 서비스팩 1을 설치한다.

#. Intel Parallel Studio Composer Edition을 설치한다.
   `인텔 포트란 컴파일러 페이지 <https://software.intel.com/en-us/fortran-compilers>`_\ 에서
   Try & Buy를 선택한다. Parallel Studio Composer Edition for Windows를 선택한다.
   포트란과 C++을 사용하는 버전 대신 포트란만 사용하는 버전을 선택할 수 있다.
   30일 무료 체험판을 사용할 수 있다. 이메일 주소를 포함한 양식을 작성하면 다운로드 링크를 받을 수 있다.

   * 파이썬3: Intel Parallel Studio XE Composer Edition for Fortran Windows를 받고 설치한다.

   * 파이썬3:  Intel Parallel Studio XE Composer Edition for Fortran Windows 다운로드 페이지를 연다.
     Additional downloads, latest updates and prior versions을 선택하고 version 2013 Update 6를 선택한다.
     Intel Visual Fortran Composer XE 2013 SP1 (compiler version 14.0)은 비주얼 스튜디오 2008과 함께 사용할 수 있는
     가장 최신 버전의 인텔 포트란 컴파일러다. Choose Download Now를 선택하고 이 버전을 설치한다.

#. 빌드를 위해 깃헙에서 pySLALIB 패키지 소스를 검색하기 때문에 반드시 깃이 있어야 한다. 깃을 설치한다. ::

     conda install git

#. 래시피를 만든다. 처음부터 래시피를 만들거나
   `우리가 작성한 래시피 <https://github.com/conda/conda-docs/tree/master/docs/source/user-guide/tutorials/pyslalib>`_\
   를 사용한다. 이 래시피는 다음 파일을 포함한다.

   * ``meta.yaml`` 파일은 pySLALIB의 깃헙 경로와 시스템이 ``intel_fortran_use.patch``\ 를 적용하는 방식을 설정한다.
   * ``bld.bat`` 파일은 윈도우 배치 스크립트로 빌드와 실행 과정에서 알맞은 32비트, 64비트 라이브러리가 링크되도록 보장한다.
   * ``run_test.py`` 파일은 pySLALIB 깃헙 레포지토리에서 가져온 테스트로 빌드가 성공적으로 마무리되었는지 확인한다.
   * ``intel_fortran_use.patch`` 파일은 pySLALIB 포트란 코드가 인텔 포트란 컴파일러와 함께 작동하도록 하는 패치다.

#. 홈 디렉토리에서 ``pyslalib``\ 라는 이름으로 래시피 디렉토리를 만들고 위의 4개의 파일을 복사한다.

#. 패키지를 빌드한다.

   * 파이썬3: 인텔 패러랠 스튜디오 XE 2016의 **Apps** 메뉴에서
     Compiler 16.0 Update 3 for Intel 64ㅡVisual Studio 2015 environment command prompt를 연다.

   * 파이썬2: 인텔 패러랠 스튜디오 XE 2013의 **Apps** 메뉴에서
     Intel 64 Visual Studio 2008 mode command prompt를 연다.

#. ``conda-build``를 실행한다. 알맞은 사용자명과 래시피 디렉토리 경로를 사용한다.
   여기에서는 사용자명으로 "builder"를 사용했다. ::

     conda-build C:\Users\builder\pyslalib

#. 빌드가 성공적으로 끝났는지 확인하기 위해 출력을 확인한다.
   출력은 최종 패키지 파일의 위치와 패키지를 클라우드에 업로드하는 명령을 포함한다.

#. 링크나 컴파일러 에러가 나타나면 래시피를 수정하고 다시 빌드한다.
