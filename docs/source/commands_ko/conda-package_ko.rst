
.. _package_ref:

conda package
=======================

.. raw:: html

   <PRE>
   <!-- Manpage converted by man2html 3.0.1 -->
   <B>CONDA(1)</B>                         사용자 명령                        <B>CONDA(1)</B>




   </PRE>
   <H2>이름</H2><PRE>
          conda - conda package


   </PRE>
   <H2>설명</H2><PRE>
          사용법:  conda  package  [-h]  [-n ENVIRONMENT | <B>-p</B> PATH] [-w PATH [PATH
          ...]] [-r]

          [-u] [--pkg-name PKG_NAME] [--pkg-version PKG_VERSION]
                 [--pkg-build PKG_BUILD]

          로우 레벨 콘다 패키지 유틸리티 (실험중)


   </PRE>
   <H2>옵션</H2><PRE>
      <B>선택</B> <B>인수:</B>
          <B>-h</B>, <B>--help</B>
                 이 명령의 도움말을 보고 종료한다.

          <B>-n</B> ENVIRONMENT, <B>--name</B> ENVIRONMENT
                 환경의 이름. (envs 디렉토리 안에서)

          <B>-p</B> PATH, <B>--prefix</B> PATH
                 환경 접두어의 전체 경로  (기본: <I>root</I> <I>prefix/envs/conda-docs</I>).

          <B>-w</B> PATH [PATH ...], <B>--which</B> PATH [PATH ...]
                 콘다 패키지를 가져오는 경로 프린트가 주어진다.

          <B>-r</B>, <B>--reset</B>
                 추적되지 않은 파일을 모두 삭제하고 종료한다.

          <B>-u</B>, <B>--untracked</B>
                 추적되지 않은 모든 파일을 표시하고 종료한다.

          <B>--pkg-name</B> PKG_NAME
                 생성된 패키지의 이름.

          <B>--pkg-version</B> PKG_VERSION
                 생성된 패키지의 버전.

          <B>--pkg-build</B> PKG_BUILD
                 생성된 패키지의 빌드 번호.




   </PRE>
   <H2>Anaconda, Inc.                     12i 2017                           CONDA(1)</H2><PRE>
   </PRE>
