# NAOS Core

Local device control, update coordination, container integration, and watchdog
support for NAOS systems.

## Downloads

Download `naos-core-linux-arm64.tar.gz` from
[Releases](https://github.com/wushuki/naos-core/releases).

The Linux ARM64 package includes the static executable, OpenRC service scripts,
default configuration, dependency license notices, build metadata, and an
SPDX 2.3 SBOM.

## Install

Extract the archive into a temporary directory:

```sh
tar -xzf naos-core-linux-arm64.tar.gz
sudo install -Dm0755 usr/bin/naos-core /usr/bin/naos-core
sudo install -Dm0755 etc/init.d/naos-core /etc/init.d/naos-core
sudo install -Dm0600 etc/naos-core/device.ini /etc/naos-core/device.ini
```

Configure `/etc/naos-core/device.ini` before enabling the service:

```sh
sudo rc-update add naos-core default
sudo rc-service naos-core start
naos-core --help
```

Container integration uses the separately installed
[NAOS Container](https://github.com/wushuki/naos-container) runtime. The archive
also provides its OpenRC service script and configuration under `etc/init.d/naosd`
and `etc/naosd/config.yml`.

RAUC, D-Bus, Avahi, a hardware watchdog, and the platform's boot/storage
integration are required for their corresponding features.

## Package metadata

`build-info.json` records the binary and build identity. `sbom.spdx.json`
lists package files and reported dependencies. Dependency license notices are
in `usr/share/licenses/naos-core/`.
