---
## Front matter
title: "Отчёт по лабораторной работе №3"
subtitle: "Computer Skills for Scientific Writing"
author: "Мунтаха Сидратул"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true
toc-depth: 2
lof: true
lot: true
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
mainfont: IBM Plex Serif
romanfont: IBM Plex Serif
sansfont: IBM Plex Sans
monofont: IBM Plex Mono
mathfont: STIX Two Math
mainfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
romanfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
sansfontoptions: Ligatures=Common,Ligatures=TeX,Scale=MatchLowercase,Scale=0.94
monofontoptions: Scale=MatchLowercase,Scale=0.94,FakeStretch=0.9
mathfontoptions:
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
  - \usepackage{float}
  - \floatplacement{figure}{H}
---

# Цель работы

Изучение возможностей математического режима LaTeX, включая встроенные и отображаемые формулы, использование пакета `amsmath`, управление выравниванием и нумерацией уравнений, а также применение различных математических шрифтов и обозначений.


# Ход выполнения

## Компиляция и проверка задания *Exercise 3.8*

На первом этапе был открыт исходный файл `exercise_3_8.tex` с помощью текстового редактора и выполнена его компиляция командой `pdflatex`.

В процессе компиляции использовался дистрибутив **TeX Live 2025** и стандартный класс документа `article` с подключённым пакетом `amsmath`. В выводе компилятора отображается загрузка дополнительных пакетов для работы с математикой и шрифтами, включая `amssymb`, `amsfonts` и `bm`.

Результат выполнения команды `pdflatex exercise_3_8.tex` показан на скриншоте:

![Компиляция exercise_3_8.tex](01.png){ #fig:001 width=70% }

Во время компиляции было выведено предупреждение о недостающем символе в шрифте (`Missing character: There is no b in font msbm10`), однако оно не повлияло на успешное создание PDF-документа.

## Анализ сгенерированного документа *Exercise 3.8*

Сформированный PDF-файл содержит несколько тематических разделов, демонстрирующих расширенные возможности математического режима LaTeX.

![Результат Exercise 3.8](04.png){ #fig:002 width=70% }

В документе представлены следующие элементы:

- переход от встроенного математического режима к display-формулам на примере интеграла;
- вывод строчных и заглавных греческих букв;
- сравнение различных математических шрифтов (`\mathrm`, `\mathbf`, `\mathit`, `\mathsf`, `\mathtt`);
- проверка вложенности шрифтовых команд;
- демонстрация жирного математического начертания с использованием `\mathbf` и `\bm`.

## Компиляция варианта с опциями `fleqn` и `leqno`

Далее был открыт файл `exercise_3_8_options.tex`, в котором используются дополнительные опции класса документа:

- `fleqn` — выравнивание формул по левому краю;
- `leqno` — размещение номеров формул слева.

Выполнена компиляция файла командой `pdflatex exercise_3_8_options.tex`.

![Компиляция exercise_3_8_options.tex](03.png){ #fig:003 width=70% }

Вывод компилятора подтверждает загрузку соответствующих файлов конфигурации (`fleqn.clo`, `leqno.clo`) и корректную сборку документа.

## Результат работы с `fleqn` и `leqno`

В итоговом PDF-файле наглядно показано влияние указанных опций:

![Результат с fleqn и leqno](05.png){ #fig:004 width=70% }

В документе:

- формулы выровнены по левому краю страницы;
- номера уравнений располагаются слева от формул;
- показаны как одиночные уравнения, так и система уравнений с последовательной нумерацией.

## Выполнение заданий *Section 3.6* (amsmath)

Следующим этапом были открыты и скомпилированы файлы `exercise_3_6_simple.tex` и `exercise_3_7_simple.tex`.

Компиляция выполнена стандартной командой `pdflatex`, о чём свидетельствует вывод терминала:

![Компиляция exercise_3_6_simple.tex и exercise_3_7_simple.tex](06.png){ #fig:005 width=70% }

## Анализ результата *Section 3.6*

Сгенерированный документ демонстрирует расширенные возможности пакета **amsmath**.

![Результат Section 3.6](07.png){ #fig:006 width=70% }

В документе представлены:

- стандартные матричные окружения `pmatrix` и `bmatrix`;
- выравнивание уравнений с помощью окружения `align` с нумерацией и без неё;
- многострочные формулы с использованием `gather`;
- стрелочные обозначения с текстом над и под стрелкой.

## Выполнение заданий *Section 3.7*

На заключительном этапе был открыт и просмотрен результат компиляции файла `exercise_3_7_simple.tex`, посвящённого более сложным математическим конструкциям.

![Результат Section 3.7](09.png){ #fig:007 width=70% }

Документ содержит:

- определённые интегралы и суммы с пределами;
- логические квантификаторы;
- сравнение различных математических алфавитов и начертаний;
- пример физических уравнений (уравнения Максвелла) с корректной нумерацией.

# Вывод

В ходе выполнения задания были успешно изучены и протестированы:

- inline и display математический режим LaTeX;
- возможности пакета **amsmath** для выравнивания и многострочных формул;
- управление шрифтами и жирным начертанием в математике;
- влияние опций `fleqn` и `leqno` на форматирование формул.

Все файлы были корректно скомпилированы, а результаты соответствуют ожидаемому поведению математического набора LaTeX.
