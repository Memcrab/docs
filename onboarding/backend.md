---
parent: Onboarding
title: Backend
---

# Backend Onboarding
{: .no_toc}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# PHP

## PHP PSR:
* psr-0
* psr-3
* psr-4
* psr-7
* psr-11

## ООП 5 патернів програмування (приклади використання, Singleton і глобальні перемінні)

##  ReactPHP. [Http Server](https://reactphp.org/http/)

### Обєкти 
* request
* response
* midddleware 

### EventLoop
 * addPeriodicTimer (створити декілька незалежних таймерів)

# Postman

# Redis  (приклади використання)
## Tokens
## Personal Data
## Cache Level

# Queues RabbitMQ (приклади використання, як будуються черги, хто куди звертається)
## Worker php

* підняти сервер - можна в контейнері можна локально
* запустити listener (Worker) на php
* Запустити ReactPHP HTTP Server процесс який відправляє в чергу повідомлення при запиті від кліэнта

```terminal 
наприклад записати до файлу,щось максимально просте, що
він отримав це повідомлення з іншого боку повинен бути наш процес на ReactPHP.
в який з постмена слати запит, а він покладе його
в цю чергу.
```

# X-debug + Docker

# Docker

* Створити контейнер з докер файлу, збілдити контейнер в імедж, запустити контейнер, виконати в ньому код, підключитьсь в консоль до контейнера.
* видалити контейнер
* видалити імедж

## Docker Compose
* Створити файл управління, 
* підключити PHP контейнер, 
* монтувати туди папку з кодом, зробити його там робочим, 
* підключити в конпоуз контейнер бази даних, 
* зробити так щоб код спілкувався з базою. 

# Monolog

## InfluxDB, 

## Loki,  

## Grafana, 

# Налаштувати Sublime з розширеннями 
* Линтер для Sublime text, который мы юзаем
* phpfmt

```
В настройках плагина (User) прописать. Путьк бинарнику пыхи php_bin зависит от системы, но в Линуксе "/usr/bin/php"
{
	"indent_with_space": 4,
	"option": "value",
	"php_bin": "/usr/bin/php",
	"version": 1
}
```

# Core architecture
## Balancers
## Multiprocess
## Fault Tolerance
## Routing
## Caching
* CDN
* Redis
* Frontend state
* In Memory Caceh `ImCache`
	* Activete by requests
* Data Objects state in process
	* Timers
 
# Sockets
## Web Sockets based on Ratchet

# AWS S3 storage (API+ SDK)

# AWS SQS (API+ SDK)

# AWS SES (API+ SDK)

# AWS SES

# Firebase

# Mandril from Mailchimp (API+ SDK)

# Payment Getaways
## Stripe
## Fondy

# Jira (принципи роботи)
# Bitbucket (принципи роботи)
## Pull-Requests

* One linter for all

# Elastic Search

* DB structures
* Manipulate with data
* Search Enging configuration

# Video streaming by Janus
## Configuration
## Publishing

* videoroom
* controls
* Recording
* Codecs

## FFMPEG
* configuration
* Video History generation
* Mixing audiio
* Place video in frames
* Recover damaged files

