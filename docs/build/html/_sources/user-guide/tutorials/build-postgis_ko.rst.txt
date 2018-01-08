=================================================
일반 코드 프로젝트를 위한 콘다 패키지 빌드
=================================================

.. contents::
   :local:
   :depth: 1

어떤 언어로 작성된 프로젝트라도 콘다 패키지로 빌드할 수 있다.
이 튜토리얼은 포스트지아이에스(postgis) 패키지를 위한 래시피를 작성하고 빌드한다.
빌드한 패키지를 `anaconda.org <http://anaconda.org/>`_\ 에 업로드하고 콘다를 사용해 설치한다.


튜토리얼 대상
=================

파이썬이 아닌 언어로 작업된 소스 코드 프로젝트로 콘다 패키지를 만들고자 하는 맥OS, 리눅스 사용자를 위한 튜토리얼이다.
C/C++ 패키지를 설정, 컴파일, 설치하는 방법을 알고 있어야 한다.


.. _before-you-start3:

시작에 앞서
=================

튜토리얼을 시작하기 전에 :doc:`요구 사항 <index_ko>`\ 을 확인한다.


.. _depends:

의존 요소 나열하기
=====================

콘다 래시피를 생성할 때 가장 중요한 것은 의존 요소를 알맞게 나열하는 것이다.

`README.postgis`_ 파일에서 최소 요구 버전에 필요한 패키지를 알 수 있다.

.. _README.postgis: https://github.com/postgis/postgis/blob/2.2.2/README.postgis

.. code-block:: bash

    postgresql version 9.1
    proj4 version 4.0.6
    geos version 3.4
    libxml2 version 2.5
    json-c version 0.9
    gdal version 1.9

콘다 빌드(conda build)는 포스트지아이에스를 위한 소스 코드로부터 개인 환경을 만들고
이 환경에 콘다는 필요한 의존 요소를 모두 설치해야 한다.
따라서 각 의존 요소는 ``conda install``\ 로 설치할 수 있어야 한다.

#. ``conda search``\ 를 사용해 의존 요소로 필요한 패키지들을 검색한다.

   기본 채널에서 설치할 수 없는 패키지는 json-c 하나다.

#. json-c를 설치하기 위해 ``conda config`` 명령으로 ``jlaura`` 채널을 추가한다.

   .. code-block:: bash

       conda config --add channels jlaura

모든 의존 요소 패키지가 설치 가능함을 확인했다. 다음 단계는 콘다 래피시(conda recipe) 작성이다.


.. _conda-recipe:

콘다 래시피 작성하기
======================

콘다 래시피는 세가지 주요 구성 요소를 갖는다.

* 패키지 이름과 버전
* 소스 코드 위치
* 패키지 빌드와 실행을 위해 필요한 의존 패키지

콘다 래시피에 소스 코드 위치를 지정하는 방법은 많다.
여기에서는 깃헙(Github) 레포지토리와 원하는 리비전 태그로 경로를 지정한다.

주의: 모든 깃헙 레포지토리가 리비전 태그를 사용하진 않는다. 가장 최근 커밋을 사용하는게 좋은 경우도 있다.

#. 콘다 래피시 파일을 저장할 디렉토리를 생성한다.

   .. code-block:: bash

      mkdir postgis
      cd postgis

#. 텍스트 편집기를 열고 ``postgis`` 디렉토리에 ``meta.yaml`` 파일을 생성한다. 생성된 파일에 다음 코드를 입력한다.

   .. code-block:: yaml

       package:
         name: postgis
         version: "2.2.2"

       source:
         git_rev: 2.2.2
         git_url: https://github.com/postgis/postgis.git

       build:
         number: 0

       requirements:
         build:
           - gdal
           -  geos
           -  proj4
           -  json-c
           -  libxml2
           -  postgresql >=9.1
         run:
           -  gdal
           -  geos
           -  proj4
           -  json-c
           -  libxml2
           -  postgresql >=9.1

       about:
         home: http://postgis.net
         license: GPL2

주의: 콘다 빌드는 빌드 의존 요소로 지정된 패키지로 격리된 환경을 만들고 그 환경에서 패키지를 생성한다.
작업 중인 환경에 패키지를 설치해도 콘다 빌드에 영향을 주지 않는다.


.. _build-script:

빌드 스크립트 작성하기
=======================

콘다 래시피를 준비하는 마지막 단계는 빌드 스크립트를 작성하는 것이다.
포스트지아이에스는 맥OS와 리눅스를 위해 빌드되었기 때문에 ``postgis`` 디렉토리에 ``build.sh`` 파일 하나만 있으면 된다.

빌드 스크립트는 소스 프로젝트를 설정, 빌드, 설치하는데 필요한 모든 명령을 포함한다.
이 스크립트는 반드시 사용자 간섭 없이 실행해야 한다.

`포스트지아이에스 컴파일 문서 <http://postgis.net/docs/manual-2.2/postgis_installation.html#installation_configuration>`_\ 에서
의존 패키지의 위치를 표시하기 위해 ``configure`` 명령에 반드시 추가해야 하는 플래그를 볼 수 있다.

``conda-build`` 명령을 실행하는 동안 $PREFIX 환경 변수는 콘다 패키지 설치 경로를 나타내는데 사용된다.
이 예제에서 ``configure`` 명령은 $PREFIX를 통해 콘다 래시피 requirements 섹션의 build와 run에 나열된 의존 패키지 위치를 알 수 있다.

#. 터미널에서 ``postgis`` 디렉토리로 간다.

#. 텍스트 편집기에서 ``build.sh`` 파일을 생성하고 다음 코드를 입력한다.

   .. code-block:: bash

       sh autogen.sh
       ./configure \
         --prefix=$PREFIX \
         --with-pgconfig=$PREFIX/bin/pg_config \
         --with-gdalconfig=$PREFIX/bin/gdal-config \
         --with-xml2config=$PREFIX/bin/xml2-config \
         --with-geosconfig=$PREFIX/bin/geos-config \
         --with-projdir=$PREFIX \
         --with-jsondir=$PREFIX \
         --without-raster \
         --without-topology

       make
       make install

   주의: $PREFIX 환경 변수로의 레퍼런스가 없으면 ``configure`` 명령은 기본 시스템 디렉토리에서 필요한 패키지를 찾는다.
   패키지가 잘빌드되었더라도 다른 사용자가 컴파일된 콘다 패키지를 제대로 설치할 수 있을거란 보장은 없다.

   주의: 이 래시피에서 콘다 빌드를 실행하려면 C/C++ 컴파일러인 autoconf와 automake를 설치해야 한다.
   이 패키지들은 콘다로 설치할 수 없고 시스템 레벨에서 설치해야 한다.

#. 파일을 ``postgis`` 디렉토리에 저장한다.


.. _build-postgis:

패키지 빌드하기
=====================

래시피을 완성했으면 이제 ``postgis`` 디렉토리에서 ``conda-build`` 명령을 실행해 콘다 패키지를 빌드한다.

.. code-block:: bash

    conda-build .

``conda-build``\ 의 출력은 다음과 같이 시작한다.

.. code-block:: text

    Removing old build environment
    Removing old work directory
    BUILD START: postgis-2.2.2-0
    Using Anaconda Cloud api site https://api.anaconda.org
    Fetching package metadata: ..........
    Solving package specifications: .........

콘다 빌드가 의존 패키지를 성공적으로 설치하고 소스 코드를 컴파일하면 다음 메세지 중 하나가 나타나면서 종료된다.

* 맥OS:

  .. code-block:: text

      BUILD END: postgis-2.2.2-0
      Nothing to test for: postgis-2.2.2-0
      # If you want to upload this package to anaconda.org later, type:
      #
      # $ anaconda upload /Users/adefusco/Applications/anaconda3/conda-bld/osx-64/postgis-2.2.2-0.tar.bz2
      #
      # To have conda build upload to anaconda.org automatically, use
      # $ conda config --set anaconda_upload yes

* 리눅스:

  .. code-block:: text

      BUILD END: postgis-2.2.2-0
      Nothing to test for: postgis-2.2.2-0
      # If you want to upload this package to anaconda.org later, type:
      #
      # $ anaconda upload /home/adefusco/anaconda3/conda-bld/linux-64/postgis-2.2.2-0.tar.bz2
      #
      # To have conda build upload to anaconda.org automatically, use
      # $ conda config --set anaconda_upload yes


주의: 경로는 아나콘다가 설치된 위치에 따라 달라진다.

패키지는 동일한 아키텍처의 시스템에만 설치될 수 있다.
각 아키텍처를 위한 패키지를 만들려면 맥OS나 리눅스에서 별도로 ``conda-build`` 명령을 실행해야 한다.


.. _install:

패키지 배포와 설치하기
=======================================

#. 다음 명령으로 로컬 컴퓨터에 패키지를 설치한다.

   .. code-block:: bash

      conda install postgis --use-local

   위 방법 대신 ``conda-build`` 출력 끝에 나오는 ``anaconda-upload`` 명령을 사용해
   사용자의 Anaconda.org_ 에 패키지를 업로드할 수 있다.

#. 다음 명령으로 어떤 사용자도 패키지를 설치할 수 있다.

   .. code-block:: bash

      conda install -c CHANNEL postgis

   주의: ``CHANNEL``\ 를 사용자의 Anaconda.org_ 사용자명으로 바꾼다.


추가 정보
================

콘다 래시피 ``meta.yaml`` 파일에 사용할 수 있는 추가 옵션은 :doc:`../tasks/build-packages/define-metadata`\ 와
:doc:`../tasks/build-packages/sample-recipes`\ 에서 볼 수 있다.
