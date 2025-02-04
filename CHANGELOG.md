# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

Note that the `[Unreleased]` section contains all changes that haven't yet made it to the `stable` branch.

## [Unreleased]
### Added
- Added `BUILDING.md`
- Added support for custom installing directories during builds (#61).

### Changed
- Show a warning when using Arch Linux styled architectures (those can be seen from the output of `uname -p`). Such architectures are still allowed for builds, but makedeb prompts the user to switch the architecture listing in the PKGBUILD to the Debian styled one (which can be seen from the output of `dpkg --print-architecture`).
- Updated `CONTRIBUTING.md` with better guidelines.
- Require `pkgdesc` to not be empty and contain characters other than spaces.
- Show warning when `pkgdesc` or a maintainer entry isn't present in PKGBUILDs.
- Show warning when more than one maintainer is specified.
- Disallow distribution and architecture-specific variables from pairing up with each other (#150).
- Require sources with distribution or architecture extensions in the variable name to have a matching
 hashsum entry with the same extensions (#150).

### Deprecated
- An architecture listing of `any` now sets the package architecture to the system's DPKG architecture (as required by the [Debian control file specification](https://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-architecture)). Previously `any` was automatically converted to `all` (which identifies an architecture-independent package), and using `all` now fulfills that purpose.

### Fixed
- Implement a changelog (#145).
- Move all code to `src/makepkg` codebase (#130).
- Disable all colored output if file descriptor 2 isn't a terminal (#81).
- Allow `pkgver` to include all characters allowed in the [Debian control file specification](https://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-version).
- Don't require `pkgver` to start with a number.
