# 💡 HTTP/S

     -A PREROUTING -i eth0 -p tcp -m multiport --dports 80,443 -j DNAT --to-destination 172.31.95.11
# 💡  FTP/S

    -A PREROUTING -i eth0 -p tcp -m tcp --dport 990 -j DNAT --to-destination 172.31.95.11
    -A PREROUTING -i eth0 -p tcp -m tcp --dport 21 -j DNAT --to-destination 172.31.95.11
    -A PREROUTING -i eth0 -p tcp -m tcp --dport 10000:10100 -j DNAT --to-destination 172.31.95.11
# 💡  REMOTE CLIENT    
    -A PREROUTING -i eth0 -p tcp -m tcp --dport 3389 -j DNAT --to-destination 172.31.96.13
    -A PREROUTING -i eth0 -p tcp -m tcp --dport 3390 -j DNAT --to-destination 172.31.96.14:3389
# 💡  EMAIL SERVER

    -A PREROUTING -i eth0 -p tcp -m tcp --dport 25 -j DNAT --to-destination 172.31.96.11
    -A PREROUTING -i eth0 -p tcp -m tcp --dport 465 -j DNAT --to-destination 172.31.96.11
    -A PREROUTING -i eth0 -p tcp -m tcp --dport 587 -j DNAT --to-destination 172.31.96.11
    -A PREROUTING -i eth0 -p tcp -m tcp --dport 110 -j DNAT --to-destination 172.31.96.11
    -A PREROUTING -i eth0 -p tcp -m tcp --dport 143 -j DNAT --to-destination 172.31.96.11
    -A PREROUTING -i eth0 -p tcp -m tcp --dport 993 -j DNAT --to-destination 172.31.96.11
    -A PREROUTING -i eth0 -p tcp -m tcp --dport 995 -j DNAT --to-destination 172.31.96.11
# 💡  WAZUH SERVER

    -A PREROUTING -i eth0 -p tcp -m tcp --dport 444 -j DNAT --to-destination 172.31.96.12:443
# 💡  NAT

    -A POSTROUTING -o eth0 -j MASQUERADE
