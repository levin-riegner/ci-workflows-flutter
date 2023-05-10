# Changelog

All notable changes to this project will be documented in this file.

## 2023-10-10

### Changed

- Update JAVA_VERSION example to use SemVer notation.
- Support changelog file changes via pull request.

## 2022-10-10

### Changed

- Upgraded all workflow dependencies to latest versions.

## 2022-06-15

### Added

- Step parsing flutter version from [fvm](https://fvm.app/). The ci will look for the flutter version in the following order:
    1. `FLUTTER_VERSION` variable inside the .env file.
    2. `flutterSdkVersion` inside .fvm folder.

### Removed

- FLUTTER_VERSION variable inside the .env file is now deprecated. Please use fvm instead.
