---
## Front matter
lang: ru-RU
title: Лабораторная работа №6
subtitle: Работа с библиографией в LaTeX natbib и biblatex
author:
  - Мунтаха Сидратул
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 20 ноября 2025

## Formatting pdf
toc: false
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
---

# Цель работы

## Основная цель

Изучить работу систем библиографии **natbib** и **biblatex**,  
освоить полный цикл генерации ссылок через **BibTeX** и **Biber**,  
добавлять новые записи в `.bib` и анализировать корректность ссылок.

# Работа с natbib

## Первичная компиляция

Выполнена команда:

```
pdflatex biblio1.tex
```

![Первая компиляция natbib](1.png){ width=70% }

## Запуск BibTeX

```
bibtex biblio1
```

![Запуск BibTeX](2.png){ width=70% }

## Повторная компиляция

```
pdflatex biblio1.tex
pdflatex biblio1.tex
```

![Обновление ссылок](3.png){ width=70% }

## Результат natbib

Готовый PDF содержит:

- числовые ссылки (`[1]`, `[2]`);
- раздел *References*;
- корректные авторо-дата ссылки.

![Результат natbib](4.png){ width=70% }

# Пример natbib_example

## Первая компиляция

```
pdflatex natbib_example.tex
```

![Компиляция natbib_example](5.png){ width=70% }

# Работа с biblatex

## Первая компиляция

```
pdflatex biblatex_example.tex
```

![Первая компиляция biblatex](6.png){ width=70% }

## Запуск Biber

```
biber biblatex_example
```

![Запуск Biber](7.png){ width=70% }

## Обновление PDF

```
pdflatex biblatex_example.tex
pdflatex biblatex_example.tex
```

![Обновлённый PDF biblatex](8.png){ width=70% }

## Результат biblatex

Используется стиль *authoryear*, ссылки форматируются иначе, чем в natbib.

![Пример стиля biblatex](9.png){ width=70% }

# biblatex — стиль numeric

## Компиляция numeric-версии

```
pdflatex biblatex_numeric.tex
biber biblatex_numeric
pdflatex biblatex_numeric.tex
pdflatex biblatex_numeric.tex
```

![Компиляция numeric](10.png){ width=70% }
![Часть PDF numeric](11.png){ width=70% }

## Результат numeric

Формат:

```
[2] и [1]
```

![Стиль numeric](12.png){ width=70% }

## Ошибка ссылок

Добавлена ссылка, отсутствующая в базе данных.

![Некорректные ссылки](14.png){ width=70% }

# Сравнение систем

## natbib

- использует **BibTeX**  
- цикл: *LaTeX → BibTeX → LaTeX → LaTeX*  
- стиль numeric через: `\usepackage[numbers]{natbib}`
- отсутствующие ссылки → `?`

## biblatex

- использует **Biber**  
- цикл: *LaTeX → Biber → LaTeX → LaTeX*  
- стиль numeric через: `\usepackage[style=numeric]{biblatex}`
- более гибкая настройка форматов

# Выводы

## Итоги работы

В ходе лабораторной работы были освоены:

- компиляция документа с использованием **natbib** и **biblatex**;
- работа с **BibTeX** и **Biber**;
- добавление новых записей в `.bib`;
- анализ корректных и отсутствующих цитат;
- сравнение стилей выводов ссылок, включая `numeric`.
