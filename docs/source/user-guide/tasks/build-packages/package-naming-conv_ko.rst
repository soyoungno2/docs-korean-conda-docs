==========================
패키지 작명 규칙
==========================

문서화와 소통이 용이하도록 콘다는 아래에 나열된 패키지 작명 규칙을 따른다.

.. _package_name:
.. index::
    pair: terminology; package name
    seealso: name; package name

패키지 이름
============

패키지 이름으로 특정 버전을 나타내지 않는다.
콘다 패키지 이름은 표준화되어 있고 소문자 알파뱃, 숫자, 밑줄(_), 하이픈(-), 점(.)만을 사용한다.
사용 문서에서 ``package_name``\ 으로 나타낸다.

.. _package_version:
.. index::
    pair: terminology; package version
    seealso: name; package version

패키지 버전
===============

버전 번호 또는 문자열로 주로 ``X.Y``\ 이나 ``X.Y.Z``\ 의 형태이다. 다른 형태도 사용될 수 있다.

.. _build_string:
.. index::
    pair: terminology; build string
    seealso: name; build string

빌드 문자열
============

An arbitrary string that identifies a particular build of a
package for conda.  It may contain suggestive mnemonics, but
these are subject to change, and you should not rely on it or try
to parse it for any specific information.

.. _canonical_name:
.. index::
    pair: terminology; canonical name
    seealso: name; canonical name

정식 명칭
==============

패키지 이름에 버전과 빌드 문자열을 하이픈(-)으로 합쳐 사용한다. 패키지이름-버전-빌드문자열 형태이다.
사용 문서에서 ``canonical_name``\ 으로 나타낸다.

.. _filename:
.. index::
    pair: terminology; filename

파일명
========

콘다 패키지 파일명은 정식 명칭에 접미어(suffix) ``.tar.bz2``\ 를 더해 사용한다.

다음 도표는 패키지 정식 명칭과 파일명을 비교한다.

.. figure:: /img/conda_names.png
   :align:  center

   콘다 패키지 작명.

|


.. _package_spec:
.. index::
    pair: terminology; package specification
    seealso: package spec; package specification

패키지 사양
=====================

패키지 이름과 패키지 버전 사이에 등호를 둔다. 패키지 버전은 쓰지 않기도 한다.

예시:

* ``python=2.7.3``
* ``python=2.7``
* ``python``

사용법 문서에서 ``package_spec``\ 으로 나타낸다.
