<p align="center">
    <a href="https://github.com/yii-tools/actions" target="_blank">
        <img src="https://avatars.githubusercontent.com/u/121752654?s=200&v=4" height="100px">
    </a>
    <h1 align="center">Actions</h1>
    <br>
</p>

### Usage:

To use these reusable github actions, simply create your `.yml` file, in your `.github/workflows` directory in your repository, and simply paste the code below:

#### Composer require checker for monorepo

`file: .github/workflows/dependency-checker.yml`

```yaml
on:
  pull_request:
    paths-ignore:
      - 'docs/**'
      - 'README.md'
      - 'CHANGELOG.md'
      - '.gitignore'
      - '.gitattributes'
      - 'infection.json.dist'
      - 'psalm.xml'

name: dependency-check

jobs:
  composer-require-checker:
    uses: yii-tools/actions/.github/workflows/split-tests.yml@main
    with:
      os: >-
        ['ubuntu-latest']
      packages-name: >-
        ['html', 'model']
      php: >-
        ['8.1', '8.2']
      test-command: composer-require-checker
```

#### Phpunit tests for monorepo

`file: .github/workflows/phpunit.yml`

```yaml
on:
  pull_request:
    paths-ignore:
      - 'docs/**'
      - 'README.md'
      - 'CHANGELOG.md'
      - '.gitignore'
      - '.gitattributes'
      - 'infection.json.dist'
      - 'psalm.xml'

name: build

jobs:
  phpunit:
    uses: yii-tools/actions/.github/workflows/split-tests.yml@main
    with:
      os: >-
        ['ubuntu-latest', 'windows-latest']
      packages-name: >-
        ['html', 'model']
      php: >-
        ['8.1', '8.2']

```

### Psalm static analysis for monorepo

`file: .github/workflows/psalm.yml`

```yaml
on:
  pull_request:
    paths-ignore:
      - 'docs/**'
      - 'README.md'
      - 'CHANGELOG.md'
      - '.gitignore'
      - '.gitattributes'
      - 'infection.json.dist'
      - 'psalm.xml'

name: static-analysis

jobs:
  psalm:
    uses: yii-tools/actions/.github/workflows/split-tests.yml@main
    with:
      os: >-
        ['ubuntu-latest']
      packages-name: >-
        ['html', 'model']
      php: >-
        ['8.1', '8.2']
      test-command: psalm
```

### License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

### Our social networks

[![Twitter](https://img.shields.io/badge/twitter-follow-1DA1F2?logo=twitter&logoColor=1DA1F2&labelColor=555555?style=flat)](https://twitter.com/Terabytesoftw)
