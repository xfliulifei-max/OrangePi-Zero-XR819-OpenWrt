# Orange Pi Zero H2/H2+ — OpenWrt 23.05.2 + XR819 Wi-Fi

这个仓库用于 GitHub Actions 云编译 Orange Pi Zero（H2/H2+）固件。

## 固件内容

- OpenWrt 23.05.2
- Linux 5.15.137
- Orange Pi Zero / Allwinner H2+
- 板载 XR819 2.4 GHz Wi-Fi
- XR819 xradio 驱动和固件
- LuCI
- DHCP / 防火墙 / SSH
- 默认 LAN：192.168.10.1
- Ethernet eth0：WAN（DHCP）
- Wi-Fi：AP，接入 LAN
- 可在 Actions 运行时设置 SSID 和密码

XR819 部分基于 melsem/opi-zero-cyberwrt 的 OpenWrt 23.05.2 补丁和 xradio feed。
项目原作者明确记录了 OpenWrt 23.05.2 + xradio-xr819 工作正常。

## 使用方法

1. 在 GitHub 新建一个 Public 或 Private repository。
2. 上传本仓库的 `.github/workflows/build.yml`。
3. 打开仓库：
   `Actions` → `Build Orange Pi Zero XR819 OpenWrt`
4. 点击 `Run workflow`。
5. 设置：
   - Wi-Fi SSID
   - Wi-Fi password
   - Root filesystem size 保持 512 MB
6. 等待编译完成。
7. 在该次 Workflow 页面底部的 `Artifacts` 下载：
   `orangepi-zero-xr819-openwrt-23.05.2`
8. 解压后选择类似：
   `openwrt-23.05.2-sunxi-cortexa7-xunlong_orangepi-zero-ext4-sdcard.img.gz`
9. 用 Rufus / balenaEtcher / Win32DiskImager 写入 TF 卡。

## 第一次启动

Orange Pi Zero 接上网线到上级路由器，插入 TF 卡并通电。

然后用手机/电脑搜索你在 Actions 中设置的 Wi-Fi。

管理地址：

`http://192.168.10.1`

注意：XR819 是老旧的 2.4 GHz 芯片，适合低成本 AP/转发测试，不适合追求高速 Wi-Fi。
