#After you configured your OpenVPN Server and clients

#With your certificates and every 'tunnel' ready to start

#You must:

# SERVER (ENTA)

    Systemctl restart openvpn@server_ra
    Systemctl restart openvpn@server_ss
    Systemctl status openvpn@server_ra
    Systemctl status openvpn@server_ss
   
💡  Check if your 'tunnel' opened:

    ip a
    
# CLIENT (INOVA)

    Systemctl restart openvpn@server_ss
    Systemctl status openvpn@server_ss
    
💡  Check if your 'tunnel' opened:

    ip a

# CLIENT (REMOTE)

    Systemctl restart openvpn@server_ra
    Systemctl restart openvpn@server_ss
    
💡  Now you should check if your instances are all connected to each other

    ping INSTANCE_IP
    
   
#Same process if the 'Main Server' is INOVA
