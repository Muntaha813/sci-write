---
lang: ru-RU
title: Лабораторная работа №7
subtitle: Презентации в LaTeX — класс beamer
author:
  - Мунтаха Сидратул
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 04 декабря 2025

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

Изучить приёмы создания презентаций в LaTeX с использованием класса **beamer**,  
включая:

- структуру слайдов;
- работу с блоками (`block`, `exampleblock`);
- пошаговое раскрытие элементов с `\pause`;
- точное управление отображением через `\uncover`;
- изменение тем и цветовых схем.

# Подготовка файлов

## Файлы примеров

В рабочей директории размещены файлы:

- `beamer_basic.tex`
- `beamer_blocks.tex`
- `beamer_pauses.tex`
- `beamer_uncover.tex`
- `beamer_layout.tex`

![Открытие файлов](1.png){ width=70% }

# Компиляция примеров

## beamer_basic.tex

Первая компиляция:

- отсутствует файл `.nav`;
- предупреждение `rerunfilecheck`.

Результат: **3-страничная презентация**.

![Компиляция basic](2.png){ width=70% }

## beamer_blocks.tex

Файл демонстрирует работу **блоков**.

![Компиляция blocks](3.png){ width=70% }

## beamer_blocks.tex

Результат:

- предупреждение о повторной компиляции,
- создан **1-страничный PDF**.

![Завершение blocks](4.png){ width=70% }

## beamer_pauses.tex

Пример с `\pause`:

![Компиляция pauses](5.png){ width=70% }

## beamer_pauses.tex

Результат: **5 страниц**, соответствующие числу появлений объектов.

![Завершение pauses](6.png){ width=70% }

## beamer_uncover.tex

Использование `\uncover<n->`:

![Компиляция uncover](7.png){ width=70% }

Результат: **4 шага раскрытия**.

## beamer_layout.tex

Пример изменения темы и цветовой схемы.

![Компиляция layout](8.png){ width=70% }

## beamer_layout.tex

И финальное открытие всех PDF:

![Открытые PDF](8_1.png){ width=70% }

# Просмотр слайдов

## Базовая презентация

![Титульный и первый слайды](9.png){ width=70% }

## Базовая презентация

![Слайд с текстом](10.png){ width=70% }

## Блоки

![Блоки](11.png){ width=70% }

## Pause — пошаговое раскрытие

![Pause1](12.png){ width=70% }

## Pause — пошаговое раскрытие

![Pause2](13.png){ width=70% }

## Pause — пошаговое раскрытие

![Pause3](14.png){ width=70% }

## Uncover — точное управление

![Uncover1](15.png){ width=70% }

## Uncover — точное управление

![Uncover2](16.png){ width=70% }

## Темы оформления

![Смена темы](17.png){ width=70% }

# Выводы

## Итоги работы

В ходе лабораторной работы были освоены:

- структура презентации beamer;
- работа с различными типами блоков;
- использование `\pause` и `\uncover` для анимации;
- применение тем (Warsaw, Copenhagen) и цветовых схем;
- анализ визуальных результатов и поведения механизмов beamer.

Работа подтвердила, что **beamer** предоставляет гибкие инструменты  
для создания научных и учебных презентаций в LaTeX.
