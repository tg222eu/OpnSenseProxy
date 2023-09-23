# OpnSenseProxy

A configuration to setup a proxy, blacklist and webfiltering on a OpnSense firewall based on Squid. 

Prerequisite: OpnSense already installed

First we have to create a trusted certificate

System -> Trust -> Authorities then click add (+) button
Give the certificate any descriptive name, select method "Create an Internal Certificate Authority", leave the rest as default, fill in the distinguished name section by your choice

Download the newly created certificate by pressing "Export CA cert" button" and apply it on the client. Run through the wizard, store it on the local machine and select "Place all certificates in the following store", browse into "Trusted root Certification Authorities" then finish.

Head to Services -> Web Proxy -> Administration
Select Enable proxy

On the same page, head over toi the Forward Proxy tab
Select the "i" icon to bring up the description for "Enable Transparent HTTP Proxy". There will be a warning description that explains you need to configure a firewall rule. Click on the "Add new firewall rule", once clicked a populated firewall rule will appear and the only thing you have here is to click save, Then apply changes.

Head back to Forward Proxy Tab. Select "Enable Transparent HTTP Proxy" and "Enable SSL Inspection", fill in your newly created certificate authority in "CA to use". Hit apply, this will take up to 30 sec to apply.


Configuration
