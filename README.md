# OpnSenseProxy

A configuration to setup a proxy, blacklist and webfiltering on a OpnSense firewall based on Squid. 

Prerequisite: OpnSense already installed

First we have to create a trusted certificate

System -> Trust -> Authorities then click add (+) button
Give the certificate any descriptive name, select method "Create an Internal Certificate Authority", leave the rest as default, fill in the distinguished name section by your choice

Download the newly created certificate by pressing "Export CA cert" button" and apply it on the client. Run through the wizard, store it on the local machine and select "Place all certificates in the following store", browse into "Trusted root Certification Authorities" then finish.

Head to Services -> Web Proxy -> Administration
Select Enable proxy

Configuration
