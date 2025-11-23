---
## Front matter
title: "Отчёт по лабораторной работе №6"
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

Изучить основные принципы работы с библиографическими системами **natbib** и **biblatex** в LaTeX. Освоить полный цикл генерации библиографии с помощью BibTeX и Biber, научиться добавлять новые источники в базу данных, создавать корректные и некорректные (отсутствующие) ссылки, а также сравнить вывод различных стилей цитирования, включая числовой формат.

# Ход выполнения

## Тестирование библиографии с использованием `natbib`

### Подготовка файлов и первая компиляция

Открыты исходные файлы `biblio1.tex` и `references.bib`, после чего выполнена первая компиляция с помощью:

```
pdflatex biblio1.tex
```

На этом этапе появляются предупреждения `natbib` об отсутствующих цитатах, так как файл `.aux` ещё не создан и BibTeX не запускался.

![Первая компиляция natbib](1.png){ #fig:001 width=70% }

Далее выполнен запуск BibTeX:

```
bibtex biblio1
```

![Запуск BibTeX](2.png){ #fig:002 width=70% }

После обработки библиографии выполнена последовательность двух повторных компиляций `pdflatex`:

```
pdflatex biblio1.tex
pdflatex biblio1.tex
```

![Повторная компиляция для обновления ссылок](3.png){ #fig:003 width=70% }

### Результат компиляции `natbib`

Полученный PDF-файл корректно отображает:

* числовые ссылки `[1]`, `[2]`,
* раздел *References*,
* форматирование, характерное для `natbib`.

![Результат natbib](4.png){ #fig:004 width=70% }

### Тестирование примера `natbib_example.tex`

Файл `natbib_example.tex` скомпилирован аналогичным циклом, начав с:

```
pdflatex natbib_example.tex
```

![Компиляция natbib\_example.tex](5.png){ #fig:005 width=70% }

После выполнения полного цикла команд появились корректные числовые и авторо-дата ссылки.

## Тестирование библиографии с использованием `biblatex`

### Первоначальная компиляция

Открыт файл `biblatex_example.tex`, затем выполнен запуск:

```
pdflatex biblatex_example.tex
```

![Первая компиляция biblatex](6.png){ #fig:006 width=70% }

### Обработка библиографии через Biber

Для `biblatex` используется Biber вместо BibTeX:

```
biber biblatex_example
```

![Запуск Biber](7.png){ #fig:007 width=70% }

После этого выполняются две повторные компиляции:

```
pdflatex biblatex_example.tex
pdflatex biblatex_example.tex
```

![Повторная компиляция biblatex](8.png){ #fig:008 width=70% }

### Результат работы `biblatex`

Формат выводимых ссылок и библиографии отличается от `natbib` — используется стиль по умолчанию (`authoryear`).

![PDF результат biblatex](9.png){ #fig:009 width=70% }

## Эксперименты со стилями и отсутствующими записями

### Тест — вариант со стилем `numeric` (`biblatex_numeric.tex`)

Файл скомпилирован последовательно:

```
pdflatex biblatex_numeric.tex
biber biblatex_numeric
pdflatex biblatex_numeric.tex
pdflatex biblatex_numeric.tex
```

![Компиляция numeric](10.png){ #fig:010 width=70% }
![Материал из PDF numeric](11.png){ #fig:011 width=70% }

Результат — ссылки отображаются в виде:

```
[2] и [1]
```

![Числовой стиль biblatex](12.png){ #fig:012 width=70% }

![Числовой стиль biblatex](13.png){ #fig:013 width=70% }

## Проверка отсутствующих цитат

Добавлена цитата, которой нет в `references.bib`.

Результат — `?`, `??` или строки с вопросительными знаками вместо корректного года/автора:

![Отсутствующие цитаты](14.png){ #fig:014 width=70% }

Это ожидаемое поведение обоих пакетов (`natbib` и `biblatex`).

## Сравнение поведения разных пакетов

### `natbib`:

* использует BibTeX;
* цикл компиляции: **LaTeX → BibTeX → LaTeX → LaTeX**;
* стиль `numeric` подключается через `\usepackage[numbers]{natbib}`;
* при отсутствии записи выдаёт предупреждения и отображает `?`.

### `biblatex`:

* использует Biber;
* цикл компиляции: **LaTeX → Biber → LaTeX → LaTeX**;
* стиль задаётся параметром: `\usepackage[style=numeric]{biblatex}`;
* гибкая настройка формата вывода;
* отсутствующие записи также выводятся как `?`.

# Вывод

В ходе выполнения работы были исследованы механизмы формирования библиографии в LaTeX с использованием пакетов **natbib** и **biblatex**. Были выполнены последовательные циклы компиляции для обоих инструментов, изучен процесс работы BibTeX и Biber, протестировано добавление новых записей в файл `.bib`, а также проверено поведение системы при ссылках на отсутствующие элементы.

В результате работы были освоены следующие аспекты:

* проведение полного цикла компиляции для `natbib` (LaTeX → BibTeX → LaTeX → LaTeX);
* проведение полного цикла компиляции для `biblatex` (LaTeX → Biber → LaTeX → LaTeX);
* добавление новых источников в файл библиографии и корректное использование ключей цитирования;
* анализ отображения некорректных или отсутствующих ссылок;
* сравнение форматов вывода ссылок в `natbib` и `biblatex`, включая стиль `numeric`.

Полученные результаты подтверждают различия в подходах двух систем и демонстрируют преимущества `biblatex` в гибкости оформления, а также типичный рабочий процесс при использовании обоих пакетов.
