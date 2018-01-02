
.. _search_ref:

conda search
=======================

.. raw:: html

   <PRE>
   <!-- Manpage converted by man2html 3.0.1 -->
   <B>CONDA(1)</B>                         사용자 명령                        <B>CONDA(1)</B>
   
   
   
   
   </PRE>
   <H2>이름</H2><PRE>
          conda - conda search
   
   
   </PRE>
   <H2>설명</H2><PRE>
          사용법: conda search [-h] [-n ENVIRONMENT | <B>-p</B> PATH] [--canonical] [-f]
   
          [--names-only] [--use-index-cache] [-o]
                 [--platform  {win-32,win-64,osx-64,linux-32,linux-64}]  [--spec]
                 [--reverse-dependency]   [--offline]   [-c   CHANNEL]   [--over-
                 ride-channels] [--json] [--debug] [--verbose] [--use-local] [-k]
                 [regex]
   
          패키지를 검색하고 그 정보를 표시한다. 입력은 파이썬 정규 표현식이다.
          -로 시작하는 검색 문자열로 검색하기 위해 <B>--</B> 를 사용해 search와 옵션을 분리한다.
          'conda search <B>--</B> <B>-h</B>' 와 같이 한다.
   
          결과의 별표(*)는 현재 환경에 그 패키지가 설치된다는 의미다.
          A는 패키지가 설치되진 않았지만 pkgs 디렉토리에 캐시되어 있다는 의미다.

   
   </PRE>
   <H2>옵션</H2><PRE>
      <B>위치</B> <B>인수:</B>
          regex  이 명령으로 검색할 패키지 사양이나 파이썬 정규 표현식이다. (기본: 모든 패키지를 표시한다.)

      <B>선택</B> <B>인수:</B>
          <B>-h</B>, <B>--help</B>
                 이 명령의 도움말을 보고 종료한다.
   
          <B>-n</B> ENVIRONMENT, <B>--name</B> ENVIRONMENT
                 환경의 이름이다.(envs 디렉토리에서)
   
          <B>-p</B> PATH, <B>--prefix</B> PATH
                 콘다 환경 접두어로의 전체 경로다.  (기본: <I>root</I>  <I>prefix/envs/conda-docs</I>).

          <B>--canonical</B>
                 패키지의 정식 명칭만을 출력한다.
   
          <B>-f</B>, <B>--full-name</B>
                 전체 이름만을 검색한다. 예시: ^&lt;regex&gt;$.
   
          <B>--names-only</B>
                 패키지 이름만을 출력한다.

          <B>--use-index-cache</B>
                 채널 인덱스 파일의 캐시를 사용한다.
   
          <B>-o</B>, <B>--outdated</B>
                 설치되었지만 만료된 패키지만을 표시한다.

          <B>--platform</B> {win-32,win-64,osx-64,linux-32,linux-64}
                 주어진 플랫폼을 검색한다.
                 'osx-64', 'linux-32', 'win-64'와 같은 형식이어야 한다. 기본은 현재 플랫폼을 검색한다.

          <B>--spec</B> (package_name[=version[=build]]) 대신 regex  인수를 패키지 사양으로 취급한다.

          <B>--reverse-dependency</B>
                 반대 의존 요소 검색을 수행한다.
                 이 플래그를 사용할 때는 <B>--full-name</B> 플래그를 권장한다.
                 'conda info package'를 사용해 패키지 의존 요소를 본다.

          <B>--offline</B>
                 오프라인 모드로 인터넷에 연결하지 않는다.
   
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
   
          <B>--json</B> 모든 출력을 json으로 보고한다. 콘다를 프로그래머식으로 사용할 때 적합하다.

          <B>--debug</B>
                 디버그 출력을 본다.
   
          <B>--verbose</B>, <B>-v</B>
                 한번 사용하면 정보, 두번 사용하면 디버그, 세번 사용하면 기록을 본다.
   
          <B>--use-local</B>
                 로컬에서 빌드된 패키지를 사용한다.
   
          <B>-k</B>, <B>--insecure</B>
                 콘다가 안전하지 않은 SSL 연결과 전송을 하도록 허용한다.
                 'ssl_verify'를 'false'로 설정하는 것과 동일하다.
   
   
   </PRE>
   <H2>예시</H2><PRE>
          이름이 'scikit' 인 패키지를 검색한다.

                 conda search scikit
   
          'python'  패키지를 검색한다. (이름에 'python'을 포함하는 패키지는 검색하지 않는다.)

                 conda search -f python
   
          64비트 리눅스를 위한 패키지를 검색한다. (기본으로 현재 플랫폼을 위한 패키지가 나타난다.)

                 conda search --platform linux-64
   
   
   
   
   </PRE>
   <H2>Anaconda, Inc.                     12i 2017                           CONDA(1)</H2><PRE>
   </PRE>
