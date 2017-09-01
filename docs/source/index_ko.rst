.. 콘다 문서 마스터 파일
   Sat Nov  3 16:08:12 2012 에 sphinx-quickstart 로 생성.
   이 파일을 사용자의 선호에 따라 수정해도 되지만 최소한 루트 `toctree` 명령어는 포함해야 한다.

.. =====
.. 콘다
.. =====

.. figure::  images/conda_logo.svg
   :align:   center

**패키지, 하위 요소, 환경 관리를 어떤 언어에서도:Python, R, Scala, Java, Javascript, C/ C++, FORTRAN**

콘다는 오픈소스 패키지 관리 시스템과 환경 관리 시스템으로 여러 버전의 패키지와 그 하위요소를 설치하고 이들 간에 전환을 손쉽게 할 수 있다.
리눅스, OS X, 윈도우에서 작동하고 파이썬 프로그램을 위해 제작 되었지만 어떤 소프트웨어도 배포할 수 있다.

콘다는 아나콘다와 미니콘다에 포함되어 있다. 콘다는 Continuum 아나콘다 `구독 <https://www.continuum.io/anaconda-subscriptions>`_ 에도 포함된다.
아나콘다 구독은 파이썬, R, Node.js, 자바, 그 외 다른 어플리케이션을 위한 기업 실무 패키지와 환경 관리를 제공한다.
pypi 를 통해 콘다를 사용할 수 있지만 최신 버전이 아닐 수 있다.

**미니콘다** 는 콘다, 파이썬 그리고 이들이 의존하는 패키지들을 포함하는 부트스트랩 버전이다.
conda install 커맨드를 사용해 720 여개의 과학 연구용 패키지와 그 하위 요소들을 Continuum 저장소로부터 개별적으로 설치할 수 있다.

**아나콘다** 는 콘다, 콘다 빌드, 파이썬, 150 여개의 자동 설치되는 과학 연구용 패키지와 그 하위 요소를 포함한다.
미니콘다와 마찬가지로 conda install 커맨드를 사용해 250 여개의 추가 과학 연구용 패키지를 설치할 수 있다.

`conda` `아나콘다 <http://docs.continuum.io/anaconda/index.html>`_ 설치를 관리하기 위한 기초 인터페이스이다
아나콘다 패키지 인덱스와 현재 아나콘다 설치를 쿼리, 검색할 수 있고 새로운 환경을 생성하거나 기존 환경에 패키지를 설치, 업데이트 할 수 있다.



.. toctree::
   :hidden:

   announcements_ko
   get-started_ko
   using/index_ko
   building/build_ko
   help/help_ko
   get-involved_ko

프레젠테이션 & 블로그 포스트
--------------------------

`콘다로 패키지화 하고 배포하기 - Travis Oliphant <https://speakerdeck.com/teoliphant/packaging-and-deployment-with-conda>`_

`아나콘다의 파이썬 3 지원 - Ilan Schnell <https://www.continuum.io/content/python-3-support-anaconda>`_

`콘다 진전 사항 - Ilan Schnell <https://www.continuum.io/blog/developer/new-advances-conda>`_

`콘다의 파이선 패키지와 환경 - Bryan Van de Ven <https://www.continuum.io/content/python-packages-and-environments-conda>`_

`콘다 고급 기능, 파트 1 - Aaron Meurer <https://www.continuum.io/blog/developer/advanced-features-conda-part-1>`_

`콘다 고급 기능, 파트 2 - Aaron Meurer <https://www.continuum.io/blog/developer/advanced-features-conda-part-2>`_

요구사항
------------

* 파이썬 2.7, 3.4, 3.5, or 3.6
* pycosat
* pyyaml
* requests

콘다 4.3 에서 달라진 점
------------------------

이번 배포는 성능, 경고와 에러 메시지, 콘다의 디스트 접근, 다운로드, 패키지 캐싱 방법에서 많은 향상을 이루었습니다.
또한 noarch/universal 타입의 파이썬 패키지를 공식 지원하고 파이썬 API 모듈이 추가 되었으며 'r' 채널은 이제 디폴트 채널이 되었습니다.
`changelog <https://github.com/conda/conda/releases/tag/4.3.4>`_ 에서 변경사항을 볼 수 있습니다.

* **Unlink and Link Packages in a Single Transaction**: This provides improved
  error recovery by ensuring that conda is safe, defensive and fault-tolerant
  whenever it changes data on disk.

* **Progressive Fetch and Extract Transactions**: If errors are encountered
  while downloading packages, conda now keeps the packages that downloaded
  correctly and only re-downloads those with errors.

* **Generic- and Python-Type Noarch/Universal Packages**: Along with conda-build 2.1.0, a
  noarch/universal type for python packages is now officially supported. These are much like universal
  python wheels. Files in a python noarch package are linked into a prefix just like any other
  conda package, with the following additional features:

  1. conda maps the ``site-packages`` directory to the correct location for the python version
     in the environment,
  2. conda maps the python-scripts directory to either ``$PREFIX/bin`` or ``$PREFIX/Scripts`` depending
     on platform,
  3. conda creates the python entry points specified in the conda-build recipe, and
  4. conda compiles pyc files at install time when prefix write permissions are guaranteed.

  Python noarch packages must be "fully universal."  They cannot have OS- or
  python version-specific dependencies.  They cannot have OS- or python version-specific "scripts"
  files. If these features are needed, traditional conda packages must be used.

* **Multi-User Package Caches**: Package cache handling has been improved while
  preserving the on-disk package cache structure. Both writable and read-only
  package caches are fully supported.

* **Python API Module**: The new ``conda.cli.python_api`` module allows using
  conda as a Python library without needing to "shell out" to another Python
  process. There is also a ``conda.exports`` module for longer-term use of
  conda as a library across conda releases, although conda's Python code is
  considered internal and private and is subject to change across releases. For
  now conda will not install itself into environments other than its original
  install environment.

* **Remove All Locks**: Locking in conda had bugs and often created a false
  sense of security, and has been removed. The multi-user package caches in
  this release have improved safety by hard-linking packages in read-only
  caches to the user's primary user package cache. However, undefined behavior
  can still result when conda is running in multiple processes and operating on
  the same package caches or the same environments.

* Conda can now refuse to clobber existing files that are not within the unlink
  instructions of the transaction. The `path_conflict` configuration option can
  be set to ``clobber``, ``warn``, and ``prevent``. The current behavior and
  default in 4.3 is ``clobber``. The default in 4.4 will be ``warn``. The
  default in 4.5 and beyond will be ``prevent``. This can be overridden with
  the ``--clobber`` command line flag.

* Conda signed packages were vulnerable and created a false sense of security
  and have now been removed. Work has begun to incorporate The Update Framework
  into conda as a replacement.

* Conda 4.4 will drop support for older versions of conda-build.

* To verify that a channel URL is a valid conda channel, conda now checks that
  ``noarch/repodata.json`` or ``noarch/repodata.json.bz2`` exist. The check
  does pass if one or both of these files exist but are empty.

* A new "trace" log level with extremely verbose output, enabled with the
  ``-v -v -v`` or ``-vvv`` command-line flags, the ``verbose: 3`` configuration
  parameter, or the ``CONDA_VERBOSE=3`` environment variable.

* Conda can now be installed with pip, but only when used as a library or dependency.

* The 'r' channel is now part of the default channels.

* ``conda info`` now shows user-agent, UID, and GID.

* HTTP timeouts are configurable.

* The conda home page is now updated to conda.io.

* Fetch and extract for explicit URLs are now separate passes.

* Vendor URLs are now parsed by urllib3.

* Use of the Cache-Control max-age header for repodata is now implemented.

* Conda now caches repodata locally without remote server calls and has a
  ``repodata_timeout_secs`` configuration parameter.

* Conda now has a ``pkgs_dirs`` configuration parameter, an ``always_softlink``
  option, ``local_repodata_ttl`` configurability, and ``path_conflict`` and
  ``clobber`` configuration options.

* Package resolution/solver hints have been improved with better messaging.

* Further bug fixes, performance improvements, and better error and warning messages.

See the `changelog <https://github.com/conda/conda/releases/tag/4.3.4>`_ for
a complete list of changes.
