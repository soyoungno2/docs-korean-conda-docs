===================
리눅스에서 설치
===================

#. 인스톨러를 다운로드한다.

   * `리눅스용 미니콘다 인스톨러 <https://conda.io/miniconda.html>`_.

   * `리눅스용 아나콘다 인스톨러 <https://www.anaconda.com/download/>`_.

#. 터미널에서 다음을 실행한다.

   * 미니콘다:

     .. code::

        bash Miniconda3-latest-Linux-x86_64.sh

   * 아나콘다:

     .. code::

        bash Anaconda-latest-Linux-x86_64.sh

#. 설치 화면의 프롬프트를 따라 진행한다.

   어떤 설정에 대해 잘모르겠다면 기본으로 설정한다. 이후에 변경할 수 있다.

#. 터미널을 종료하고 다시 열어야 변경사항이 적용된다.

#. :doc:`설치를 테스트한다 <test-installation_ko>`.


.. _install-linux-silent:

자동 설치
=========================

:ref:`맥OS에서 자동 설치 <install-macos-silent>`\ 에서 설명을 볼 수 있다.


아나콘다/미니콘다 업데이트
==============================

#. 터미널을 연다.

#. ``conda update conda``\ 를 실행한다.


아나콘다/미니콘다 삭제
==================================

#. 터미널을 연다.

#. 다음 명령으로 미니콘다 설치 디렉토리를 전체 삭제한다. ::

     rm -rf ~/miniconda

#. 선택: ``~/.bash_profile``\ 을 수정해 미니콘다 디렉토리를 PATH 환경 변수에서 삭제한다.

#. 선택: 홈 디렉토리에 생성되었을 수 있는 숨겨진 파일과 폴더를 삭제한다.

   * ``.condarc`` 파일
   * ``.conda`` 디렉토리
   * ``.continuum`` 디렉토리

   다음을 실행한다. ::

     rm -rf ~/.condarc ~/.conda ~/.continuum
