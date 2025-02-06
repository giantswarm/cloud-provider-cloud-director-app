# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Changed

- Update to `1.6.0-gs` of CPI. (Upstream `1.6.0` plus custom patch from previous release.)

## [0.3.1] - 2024-07-24

### Changed

- Update to custom patch `1.5.1-gs` of CPI to address LB health monitor upgrade issue until upstream patch is available.

## [0.3.0] - 2024-07-18

### Changed

- Rollback CPI from `1.6.0` to `1.5.0` due to IP Spaces incompatibility.

## [0.2.11] - 2024-05-30

### Changed

- Switch all images to Azure CR.
- Consume retagged upstream images of cpi and csi.

## [0.2.10] - 2024-02-13

### Added

- Add `global.podSecurityStandards.enforced` value for PSS migration.

## [0.2.9] - 2023-12-12

### Changed

- Improve default Storage Class handling

## [0.2.8] - 2023-06-21

### Changed

- Update `quay.io/giantswarm/csi-cloud-director` version for `csi-vcd-nodeplugin` to support newer k8s versions.

## [0.2.7] - 2023-05-02

### Changed

- Update csi plugin for cloud-director image to inject cluster id as description to named disks.

## [0.2.6] - 2023-04-04

### Changed

- Added `controlplane` in the tolerations to support 1.24 which no longer adds the `master` label.

## [0.2.5] - 2023-03-17

### Fixed

- Fixed double secrets helmrelease issue.

## [0.2.4] - 2023-03-17

### Added

- Allow providing arbitrary credentials secret with `.global.basicAuthSecret.name`.

### Fixed

- Fix credential Secret creation check to use `global` values.

### Removed

- Remove unused top-level credential Secret template (this is cosmetic, the sub-charts secrets remain in place).

### Changed

- Change `enableVirtualServiceSharedIP` default value to `true` and `oneArm.enabled` to `false`.


## [0.2.3] - 2023-02-23

### Added

- Add support for `enableVirtualServiceSharedIP`.

## [0.2.2] - 2023-02-21

### Added

- Add network policy for csi-vcd-controllerplugin to access cloud-director api.

## [0.2.1] - 2023-02-20

### Changed

- Add `compatibleProviders` to `Chart.yaml`.
- Set `dnsPolicy` as `ClusterFirst`.
- Fix IP types of nodes for multi-nic case.

## [0.2.0] - 2022-12-08

### Changed

- Update CPI to 1.2.0.

## [0.1.3] - 2022-12-01

### Changed

- Removed username/credentials from authentication options to match [cluster chart](https://github.com/giantswarm/cluster-cloud-director/pull/35).
- Changed the default value of `global.vcdConfig.immutable` from `false` -> `true`.
- Add quoting for storage profiles in the StorageClass resources.

## [0.1.2] - 2022-09-08

### Added

- Add support for fsGroup.

## [0.1.1] - 2022-08-25

### Added

- Add storage class creation.

## [0.1.0] - 2022-06-24

### Changed

- Updated repo config to push to default app catalog.
- Move shared vars under the `global` value key.
- Use images retagged from Quay.
- Renamed chart to align with best practises.

### Added

- Initial chart implementation.

[Unreleased]: https://github.com/giantswarm/cloud-provider-cloud-director-app/compare/v0.3.1...HEAD
[0.3.1]: https://github.com/giantswarm/cloud-provider-cloud-director-app/compare/v0.3.0...v0.3.1
[0.3.0]: https://github.com/giantswarm/cloud-provider-cloud-director-app/compare/v0.2.11...v0.3.0
[0.2.11]: https://github.com/giantswarm/cloud-provider-cloud-director-app/compare/v0.2.10...v0.2.11
[0.2.10]: https://github.com/giantswarm/cloud-provider-cloud-director-app/compare/v0.2.9...v0.2.10
[0.2.9]: https://github.com/giantswarm/cloud-provider-cloud-director-app/compare/v0.2.8...v0.2.9
[0.2.8]: https://github.com/giantswarm/cloud-provider-cloud-director-app/compare/v0.2.7...v0.2.8
[0.2.7]: https://github.com/giantswarm/cloud-provider-cloud-director-app/compare/v0.2.6...v0.2.7
[0.2.6]: https://github.com/giantswarm/cloud-provider-cloud-director-app/compare/v0.2.5...v0.2.6
[0.2.5]: https://github.com/giantswarm/cloud-provider-cloud-director-app/compare/v0.2.4...v0.2.5
[0.2.4]: https://github.com/giantswarm/cloud-provider-cloud-director-app/compare/v0.2.3...v0.2.4
[0.2.3]: https://github.com/giantswarm/cloud-provider-cloud-director-app/compare/v0.2.2...v0.2.3
[0.2.2]: https://github.com/giantswarm/cloud-provider-cloud-director-app/compare/v0.2.1...v0.2.2
[0.2.1]: https://github.com/giantswarm/cloud-provider-cloud-director-app/compare/v0.2.0...v0.2.1
[0.2.0]: https://github.com/giantswarm/cloud-provider-cloud-director-app/compare/v0.1.3...v0.2.0
[0.1.3]: https://github.com/giantswarm/cloud-provider-cloud-director-app/compare/v0.1.2...v0.1.3
[0.1.2]: https://github.com/giantswarm/cloud-provider-cloud-director-app/compare/v0.1.1...v0.1.2
[0.1.1]: https://github.com/giantswarm/cloud-provider-cloud-director-app/compare/v0.1.0...v0.1.1
[0.1.0]: https://github.com/giantswarm/cloud-provider-cloud-director-app/releases/tag/v0.1.0
