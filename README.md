dnsmasq_gw
==========

dnsmasq + ipset + iproute2 ＋ iptables 策略路由（通过域名选择出口）， 但在路由本机无法做到，所以我在dnsmasq里添加了一个iproute.c,通过配置文件设置，为每一个域名设置默认网关。

设置：

1. ipset -N vpn hash:ip    /* 创建一个名为vpn 的设置 */
配置文件格式做了一点扩展
server=/googleapis.com/127.0.0.1
ipset=/google.com/vpn:ppp0    /* google.com 的域名走ppp0 网卡出去 */

在不修改dnsmasq 的源代码的前提下，也可以用小脚本完成。如：

for ip in `ipset list | awk 'NR>6'`;do ip route add $ip dev ppp0;done
