=====================
윈도우에서 설치
=====================

#. 인스톨러를 다운로드 한다.

   * `윈도우용 미니콘다 인스톨러 <https://conda.io/miniconda.html>`_.

   * `윈도우용 아나콘다 인스톨러 <https://www.anaconda.com/download/>`_.

#. ``.exe`` 파일을 더블클릭한다.

#. 화면에 나타난 설명을 따라 진행한다.

   어떤 설정에 대해 잘모르겠다면 기본으로 설정한다. 이후에 변경할 수 있다.

   설치가 완료되면 **시작** 메뉴의 아나콘다 프롬프트를 연다.

#. :doc:`설치를 테스트한다 <test-installation_ko>`.


.. _install-win-silent:

자동 설치
=========================

주의: 다음은 미니콘다를 위한 설명이다. 아나콘다에서는 모든 명령의 ``Miniconda``\ 를 ``Anaconda``\ 로 바꾼다.

윈도우용 미니콘다 인스톨러의 :ref:`자동 설치 <silent-mode-glossary>`\ 를 위해 ``/S`` 인수를 사용한다.
다음 선택 인수를 지원한다.

* ``/InstallationType=[JustMe|AllUsers]``---기본은 ``JustMe``\ 다.
* ``/AddToPath=[0|1]``---기본은 ``1``\ 이다.
* ``/RegisterPython=[0|1]``---현재 시스템의 기본 파이썬을 만든다.
  ``0``\ 은 기본인 ``JustMe``, ``1``\ 은 ``AllUsers``\ 를 나타낸다.
* ``/S``---자동 설치한다.
* ``/D=<installation path>``---설치 경로를 지정한다.
  마지막 인수가 되어야 한다. 인용 문자로 둘러싸지 않는다. ``/S`` 인수를 사용할 때 요구된다.

모든 인수는 대소문자를 구별한다.

예시: 다음 명령은 파이썬을 시스템의 기본 설정으로 등록하지 않고 현재 사용자 계정에 미니콘다를 설치한다.

.. code-block:: bat

   start /wait "" Miniconda4-latest-Windows-x86_64.exe/InstallationType=JustMe /RegisterPython=0 /S /D=%UserProfile%\Miniconda3


콘다 업데이트
==============

#. 시작 메뉴의 아나콘다 프롬프트를 연다.

#. ``anaconda``\ 로 간다.

#. ``conda update conda``\ 를 실행한다.


콘다 삭제
==================

#. 윈도우 제어판에서 프로그램 추가 제거를 클릭한다.

#. Python X.X (미니콘다)를 선택한다. X.X는 사용자의 파이썬 버전이다.

#. 프로그램 삭제를 클릭한다.

주의: 윈도우10에서는 다른 방법으로 삭제한다.
