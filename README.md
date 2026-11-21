# V2bX

一个基于多内核（Xray / sing-box / Hysteria2）的 V2board / Xboard 节点服务端，修改自 XrayR，支持 Vmess/Vless、Trojan、Shadowsocks、Hysteria1/2 等协议。

本仓库为 [wyx2685/V2bX](https://github.com/wyx2685/V2bX) 的维护分支（maogepw/V2bX），已升级至 go1.27 + 最新版三大内核（xray-core、sing-box v1.14、hysteria v2.12）。

**注意：需搭配[修改版 V2board](https://github.com/wyx2685/v2board) 或 Xboard 使用。**

## 特点

* 永久开源且免费。
* 支持 Vmess/Vless、Trojan、Shadowsocks、Hysteria1/2 多种协议及 Vless、XTLS 等新特性。
* 单实例对接多节点，无需重复启动；修改配置自动重启实例。
* 支持在线 IP 限制、TCP 连接数限制、节点/用户级别限速。
* 自动申请与续签 TLS 证书，自定义 DNS，审计规则。
* 支持条件编译，可仅编译需要的内核。

## 下载安装

### 一键安装（Linux）

```
wget -N https://raw.githubusercontent.com/maogepw/V2bX-script/master/install.sh && bash install.sh
```

### 手动下载

| 平台 | 下载 |
|------|------|
| Linux x86_64 | [V2bX-linux-64.zip](https://github.com/maogepw/V2bX/releases/latest/download/V2bX-linux-64.zip) |
| Linux arm64 | [V2bX-linux-arm64.zip](https://github.com/maogepw/V2bX/releases/latest/download/V2bX-linux-arm64.zip) |
| Windows x86_64 | [V2bX-windows-64.zip](https://github.com/maogepw/V2bX/releases/latest/download/V2bX-windows-64.zip) |
| Windows arm64 | [V2bX-windows-arm64.zip](https://github.com/maogepw/V2bX/releases/latest/download/V2bX-windows-arm64.zip) |
| macOS Apple Silicon | [V2bX-macos-arm64.zip](https://github.com/maogepw/V2bX/releases/latest/download/V2bX-macos-arm64.zip) |

全部发布版本见 [Releases](https://github.com/maogepw/V2bX/releases)。压缩包内含示例配置与 geoip/geosite 数据文件。

### 手动安装教程

[手动安装教程](https://v2bx.v-50.me/v2bx/v2bx-xia-zai-he-an-zhuang/install/manual)

## 构建

``` bash
# 通过-tags选项指定要编译的内核， 可选 xray， sing, hysteria2
# 需要 go >= 1.27，Windows 下可执行文件名需加 .exe 后缀
GOEXPERIMENT=jsonv2 go build -v -o build_assets/V2bX -tags "sing xray hysteria2 with_quic with_grpc with_utls with_wireguard with_acme with_gvisor" -trimpath -ldflags "-checklinkname=0 -s -w -buildid="
```

## 配置文件及详细使用教程

[详细使用教程](https://v2bx.v-50.me/)

## 问题反馈

使用中遇到问题请在 [Issues](https://github.com/maogepw/V2bX/issues) 反馈。

## Thanks

* [XrayR](https://github.com/XrayR/XrayR)（项目起源）
* [Project X / Xray](https://github.com/XTLS/)
* [sing-box](https://github.com/SagerNet/sing-box)
* [Hysteria](https://github.com/apernet/hysteria)
* [V2board](https://github.com/v2board/v2board) / [Xboard](https://github.com/xboard-panel/xboard)

## License

[MIT](LICENSE)
