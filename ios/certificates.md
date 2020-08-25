---
parent: iOS
title: Certificates
---

# All Certificates guidlines
{: .no_toc}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Certificate for push notifications

1. Run Keychan on OS X
	1. Go to Keychain Access -> Certificate Assistance -> Request a Certificate from Certificarte Authority
	2. In User Email Address Place your apple ID email
	3. Set checkbox `Save to disk`
	4. Save
2. In [create link](https://developer.apple.com/account/ios/certificate/create/) generate new `.cer` file 
	1. Choose Services->Apple Push Notification service SSL (Sandbox & Production) (In already created app account with registered app)
	2. Choose Your Bundle ID `48TTJG4PT9.com.example`
	3. Upload a Certificate Signing Request generated in Step #1 and press Continue
	4. Download Your Certificate
3. Open `.cer` with `Keychain` on OS X in Login and Certificates tabs
4. Right Click on Certificate and choose export function as .p12 file
5. Copy both `.cer` and `.p12` certificates to project path

```terminal
$ openssl x509 -inform der -in aps_development.cer -out certificate.pem
```

Where:
- `aps_development.cer` - your certificate from developer.apple.com
- `certificate.pem` - new pem certificate

```terminal
$ openssl pkcs12 -nocerts -in Certificates.p12 -out p12Certificates.pem
```
Where `passwords` - your current pass phrase for generated certificate

6. Generate apns pem file

```terminal
$ cat certificate.pem p12Certificates.pem > apns_cert.pem
```

To verify the APNS Certificate use the following command:

```terminal
$ openssl s_client -connect gateway.sandbox.push.apple.com:2195 -cert apns_cert.pem -key apns_cert.pem
```
Where `passwords` - your current pass phrase for generated certificate

Response example:

```Terminal
CONNECTED(00000006)
depth=2 O = Entrust.net, OU = www.entrust.net/CPS_2048 incorp. by ref. (limits liab.), OU = (c) 1999 Entrust.net Limited, CN = Entrust.net Certification Authority (2048)
verify return:1
depth=1 C = US, O = "Entrust, Inc.", OU = See www.entrust.net/legal-terms, OU = "(c) 2012 Entrust, Inc. - for authorized use only", CN = Entrust Certification Authority - L1K
verify return:1
depth=0 C = US, ST = California, L = Cupertino, O = Apple Inc., CN = gateway.sandbox.push.apple.com
verify return:1
---
Certificate chain
 0 s:/C=US/ST=California/L=Cupertino/O=Apple Inc./CN=gateway.sandbox.push.apple.com
   i:/C=US/O=Entrust, Inc./OU=See www.entrust.net/legal-terms/OU=(c) 2012 Entrust, Inc. - for authorized use only/CN=Entrust Certification Authority - L1K
 1 s:/C=US/O=Entrust, Inc./OU=See www.entrust.net/legal-terms/OU=(c) 2012 Entrust, Inc. - for authorized use only/CN=Entrust Certification Authority - L1K
   i:/O=Entrust.net/OU=www.entrust.net/CPS_2048 incorp. by ref. (limits liab.)/OU=(c) 1999 Entrust.net Limited/CN=Entrust.net Certification Authority (2048)
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIHeTCCBmGgAwIBAgIRAPbAgfgVBaKmAAAAAFD2zUQwDQYJKoZIhvcNAQELBQAw
gboxCzAJBgNVBAYTAlVTMRYwFAYDVQQKEw1FbnRydXN0LCBJbmMuMSgwJgYDVQQL
Ex9TZWUgd3d3LmVudHJ1c3QubmV0L2xlZ2FsLXRlcm1zMTkwNwYDVQQLEzAoYykg
...
...
-----END CERTIFICATE-----
subject=/C=US/ST=California/L=Cupertino/O=Apple Inc./CN=gateway.sandbox.push.apple.com
issuer=/C=US/O=Entrust, Inc./OU=See www.entrust.net/legal-terms/OU=(c) 2012 Entrust, Inc. - for authorized use only/CN=Entrust Certification Authority - L1K
---
Acceptable client certificate CA names
/C=US/O=Apple Inc./OU=Apple Certification Authority/CN=Apple Root CA
/CN=Apple Application Integration 2 Certification Authority/OU=Apple Certification Authority/O=Apple Inc./C=US
/C=US/ST=CA/L=Cupertino/O=Apple Inc./OU=Internet Software and Services/CN=iCloud Test/emailAddress=APNS-Dev@group.apple.com
/CN=Apple Corporate Authentication CA 1/OU=Certification Authority/O=Apple Inc./C=US
/C=US/O=Apple Inc./OU=Apple Worldwide Developer Relations/CN=Apple Worldwide Developer Relations Certification Authority
/C=US/ST=California/L=Cupertino/O=Apple Inc./CN=gateway.sandbox.push.apple.com
/CN=Apple Corporate Root CA/OU=Certification Authority/O=Apple Inc./C=US
/C=US/O=Apple Inc./OU=Apple Certification Authority/CN=Apple Application Integration Certification Authority
---
SSL handshake has read 4438 bytes and written 2341 bytes
---
New, TLSv1/SSLv3, Cipher is DES-...
Server public key is 2048 bit
Secure Renegotiation IS supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
SSL-Session:
    Protocol  : TLSv1.2
    Cipher    : DES-CB...
    Session-ID: 
    Session-ID-ctx: 
    Master-Key: 38AEEFB6EC4443044EBBB561BBCEE1662E28E436B835F7...
    Start Time: 1598357126
    Timeout   : 7200 (sec)
    Verify return code: 0 (ok)
---
```

[source](https://www.youtube.com/watch?v=3HGPnuiLHM0)