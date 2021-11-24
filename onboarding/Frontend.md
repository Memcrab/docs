---
author: Max Mykhailenko
tags: onboarding, JS, TS
parent: Onboarding
title: Frontend Onboarding
---
# Frontend

## Управление задачами
- Ознакомиться с workflow
- системой логирования
- Освежить в памяти базовые принципы Agile  

## Совместная работа
- Git
- Docker
- CI/CD
- Husky
- eslint-config-memcrab

## Асинхронная догрузка модулей
- chunking
- React lazy, React Suspense

## Производительность
- Performance dev tools: Long task etc  
- RAF
- Headers Cache-control

## HTML/CSS
- Images lazy load (html)
- Размеры в CSS (em, rem, pt, px, vw, vh, etc)
- Scroll snap
- css variables
- GPU accelerated animations
- Canvas, SVG
- Adaptation for Retina displays
- Lighthouse/pagespeed
- Accessebility

## Javascript/Typescript
- ES 2016+
	- Async Generators
- Browsers API
- Видео по архитектуре
- Custom Errors classes
- Typescript — полностью вся документация. Понимание когда type, а когда interface. Понимание работы generic и умение писать свои. Уметь типизировать все стандартные конструкции map, reduce, Object.keys
- Typescript Generic
- Zod — либа для валидации данных. Научиться интегрирвать с TS и писать как будто писал всю жизнь схема
- Иммутабельные подходы по взаимодействию с данными

## Умение использовать Промисы

### Понятия, которыми нужно владеть

-   Promise
-   async/await
-   try/catch
-   Что возвращает метод then?
-   Можно ли заменить catch методом then?
-   Можем ли мы делать throw new Error(“”) или мы должны делать только return Promise.reject(new Error(“”)) в async функциях?

### Практические задачи для выполнения (на javascript)

1.  Написать функцию sleep. Использоваться будет так “await sleep(ms)”, основной поток не блокирует.


## React
- NodeJs
	- http
	- qs
- React SSR
- React router

## Тестирование
- Jest — snapshot, act и остальные части докумнетации. Попробовать написать для тестового. Эмулиция кликов и прочих взаимодействий без использования enzyme, только react-test-renderer и jest
- react-test-renderer
- jest mocks for fetch, cookies, etc

## Решить все задания
![[👉 Hard Baseline]]