========
기능
========

기능(feature)으로 이름과 버전이 같은 두 패키지를 구별한다.
예를 들어, 기능은 특화된 컴파일러 또는 런타임이나 패키지의 포크(fork)를 나타낼 수 있다.
기능의 대표적인 예시는 아나콘다 엑셀러레이트(Anaconda Accerlerate)의 mkl 기능이다.
넘파이(NumPy)와 같은 MKL로 컴파일된 패키지는 mkl 기능 모음을 갖는다.
mkl 메타패키지는 mkl 기능 모음을 track_features에 가지고 있다.
따라서 이러한 패키지를 설치하면 mkl 기능을 설치하게 된다.
기능 이름은 패키지 이름과는 별개이며 mkl이 패키지 이름이면서 패키지가 추적하는 기능의 이름인 것은 우연일 뿐이다.

기능은 패키지 자체가 아니라 패키지가 설치된 환경에 속하는 것으로 생각한다.
기능이 설치되면 콘다는 자동으로 설치된 기능이 있는 패키지로 교체한다.
예를 들어, mkl 기능이 설치되면 일반 넘파이는 삭제되고 mkl 기능이 있는 넘파이 패키지가 설치된다.
기능을 활성한다고 해서 아직 설치되지 않은 어떤 패키지를 설치하는 것은 아니다.
하지만 설치된 기능을 갖는 패키지를 이후에 설치한다면 기능과 같은 환경에 설치하는 것이 좋다.

기능을 설치하려면 그 기능을 추적하는 패키지를 설치한다.
``conda remove --features`` 명령으로 기능을 삭제한다.

track_features를 위한 메타패키지를 생성하는 것이 좋다.
기능이 없는 버전이 있는 패키지에 track_features를 추가하면 기능이 없는 패키지는 절대 선택되지 않는다.
패키지의 track_features 사양으로부터 기능을 설치하면 콘다는 항상 기능을 추가하기 때문이다.

예시: 기능 디버그를 갖는 패키지를 생성하고 싶다면 다음 코드로 패키지를 생성한다.

.. code-block:: yaml

   build:
     features:
       - debug

위 코드를 사용하면 다음과 같은 특별한 메타패키지를 생성한다.

.. code-block:: yaml

   package:
     # This name doesn't have to be the same as the feature, but can avoid confusion if it is
     name: debug
     # This need not relate to the version of any of the packages with the
     # feature. It is just a version for this metapackage.
     version: 1.0

   build:
     track_features:
       - debug

.. or use ``conda install --features``, blocking on
.. https://github.com/conda/conda/issues/543
