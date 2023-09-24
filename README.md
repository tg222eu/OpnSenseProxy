# OpnSense Proxy

A configuration to setup a proxy that blacklist webpages on a OpnSense firewall based on Squid. 

Prerequisite: OpnSense already installed

# Configuration

First we have to create a certificate

![alt text](https://github.com/tg222eu/OpnSenseProxy/blob/main/Screenshot/Certificate.JPG) <br>
System -> Trust -> Authorities then click add (+) button
Give the certificate any descriptive name, select method "Create an Internal Certificate Authority", leave the rest as default, fill in the distinguished name section by your choice

Download the newly created certificate by pressing "Export CA cert" button" and apply it on the client. Run through the wizard, store it on the local machine and select "Place all certificates in the following store", browse into "Trusted root Certification Authorities" then finish.

![alt text](https://github.com/tg222eu/OpnSenseProxy/blob/main/Screenshot/WebproxyAdmin.JPG)<br>
Head to Services -> Web Proxy -> Administration
Select Enable proxy

![alt text](https://github.com/tg222eu/OpnSenseProxy/blob/main/Screenshot/forwardproxy.JPG)<br>
On the same page, head over to the Forward Proxy tab
Select the "i" icon to bring up the description for "Enable Transparent HTTP Proxy". There will be a warning description that explains you need to configure a firewall rule. Click on the "Add new firewall rule", once clicked a populated firewall rule will appear and the only thing you have here is to click save, Then apply changes. REPEAT THE STEP FOR "ENABLE SSL INSPECTION"

![alt text](https://github.com/tg222eu/OpnSenseProxy/blob/main/Screenshot/firewallrule.JPG)<br>
Make a firewall rule that block ports 443, 80 from LAN source to any destination. This will prevent any bypass of the proxy filter

Head back to Forward Proxy Tab. Select "Enable Transparent HTTP Proxy" and "Enable SSL Inspection", fill in your newly created certificate authority in "CA to use". Hit apply, this will take up to 30 sec to apply.

![alt text](https://github.com/tg222eu/OpnSenseProxy/blob/main/Screenshot/blacklist.JPG)<br>
Next head over to "Remote Access Control Lists" Tab, hit the "Add" button. Add a filename for storing the configuration and in the URL section fill in ftp://ftp.ut-capitole.fr/pub/reseau/cache/squidguard_contrib/blacklists.tar.gz <br> This link is provided by The Université Toulouse which gives out their blacklist for free and keeps growing. This is also the list OPNsense recommend in their documentation . Hit Save and then download ACLs 

The firewall should now block webpages based on Université Toulouse filter

# Troubleshooting

If blacklisted website dont get the message "Access Denied" but instead "This site can’t be reached" the NAT port forwarding might not be set up correctly.

