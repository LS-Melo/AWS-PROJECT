# 💡  HTTP/S

    -A PREROUTING -i eth0 -p tcp -m multiport --dports 80,443 -j DNAT --to-destination 172.31.97.11
# 💡  WAZUH SERVER
    
    -A PREROUTING -i eth0 -p tcp -m tcp --dport 444 -j DNAT --to-destination 172.31.98.12:443
# 💡  REMOTE CLIENT

    -A PREROUTING -i eth0 -p tcp -m tcp --dport 3389 -j DNAT --to-destination 172.31.98.13
    -A PREROUTING -i eth0 -p tcp -m tcp --dport 3390 -j DNAT --to-destination 172.31.98.14:3389
# 💡  NAT

    -A POSTROUTING -o eth0 -j MASQUERADE
