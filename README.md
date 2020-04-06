# action-library-packaging

This Github Action hosts machinery for building, testing, and deploying QIIME
2 plugins to the [QIIME 2 Library](https://library.qiime2.org).

## inputs

* `recipe-path`: Path to recipe
* `plugin-name`: Name of QIIME 2 plugin
* `additional-tests`: Additional tests to run post-build

## outputs

NA

## example usage

On every pull request, build and test:

```yml
name: build-test
on:
  pull_request:

jobs:
  build-and-test-plugin:
    strategy:
      matrix:
        os: [macos-latest, ubuntu-latest]
    runs-on: ${{ matrix.os }}
    steps:
    - uses: actions/checkout@v2
    - uses: qiime2/action-library-packaging@alpha1
      with: 
        plugin-name: q2-types
        additional-tests: pytest --pyargs q2_types
```
