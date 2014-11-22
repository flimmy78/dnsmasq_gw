dnsmasq_gw
==========

dnsmasq + ipset + iproute2 ＋ iptables 策略路由（通过域名选择出口）， 但在路由本机无法做到，所在我在dnsmasq里添加了一个iproute.c,通过配置文件设置，为每一个域名设置默认网关。
