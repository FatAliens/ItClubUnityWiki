---
description: >-
  Установка Unity Hub, Unity 2019 и Visual Studio 2019 и знакомство с
  интерфейсом Unity
---

# 🎯 Занятие 1: установка и знакомство с интерфейсом

## Скачивание Unity Hub

Переходим на сайт [Unity](https://unity.com/ru) и нажимаем кнопку <mark style="color:green;">Начать</mark>

![](<.gitbook/assets/image (33) (1).png>)

После перехода на выбор тарифа открываем вкладку <mark style="color:green;">Физическое Лицо</mark> и выбираем вариант <mark style="color:green;">Personal</mark>

![](<.gitbook/assets/image (19).png>)

Далее нам предложит скачать Unity Hub Beta, вместо это отправляемся чуть ниже и качаем стабильную версию для Windows

![](<.gitbook/assets/image (27) (1).png>)

После этого устанавливаем и запускаем Unity Hub

## Настройка Unity Hub

Высветится уведомление что нам нужно активировать лицензию:

![](<.gitbook/assets/image (8).png>)

Для начала нужно зайти в свой аккаунт Unity (или зарегистрироваться)

![](<.gitbook/assets/image (10).png>)

Выбирайте нужный вам пункт, после чего произойдет переход в браузер для ввода данных для входа. После входа вас перебросит обратно в Unity Hub, где будет указан ваш аккаунт

Далее нажимаем кнопку <mark style="color:green;">Manage Licenses</mark> и видим список активных лицензий _(верно, он пуст)_

![](<.gitbook/assets/image (29).png>)

Тыкаем на <mark style="color:green;">Add license</mark> и выбираем <mark style="color:green;">Personal License</mark>

![](<.gitbook/assets/image (14).png>)

Соглашаемся со всеми лицензионными соглашениями и персональная лицензия появляется у нас в списке

## Установка Unity и Visual Stidio

Unity Hub - лишь программа для установки редактора Unity и управления проектами.\
Теперь перейдем к установке нужной версии Unity

{% hint style="info" %}
Мы будем использовать LTS версию _(долгосрочная поддержка)_ 2019 года
{% endhint %}

Открываем вкладку <mark style="color:green;">Installs</mark> - тут будут располагаться все установленные версии Unity\
Затем нажимаем кнопку <mark style="color:green;">Install Editor</mark> для добавления новой версии Unity

![](<.gitbook/assets/image (25).png>)

После этого жмем <mark style="color:green;">Install</mark> напротив нужной нам версии - <mark style="color:green;">2019 LTS</mark>

![](<.gitbook/assets/image (7).png>)

Выбираем поддержку разработки под <mark style="color:green;">Android</mark>, и не забудем установить <mark style="color:green;">Visual Studio</mark>, если все еще этого не сделали. После этого жмем привычное <mark style="color:green;">Continue</mark>, одновременно соглашаясь со всеми ~~<mark style="color:red;">кругами ада</mark>~~ юридическими нюансами :sunglasses:

![](<.gitbook/assets/image (39).png>)

{% hint style="info" %}
Скачивание и установка Unity обычно занимает менее **30 минут**
{% endhint %}

## Создание своего первого проекта

Во вкладке <mark style="color:green;">Projects</mark> собраны все все проекты которые вы создали либо же открыли\
Для создания нового проект нажмите кнопку <mark style="color:green;">Net Project</mark>

![](<.gitbook/assets/image (28).png>)

Нам предложат выбрать шаблон - пустой 3D проект идеально подойдет.\
Также нам нужно указать название проекта и путь, куда он будет сохранен.

![](<.gitbook/assets/image (21).png>)

{% hint style="info" %}
Лучше сохранять проект на SSD, чтобы в последующем он открывался максимально быстро
{% endhint %}

Нажимаем кнопку <mark style="color:green;">Create Project</mark> и ждем создания проект. Он автоматически откроется в редакторе

## Настройка редактора

![](<.gitbook/assets/image (40).png>)

Наконец мы добрались до самого интересного - редактора Unity :tada: именно тут будет протекать 90% нашей работы

### Рабочая среда по умолчанию

Если панели расположены не так как на скрине (_или вы случайно все сломали_), то неплохо будет выбрать в верхнем меню <mark style="color:green;">Window</mark> -> <mark style="color:green;">Layout</mark> (_комбинацию окон_) -> <mark style="color:green;">Default</mark> (_по умолчанию_)

![](<.gitbook/assets/image (42).png>)

### Изменение темы редактора

Если же у вас не устраивает светлая тема или наоборот хочется ее поставить :grimacing: то перейдите в верхнее меню <mark style="color:green;">Edit -> Preferences -> Editor Theme -> Light/Dark</mark>

![](<.gitbook/assets/image (1).png>)

### Связь Unity c Visual Studio

Для этого перейдем в верхнее меню <mark style="color:green;">Edit -> Preferences -> External Tools</mark>\
В открывшемся окне выберем в качестве <mark style="color:green;">External Script Editor</mark> (_редактора кода_) <mark style="color:green;">Visual Studio 2019</mark> и нажмем кнопку <mark style="color:green;">Regenerate Project Files</mark> - это позволит редактору не только открывать отдельные скрипты в Visual Studio, но и воспринимать их как единый проект, а также отображать подсказки по коду (_Intellisense_).

![](<.gitbook/assets/image (37).png>)
