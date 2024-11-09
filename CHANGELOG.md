# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [6.3.1] - 2024-11-09

### Changed

- Upgrade bun to 1.1.34

### Fixed

- Rebuild dist index.js with bun 1.1.34

## [6.3.0] - 2024-10-23

### Changed

- Upgrade bun to 1.1.32

## [6.2.1] - 2023-12-23

### Changed

- Update branding.

## [6.2.0] - 2023-10-10

### Added

- Support `WAKATIME_BASE_URL` to use self-hosted wakatime server.
- Support naming the gist with `gist-name` input.

## [6.1.0] - 2023-10-08

### Changed

- Remove `wakatime-client` dependency, call wakatime API manually.
- Pre-build main file for next usage.
- Refurbish README.

## [6.0.0] - 2023-10-07

### Changed

- Set `GIST_ID` in secrets instead of hardcoding it in the example workflow.
- Fast run with <https://bun.sh/>.
