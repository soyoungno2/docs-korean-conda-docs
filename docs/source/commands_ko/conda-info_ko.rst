
.. _info_ref:

conda info
=======================

.. raw:: html

   <PRE>
   <!-- Manpage converted by man2html 3.0.1 -->
   <B>CONDA(1)</B>                         사용자 명령                        <B>CONDA(1)</B>




   </PRE>
   <H2>이름</H2><PRE>
          conda - conda info


   </PRE>
   <H2>설명</H2><PRE>
          사용법:  conda info [-h] [--json] [--debug] [--verbose] [--offline] [-a]
          [-e]

                 [-l] [-s] [--root] [--unsafe-channels] [packages [packages ...]]

          현재 콘다 설치에 대한 정보를 표시한다.


   </PRE>
   <H2>옵션</H2><PRE>
      <B>위치</B> <B>인수:</B>
          packages
                 패키지에 대한 정보를 표시한다.

      <B>선택</B> <B>인수:</B>
          <B>-h</B>, <B>--help</B>
                 도움말 메세지를 보고 종료한다.

          <B>--json</B> 모든 출력을 json으로 보고한다. 콘다를 프로그래머식으로 사용할 때 적합하다.

          <B>--debug</B>
                 디버그 출력을 본다.

          <B>--verbose</B>, <B>-v</B>
                 한번 사용하면 정보, 두번 사용하면 디버그, 세번 사용하면 기록을 본다.

          <B>--offline</B>
                 오프라인 모드로 인터넷에 연결하지 않는다.

          <B>-a</B>, <B>--all</B>
                 모든 정보를 본다. (환경, 라이센스, 시스템 정보)

          <B>-e</B>, <B>--envs</B>
                 확인된 모든 콘다 환경을 나열한다.

          <B>-l</B>, <B>--license</B>
                 로컬 콘다 라이센스 목록에 대한 정보를 표시한다.

          <B>-s</B>, <B>--system</B>
                 환경 변수를 나열한다.

          <B>--root</B> 루트 환경 경로를 표시한다.

          <B>--unsafe-channels</B>
                 토큰이 노출된 채널 목록을 표시한다.


   </PRE>
   <H2>예시</H2><PRE>
                 conda info -a




   </PRE>
   <H2>Anaconda, Inc.                     12i 2017                           CONDA(1)</H2><PRE>
   </PRE>
