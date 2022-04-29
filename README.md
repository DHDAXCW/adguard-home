# adguard-home
### AdGuard Home 是一款全网广告拦截与反跟踪软件。在您将其安装完毕后，它将保护您所有家用设备，同时您不再需要安装任何客户端软件。随着物联网与连接设备的兴起，掌控您自己的整个网络环境变得越来越重要。    
—— AdGuard Home

## 1.开始工作
- AdGuard Home 后台
- 在浏览器中打开 AdGuard Home 的后台，进入安装向导，点击 “开始配置”。默认后台地址为：​http://IP:3000/​

![image](https://user-images.githubusercontent.com/74764072/165743827-32c902af-535c-4bef-a7a6-24b6a99df837.png)

- 将后台的访问端口更改为 3000，避免与 NAS 后台的 80 端口发生冲突，DNS 端口保持为 6855 即可， 如果是53的话 可能会有提示被占用。

![image](https://user-images.githubusercontent.com/74764072/165743929-5c6906bd-c553-45ac-8cf9-c08bea7fcc0a.png)

### 设置账号和密码

![image](https://user-images.githubusercontent.com/74764072/165743999-d271a762-c802-4f32-a73b-9e33ac82bf4d.png)

### 完成初始化设置

![image](https://user-images.githubusercontent.com/74764072/165744097-3bb205cb-ef58-401b-8ebb-6e780f8dd711.png)

![image](https://user-images.githubusercontent.com/74764072/165744154-e223407e-1316-45af-b5ae-b39248971c2a.png)

### 常规设置

![image](https://user-images.githubusercontent.com/74764072/165744269-2f235cac-9d79-42bf-9083-7822463819fe.png)

- 过滤器更新间隔：DNS 过滤清单默认更新间隔，一般为 3 天 - 7 天
- 使用 AdGuard 「浏览安全」网页服务：作用与 Chrome 网页安全性检查类似，开启后，当用户访问存在潜在威胁的网站时，AdGuard 会主动拦截并弹出提示
- 使用 AdGuard 「家长控制」 服务：如果家中有尚未成年的孩子，建议开启，避免访问不良网站
- 强制安全搜索：隐藏 Bing、Google、Yandex、YouTube 网站上 NSFW 等不适宜的内容
- 查询记录保留时间：AdGuard Home 服务端采用 Sqlite 文件数据库存储日志，长时间保留可能会降低运行速度，同时占用大量的储存空间，家庭用户一般保留 24 小时 - 7 天即可
- 统计数据保留时间：用于仪表盘的数据展示，一般保留 24 小时 - 7 天即可

### DNS 设置

![image](https://user-images.githubusercontent.com/74764072/165744440-7511089d-99a7-4387-a696-0eafd992707d.png)

- 上游 DNS 服务器：AdGuard Home 的上游 DNS 服务器，可参考下方推荐列表，一般保留 1 - 2 个即可。AdGuard Home 除了可以作为广告过滤网关，如果设置了纯净 DNS 后，还可以避免运营商的 DNS 劫持
- BootStrap DNS 服务器地址：作为 DoH / DoT DNS 的前置 DNS 解析器，可参考下方推荐列表
- 查询方式、速度限制、EDNS、DNSSEC、拦截模式、DNS 缓存设置、访问设置可根据需要进行调整，一般保持默认设置即可

![image](https://user-images.githubusercontent.com/74764072/165878997-4f612814-68d5-4800-a1bc-f5968eb59ed0.png)
- 忽略解析文件 这个就是本机缓存 但是我们使用了ADG的 ADG会帮我们缓存
### DNS 服务器推荐
- 不同地区连接至 DNS 服务器的速度各有差异，各位可以通过 Ping 测速的方式寻找当地连接延迟最低的 DNS 服务器。更多 DNS 服务器可以在 AdGuard 文档中找到。

- 阿里	IPv4 DNS	```223.5.5.5```
- IPv6 DNS	```2400:3200:baba::1```
- DNS-over-Https	``` https://dns.alidns.com/dns-query ```
- DNSPod	IPv4 DNS	```119.29.29.29```
- DNS-over-Https	```https://doh.pub/dns-query```
- 114	IPv4 DNS	```114.114.114.114```
- Google	IPv4 DNS	```8.8.8.8```
- IPv6 DNS	```2001:4860:4860::8888```
- DNS-over-Https	```https://dns.google/dns-query```
- Cloudflare	IPv4 DNS	```1.1.1.1```
- IPv6 DNS	```2606:4700:4700::1111```
- DNS-over-Https	```https://dns.cloudflare.com/dns-query```

### DNS 封锁清单
为了更好地发挥 AdGuard Home 去广告的功能，仅依靠默认的过滤规则是不够的，但也不宜过多，过多的过滤规则会影响解析的速度，各位可以根据需要添加过滤规则。
![image](https://user-images.githubusercontent.com/74764072/165744929-35204abf-d8ec-4579-8119-154c28a7c952.png)

- 名称	简介	地址
- AdGuard DNS Filter	AdGuard 官方维护的广告规则，涵盖多种过滤规则	```https://raw.githubusercontent.com/AdguardTeam/FiltersRegistry/master/filters/filter_15_DnsFilter/filter.txt```
- EasyList	Adblock Plus 官方维护的广告规则	```https://easylist-downloads.adblockplus.org/easylist.txt```
- EasyList China	面向中文用户的 EasyList 去广告规则	```https://easylist-downloads.adblockplus.org/easylistchina.txt```
- EasyPrivacy	反隐私跟踪、挖矿规则	```https://easylist-downloads.adblockplus.org/easyprivacy.txt```
- Halflife 规则	涵盖了 EasyList China、EasyList Lite、CJX ’s Annoyance、乘风视频过滤规则，以及补充的其它规则	```https://gitee.com/halflife/list/raw/master/ad.txt```
- Xinggsf 乘风过滤	国内网站广告过滤规则	```https://gitee.com/xinggsf/Adblock-Rule/raw/master/rule.txt```
- Xinggsf 乘风视频过滤	视频网站广告过滤规则	```https://gitee.com/xinggsf/Adblock-Rule/raw/master/mv.txt```
- MalwareDomainList	恶意软件过滤规则	```https://www.malwaredomainlist.com/hostslist/hosts.txt```
- Adblock Warning Removal List	去除禁止广告拦截提示规则	```https://easylist-downloads.adblockplus.org/antiadblockfilters.txt```
- Anti-AD	命中率高、兼容性强	```https://anti-ad.net/easylist.txt```
- Fanboy’s Annoyances List	去除页面弹窗广告规则	```https://easylist-downloads.adblockplus.org/fanboy-annoyance.txt```

- 以浏览国内网站为主的用户可以使用 anti-AD + Halflife 过滤规则，如有浏览国外网站的需要，可以根据需要添加 AdGuard DNS Filter、Fanboy's Annoyances List 等规则。不同规则之间会存在重叠的情况，可以通过 AdGuard Home 的拦截日志分析哪些规则的使用频率最高，哪些规则拦截频率最低，再加以取舍。

### 替换设备 DNS
完成 AdGuard Home 的设置后，便可将 AdGuard Home 的 DNS 地址部署到局域网设备上。

- passwall

![image](https://user-images.githubusercontent.com/74764072/165879116-07f24f2d-55f8-4565-8bce-7e3b80f70c26.png)

- shadowsocksr

![image](https://user-images.githubusercontent.com/74764072/165879433-73810d04-bd3e-40f9-b87c-bf6c41ff6a63.png)


- helloword
和上面一样

### 更改路由器 DNS 地址
不同品牌路由器修改的方法各有差异，具体步骤可参照说明书或网上的教程（路由器型号 + 更改 DNS）

原文地址来自 https://sspai.com/post/63088
