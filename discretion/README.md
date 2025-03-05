## 概述

一些域名可能与广告/跟踪有关，但部分情况下它们发挥着其他的作用，拦截它们可能会造成额外的问题。本项目对部分此类有争议的域名做了整理和简单说明，您可根据自己的需要自行添加额外规则放行或拦截相关域名。

## 加密 DNS

[加密 DNS 域名列表](./dns.txt)

anti-AD 项目在域名层级屏蔽广告，很多广告拦截工具都是通过接管本地 DNS 阻止广告域名的正确解析来实现广告拦截的，而部分程序通过使用内置加密 DNS（HTTPDNS, DoH, DoT 等）绕过本地 DNS 进行域名解析，通过 DNS 实现的广告拦截将会失效。

当广告程序无法使用加密 DNS 时，通常会 fallback 到本地 DNS。若能拦截相关加密 DNS 流量（或阻止使用域名的加密 DNS 自身域名的解析），则能避免广告程序通过加密 DNS 规避广告拦截。

### 拦截加密 DNS 可能存在的问题

1. 部分加密 DNS 可能是用户自行启用的
2. 部分应用使用特定加密 DNS 的目的可能是为用户选取体验更优的 IP（如将域名解析到更快的 CDN 或特定的内网地址）

## 运营商本机号码自动登录

[本机号码自动登录域名列表](./anv.txt)

部分应用使用了运营商提供的基于网络的本机号码自动登录服务，通过后台访问特定 API 从运营商处获取当前流量归属的手机号码。

这为免密码一键登录提供了方便，但本身有泄露隐私的风险，应用可能不经用户同意窃取用户的手机号码。

anti-AD 已默认拦截相关域名，若您希望使用免密码一键登录功能，需自行放行相关域名。

## PCDN

[PCDN 域名列表](./pcdn.txt)

部分应用可能未经用户明确同意，后台使用用户网络带宽对外提供上传服务，为自身减少带宽压力或是直接牟利。这会影响用户的网络体验，消耗设备寿命。

但也有部分用户主动与相关企业合作，通过主动提供 PCDN 服务从相关企业处获得奖励。

## 个别域名情况说明

- `mmstat.com`

阿里系域名，已被加白。有明显的收集统计资料行为，但拦截后可能出现此类问题：1. 优酷视频播放异常；2. 淘宝等 App 验证码无法显示； 3. 某些阿里系 App 登录异常

相关 issues: [#177], [#261], [#605], [#680], [#959]

[#177]:https://github.com/privacy-protection-tools/anti-AD/issues/177
[#261]:https://github.com/privacy-protection-tools/anti-AD/issues/261
[#605]:https://github.com/privacy-protection-tools/anti-AD/issues/605
[#680]:https://github.com/privacy-protection-tools/anti-AD/issues/680
[#959]:https://github.com/privacy-protection-tools/anti-AD/issues/959

- `shouji.sogou.com`

搜狗域名，已被加白。与数据收集跟踪有关，但拦截后会影响搜狗输入法跨屏输入，词库同步/下载等功能

相关 issues: [#623], [#822], [#952]

[#623]:https://github.com/privacy-protection-tools/anti-AD/issues/623
[#822]:https://github.com/privacy-protection-tools/anti-AD/issues/822
[#952]:https://github.com/privacy-protection-tools/anti-AD/issues/952

- `activity.windows.com`

微软域名，与数据收集跟踪有关，已被拦截

拦截后可能影响部分微软服务运行，已有 Microsoft Edge、Microsoft Authenticator 同步功能无法工作的报告，已加白其子域名 `edge.activity.windows.com` 和 `edge-enterprise.activity.windows.com`

相关 issues: [#330], [#401] 等

[#330]:https://github.com/privacy-protection-tools/anti-AD/issues/330
[#401]:https://github.com/privacy-protection-tools/anti-AD/issues/401
