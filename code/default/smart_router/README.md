


command to make linux allow non-root user listen on 53 port:
`sudo setcap 'cap_net_bind_service=+ep' /usr/bin/python2.7`

setcap is in the debian package libcap2-bin
at least a 2.6.24 kernel





sudo iptables -t nat -N REDSOCKS
sudo iptables -t nat -A REDSOCKS -p tcp -j REDIRECT --to-ports 8083
sudo iptables -t nat -A PREROUTING --in-interface $interface -p tcp -j REDSOCKS


clean iptables:
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -t nat -F
iptables -t mangle -F
iptables -F
iptables -X