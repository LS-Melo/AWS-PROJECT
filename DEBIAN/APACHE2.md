apt update && apt upgrade
	
	apt install apache2
	a2enmod ssl
	a2ensite default-ssl.conf
	systemctl restart apache2

nano /etc/apache2/sites-available/default-ssl.conf

💡	DocumentRoot /var/www/htmls
💡	#Insert your certificates directories


cd /var/www/
cp -r html/ htmls

cd html/

💡	> index.html
💡	nano index.html 		# WRITE SOMETHING FOR YOUR PORT: 80 PAGE

cd../htmls

💡	> index.html
💡	nano index.html 		# WRITE SOMETHING FOR YOUR PORT: 443 PAGE
	
systemctl restart apache2

#Open your browser or your client browser (if you have your DNS Server working and iptables rules defined)

#You can search by "www.server.world" and "https://www.server.world/"
#Otherwhise...
#Search by your Public IP

#Now you have your apache2 working :)
#NOTE: To try secure connection, you must have your "ca.crt" uploaded at your "browser certificates > Authorities"