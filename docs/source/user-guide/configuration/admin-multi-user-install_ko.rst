=============================================
다중 사용자 콘다 설치 관리
=============================================

기본으로 콘다와 아나콘나(Anaconda)를 포함한 콘다가 설치하는 모든 패키지는 사용자 특정 설정으로 로컬에 설치된다.
관리자 권한은 요구되지 않으며 콘다 설치는 업스트림(upstream) 파일이나 다른 사용자에 영향을 주지 않는다.

콘다와 여러 패키지를 한명 이상의 사용자 그룹과 공유하면서 공유받은 사용자가 원치않는 패키지를 설치하는 것을 방지할 수 있다.

#. 관리자 제어 아래 있으면서 사용자가 접근할 수 있는 위치에 콘다와 허용할 패키지를 설치한다.

#. :doc:`.condarc 시스템 설정 파일 <use-condarc_ko>`\ 을 설치의 루트 디렉토리에 생성한다.
   이 시스템 레벨 설정 파일은 사용자에 의해 생성된 다른 사용자 레벨 설정 파일을 덮어쓴다.

각 사용자는 홈 디렉토리에 있는 사용자의 ``.condarc`` 설정 파일의 설정을 읽는 중앙 콘다 설치에 접근한다.
:ref:`admin-inst-user`\ 에서 보여지는 대로 사용자 파일로의 경로는 ``conda info`` 명령으로 나타나는 루트 환경 접두어(prefix)와 같다.
사용자의 ``.condarc`` 파일은 시스템의 ``.condarc`` 파일에 의해 제한된다.

시스템 구성 설정은 주로 시스템 ``.condarc`` 파일에 사용되지만 사용자 ``.condarc`` 파일에도 사용될 수 있다.
모든 사용자 구성 설정 또한 시스템 ``.condarc`` 파일에 사용될 수 있다.

``.condarc`` 파일 설정에 대한 정보는 :doc:`use-condarc_ko`\ 에 있다.


.. _admin-inst:

관리자 제어 설치 예시
=============================================

다음 예시는 시스템 설정 파일을 읽어 설정을 검토하고 사용자의 설정 파일과 비교하는 방법을 설명한다.
사용자가 차단된 채널의 파일에 접근할 때 어떤 일이 생기는지도 볼 것이다.
그리고 관리자에 의해 허용된 채널에 접근하기 위해 설정 파일에 어떤 수정을 해야 하는지 설명한다.


시스템 설정 파일
---------------------------

#. 시스템 설정 파일은 반드시 콘다 설치 디렉토리의 최상위에 있어야 한다. 콘다가 위치한 경로를 확인한다.

   .. code-block:: bash

      $ which conda
      /tmp/miniconda/bin/conda

#. 관리자 디렉토리에 있는 ``.condarc`` 파일의 내용을 본다.

   .. code-block:: bash

      cat /tmp/miniconda/.condarc

   다음 관리자 ``.condarc`` 파일은 ``allow_other_channels``\ 를 ``False``\ 로 설정해
   사용자가 ``admin`` 채널에서만 패키지를 다운 받을 수 있게 설정한다.

   .. code-block:: bash

     $ cat /tmp/miniconda/.condarc
     allow_other_channels : false
     channel_alias: https://conda.anaconda.org/
     channels:
       - admin

   주의: admin 채널은 https://conda.anaconda.org/admin/ 로 나타낼 수도 있다.

   ``allow_other_channels``\ 가 ``False``\ 이고 기본 채널이 명시적으로 설정되지 않았기 때문에
   사용자는 기본 채널에서 패키지를 다운로드할 수 없다. 다음 단계에서 이를 확인한다.

.. _admin-inst-user:

사용자 설정 파일
-------------------------

#. 사용자의 콘다가 설치된 위치를 확인한다.

   .. code-block:: bash

     $ conda info
     Current conda install:
     . . .
            channel URLs : http://repo.continuum.io/pkgs/free/osx-64/
                           http://repo.continuum.io/pkgs/pro/osx-64/
            config file : /Users/gergely/.condarc

   ``conda info`` 명령으로 콘다가 ``/Users/gergely/.condarc``\ 에 있는 ``.condarc`` 파일과
   기본 채널로 channel URLs에 나열된 ``repo.continuum.io``\ 와 같은 채널을 사용함을 알 수 있다.

#. 1단계에서 확인한 디렉토리에서 ``.condarc`` 파일의 내용을 본다.

   .. code-block:: bash

     $ cat ~/.condarc
     channels:
       - defaults

   이 사용자 ``.condarc`` 파일은 기본 채널만을 지정하지만
   관리자 설정 파일은 허용 채널을 ``admin``\ 으로만 지정해 기본 채널을 차단하고 있다.
   이 사용자가 기본 채널에서 패키지를 검색하면 다음과 같은 메세지가 나타나고 허용되는 채널을 알 수 있다.

   .. code-block:: bash

      $ conda search flask
      Fetching package metadata:
      Error: URL 'http://repo.continuum.io/pkgs/pro/osx-64/' not
      in allowed channels.
      Allowed channels are:
       - https://conda.anaconda.org/admin/osx-64/

   이 에러 메세지는 사용자의 설정 파일에 ``admin`` 채널을 추가해야 함을 알려준다.

#. 사용자는 반드시 로컬 ``.condarc`` 설정 파일을 수정해 admin 채널을 통해 패키지에 접근해야 한다.

   .. code-block:: yaml

     channels:
       - admin

   이제 사용자는 허용된 ``admin`` 채널에서 패키지를 검색할 수 있다.
