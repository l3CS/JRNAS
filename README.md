#language: python
python:
  - "3.8"
install:
  - pip install tox
script:
  - tox
addons:
  apt:
    packages:
    - swig
jobs:
  include:
    - stage: test
      script: (cd pure-python-package && tox)
    -
      script: (cd cython-pure-python-package && tox)
    -
      script: (cd cython-pure-cpp-package && tox)
    -
      script: (cd swig-python-package && tox)
