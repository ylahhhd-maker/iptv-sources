# IPTV Sources

每日自动同步的 IPTV 直播源订阅。播放列表由 GitHub Actions 从上游仓库拉取并提交到本仓库。

## 订阅地址

把下面的链接粘贴到播放器（APTV / TiviMate / 影视仓 / TVBox / Kodi 等）的“添加 M3U 订阅”里：

| 文件 | 订阅地址 | 说明 |
| --- | --- | --- |
| `iptv.m3u8` | https://raw.githubusercontent.com/ylahhhd-maker/iptv-sources/main/iptv.m3u8 | 综合源，央视、卫视、地方台 |
| `myiptv-ipv4.m3u` | https://raw.githubusercontent.com/ylahhhd-maker/iptv-sources/main/myiptv-ipv4.m3u | 典藏版，高清、带台标和节目预告（IPv4） |
| `myiptv-ipv6.m3u` | https://raw.githubusercontent.com/ylahhhd-maker/iptv-sources/main/myiptv-ipv6.m3u | 同上，仅 IPv6 网络 |

## 同步机制

- `.github/workflows/sync.yml` 在每次 push、以及每天 02:00 UTC 自动运行。
- 每次运行会下载上游播放列表，做基本校验（文件大小 > 5KB 且包含 `EXTINF`），校验通过才提交。
- 下载失败或校验不通过时，本次运行失败，**不会**用坏文件覆盖已有列表。

## 上游来源

- 综合源：https://github.com/joevess/IPTV
- 典藏版：https://github.com/suxuang/myIPTV

## 注意

- 源为第三方公开采集，可用性随时间衰减，不要用于二次分发。
- 若播放器拉取 raw 链接很慢，可在链接前加 GitHub 加速前缀。
