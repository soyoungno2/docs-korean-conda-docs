.. _build:

=================
패키지 빌드
=================

콘다 패키지를 빌드하려면 :doc:`콘다 빌드(conda build)를 설치 <install-conda-build_ko>`\ 하고
콘다 :doc:`래시피(recipe) <recipe>`\ 를 생성해야 한다.
``conda build`` 명령을 사용해 콘다 래시피로부터 콘다 패키지를 빌드한다.

파이썬 등 다양한 소스 코드 프로젝트로부터 콘다 패키지를 빌드할 수 있다.
파이썬 프로젝트의 패키지화에 대한 도움말은 `셋업툴즈(Setuptools) 문서 <https://setuptools.readthedocs.io/en/latest/>`_\ 를 본다.

팁: 콘다를 사용한 패키지 빌드가 처음이라면 :doc:`튜토리얼 <../../tutorials/index_ko>`\ 을 따라해 본다.

선택: 아나콘다 클라우드(Anaconda Cloud)에 패키지를 업로드할 생각이라면 `아나콘다 클라우드 <http://anaconda.org>`_ 계정과 클라이언트가 있어야 한다.

.. toctree::
   :maxdepth: 1

   install-conda-build_ko
   package-spec
   package-naming-conv_ko
   recipe_ko
   define-metadata
   build-scripts_ko
   features_ko
   environment-variables
   make-relocatable
   link-scripts
   variants
   use-shared-libraries
   compiler-tools
   add-win-start-menu-items
   sample-recipes_ko
   build-without-recipe
   wheel-files
