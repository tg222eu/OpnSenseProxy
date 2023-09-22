# OpnSenseProxy

A configuration to setup a proxy, blacklist and webfiltering on a OpnSense firewall based on Squid. 

Prerequisite: OpnSense already installed

First we have to create a trusted certificate

System -> Trust -> Authorities then click add
Give the certificate any descriptive name, select method "Create an Internal Certificate Authority", leave the rest as default, fill in the distinguished name section by your choice

Configuration
