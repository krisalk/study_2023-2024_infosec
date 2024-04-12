---
## Front matter
title: "Лабораторная работа №5"
subtitle: "Дискреционное разграничение прав в Linux. Исследование влияния дополнительных атрибутов"
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

Изучение механизмов изменения идентификаторов, применения
SetUID- и Sticky-битов. Получение практических навыков работы в консоли с дополнительными атрибутами. Рассмотрение работы механизма смены идентификатора процессов пользователей, а также влияние бита
Sticky на запись и удаление файлов.

# Теоретическое введение

Более подробно про Unix см. в [@tanenbaum_book_modern-os_ru; @robbins_book_bash_en; @zarrelli_book_mastering-bash_en; @newham_book_learning-bash_en]. 

# Выполнение лабораторной работы

1. От имени пользователя guest определите расширенные атрибуты файла /home/guest/dir1/file1 командой lsattr /home/guest/dir1/file1(рис. [-@fig:001]).

![lsattr](image/1.png){#fig:001 width=70%}

2. Установите командой
chmod 600 file1
на файл file1 права, разрешающие чтение и запись для владельца файла.(рис. [-@fig:002]).

![сhmod 600](image/2.png){#fig:002 width=70%}

3. Попробуем установить на файл /home/guest/dir1/file1 расширенный атрибут a от имени пользователя guest:
chattr +a /home/guest/dir1/file1
В ответ получаем отказ от выполнения операции.(рис. [-@fig:003])

![chattr +a /home/guest/dir1/file1 отказ](image/3.png){#fig:003 width=70%}

4. Повысим свои права с помощью команды su. Попробуем установить расширенный атрибут a на файл /home/guest/dir1/file1 от имени суперпользователя (рис. [-@fig:004])

![/home/guest/dir1/file1 от имени суперпользователя](image/5.png){#fig:004 width=70%}

5. От пользователя guest проверим правильность установления атрибута:
lsattr /home/guest/dir1/file1 (рис. [-@fig:005])

![lsattr /home/guest/dir1/file1 ](image/5.png){#fig:005 width=70%}

6. Выполним дозапись в файл file1 слова «test» командой
echo "test" /home/guest/dir1/file1
После этого выполним чтение файла file1 командой
cat /home/guest/dir1/file1
Убедимся, что слово test было успешно записано в file1. (рис. [-@fig:006]).

![test](image/6.png){#fig:006 width=70%}

7. Попробуем удалить файл file1 либо стереть имеющуюся в нём информацию командой. Попробуем переименовать файл
echo "abcd" > /home/guest/dirl/file1 (рис. [-@fig:007]).

![изменение прав директории](image/7.png){#fig:007 width=70%}

8. Попробуем с помощью команды chmod 000 file1 установить на файл file1 права, например, запрещающие чтение и запись для владельца файла. "Удалось ли вам успешно выполнить указанные команды?" Нет (рис. [-@fig:008]).

![chmod 000 file1](image/8.png){#fig:008 width=70%}

9. Снимим расширенный атрибут a с файла /home/guest/dirl/file1 от имени суперпользователя командой
chattr -a /home/guest/dir1/file1 (рис. [-@fig:009])

![снятие атрибута](image/9.png){#fig:009 width=70%}

10. Повторим операции, которые нам ранее не удавалось выполнить. (рис. [-@fig:010])

![повторение](image/10.png){#fig:010 width=70%}

# Выводы

Мы изучили механизмы изменения идентификаторов, примененили
SetUID- и Sticky-биты. Получили практические навыки работы в консоли с дополнительными атрибутами. Рассмотрели работы механизма смены идентификатора процессов пользователей, а также влияние бита
Sticky на запись и удаление файлов.

# Список литературы{.unnumbered}

Более подробно про Unix см. в [@tanenbaum_book_modern-os_ru; @robbins_book_bash_en; @zarrelli_book_mastering-bash_en; @newham_book_learning-bash_en].

::: {#refs}
:::
