---
parent: Docker
title: Ubuntu
---

# ubuntu-configuration
{: .no_toc}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Configure docker for Run without sudo

```
$ sudo groupadd docker
$ sudo usermod -aG docker $USER
$ newgrp docker 
```
