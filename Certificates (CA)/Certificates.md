💡  After we've done a [SubCA](https://github.com/LS-Melo/AWS-PROJECT/blob/main/Certificates%20(CA)/SUBCA.md) 

1.  We can start creating all the certificates that we need in this project
2.  And set them in the right directory

# Certificates for INOVA

INOVA

💡  cd /etc/easy-rsa/

    ./easyrsa build-server-full vpn.inovasrv.pt nopass      #For OpenVPN as INOVA is the main server (RA)
    ./easyrsa build-client-full vpn.inovacli.pt nopass      #For OpenVPN as INOVA is SS-Client
    ./easyrsa build-server-full www.inova.pt nopass         #For apache2 and ftp (used the same certificate for both)
    ./easyrsa build-server-full tele.inova.pt nopass        #For Teleport Server  
    ./easyrsa build-client-full vpn.remote.pt nopass        #For Remote Client OpenVPN Remote Access (RedHaT)
    ./easyrsa build-client-full vpn.remote2.pt nopass       #For Remote Client OpenVPN Remote Access (Debian)
    
💡  Send them to SSL directory:

    cp /etc/easy-rsa/pki/issued/* /etc/ssl/certs/
    cp /etc/easy-rsa/pki/private/* /etc/ssl/private/

# Certificates for ENTA

ENTA

💡  cd /etc/easy-rsa/3/

    ./easyrsa gen-req vpn.entasrv.pt nopass               #For OpenVPN as ENTA is the main server (RA)
    ./easyrsa gen-req vpn.entacli.pt nopass               #For OpenVPN as ENTA is SS-Client
    ./easyrsa gen-req www.enta.pt nopass                  #For httpd Server

💡  Now we need to send the requests (.req) to the CA Server (INOVA)

    cat /etc/easyrsa/3/pki/reqs/vpn.entasrv.pt.req        #We will sign OpenVPN Server (RA) Certificate
    #Copy it

INOVA

💡  nano /etc/easy-rsa/pki/reqs/vpn.entasrv.pt.req
    
    #Paste here
💡  Now we will sign it:

    ./easyrsa sign-req server vpn.entasrv.pt
💡  Send the result .crt file back to ENTA

    cat /etc/easy-rsa/pki/issued/vpn.entasrv.pt.crt
    #Copy it

ENTA

💡  We will send directly to the folder where we will use/need the certificate:

In this case, OpenVPN.

    nano /etc/openvpn/vpn.entasrv.pt.crt
    #Paste It
    
💡  Send another .req:

    cat /etc/easyrsa/3/pki/reqs/vpn.entacli.pt.req        #We will sign OpenVPN Client (SS) Certificate
    #Copy it
    
INOVA

💡  nano /etc/easy-rsa/pki/reqs/vpn.entasrv.pt.req

    #Paste here
💡  Now we will sign it:

    ./easyrsa sign-req client vpn.entacli.pt
💡  Send the result .crt file back to ENTA

    cat /etc/easy-rsa/pki/issued/vpn.entacli.pt.crt
    #Copy it

ENTA

💡  We will send directly to the folder where we will use/need the certificate

    nano /etc/openvpn/vpn.entacli.pt.crt
    #Paste Here
💡  Send another .req:

    cat /etc/easyrsa/3/pki/reqs/www.enta.pt.req        #We will sign HTTPD Server Certificate
    #Copy it
INOVA

💡  nano /etc/easy-rsa/pki/reqs/www.enta.pt.req 

    #Paste here
💡  Now we will sign it:

    ./easyrsa sign-req server www.enta.pt
💡  Send the result .crt file back to ENTA

    cat /etc/easy-rsa/pki/issued/vpn.entacli.pt.crt
    #Copy it
ENTA

💡  We will send directly to the folder where we will use/need the certificate

    nano /etc/pki/tls/certs/www.enta.pt.crt
    #Paste Here
    
# Certificates for Remote Client

💡  Now we will send the certificates for Remote Client

💡  We created them directly from INOVA so we do not need to receive any .req. We already had signed them.

    cat /etc/easy-rsa/pki/issued/vpn.remote.pt.crt
    #Copy It

Remote Client

💡  Send directly to OpenVPN folder:

    nano /etc/openvpn/vpn.remote.pt.crt
    #Paste Here

INOVA

    cat /etc/easy-rsa/pki/issued/vpn.remote2.pt.crt
    #Copy it

Remote Client

💡  Send directly to OpenVPN folder:

    nano /etc/openvpn/vpn.remote2.pt.crt
    #Paste Here

