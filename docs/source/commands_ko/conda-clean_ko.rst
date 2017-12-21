
.. _clean_ref:

conda clean
=======================

.. raw:: html

   <PRE>
   <!-- Manpage converted by man2html 3.0.1 -->
   <B>CONDA(1)</B>                         사용자 명령                        <B>CONDA(1)</B>




   </PRE>
   <H2>이름</H2><PRE>
          conda - conda clean


   </PRE>
   <H2>설명</H2><PRE>
          사용법: conda clean [-h] [-y] [--dry-run] [--json] [--debug] [--verbose]
          [-a]

                 [-i] [-l] [-t] [-p] [-s]

          사용하지 않는 패키지와 캐시를 삭제한다.


   </PRE>
   <H2>옵션</H2><PRE>
      <B>선택</B> <B>인수:</B>
          <B>-h</B>, <B>--help</B>
                 명령의 도움말을 보고 종료한다.

          <B>-y</B>, <B>--yes</B>
                 진행 중에 확인을 요청하지 않는다.

          <B>--dry-run</B>
                 수행된 작업만을 표시한다.

          <B>--json</B> 모든 출력을 json으로 보고한다. 콘다를 프로그래머식으로 사용할 때 적합하다.

          <B>--debug</B>
                 디버그 출력을 본다.

          <B>--verbose</B>, <B>-v</B>
                 한번 사용하면 정보, 두번 사용하면 디버그, 세번 사용하면 기록을 본다.

          <B>-a</B>, <B>--all</B>
                 인덱스 캐시, 잠금 파일, 타르볼, 사용하지 않는 캐시 패키지,
                 소스 캐시를 삭제한다.

          <B>-i</B>, <B>--index-cache</B>
                 인덱스 캐시를 삭제한다.

          <B>-l</B>, <B>--lock</B>
                 모든 콘다 잠금 파일을 삭제한다.

          <B>-t</B>, <B>--tarballs</B>
                 캐시된 패키지 타르볼을 제거한다.

          <B>-p</B>, <B>--packages</B>
                 사용하지 않는 캐시 패키지를 삭제한다.
                 주의: 심볼릭 링크된 패키지를 확인하지 않는다.

          <B>-s</B>, <B>--source-cache</B>
                 콘다 빌드의 소스 캐시 파일을 삭제한다.


   </PRE>
   <H2>예시</H2><PRE>
                 conda clean --tarballs




   </PRE>
   <H2>Anaconda, Inc.                     12i 2017                           CONDA(1)</H2><PRE>
   </PRE>
