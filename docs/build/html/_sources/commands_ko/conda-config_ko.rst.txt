
.. _config_ref:

conda config
=======================

.. raw:: html

   <PRE>
   <!-- Manpage converted by man2html 3.0.1 -->
   <B>CONDA(1)</B>                         사용자 명령                        <B>CONDA(1)</B>




   </PRE>
   <H2>이름</H2><PRE>
          conda - conda config


   </PRE>
   <H2>설명</H2><PRE>
          사용법: conda config [-h] [--json] [--debug] [--verbose]

          [--system | <B>--env</B> | <B>--file</B> FILE]
                 (<B>--show</B>  | <B>--show-sources</B> | <B>--validate</B> | <B>--describe</B> | <B>--get</B> [KEY
                 [KEY ...]] | <B>--append</B> KEY VALUE | <B>--prepend</B> KEY  VALUE  |  <B>--set</B>
                 KEY VALUE | <B>--remove</B> KEY VALUE | <B>--remove-key</B> KEY)

          .condarc 파일의 설정 값을 변경한다.
          이 명령은 git config 명령을 참고하여 만들어 졌다.
          기본으로 사용자의 .condarc 파일을 변경한다 (<I>user</I> <I>.condarc</I>  <I>path</I>)


   </PRE>
   <H2>옵션</H2><PRE>
      <B>선택</B> <B>인수:</B>
          <B>-h</B>, <B>--help</B>
                 이 명령의 도움말을 보고 종료한다.

          <B>--json</B> 모든 출력을 json으로 보고한다. 콘다를 프로그래머식으로 사용할 때 적합하다.

          <B>--debug</B>
                 디버그 출력을 본다.

          <B>--verbose</B>, <B>-v</B>
                 한번 사용하면 정보, 두번 사용하면 디버그, 세번 사용하면 기록을 본다.

          <B>--system</B>
                 시스템 .condarc 파일을 변경한다. (<I>system</I> <I>.condarc</I> <I>path</I>)
                 이 옵션이 없으면 사용자 설정 파일을 변경한다. (<I>user</I> <I>.condarc</I> <I>path</I>)

          <B>--env</B>  활성화된 콘다 환경의 .condarc 파일을 변경한다.
                 (<I>root</I> <I>pre-</I> <I>fix/envs/conda-docs</I>)
                 활성화된 환경이 없으면 사용자의 설정 파일을 변경한다.
                 (<I>user</I> <I>.condarc</I> <I>path</I>)

          <B>--file</B> FILE
                 주어진 설정 파일을 변경한다. 이 옵션이 없으면 사용자의
                 설정 파일(<I>user</I> <I>.condarc</I> <I>path</I>)이나
                 'CONDARC' 환경 변수에 설정된 경로의 파일을 변경한다.
                 (기본: <I>user</I> <I>.condarc</I> <I>path</I>).

          <B>--show</B> 계산되고 컴파일된 모든 설정값이 나타난다.

          <B>--show-sources</B>
                 식별된 모든 설정 소스가 나타난다.

          <B>--validate</B>
                 모든 설정 소스를 검사한다.

          <B>--describe</B>
                 사용 가능한 설정 매개 변수를 보여준다.

          <B>--get</B> [KEY [KEY ...]]
                 설정값을 얻는다.

          <B>--append</B> KEY VALUE
                 키 목록 끝에 설정값을 하나 추가한다.

          <B>--prepend</B> KEY VALUE, <B>--add</B> KEY VALUE
                 키 목록 앞에 설정값을 하나 추가한다.

          <B>--set</B> KEY VALUE
                 부올리언이나 문자열 키를 설정한다.

          <B>--remove</B> KEY VALUE
                 키 목록에서 설정값을 삭제한다. 이 옵션은 키의 모든 인스턴스를 삭제한다.

          <B>--remove-key</B> KEY
                 설정 키와 그 값을 삭제한다.

          `conda config <B>--describe</B>` 나 https://conda.io/docs/config.html 에서
          .condarc 파일에 사용할 수 있는 모든 옵션에 대한 세부사항을 볼 수 있다.


   </PRE>
   <H2>예시</H2><PRE>
          계산되고 컴파일된 모든 설정값을 본다.

                 conda config --show

          식별된 모든 설정 소스를 본다.

                 conda config --show-sources

          사용 가능한 모든 설정 옵션을 설명한다.

                 conda config --describe

          conda-canary 채널을 추가한다.

                 conda config --add channels conda-canary

          출력 verbosity를 가장 높은 3으로 설정한다.

                 conda config --set verbosity 3




   </PRE>
   <H2>Anaconda, Inc.                     12i 2017                           CONDA(1)</H2><PRE>
   </PRE>
