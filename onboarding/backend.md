---
parent: Onboarding
title: Backend
---

# Backend
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

## Паттерны проектирования ООП
* https://refactoring.guru/ru/design-patterns
	* Выбрать 5 самых полезных и изучить
	* Уметь обяснить их человеку который не знаком с патернами: зачем патерн, как его сделать, где можно применить.
* обсудить Singleton и глобальные переменные
* обсудить Константы отдельно и в классах

##  ReactPHP. [Http Server](https://reactphp.org/http/)

### Объекты
* Request
* Response
* Middleware 

### EventLoop
 * addPeriodicTimer
 	* создать независимые таеймеры с выводом чего либо в STDOUT с разной периодичностью

# Postman

# Redis  
* Установить самостоятельно
* Записать в пару ключей разного типа данные через его родную консоль
* Считать данные по этим ключам
* Удалить ключи из хранилища
* Примеры использования в бизнес задачах

## Tokens
## Personal Data
## Cache Level

# Git for teams
* Пройти игру по Git полностью с пониманием - https://learngitbranching.js.org
* Изучить принципы git Flow https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow

# Queues RabbitMQ 
* обсудить:
	* примеры использования в бизнес кейсах
	* как строятся очереди
	* кто к кому образщается в схеме коммуникации
	* Workers
* Установить самостоятельно
* Написать на php консольный скрипт который создает очередь и ложит сообщения в очередь
* Написать на php консольный скрипт-listener (Worker) который считает сообщения из очереди цыклически - не умирая как процесс и запишет эти сообщения в файл новой строчкой
* Запустить ReactPHP HTTP Server процесс который отправляет в ту же очередь сообщения при запросе от клиента
* Запросы на HTTP Server слать через Postman

# X-debug + Docker
* общаемся 
	* о задачах
	* о не применимой области
	* о аналогах
	* о контенерах докера

# Docker

* Создать свой контейнер для консольного PHP на базе голого контейнера Ubuntu через docker file , 
* Сделать build докер файла в image c тегом (Названием), 
* запустить контейнер с полученного image, 
* Исполнить в контейнере php code/file (через entripoint) который создаст файл лога в конейнере , 
* уметь подключится в консоль контейнера и найти созданный файл.
* уметь посмотреть запущенные контейнеры
* уметь посмотреть НЕ запущенные контейнеры
* уметь удалить контейнер
* уметь удалить image

## Docker Compose
* Создать пусковой конфигурационный файл, 
* подключить php контейнер, 
* подготовить папку с кодом в которой будет наш тестовый reactPHP
* монтировать в php контейнер папку с твоим кодом, контейнер должен запускать  reactphp и не умирая слушать запросы от клиентов на порту 8000
* Добавить в Docker Compose контейнер базы данных Mysql 8, 
* Изменить код проекта так чтоб принимая запрос от клиента reactphp писал сообщение в таблицу Mysql (структура таблицы максимально простая и не играет роли в задании). 

# Monolog

## InfluxDB, 
* проговорить полностью системы мониторинга
## Loki,  
* проговорить для поддержки текущих проектов
## Grafana, 
* проговорить для поддержки текущих проектов

# Настройки Sublime с расширениями
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

# VSCODE
## plugins
	Name: Docker
	Id: ms-azuretools.vscode-docker
	Description: Makes it easy to create, manage, and debug containerized applications.
	Version: 1.18.0
	Publisher: Microsoft
	VS Marketplace Link: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker
	
	
	Name: Jira and Bitbucket (Atlassian Labs)
	Id: atlassian.atlascode
	Description: Bringing the power of Jira and Bitbucket to VS Code - With Atlassian for VS Code you can create and view issues, start work on issues, create pull requests, do code reviews, start builds, get build statuses and more!
	Version: 2.10.0
	Publisher: Atlassian
	VS Marketplace Link: https://marketplace.visualstudio.com/items?itemName=Atlassian.atlascode
	
	
	Name: PHP Intelephense
	Id: bmewburn.vscode-intelephense-client
	Description: PHP code intelligence for Visual Studio Code
	Version: 1.8.0
	Publisher: Ben Mewburn
	VS Marketplace Link: https://marketplace.visualstudio.com/items?itemName=bmewburn.vscode-intelephense-client
	
	
	Name: Psalm (PHP Static Analysis Linting Machine)
	Id: getpsalm.psalm-vscode-plugin
	Description: VS Code Plugin for Psalm
	Version: 2.4.0
	Publisher: Psalm
	VS Marketplace Link: https://marketplace.visualstudio.com/items?itemName=getpsalm.psalm-vscode-plugin
	
	
	Name: Todo Tree
	Id: gruntfuggly.todo-tree
	Description: Show TODO, FIXME, etc. comment tags in a tree view
	Version: 0.0.214
	Publisher: Gruntfuggly
	VS Marketplace Link: https://marketplace.visualstudio.com/items?itemName=Gruntfuggly.todo-tree