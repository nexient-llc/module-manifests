## Inputs

* `mode`: Sets the versioning type to use. For options see https://github.com/restechnica/semverbot#modes (default: "minor")

## Notes

* mode is defaulted to minor as this repository will have it's major version manually bumped should a major refactor warrent it.

## Example

```yaml
name: "Run Make Release"
on: pull_request

jobs:
  dockerfile-test:
    runs-on: nexient-llc/platform-images
    steps:
    - name: checkout source
      uses: actions/checkout@master
    - name: Run Make Release
      uses: ./.github/actions/release
```
