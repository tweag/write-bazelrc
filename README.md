# Write / update a bazelrc file

[![Continuous Integration](https://github.com/tweag/write-bazelrc/actions/workflows/ci.yaml/badge.svg?event=schedule)](https://github.com/tweag/write-bazelrc/actions/workflows/ci.yaml)

GitHub action to write / append content to a bazelrc file.

## Usage

By default, the action will create / update `.bazelrc.local`.

```yaml
jobs:
  build-and-test:
    name: Build & Test
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Write to default location (.bazelrc.local)
        uses: tweag/write-bazelrc@v0
        with:
          content: |
            build --config=foo
            build --config=bar
```

You can customize the bazelrc path by specifying the `bazelrc_path` parameter.

```yaml
jobs:
  build-and-test:
    name: Build & Test
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Write to custom location
        uses: tweag/write-bazelrc@v0
        with:
          bazelrc_path: .bazelrc.auth
          content: |
            build --config=foo
            build --config=bar
```

## Inputs

| Input | Description | Default |
| --- | --- | --- |
| `content` | The string that should be writtent to the bazelrc file. | |
| `bazelrc_path` | The path of the bazelrc file. | `.bazelrc.local` |
