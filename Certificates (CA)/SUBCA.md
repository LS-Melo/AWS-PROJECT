In this project we need a 'Subordinte CA' localized at 'control.inova.pt'

We'll start by installing the Easy-RSA package (for INOVA & ENTA)
# ENTA & INOVA (DO ON BOTH)
💡  UBUNTU

    apt install easy-rsa
    cp -r /usr/share/easy-rsa/ /etc/
    cd /etc/easy-rsa/
💡  REDHAT
    
    amazon-linux-extras install epel
    yum install easy-rsa
    cp -r /usr/share/easy-rsa/ /etc/
    cd /etc/easy-rsa/3/
💡  nano openssl-easyrsa.conf

    Comment #RANDFILE

mv vars.example vars

💡  nano vars

    #Add the details from your company/entity by:
    #Changing 'ca_only' to 'org'
    
    set_var EASYRSA_DN     "org"

    set_var EASYRSA_REQ_COUNTRY    "Country"
    set_var EASYRSA_REQ_PROVINCE   "Province"
    set_var EASYRSA_REQ_CITY       "City"
    set_var EASYRSA_REQ_ORG        "ORG"
    set_var EASYRSA_REQ_EMAIL      "webmaster@email.com"
    set_var EASYRSA_REQ_OU         "ID"
    
# ENTA

💡  In ENTA Server we must create a normal 'ca' key

    ./easyrsa init-pki
    ./easyrsa build-ca
   
# INOVA (SUBCA SERVER)

💡  In INOVA Server we will request a SUBCA so we can send '.req' to ENTA to sign it!

    ./easyrsa init-pki
    ./easyrsa build-ca subca
Copy the certificate request

    cat /etc/easy-rsa/pki/reqs/ca.req
    
# ENTA

💡  We need to import the subca request from INOVA and sign it!

    cd /etc/easyrsa/3/pki/reqs/
    #Paste subca request here:
    nano subca.req
cd ../..

    ./easyrsa sign-req ca subca
💡  Now we must have both 'CA' (from INOVA and ENTA) together in just one file (subca.crt)

💡  So we should send ENTA 'ca' content inside 'subca.crt'

    cat /etc/easy-rsa/3/pki/ca.crt >> /etc/easy-rsa/3/pki/issued/subca.crt
    #Now copy the new subca
    cat /etc/easy-rsa/3/pki/issued/subca.crt
# INOVA

💡  Paste the subca in:

    nano /etc/easy-rsa/pki/ca.crt
    
#Now we can start creating our certificates :)  [Certificates (CA)](https://github.com/LS-Melo/AWS-PROJECT/blob/main/Certificates%20(CA)/Certificates.md)
