=================
명령 레퍼런스
=================

.. contents::
   :local:
   :depth: 1

콘다는 패키지와 환경 관리를 위한 많은 명령을 제공한다.
이 페이지의 링크에서 각 명령에 대한 도움말을 볼 수 있다.
명령줄에서 ``--help`` 플래그를 사용해도 동일한 도움말을 볼 수 있다.

.. code-block:: bash

   conda install --help


콘다 일반 명령
======================

다음 명령들이 콘다를 구성한다.

.. toctree::
   :glob:
   :maxdepth: 2

   commands_ko/*

콘다 빌드 명령
====================

다음 명령들이 콘다 빌드(conda build) 패키지를 구성한다.
콘다 빌드는 ``conda install conda-build``\ 로 설치할 수 있다.

.. toctree::
   :glob:
   :maxdepth: 2

   commands/build/*

콘다 환경 명령
==========================

다음 명령들이 콘다와 함께 자동 설치되는 콘다 환경(conda-env) 패키지를 구성한다.

.. toctree::
   :glob:
   :maxdepth: 2

   commands_ko/env/*

Conda / pip / virtualenv 명령 비교
=====================================

이전에 pip나 virtualenv를 사용한 경험이 있다면 콘다로도 동일한 작업을 수행할 수 있다.
pip는 패키지 관리자, virtualenv는 환경 관리자이며 콘다는 패키지와 환경을 모두 관리한다.

=====================================   ========================================================   ==========================================================================   ========================================================
작압                                     콘다 패키지/환경 관리 명령                                        pip 패키지 관리 명령                                                             Virtualenv 환경 관리 명령
=====================================   ========================================================   ==========================================================================   ========================================================
패키지 설치                                ``conda install $PACKAGE_NAME``                            ``pip install $PACKAGE_NAME``                                                X
패키지 업데이트                             ``conda update --name $ENVIRONMENT_NAME $PACKAGE_NAME``    ``pip install --upgrade $PACKAGE_NAME``                                      X
패키지 관리자 업데이트                        ``conda update conda``                                     리눅스, 맥OS: ``pip install -U pip`` 윈도우: ``python -m pip install -U pip``    X
패키지 제거                                ``conda remove --name $ENVIRONMENT_NAME $PACKAGE_NAME``    ``pip uninstall $PACKAGE_NAME``                                              X
환경 생성                                  ``conda create --name $ENVIRONMENT_NAME python``           X                                                                            ``cd $ENV_BASE_DIR; virtualenv $ENVIRONMENT_NAME``
환경 활성화                                ``source activate $ENVIRONMENT_NAME``                      X                                                                            ``source $ENV_BASE_DIR/$ENVIRONMENT_NAME/bin/activate``
환경 비활성화                               ``source deactivate``                                      X                                                                            ``deactivate``
사용 가능한 패키지 검색                       ``conda search $SEARCH_TERM``                              ``pip search $SEARCH_TERM``                                                  X
특정 소스로부터 패키지 설치                    ``conda install --channel $URL $PACKAGE_NAME``             ``pip install --index-url $URL $PACKAGE_NAME``                               X
설치된 패키지 나열                           ``conda list --name $ENVIRONMENT_NAME``                    ``pip list``                                                                 X
requirements 파일 생성                    ``conda list --export``                                    ``pip freeze``                                                               X
모든 환경 나열                             ``conda info --envs``                                      X                                                                            Install virtualenv wrapper, then ``lsvirtualenv``
다른 패키지 관리자 설치                       ``conda install pip``                                      ``pip install conda``                                                        X
파이썬 설치                                ``conda install python=x.x``                               X                                                                            X
파이썬 업데이트                             ``conda update python``\*                                  X                                                                            X
=====================================   ========================================================   ==========================================================================   ========================================================

\* ``conda update python`` 명령은 파이썬을 시리즈의 가장 최신 버전으로 업데이트한다. 예를 들어, 파이썬 2.X는 파이썬2의 최신 버전으로 업데이트되고 파이썬 3.X는 파이썬3의 최신 버전으로 업데이트된다.

.. Show what files a package has installed ``pip show --files $PACKAGE_NAME``  not possible
.. Print details on an individual package ``pip show $PACKAGE_NAME``  not possible
.. List available environments   not possible   ``conda info -e``
.. #user will want to pass that through ``tail -n +3 | awk '{print $1;}'``
