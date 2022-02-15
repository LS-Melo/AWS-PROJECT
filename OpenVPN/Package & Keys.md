**********  Package & Keys for OpenVPN Server/Client  **********

# ENTA  (OpenVPN Server)

sudo su -

💡  Install OpenVPN package:
 
    apt install openvpn

cd /etc/openvpn/

💡  Now we need to generate a 'ta.key' and 'dh2048.pem':

    openvpn --genkey --secret ta.key
    openssl dhparam -out dh2048.pem 2048
 
💡  After that, send them to your OpenVPN Server and Clients:
    
    #Copy it
    cat ta.key/
  
# INOVA  (OpenVPN Client)

cd /etc/openvpn/
    
    #Paste your 'ta.key' into your Clients OpenVPN directory:
    nano ta.key

💡  Now go back to your Server (ENTA) and copy dh2048.pem:

    #Copy it
    cat /etc/openvpn/dh2048.pem

💡  Return to your client:

    #Paste it
    nano /etc/openvpn/dh2048.pem
    
#Now you can create your OpenVPN configuration files

#Must have your certificates (CA) and a 'ca.crt' file signed from your server

#Everything inside /etc/openvpn/
