---
## Front matter
title: "Лабораторная работа №3"
subtitle: "Дискреционное разграничение прав в Linux. Два пользователя"
author: "Салькова Кристина Михайловна"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Получение практических навыков работы в консоли с атрибутами файлов для групп пользователей


# Теоретическое введение

Более подробно про Unix см. в [@tanenbaum_book_modern-os_ru; @robbins_book_bash_en; @zarrelli_book_mastering-bash_en; @newham_book_learning-bash_en]. 

# Выполнение лабораторной работы

1. Создаём учётную запись для пользователя guest2 (рис. [-@fig:001]).

![Создание учётной записи guest2](image/1.png){#fig:001 width=70%}

2. Добавляем пользователя guest2 в группу guest (рис. [-@fig:002]).

![Добавление guest2 в группу guest2](image/2.png){#fig:002 width=70%}

3. Определяем директории для обоих пользователей с помощью команды pwd, также уточняем имя пользователя, его группу, кто в неё входит и к каким группам принадлежит (рис. [-@fig:003]), (рис. [-@fig:004]).

![pwd/ guest](image/3.png){#fig:003 width=70%}

![pwd/ guest2](image/4.png){#fig:004 width=70%}

4. Сравним выводы команды groups с командами id -Gn и id -G (рис. [-@fig:005]), (рис. [-@fig:006]).

![id/ guest](image/5.png){#fig:005 width=70%}

![id/ guest2](image/6.png){#fig:006 width=70%}

5. Просмотрим файл /etc/group для обоих пользователей с помощью cat /etc/group и сравним данные uid, gid с результатами команд выше и выясним, что данные значения совпадают (рис. [-@fig:007]), (рис. [-@fig:008]).

![cat /ect/group - guest](image/7.png){#fig:007 width=70%}

![cat /ect/group - guest2](image/8.png){#fig:008 width=70%}

6. От имени пользователя guest2 выполняем регистрацию пользователя guest2 в группе guest командой newgrp guest (рис. [-@fig:009]).

![регистрация guest2 в группе guest](image/9.png){#fig:009 width=70%}

7. От имени пользователя guest изменим права директории /home/guest, разрешив все действия для пользователей группы (рис. [-@fig:010]).

![изменение прав директории](image/10.png){#fig:010 width=70%}

8. От имени пользователя guest снимите с директории /home/guest/dir1 все атрибуты (рис. [-@fig:011]).

![снятие всех атрибутов](image/11.png){#fig:011 width=70%}

9. Заполняем таблицу 3.1 "Установленные права и разрешенные действия" (рис. [-@fig:012]), (рис. [-@fig:013]), (рис. [-@fig:014]), (рис. [-@fig:015]), (рис. [-@fig:016]), (рис. [-@fig:017]).

![Таблица "УПиРД" ч.1](image/12.png){#fig:012 width=70%}

![Таблица "УПиРД" ч.2](image/13.png){#fig:013 width=70%}

![Таблица "УПиРД" ч.3](image/14.png){#fig:014 width=70%}

![Таблица "УПиРД" ч.4](image/15.png){#fig:015 width=70%}

![Таблица "УПиРД" ч.5](image/16.png){#fig:016 width=70%}

![Таблица "УПиРД" ч.6](image/17.png){#fig:017 width=70%}

10. Заполняем таблицу 3.2 "Минимальные права для совершения операций от имени пользователей входящих в группу" (рис. [-@fig:018])

![Таблица "МПДСО"](image/18.png){#fig:018 width=70%}

# Выводы

Получили практические навыки работы в консоли с атрибутами файлов для групп пользователей

# Список литературы{.unnumbered}

Более подробно про Unix см. в [@tanenbaum_book_modern-os_ru; @robbins_book_bash_en; @zarrelli_book_mastering-bash_en; @newham_book_learning-bash_en].

::: {#refs}
:::
