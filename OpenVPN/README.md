#After you configured your OpenVPN Server and clients

1. [RedHaT Server](https://github.com/LS-Melo/AWS-PROJECT/tree/main/OpenVPN/RedHat%20(Main%20Server))

     Or if your Main Server is...
[Debian Server](https://github.com/LS-Melo/AWS-PROJECT/tree/main/OpenVPN/Debian%20(Main%20Server))

2. [Remote Client](https://github.com/LS-Melo/AWS-PROJECT/tree/main/OpenVPN/Remote%20Client)

#With your certificates and every 'tunnel' ready to start

1. [Certificates (CA)](https://github.com/LS-Melo/AWS-PROJECT/tree/main/Certificates%20(CA))

#You must:

# SERVER (ENTA)

    Systemctl restart openvpn@server_ra
    Systemctl restart openvpn@server_ss
    Systemctl status openvpn@server_ra
    Systemctl status openvpn@server_ss
   
💡  Check if your 'tunnel' is opened:

    ip a
    
# CLIENT (INOVA)

    Systemctl restart openvpn@server_ss
    Systemctl status openvpn@server_ss
    
💡  Check if your 'tunnel' is opened:

    ip a

# CLIENT (REMOTE)

    Systemctl restart openvpn@server_ra
    Systemctl restart openvpn@server_ss
    
💡  Now you should check if your instances are all connected to each other

    ping INSTANCE_IP
    
   
#Same process if the 'Main Server' is INOVA
