# Immortalwrt 18.06-k5.4 for NanoPi R4S

You can download the iwrt for NanoPi R4S firmware from [Releases](https://github.com/anmansky/np-r4s//releases). Such as `ImmortalWrt_NanoPi_R4S_${date}`.

## Instructions

1. Before burning the system, it is recommended to format the TF card (MicroSD card/TF card: 8GB SDHC card of Class10 or above), and use a writing tool such as [balenaEtcher](https://www.balena.io/etcher/) to write the *.img.gz file into the TF card.
2. Insert the completed TF card into the NanoPi-R4S card slot, power on and start (5V/2A), and see the SYS red light flashing, indicating that the system has successfully started.

## Compilation method

- Select ***`Build OpenWrt for NanoPi R4S`*** on the [Action](https://github.com/anmansky/np-r4s/actions) page.
- Click the ***`Run workflow`*** button.

## Configuration file function description

| Folder/file name | Features |
| ---- | ---- |
| .config | Firmware related configuration, such as firmware kernel, file type, software package, luci-app, luci-theme, etc. |
| files | Create a files directory under the root directory of the warehouse and put the relevant files in. You can use custom files such as network/dhcp/wireless by default when compiling. |
| feeds.conf.default | Just put the feeds.conf.default file into the root directory of the warehouse, it will overwrite the relevant files in the OpenWrt source directory. |
| diy-part1.sh | Execute before updating and installing feeds, you can write instructions for modifying the source code into the script, such as adding/modifying/deleting feeds.conf.default. |
| diy-part2.sh | After updating and installing feeds, you can write the instructions for modifying the source code into the script, such as modifying the default IP, host name, theme, adding/removing software packages, etc. |

## .github/workflow/build-openwrt-nanopi_r4s.yml related environment variable description

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
| secrets.GITHUB_TOKEN | Personal center: Settings ??? Developer settings ??? Personal access tokens ??? Generate new token ( Name: GITHUB_TOKEN, Select: public_repo ). |

## Firmware compilation parameters

| Option | Value |
| ---- | ---- |
| Target System | Rockchip |
| Subtarget | RK33xx boards (64 bit) |
| Target Profile | NanoPi R4S |
| Target Images | squashfs |
| LuCI -> Applications | in the file: .config |

## Firmware information

| Name | Value |
| ---- | ---- |
| Default IP | 10.0.10.100 |
| Default username | root |
| Default password | password |
| Default support WIFI driver rtl8812au-ac

