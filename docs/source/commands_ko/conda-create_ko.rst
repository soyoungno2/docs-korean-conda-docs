
.. _create_ref:

conda create
=======================

.. raw:: html

   <PRE>
   <!-- Manpage converted by man2html 3.0.1 -->
   <B>CONDA(1)</B>                         사용자 명령                        <B>CONDA(1)</B>
   
   
   
   
   </PRE>
   <H2>이름</H2><PRE>
          conda - conda create

   
   </PRE>
   <H2>설명</H2><PRE>
          사용법:   conda   create   [-h]  [-y]  [--dry-run]  [-f]  [--file  FILE]
          [--no-deps] [-m]
   
          [--use-index-cache] [--use-local] [--offline] [--no-pin]
                 [-c CHANNEL] [--override-channels] [-n ENVIRONMENT  |  <B>-p</B>  PATH]
                 [-q]  [--copy] [--clobber] [-k] [--alt-hint] [--update-dependen-
                 cies]      [--no-update-dependencies]       [--channel-priority]
                 [--no-channel-priority]  [--show-channel-urls]  [--no-show-chan-
                 nel-urls]   [--json]   [--debug]   [--verbose]   [--clone   ENV]
                 [--no-default-packages] [package_spec [package_spec ...]]
   
          지정된 패키지 목록으로부터 새로운 콘다 환경을 생성한다.
          생성된 환경을 사용하려면 'source activate envname' 명령을 사용한다.
          이 명령은 <B>-n</B> NAME 이나 <B>-p</B> PREFIX 옵션을 필요로 한다.
   
   
   </PRE>
   <H2>옵션</H2><PRE>
      <B>위치</B> <B>인수:</B>
          package_spec
                 콘다 환경에 설치할 패키지다.

      <B>선택</B> <B>인수:</B>
          <B>-h</B>, <B>--help</B>
                 이 명령의 도움말을 보고 종료한다.

          <B>-y</B>, <B>--yes</B>
                 진행 중에 확인을 요청하지 않는다.

          <B>--dry-run</B>
                 수행된 작업만을 표시한다.

          <B>-f</B>, <B>--force</B>
                 이미 설치된 패키지라도 강제 설치한다. <B>--no-deps</B> 를 내포한다.
   
          <B>--file</B> FILE
                 주어진 파일의 패키지 버전을 읽는다. 파일 사양을 반복해서 보낼 수 있다.
                 (예시: <B>--file</B>=<I>file1</I> <B>--file</B>=<I>file2</I>).
   
          <B>--no-deps</B>
                 의존 요소를 설치하지 않는다.

          <B>-m</B>, <B>--mkdir</B>
                 환경 디렉토리가 필요하면 생성한다.

          <B>--use-index-cache</B>
                 채널 인덱스 파일의 캐시를 사용한다.

          <B>--use-local</B>
                 로컬에서 빌드된 패키지를 사용한다.

          <B>--offline</B>
                 오프라인 모드로 인터넷에 연결하지 않는다.

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
                 default 나 .condarc 에 설정된 채널을 검색하진 않는다.
                 <B>--channel</B> 옵션을 요구한다.
   
          <B>-n</B> ENVIRONMENT, <B>--name</B> ENVIRONMENT
                 환경의 이름이다.(envs 디렉토리에서)
   
          <B>-p</B> PATH, <B>--prefix</B> PATH
                 콘다 환경 접두어로의 전체 경로다.
                 (기본:   <I>root</I>  <I>pre-</I> <I>fix/envs/conda-docs</I>).
   
          <B>-q</B>, <B>--quiet</B>
                 프로그레스 바가 나타나지 않는다.

          <B>--copy</B> 하드 링크와 소프트 링크를 사용하지 않고 패키지를 모두 복사해서 설치한다.

          <B>--clobber</B>
                 패키지 내부의 파일 경로를 덮어쓰는 클로버링을 허용하고
                 관련 경고를 출력하지 않는다.

          <B>-k</B>, <B>--insecure</B>
                 콘다가 안전하지 않은 SSL 연결과 전송을 하도록 허용한다.
                 'ssl_verify'를 'false'로 설정하는 것과 동일하다.

          <B>--alt-hint</B>
                 대체 알고리즘을 사용해 충족 불가 힌트를 생성한다.

          <B>--update-dependencies</B>, <B>--update-deps</B>
                 의존 요소를 업데이트한다. (기본: True).
   
          <B>--no-update-dependencies</B>, <B>--no-update-deps</B>
                 의존 요소를 업데이트하지 않는다. (기본: False).
   
          <B>--channel-priority</B>, <B>--channel-pri</B>, <B>--chan-pri</B>
                 패키지 버전보다 채널 선호도를 우선한다. (기본: True)
                 주의: 이 기능은 베타이며 이후 배포에 변경될 수 있다.

          <B>--no-channel-priority</B>, <B>--no-channel-pri</B>, <B>--no-chan-pri</B>
                 채널 선호도보다 패키지 버전을 우선한다. (기본:False)
                 주의: 이 기능은 베타이며 이후 배포에 변경될 수 있다.

          <B>--show-channel-urls</B>
                 채널 url을 본다. (기본: None)

          <B>--no-show-channel-urls</B>
                 채널 url을 보지 않는다.

          <B>--json</B> 모든 출력을 json으로 보고한다. 콘다를 프로그래머식으로 사용할 때 적합하다.

          <B>--debug</B>
                 디버그 출력을 본다.

          <B>--verbose</B>, <B>-v</B>
                 한번 사용하면 정보, 두번 사용하면 디버그, 세번 사용하면 기록을 본다.
   
          <B>--clone</B> ENV
                 기존 로컬 디렉토리의 이름 또는 경로.

          <B>--no-default-packages</B>
                 .condarc 파일의 create_default_packages 설정을 무시한다.

   
   </PRE>
   <H2>예시</H2><PRE>
                 conda create -n myenv sqlite
   
   
   
   
   </PRE>
   <H2>Anaconda, Inc.                     12i 2017                           CONDA(1)</H2><PRE>
   </PRE>
