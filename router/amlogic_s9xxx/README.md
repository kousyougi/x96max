# OpenWrt for Amlogic S9xxx STB

Support Amlogic S9xxx STB are `S905x3`, `S905x2`, `S922x`, `S905x`, `S905d`, `s912`, etc. such as ***`Phicomm-N1, Octopus-Planet, X96-Max+, HK1-Box, H96-Max-X3, Belink GT-King, Belink GT-King Pro, UGOOS AM6 Plus, Fiberhome HG680P, ZTE B860H`***, etc. You can download the OpwnWrt for Amlogic S9xxx STB firmware from [Releases](https://github.com/ophub/op/releases). Such as `openwrt_s9xxx_${date}`. Then write the IMG file to the USB hard disk through software such as [Rufus](https://rufus.ie/) or [balenaEtcher](https://www.balena.io/etcher/).

This OpenWrt firmware on the `Github Actions` to packaging was using ***`Flippy's`*** [Amlogic S9xxx Kernel for OpenWrt](https://github.com/ophub/amlogic-s9xxx-openwrt), and the [Install and Upgrade scripts](https://github.com/ophub/amlogic-s9xxx-openwrt/tree/main/amlogic-s9xxx/install-program), etc. Welcome to use `Fork` for [personalized OpenWrt firmware configuration](https://github.com/ophub/amlogic-s9xxx-openwrt/blob/main/router-config/README.md). If you like it, Please click the `Star`.

## Firmware instructions

| Model  | STB | OpenWrt Firmware |
| ---- | ---- | ---- |
| s905x3 | [x96](https://tokopedia.link/uMaH09s41db), [hk1](https://tokopedia.link/pNHf5AE41db), [h96](https://tokopedia.link/wRh6SVI41db) | openwrt_s905x3_v*.img |
| s905x2 | [x96max4g](https://tokopedia.link/HcfLaRzjqeb), [x96max2g](https://tokopedia.link/ro207Hsjqeb) | openwrt_s905x2_v*.img |
| s905x | [hg680p](https://tokopedia.link/NWF1Skg21db), [b860h](https://tokopedia.link/fp8wG3711db) | openwrt_s905x_v*.img |
| s922x | [belink](https://tokopedia.link/RAgZmOM41db), [belinkpro](https://tokopedia.link/sfTHlfS41db), [ugoos](https://tokopedia.link/pHGKXuV41db) | openwrt_s922x_v*.img |
| s912 | octopus | openwrt_s912_v*.img |
| s905d | n1 | openwrt_s905d_v*.img |

The OpenWrt firmware of the same `Model` is common. You can write this OpenWrt firmware to the `USB hard disk` to start. When writing into EMMC through [openwrt-install](https://github.com/ophub/amlogic-s9xxx-openwrt/tree/main/amlogic-s9xxx/install-program/files/openwrt-install), `select the name` of the Amlogic S9xxx STB you own in the menu.

For more OpenWrt firmware .dtb files are in the [dtb-amlogic](https://github.com/ophub/amlogic-s9xxx-openwrt/tree/main/amlogic-s9xxx/amlogic-dtb) directory. You can use the OpenWrt firmware to install via USB hard disk. When writing into EMMC through [openwrt-install](https://github.com/ophub/amlogic-s9xxx-openwrt/tree/main/amlogic-s9xxx/install-program/files/openwrt-install), [select 0: Enter the dtb file name of your box](https://github.com/ophub/amlogic-s9xxx-openwrt/tree/main/amlogic-s9xxx/amlogic-dtb), and use the Amlogic S9xxx STB you own.

## Install to EMMC and upgrade instructions

Choose the corresponding firmware according to your Amlogic S9xxx STB. Then write the IMG file to the USB hard disk through software such as [balenaEtcher](https://www.balena.io/etcher/). Insert the USB hard disk into the STB. Common for all `Amlogic S9xxx STB`.

***`Install OpenWrt`***

- Log in to the default IP: 192.168.1.1 → `Login in to openwrt` → `system menu` → `TTYD terminal` → input command: 

```yaml
openwrt-install
```
***`Upgrade OpenWrt`***

- Log in to the default IP: 192.168.1.1 →  `Login in to openwrt` → `system menu` → `file transfer` → upload ***`openwrt*.img.gz (Support suffix: *.img.xz, *.img.gz, *.7z, *.zip)`*** to ***`/tmp/upload/`***, enter the `system menu` → `TTYD terminal` → input command: 

```yaml
openwrt-update
```

[For more instructions please see: install-program](https://github.com/ophub/amlogic-s9xxx-openwrt/tree/main/amlogic-s9xxx/install-program)


## Compilation method

- Select ***`Build OpenWrt for S9xxx`*** on the [Action](https://github.com/ophub/op/actions) page.
- Click the ***`Run workflow`*** button.

## Configuration file function description

| Folder/file name | Features |
| ---- | ---- |
| .config | Firmware related configuration, such as firmware kernel, file type, software package, luci-app, luci-theme, etc. |
| files | Create a files directory under the root directory of the warehouse and put the relevant files in. You can use custom files such as network/dhcp/wireless by default when compiling. |
| feeds.conf.default | Just put the feeds.conf.default file into the root directory of the warehouse, it will overwrite the relevant files in the OpenWrt source directory. |
| diy-part1.sh | Execute before updating and installing feeds, you can write instructions for modifying the source code into the script, such as adding/modifying/deleting feeds.conf.default. |
| diy-part2.sh | After updating and installing feeds, you can write the instructions for modifying the source code into the script, such as modifying the default IP, host name, theme, adding/removing software packages, etc. |

## .github/workflow/*.yml related environment variable description

| Environment variable | Features |
| ---- | ---- |
| REPO_URL | Source code warehouse address |
| REPO_BRANCH | Source branch |
| FEEDS_CONF | Custom feeds.conf.default file name |
| CONFIG_FILE | Custom .config file name |
| DIY_P1_SH | Custom diy-part1.sh file name |
| DIY_P2_SH | Custom diy-part2.sh file name |
| UPLOAD_BIN_DIR | Upload the bin directory (all ipk files and firmware). Default false |
| UPLOAD_FIRMWARE | Upload firmware catalog. Default true |
| UPLOAD_RELEASE | Upload firmware to release. Default true |
| UPLOAD_COWTRANSFER | Upload the firmware to CowTransfer.com. Default false |
| UPLOAD_WERANSFER | Upload the firmware to WeTransfer.com. Default failure |
| RECENT_LASTEST | maximum retention days for release, artifacts and logs in GitHub Release and Actions. |
| TZ | Time zone setting |
| GITHUB_REPOSITORY | Github.com Environment variables. The owner and repository name. For example, ophub/op. |
| secrets.GITHUB_TOKEN | Personal center: Settings → Developer settings → Personal access tokens → Generate new token ( Name: GITHUB_TOKEN, Select: public_repo ). |

## Firmware compilation parameters

| Option | Value |
| ---- | ---- |
| Target System | QEMU ARM Virtual Machine |
| Subtarget | QEMU ARMv8 Virtual Machine(cortex-a53) |
| Target Profile | Default |
| Target Images | squashfs |
| LuCI -> Applications | in the file: .config |

## Firmware information

| Name | Value |
| ---- | ---- |
| Default IP | 192.168.1.1 |
| Default username | root |
| Default password | password |
| Default WIFI name | OpenWrt |
| Default WIFI password | none |

