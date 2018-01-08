
.. _uninstall_ref:

conda uninstall
=======================

.. raw:: html

   <PRE>
   <!-- Manpage converted by man2html 3.0.1 -->
   <B>CONDA(1)</B>                         사용자 명령                        <B>CONDA(1)</B>




   </PRE>
   <H2>이름</H2><PRE>
          conda - conda uninstall


   </PRE>
   <H2>설명</H2><PRE>
          사용법: conda uninstall [-h] [-y] [--dry-run] [--json] [--debug] [--ver-
          bose]

          [--all] [--features] [--force] [--no-pin] [-c CHANNEL]
                 [--override-channels]  [-n   ENVIRONMENT   |   <B>-p</B>   PATH]   [-q]
                 [--no-use-index-cache]     [--use-index-cache]     [--use-local]
                 [--offline] [-k] [package_name [package_name ...]]

          conda remove 명령의 별칭. conda remove <B>--help</B> 를 본다.


   </PRE>
   <H2>옵션</H2><PRE>
      <B>위치</B> <B>인수:</B>
          package_name
                 환경에서 삭제할 패키지 이름.

      <B>선택</B> <B>인수:</B>
          <B>-h</B>, <B>--help</B>
                 이 명령의 도움말을 보고 종료한다.

          <B>-y</B>, <B>--yes</B>
                 진행 중에 확인을 요청하지 않는다.

          <B>--dry-run</B>
                 수행된 작업만을 표시한다.

          <B>--json</B> 모든 출력을 json으로 보고한다. 콘다를 프로그래머식으로 사용할 때 적합하다.

          <B>--debug</B>
                 디버그 출력을 본다.

          <B>--verbose</B>, <B>-v</B>
                 한번 사용하면 정보, 두번 사용하면 디버그, 세번 사용하면 기록을 본다.

          <B>--all</B>  모든 패키지를 삭제한다. 환경 전체를 삭제하는 것과 같다.

          <B>--features</B>
                 패키지 대신 기능을 삭제한다.

          <B>--force</B>
                 패키지를 강제 삭제하고 그 패키지에 의존하는 패키지는 삭제하지 않는다.
                 이 옵션으로 인해 환경이 손상되거나 일관성을 잃을 수 있다.

          <B>--no-pin</B>
                 고정된 파일을 무시한다.

          <B>-c</B> CHANNEL, <B>--channel</B> CHANNEL
                 패키지를 검색할 추가 채널이다. 이 URL들은 주어진 순서대로 검색된다.
                 (로컬 디렉토리를 위한 file:// 형태의 URL 포함)
                 다음엔 디폴트와 .condarc 파일의 채널을 검색한다.
                 (<B>--override-channels</B> 가 주어지지 않았을 때)
                 'defaults'를 사용해 콘다를 위한 기본 패키지를 얻거나
                 'system'을 사용해 시스템 패키지를 얻을 수 있다.
                 아무 이름이나 사용하면 .condarc의 channel_alias 값이 붙는다.
                 기본 channel_alias는 http://conda.anaconda.org/ 다.

          <B>--override-channels</B>
                 default 나 .condarc 에 설정된 채널을 검색하진 않는다. <B>--channel</B> 옵션을 요구한다.

          <B>-n</B> ENVIRONMENT, <B>--name</B> ENVIRONMENT
                 환경의 이름이다.(envs 디렉토리에서)

          <B>-p</B> PATH, <B>--prefix</B> PATH
                 콘다 환경 접두어로의 전체 경로다. (기본: <I>root</I>  <I>prefix/envs/conda-docs</I>).

          <B>-q</B>, <B>--quiet</B>
                 프로그레스 바가 나타나지 않는다.

          <B>--no-use-index-cache</B>
                 채널 인덱스 파일을 강제로 가져온다.

          <B>--use-index-cache</B>
                 채널 인덱스 파일의 캐시를 사용한다.

          <B>--use-local</B>
                 로컬에서 빌드된 패키지를 사용한다.

          <B>--offline</B>
                 오프라인 모드로 인터넷에 연결하지 않는다.

          <B>-k</B>, <B>--insecure</B>
                 콘다가 안전하지 않은 SSL 연결과 전송을 하도록 허용한다.
                 'ssl_verify'를 'false'로 설정하는 것과 동일하다.


   </PRE>
   <H2>예시</H2><PRE>
                 conda uninstall -n myenv scipy




   </PRE>
   <H2>Anaconda, Inc.                     12i 2017                           CONDA(1)</H2><PRE>
   </PRE>
