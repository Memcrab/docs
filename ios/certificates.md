---
parent: iOS
title: Rsync/Lsync
---

# All Certificates guidlines
{: .no_toc}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Certificate for push notifications

1. In [create link](https://developer.apple.com/account/ios/certificate/create/) generate new `.cer` file (In already created app account with registered app)
2. Open `.cer` with `Keychain` on OS X
3. Copy certificate to login tab in `Keychain` and export it as .p12 file
4. Copy both `.cer` and `.p12` certificates to project path

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

5. Generate apns pem file

```terminal
$ cat certificate.pem p12Certificates.pem > apns_cert.pem
```

To verify the APNS Certificate use the following command:

```terminal
$ openssl s_client -connect gateway.sandbox.push.apple.com:2195 -cert apns_cert.pem -key apns_cert.pem
```
Where `passwords` - your current pass phrase for generated certificate

[source](https://www.youtube.com/watch?v=3HGPnuiLHM0)