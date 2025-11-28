Simple OpenWRT failover script utilizing policy routing, written by Citizen-2CB8A24A in 11.2025
This is developed on a three router setup, but it can be used with just one router as well. Just
do not use the (remote) link reset options (WAN1RESET, WAN2RESET) in the latter case.

Features:
* Routing changes are done by changing the routing policy
* Script determines providers next hop for cheaper pings
* Two pings will be sent, but just one has to come through
* Ping overall timeout will be 2 seconds
* Stale TCP connections get killed by "conntrack -D ..."
* No IPTABLES/netfilter involvement
* Using "/tmp/", to protect flash memory
* Session based information is gathered just once
* WAN-status at "http://router-IP/wan-status.html" (can be disabled).

Installation:
1.) Put this script in "/etc/" and ensure backup inclusion.
2.) Adjust config section.
3.) Call this script by cron every 2-5 minutes and things will be smooth.

Remarks:
The log-file "log" is created in "/tmp/failover"
Default routes are deleted in the main table on first run.
Default routes are recovered in their own tables, if an interface was down.

License:
Creative Commons Zero v1.0 Universal
https://creativecommons.org/publicdomain/zero/1.0/deed.en
