---
title: SSL (https)
has_children: false
nav_order: 2
---

# SSL (https)
{: .no_toc}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Generate root certificate

Generate Root Cert to sign all future certificates

```
$ openssl genrsa -out ca.key 4096
```

# Generate domain certificate

Generate certificate with respect to restriction by apple policy mentioned in [this article](http://blog.nashcom.de/nashcomblog.nsf/dx/more-strict-server-certificate-handling-in-ios-13-macos-10.15.htm?opendocument&comments)

* By one line command
	```
	$ openssl x509 -req -sha256 -days 800 -in server.csr -CA ca.crt -CAkey ca.key -out server.crt -CAcreateserial -extfile <(printf "extendedKeyUsage = serverAuth \n subjectAltName=DNS:tnl.api.dev,DNS:tnl.app.dev")
	```
* Or by using config file inside command
	```
	$ openssl req -x509 -nodes -days 730 -newkey rsa:2048 -keyout api.https.key -out api.https.crt -config api.openssh.conf -extensions 'v3_req'
	```
	
	Config file:
	```
	[req]
	distinguished_name = req_distinguished_name
	x509_extensions = v3_req
	prompt = no
	[req_distinguished_name]
	C = US
	ST = New York
	L = New York
	O = memCrab
	OU = memCrab
	CN = *.app.dev
	[v3_req]
	keyUsage = keyEncipherment, dataEncipherment
	extendedKeyUsage = serverAuth
	subjectAltName = @alt_names
	[alt_names]
	DNS.1 = *.app.dev
	DNS.2 = *.api.dev
	```
* Asterisk to accept all subdomains (that presented in 2.b.) was not tested as working version on iOS. iOS was working only with dirrect DNS records as placed at 2.a.

# Activate Certificates on OS X
	* add `ca.crt` and `server.crt` add to keychain tool and switch it as Always trusted - works for all browsers

# Activate certificates locally on iOS and iPad OS
	- install `Apple Configurator` app to your MacOS 
	- connect your iOS device. 
	- Create new Profile from top menu of `Apple Configurator`. 
	- Choose both ca.crt and server.crt as certificates inside profile
	- Fill `General Information` about profile
	- Store profile on disk (`cmd+s`)
	- Upload profile to iOS using `Apple Configurator` menu
	- Install profile inside iOS from `Settings->General->profiles`
	- Set certificates as trusted in `Settings->gentral->about->trusted Certificates`
	- Configure DNS server to answer on domain in local network. It can be router DNS or some iOS application with DNS redirect function. For now we prepared router DNS to specific local IP

# Activate Certificates on Ubuntu
	* need to be provided

# Activate Certificates in FireFox:
	* Open settings
	* Privacy and security
	* Authorities
	* Add Root certificate ca.crt
	* Restart browser
