========================================
아나콘다 네비게이터 어플리케이션 빌드
========================================

.. contents::
   :local:
   :depth: 1

이 튜토리얼은 `로데오(Rodeo) IDE <https://www.yhat.com/products/rodeo>`_\ 를
아나콘다 네비게이터(Anaconda Navigator) 어플리케이션으로 빌드하는 방법을 설명한다.

로데오의 콘다 빌드 래시피(conda build recipe)는 ``conda skeleton``\ 으로 생성된다.
패키지를 어플리케이션으로 선언하려면 빌드 래시피 파일에 세가지 수정을 해주어야 한다.
빌드한 패키지는 아나콘다 클라우드 채널에 업로드 된다.
네비게이터에 채널을 추가하고 나면 어플리케이션이 **Home** 탭에 나타난다.

주의: 네비게이터를 위해 빌드한 어플리케이션은 GUI를 가지고 있어야 한다. 모든 콘다 패키지가 GUI를 갖는 것은 아니다.


튜토리얼 대상
=================

PyPI 패키지로 네비게이터 어플리케이션 콘다 패키지를 만들고자 하는 윈도우,맥OS,리눅스 사용자를 위한 튜토리얼이다.
콘다 빌드나 콘다 래시피에 대한 사전 지식을 권장한다.


시작에 앞서
=================

* :doc:`요구 사항 <index_ko>`\ 을 확인한다.

* `아나콘다 클라우드 <https://anaconda.org>`_ 계정이 있어야 한다.
  사용자명이 "Anaconda Cloud channel."이 된다.


.. _skeleton:

스켈레톤 래시피 생성하기
============================

#. 사용자의 홈 디렉토리에서 ``conda skeleton`` 명령을 실행한다.

   .. code-block:: text

      conda skeleton pypi rodeo

   ``rodeo``\ 라는 이름의 디렉토리와 그 안에 3개의 스켈레톤 파일 ``meta.yaml``, ``build.sh``, ``bld.bat``\ 가 생성된다..

#. 맥OS, 리눅스의 ``ls`` 명령이나 윈도우의 ``dir`` 명령을 사용해 스켈레톤 파일이 생성되었는지 확인한다.


.. _requires:

meta.yaml의 requirements 변경하기
===================================

#. ``meta.yaml`` 파일을 텍스트 편집기에서 연다.

#. requirements에서 ``ipython`` 항목을 ``jupyter``\ 로 바꾼다.

전체 requirements는 다음과 같이 보여야 한다.

.. code-block:: yaml

    requirements:
      build:
        - python
        - setuptools
        - jupyter
        - flask >=0.10.1
        - docopt
        - pyzmq >=13
        - mistune

      run:
        - python
        - jupyter
        - flask >=0.10.1
        - docopt
        - pyzmq >=13
        - mistune


.. _app-entry:

meta.yaml에 app 입력하기
===============================

콘다 패키지를 어플리케이션으로 선언하려면 ``meta.yaml`` 파일에 app 매개 변수를 추가해야 한다.
app 섹션은 4개의 키 entry,icon,summary,type을 갖는다.

entry 태그는 네비게이터가 패키지를 실행하는 방법을 정한다.
로데오 IDE는 맥OS, 리눅스, 윈도우를 위한 entry 태그를 개별적으로 설정해야 한다.

#. 텍스트 편집기에서 ``meta.yaml`` 파일을 연다.

#. 다음과 같은 행을 추가한다.

   * 윈도우, 리눅스: entry 태그를 추가한다.

     .. code-block:: yaml

         app:
           entry: rodeo .                              [win]
           entry: rodeo .                              [linux]


   * 맥OS: 실행 스크립트를 넣어야 한다.

     #. 텍스트 편집기를 사용해 콘다 빌드 래시피 디렉토리 ``rodeo_mac.command``\ 에 파일을 생성한다.
        이 파일에 다음 코드를 추가한다.

        .. code-block:: bash

           DIR=$(dirname $0)

           $DIR/rodeo ${HOME}

     #. 이전 단계에서 생성한 파일이 설치되는지 확인하기 위해 ``build.sh`` 스크립트에 다음 행을 추가한다.

        .. code-block:: bash

           if [ `uname` == Darwin ]
           then
               cp $RECIPE_DIR/rodeo_mac.command $PREFIX/bin
           fi

     #. ``meta.yaml`` 파일의 app 섹션에 다음 행을 추가한다. ::

           entry: open ${PREFIX}/bin/rodeo_mac.command [osx]

     #. 네비게이터에 나타날 로고 PNG 파일은 콘다 빌드 래시피에 주어진다.
        깃헙 레포지토리 https://github.com/yhat/rodeo/blob/master/resources/app.png 에서
        바로 app.png 파일을 받아 ``meta.yaml`` 파일이 속한 디렉토리에 둔다.

완성된 app 섹션은 다음과 같이 보여야 한다. ::

    app:
      entry: rodeo .                              [win]
      entry: rodeo .                              [linux]
      entry: open ${PREFIX}/bin/rodeo_mac.command [osx]
      icon: app.png
      summary: Rodeo Data Science IDE
      type: web

완전한 :download:`meta.yaml <rodeo/meta.yaml>`\ 파일과 :download:`build.sh <rodeo/build.sh>` 파일을 받을 수 있다.


.. _build4:

빌드하기
==========

패키지를 모든 플랫폼에서 사용할 수 있게 하려면 로데오 패키지를 윈도우, 맥OS, 리눅스 기기에서 개별적으로 빌드하고 업로드해야 한다.

콘다 빌드로 패키지를 생성한다.

.. code-block:: bash

   conda-build rodeo

콘다 빌드가 끝나면 콘다 패키지의 경로와 파일명이 나타난다.

``conda-build`` 명령이 실패하면 :ref:`troubleshooting`\ 을 보자.

윈도우 파일 경로 예시:

.. code-block:: text

    C:\Users\jsmith\Miniconda\conda-bld\win-64\rodeo-0.4.4-py35_0.tar.bz2


맥OS 파일 경로 예시:

.. code-block:: text

    /Users/jsmith/miniconda/conda-bld/osx-64/rodeo-0.4.4-py35_0.tar.bz2

리눅스 파일 경로 예시:

.. code-block:: text

    /home/jsmith/miniconda/conda-bld/linux-64/rodeo-0.4.4-py35_0.tar.bz2


주의: 경로와 파일명은 사용자의 설치와 운영체제에 따라 달라질 수 있다. 다음 작업을 위해 경로와 파일명을 저장한다.


.. _upload:

클라우드에 업로드하기
============================

#. 터미널이나 아나콘다 프롬프트에서 루트 콘다 환경으로 간다.

#. 클라우드에 로그인한다.

   .. code-block:: text

       anaconda login

#. 클라우드 계정 이름과 암호를 요구하면 입력한다.

   로그인에 성공하면 다음과 유사한 출력이 나타난다.

   .. code-block:: text

      Using Anaconda Cloud api site https://api.anaconda.org
      Username: defusco
      defusco's Password:
      login successful

#. 사용자의 채널에 로그인했다. 이제 로데오 콘다 패키지를 업로드한다.

   * 윈도우:

     .. code-block:: text

        anaconda upload C:\Users\jsmith\Miniconda\conda-bld\win-64\rodeo-0.4.4-py35_0.tar.bz2


   * 맥OS, 리눅스:

     .. code-block:: text

        anaconda upload /home/jsmith/miniconda/conda-bld/linux-64/rodeo-0.4.4-py35_0.tar.bz2

     주의: 경로와 파일명을 :ref:`build4`\ 에서 저장한 것으로 바꾼다.
     경로와 파일명은 사용자의 설치와 운영체제에 따라 달라질 수 있다.

클라우드에 대한 더 많은 정보는 `아나콘다 클라우드 문서 <https://docs.continuum.io/anaconda-cloud/>`_\ 에 있다.


.. _navigator:

네비게이터 설정
======================

클라우드 채널에 로데오를 업로드했다. 이제 네비게이터에 채널을 추가해야 한다.

#. 네비게이터를 실행한다.

   * 윈도우, 리눅스: **시작** 메뉴를 사용한다.

   * 맥OS: 데스크탑이나 스포트라이트로 실행할 수 있다.

#. 왼쪽의 **Environments** 탭을 연다.

   .. figure:: /img/conda_navigator-home.png
      :scale: 50 %

      ..

   |

#. 사용자의 채널을 추가한다.

   #. Channel 버튼을 클릭한다.

   #. Add 버튼을 클릭한다.

   #. 사용자의 클라우드 채널 URL을 입력한다.

      .. code-block:: text

         https://conda.anaconda.org/CHANNEL

      주의: ``CHANNEL``\ 을 사용자의 클라우드 사용자명으로 바꾼다.

   #. Update Channels 버튼을 클릭한다.

      .. figure:: /img/conda_navigator-channel.png
         :scale: 50 %

         ..

      |

      네비게이터를 종료하고 다시 연다. 로데오 어플리케이션이 **Home** 탭에 나타난다.

      .. figure:: /img/conda_navigator-rodeo.png
         :scale: 50 %

         ..

      |


.. _`troubleshooting4`:

트러블슈팅
=================

콘다 빌드 실패
--------------------

콘다 래시피 빌드에 실패하면 :doc:`../troubleshooting_ko`\ 을 본다.


어플리케이션이 home 창에 나타나지 않을 때
--------------------------------------

* 콘다 패키지가 사용자의 클라우드 채널에 업데이트되었는지 확인한다.

* 사용자의 채널이 채널 목록에 추가되었는지 확인한다.

* ``.anaconda/navigator``\ 디렉토리를 삭제하고 네비게이터를 다시 실행해야 할 수도 있다.

  주의: 윈도우,맥OS,리눅스에서 ``.anaconda/navigator``\ 는 사용자의 홈 디렉토리에 있다.


어플리케이션이 실행되지 않을 때
-------------------------------

어플리케이션이 다음 명령으로 잘작동하는지 확인한다.

.. code-block:: text

    conda run rodeo

로데오가 잘실행되면 ``.anaconda/navigator``\ 디렉토리를 삭제하고 네비게이터를 다시 실행해야 할 수도 있다.

주의: 윈도우, 맥OS, 리눅스에서 ``.anaconda/navigator``\ 는 사용자의 홈 디렉토리에 있다.


.. _`help4`:

추가 정보
=================

`../../commands/build/conda-skeleton-pypi`\ 에서 더 많은 옵션을 볼 수 있다.

윈도우의 **시작** 메뉴 항목을 추가하는 방법은 menuinst_ 문서를 본다.

.. _menuinst: https://github.com/ContinuumIO/menuinst/wiki
