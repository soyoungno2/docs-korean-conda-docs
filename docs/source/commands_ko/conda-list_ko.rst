
.. _list_ref:

conda list
=======================

.. raw:: html

   <PRE>
   <!-- Manpage converted by man2html 3.0.1 -->
   <B>CONDA(1)</B>                         사용자 명령                        <B>CONDA(1)</B>
   
   
   
   
   </PRE>
   <H2>이름</H2><PRE>
          conda - conda list
   
   
   </PRE>
   <H2>설명</H2><PRE>
          사용법: conda list [-h] [-n ENVIRONMENT | <B>-p</B> PATH] [--json] [--debug]
   
                 [--verbose]  [--show-channel-urls] [--no-show-channel-urls] [-c]
                 [-f] [--explicit] [--md5] [-e] [-r] [--no-pip] [regex]
   
          콘다 환경에 연결된 패키지를 나열한다.

   
   </PRE>
   <H2>옵션</H2><PRE>
      <B>위치</B> <B>인수:</B>
          regex  이 정규 표현식과 일치하는 패키지만 나열한다.

      <B>선택</B> <B>인수:</B>
          <B>-h</B>, <B>--help</B>
                 이 명령의 도움말을 보고 종료한다.
   
          <B>-n</B> ENVIRONMENT, <B>--name</B> ENVIRONMENT
                 환경의 이름. (envs 디렉토리 안에서)

          <B>-p</B> PATH, <B>--prefix</B> PATH
                 환경 접두어의 전체 경로   (기본: <I>root</I> <I>prefix/envs/conda-docs</I>).
   
          <B>--json</B> 모든 출력을 json으로 보고한다. 콘다를 프로그래머식으로 사용할 때 적합하다.

          <B>--debug</B>
                 디버그 출력을 본다.

          <B>--verbose</B>, <B>-v</B>
                 한번 사용하면 정보, 두번 사용하면 디버그, 세번 사용하면 기록을 본다.
   
          <B>--show-channel-urls</B>
                 채널 url을 본다. (기본: None)
   
          <B>--no-show-channel-urls</B>
                 채널 url을 보지 않는다.
   
          <B>-c</B>, <B>--canonical</B>
                 패키지의 정식 명칭만을 출력한다. <B>--nopip</B> 를 내포한다.
   
          <B>-f</B>, <B>--full-name</B>
                 전체 이름만을 검색한다. 예시: ^&lt;regex&gt;$.
   
          <B>--explicit</B>
                 설치된 모든 콘다 패키지와 URL을 명시적으로 나열한다.
                 (출력은 conda create <B>--file</B> 에 사용될 수 있다.)

          <B>--md5</B>  <B>--explicit</B> 을 사용할 때 MD5 해시합을 추가한다.

          <B>-e</B>, <B>--export</B>
                 요구사항 문자열만을 출력한다.
                 (출력은 conda create <B>--file</B> 에 사용될 수 있다.)
   
          <B>-r</B>, <B>--revisions</B>
                 리비전 기록을 나열하고 종료한다.

          <B>--no-pip</B>
                 pip에서만 설치할 수 있는 패키지를 포함하지 않는다.

   
   </PRE>
   <H2>예시</H2><PRE>
          현재 환경의 모든 패키지를 나열한다.

                 conda list
   
          'myenv' 환경에 설치된 모든 패키지를 나열한다.

                 conda list -n myenv
   
          나중을 위해 패키지를 저장한다.

                 conda list --export &gt; package-list.txt
   
          export 파일의 패키지를 재설치한다.

                 conda create -n myenv --file package-list.txt
   
   
   
   
   </PRE>
   <H2>Anaconda, Inc.                     12i 2017                           CONDA(1)</H2><PRE>
   </PRE>
