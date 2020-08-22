---
parent: Linux
title: Rsync/Lsync
---

# Rsync/Lsync usage
{: .no_toc}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Rsync Server to Server copy with ssh key

```terminal
$ rsync -ISOarz --links -e "ssh -i any_rsa_or_pem_key_path" /var/www/master/storage/* REMOTE_USER@REMOTE_IP:/var/www/master/storage/
```