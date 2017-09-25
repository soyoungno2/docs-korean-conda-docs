======================
Microsoft R Open 사용
======================

R 언어의 배포판인 `Microsoft R Open (MRO) <https://mran.revolutionanalytics.com/download/mro-for-mrs/>`_ 를 콘다로 쉽게 설치할 수 있다. MRO R 언어와 다수의 프로그램들을 `아나콘다 클라우드 채널 MRO <https://anaconda.org/mro/packages/>`_ 에서 얻을 수 있다.

운영 체제 지원
---------------------------

* 64 비트 운영체제만 지원 (윈도우, OS X, 리눅스)
* 윈도우: Windows® 7.0 (SP1), 8.1, 10, and Windows Server® 2008 R2 (SP1) and 2012
* OS X: Mavericks (10.9), Yosemite (10.10), and El Capitan (10.11)
* 리눅스: CentOS, Red Hat Enterprise Linux, Debian, Ubuntu.

MRO 와 다른 R 패키지 설치
--------------------------------------------

MRO 와 다른 R 패키지를 설치하기 위한 몇가지 방법이 있다.:

* "r" 채널의 :doc:`.condarc 구성 파일<config_ko>` 에 "mro" 채널을 추가한다. ``conda install r`` 을 사용해 r 을 설치하고 콘다를 사용해 다른 패키지들을 설치한다.
* conda install 커맨드를 사용할 때마다 "mro" 채널을 지정한다.:``conda install -c mro r``
* Comprehensive R Archive Network (CRAN) 또는 Microsoft R Application Network (MRAN) 로부터 R 패키지를 설치한다. 이 방법을 사용하면 현재 활성화된 콘다 환경에 R 패키지가 설치된다. MRO 에 포함되는 `체크포인트 패키지 <https://github.com/RevolutionAnalytics/checkpoint/>`_ 는 MRAN 로부터 설치되고 향상된 `재현성 <https://mran.revolutionanalytics.com/documents/rro/reproducibility/>`_ 을 제공한다.

MRO 또는 R 패키지 사용
------------------------------

MRO 나 다른 R 패키지를 사용하려면 먼저 콘다 환경을 활성화 해야한다. 활성화 된 환경에는 MRO 와 R 패키지가 설치돼 환경 변수가 알맞게 설치되어 있어야 한다.

주의: 먼저 프로그램의 환경을 활성화 해야 한다. 환경을 활성화 하지 않고 그 환경 경로 상의 프로그램을 실행하면 오류가 발생할 수 있다.

주의: 각각의 콘다 환경은 "r" 채널 **또는** "mro" 채널로부터 설치된 패키지를 가질 수 있지만 어떤 콘다 환경도 두 채널 모두로부터 패키지를 설치하진 않는다. 패키지를 설치하는데 두가지 채널을 모두 사용하면 오류가 발생할 수 있다. 오류가 발생했다면 ``conda remove`` 커맨드로 잘못 설치된 패키지를 제거하거나 환경을 새로 생성한다.

Intel Math Kernel Library (MKL) 와 Microsoft R Open (MRO) 설치
-----------------------------------------------------------------------

Intel Math Kernel Library (MKL) 확장은 윈도우나 리눅스 상의 MRO 에서 사용가능하다. OS X 에서는 Accerlate 라이브러리를 사용한다. `운영 체제 별 MKL 패키지 다운로드 <https://mran.revolutionanalytics.com/download/>`_ 에서 다운로드 받고 아래 설명을 따라 설치하면 된다.

주의: 설치 프로세스를 사용하고 있다면 이미 `MKL 라이센스 <https://mran.revolutionanalytics.com/assets/text/mkl-eula.txt>`_ 에 동의한 것으로 간주한다. 이후의 진행은 라이센스에 대한 암묵적 동의가 된다.

MKL 이 설치되지 않았다면 R 인터프리터가 실행될 때마다 아래와 같은 메시지가 나타난다.::

  No performance acceleration libraries were detected. To take advantage of the 
  available processing power, also install MKL for MRO 3.2.3. Visit 
  http://go.microsoft.com/fwlink/?LinkID=698301 for more details.

MKL 확장이 제대로 설치되면 R 인터프리터가 실행될 때마다 아래와 같이 MKL 이 유효하다는 메시지가 나타난다.::

  Multithreaded BLAS/LAPACK libraries detected.

(MKL 과 같은 BLAS/LAPACK 라이브러리는 LAPACK 선형대수 패키지의 기초 선형대수 하위 프로그램 사양을 구현한 것이다.)

윈도우에서 MKL 설치
---------------------------

1. 알맞은 MKL 설치 파일 다운로드.
2. R의 디렉토리를 찾는다. 이를 위해 현재 사용자의 홈 디렉토리, 아나콘다 또는 미니콘다 디렉토리, 환경 디렉토리, 현재 환경 디렉토리를 본다. 예를 들어, 윈도우 8과 아나콘다를 사용하고 사용자명은 jsmith, 환경명은 my_r_env 라면 ``C:\Users\jsmith\Anaconda\envs\my_r_env\R`` 가 된다.
3. 인스톨러를 실행하고 "Enter a path to MRO" 가 나타났을 때 방금 위에서 찾은 경로를 입력한다.

이제 R 인터프리터를 실행하면 MKL 이 유효하다는 메시지가 나올 것이다.

윈도우에서 MKL 을 제거하고 R 언어를 계속 사용하고 싶다면 윈도우 관리자에서 MKL 을 제거하면 된다.

리눅스에서 MKL 설치
-------------------------

1. 적절한 MKL 패키지를 다운로드하고 추출해 현재 폴더에 넣는다. 우리는 이를 $REVOMATH 라 부른다.
2. R 이 위치할 곳을 정한다. 경로는 ``/path/to/anaconda/envs/<r environment>`` 과 같은 형태가 되고 우리는 이를 $PREFIX 라 부른다. $PREFIX 에 작성 권한이 있는지 확인한다.
3. ``$PREFIX/lib/R/lib/libRblas.so`` 과 ``$PREFIX/lib/R/lib/libRlapack.so`` 의 백업을 만들어둔다.
4. ``$REVOMATH/mkl/libs/*.so`` 의 모든 .so 파일을 ``$PREFIX/lib/R/lib`` 로 복사한다. (libRblas.so 과 libRlapack.so. 를 덮어써야 할 수도 있다.)
5. ``$PREFIX/lib/R/etc/Rprofile.site`` 파일을 열고 상단에 아래 두 줄을 추가한다.::

     Sys.setenv("MKL_INTERFACE_LAYER"="GNU,LP64")
     Sys.setenv("MKL_THREADING_LAYER"="GNU")

6. 다음을 실행한다.: ``R CMD INSTALL $REVOMATH/RevoUtilsMath.tar.gz``

콘다와 MRO 에 대한 추가 도움말
----------------------------

콘다에서 MRO 를 사용에 대한 커뮤니티 도움을 위해 `콘다 <https://groups.google.com/a/continuum.io/forum/#!forum/conda>`_ 이메일 그룹에 가입하길 바란다.
 
