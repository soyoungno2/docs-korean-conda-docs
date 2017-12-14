========================
탭 자동 완성 활성화
========================

콘다는 argcomplete 패키지를 통해 배쉬(bash) 셸에서 탭 자동완성을 지원한다.

탭 자동 완성을 활성화한다.

#. argcomplete가 설치되었는지 확인한다.

   .. code-block:: bash

      conda install argcomplete

#. 배쉬 프로파일에 다음 코드를 추가한다.

   .. code-block:: bash

      eval "$(register-python-argcomplete conda)"

#. 테스트한다.

   #. 터미널이나 아나콘다 프롬프트를 새로 연다.

   #. ``conda ins``\ 를 입력하고 탭 키를 누른다.

      다음과 같이 나타난다.

      .. code-block:: bash

         conda install

zsh에서 탭 자동 완성을 사용하려면 `콘다 zsh 자동 완성 <https://github.com/esc/conda-zsh-completion>`_\ 을 본다.
