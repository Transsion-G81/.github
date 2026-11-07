<div align="center">

# Transsion G81

**Device Trees for MediaTek Helio G81 (MT6768) Transsion phones**

![LineageOS](https://img.shields.io/badge/LineageOS-23.2-167C80?style=flat-square&logo=lineageos&logoColor=white)
![Android](https://img.shields.io/badge/Android-16-3DDC84?style=flat-square&logo=android&logoColor=white)
![SoC](https://img.shields.io/badge/SoC-Helio%20G81%20(MT6768)-informational?style=flat-square)

Infinix HOT 50i &nbsp;·&nbsp; Infinix Smart 9 &nbsp;·&nbsp; TECNO Spark 30C

</div>

---

## Supported devices

All five products run the same SoC — **MediaTek Helio G81 (MT6768, 12 nm)**.

| Device | Codename | Lineage product | Source |
| --- | --- | --- | --- |
| Infinix HOT 50i | `X6531` | `lineage_X6531` | [device](https://github.com/Transsion-G81/android_device_infinix_X6531) · [vendor](https://github.com/Transsion-G81/android_vendor_infinix_X6531) · [kernel](https://github.com/Transsion-G81/android_kernel_infinix_X6531) |
| Infinix HOT 50i (NFC) | `X6531B` | `lineage_X6531B` | built from the `X6531` tree |
| Infinix Smart 9 | `X6532` | `lineage_X6532` | [device](https://github.com/Transsion-G81/android_device_infinix_X6532) · [vendor](https://github.com/Transsion-G81/android_vendor_infinix_X6532) · [kernel](https://github.com/Transsion-G81/android_kernel_infinix_X6532) |
| TECNO Spark 30C | `KL5` | `lineage_KL5` | [device](https://github.com/Transsion-G81/android_device_tecno_KL5) · [vendor](https://github.com/Transsion-G81/android_vendor_tecno_KL5) · [kernel](https://github.com/Transsion-G81/android_kernel_tecno_KL5) |
| TECNO Spark 30C (IMX582) | `KL5n` | `lineage_KL5n` | built from the `KL5` tree (+ NFC patch) |

> `X6531B` and `KL5n` are variants of their base tree. `KL5n` applies the NFC /
> IMX582 patches at build time, so it is always built **last**.

## Build it yourself

```bash
# 1) init LineageOS 23.2
repo init -u https://github.com/LineageOS/android.git -b lineage-23.2 --git-lfs

# 2) add our manifest
mkdir -p .repo/local_manifests
curl -L https://raw.githubusercontent.com/Transsion-G81/local_manifests/refs/heads/main/local_manifest.xml \
  > .repo/local_manifests/mt6768_manifest.xml

# 3) sync
repo sync -c --force-sync --no-clone-bundle --no-tags

# 4) build every device + upload, in one shot
curl -L https://raw.githubusercontent.com/Transsion-G81/local_manifests/refs/heads/main/build-all.sh > build-all.sh
chmod +x build-all.sh
./build-all.sh
```

`build-all.sh` builds `X6531 → X6531B → X6532 → KL5 → KL5n` in order, **sha1-checks
each product's firmware before building** (a wrong / mixed-up modem is refused),
then collects the ROM zip + `boot.img` + `vendor_boot.img` and uploads them.

It also carries a pure-bash full-screen TUI menu, an optional XGSI boot/dmesg log
capture, and Telegram / webhook status notifications (including the download link
of every uploaded file). Run `./build-all.sh --help` for everything, or see the
**[local_manifests](https://github.com/Transsion-G81/local_manifests)** guide.

## Repositories

| Repository | What it is |
| --- | --- |
| [`local_manifests`](https://github.com/Transsion-G81/local_manifests) | the `repo` manifest + the `build-all.sh` build/release script |
| [`release`](https://github.com/Transsion-G81/release) | release notes and build links |
| [`android_device_infinix_X6531`](https://github.com/Transsion-G81/android_device_infinix_X6531) | device tree for `X6531` / `X6531B` |
| [`android_device_infinix_X6532`](https://github.com/Transsion-G81/android_device_infinix_X6532) | device tree for `X6532` |
| [`android_device_tecno_KL5`](https://github.com/Transsion-G81/android_device_tecno_KL5) | device tree for `KL5` / `KL5n` |
| [`android_vendor_infinix_X6531`](https://github.com/Transsion-G81/android_vendor_infinix_X6531) | vendor blobs for `X6531` / `X6531B` |
| [`android_vendor_infinix_X6532`](https://github.com/Transsion-G81/android_vendor_infinix_X6532) | vendor blobs for `X6532` |
| [`android_vendor_tecno_KL5`](https://github.com/Transsion-G81/android_vendor_tecno_KL5) | vendor blobs for `KL5` / `KL5n` |
| [`android_kernel_infinix_X6531`](https://github.com/Transsion-G81/android_kernel_infinix_X6531) | kernel source for `X6531` / `X6531B` |
| [`android_kernel_infinix_X6532`](https://github.com/Transsion-G81/android_kernel_infinix_X6532) | kernel source for `X6532` |
| [`android_kernel_tecno_KL5`](https://github.com/Transsion-G81/android_kernel_tecno_KL5) | kernel source for `KL5` / `KL5n` |

## Disclaimer

- **Unofficial** and a work in progress — not affiliated with LineageOS, Infinix
  or TECNO.
- Flashing custom firmware voids warranties and can brick your phone. **Flash at
  your own risk.**
- Please do not report issues with these builds to LineageOS.

## Credits

- [LineageOS](https://github.com/LineageOS) — the ROM and the MediaTek
  [hardware](https://github.com/LineageOS/android_hardware_mediatek) /
  [sepolicy](https://github.com/LineageOS/android_device_mediatek_sepolicy_vndr) trees
- [techyminati](https://github.com/techyminati) — `android_vendor_mediatek_ims`
- [MillenniumOSS](https://github.com/MillenniumOSS) — device tree reference
- Xiaomi `gale` / `earth` device trees — device tree reference
- Device specifications — [GSMArena](https://www.gsmarena.com)
