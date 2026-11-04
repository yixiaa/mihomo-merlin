# mihomo-merlin

华硕梅林固件（Koolcenter 软件中心）上的 Mihomo（Clash.Meta）透明代理插件，适用于 RT-AX86U 等 HND / aarch64 机型。

## 安装

1. 下载最新安装包：[mihomo.tar.gz](https://raw.githubusercontent.com/yixiaa/mihomo-merlin/release/mihomo.tar.gz)（`release` 分支）。
2. 路由器后台 → 软件中心 → 离线安装，选择该文件。
3. 打开插件页，在「订阅」页添加机场订阅，回到「基本设置」打开开关，点「保存并应用」。

## 自动更新

从 v1.7.3 起，插件安装时自动把发布地址设为：

```
https://raw.githubusercontent.com/yixiaa/mihomo-merlin/release
```

「自动更新插件」默认开启，路由器每 5 分钟检查一次 `version` 文件，发现新版本自动下载 `mihomo.tar.gz` 安装，设置保留；安装时 Mihomo 重启，断网约 10 秒。GitHub 直连打不开时自动走 gh-proxy 加速或 Mihomo 代理。

`release` 分支根目录始终放最新版本的两个文件：

| 文件 | 内容 |
|---|---|
| `version` | 只有一行版本号，如 `1.7.2` |
| `mihomo.tar.gz` | 插件安装包 |

## 主要功能

- 透明代理（TCP 重定向 + 可选 UDP TPROXY），fake-ip / redir-host DNS
- 机场 Clash 订阅 / 节点订阅 + 内置规则 / 自定义配置三种模式，多订阅管理，订阅流量与到期显示
- 覆写（混入）配置，内置秋风、217heidai 去广告规则集
- 访问控制（只代理指定设备、不走代理的设备、设备专用策略组），IPv6 DNS 防泄漏
- 守护进程（每分钟检查进程和端口），订阅热重载，内核与插件在线更新
- 内置控制面板（`http://路由器IP:9090/ui/`）：节点按国家合并、延迟测试、连接/规则/日志、全球节点卫星地球

详细更新记录见 [CHANGELOG.md](CHANGELOG.md)。

## 第三方组件

- [Mihomo](https://github.com/MetaCubeX/mihomo)（GPL-3.0），安装包内附带其 arm64 程序，源码见上游仓库
- 控制面板使用 d3-geo、topojson-client（ISC）、Natural Earth 国界数据（公有领域）、NASA 卫星影像（公有领域）、world-countries 国家坐标（ODbL）
- 去广告规则集：[AWAvenue 秋风广告规则](https://github.com/TG-Twilight/AWAvenue-Ads-Rule)、[217heidai/adblockfilters](https://github.com/217heidai/adblockfilters)，由路由器运行时在线下载
