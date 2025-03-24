---
title: Поиск текста с выделением
linktitle: Поиск текста с выделением
second_title: GroupDocs.Parser .NET API
description: Узнайте, как искать и выделять текст в документах с помощью GroupDocs.Parser для .NET. Эффективно извлекайте ценную информацию.
weight: 24
url: /ru/net/text-extraction/search-text-with-highlights/
---

# Поиск текста с выделением

## Введение
В этом руководстве мы рассмотрим, как использовать GroupDocs.Parser для .NET для поиска текста в документе и выделения результатов поиска. GroupDocs.Parser — мощная библиотека, позволяющая работать с различными форматами документов и извлекать текст, метаданные и многое другое.
## Предварительные условия
Прежде чем мы начнем, убедитесь, что у вас есть следующее:
1.  GroupDocs.Parser для .NET: загрузите и установите библиотеку с сайта[здесь](https://releases.groupdocs.com/parser/net/).
2. IDE: используйте Visual Studio или любую предпочтительную IDE для разработки .NET.
3. Образец файла: подготовьте образец документа (например, PDF, DOCX) для поиска по тексту.

## Импортировать пространства имен
Сначала начните с импорта необходимых пространств имен в ваш проект .NET:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Шаг 1. Создайте экземпляр парсера
 Начните с создания экземпляра`Parser` class с путем к файлу примера:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Ваш код здесь
}
```
## Шаг 2. Определите параметры выделения
 Укажите`HighlightOptions` чтобы настроить способ выделения результатов поиска. Например, установка контекстного окна из 15 символов:
```csharp
HighlightOptions highlightOptions = new HighlightOptions(15);
```
## Шаг 3: Поиск текста
Теперь выполните текстовый поиск внутри документа. Укажите ключевое слово, по которому вы хотите выполнить поиск (например, «лорем»):
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("lorem", new SearchOptions(true, false, false, highlightOptions));
```
## Шаг 4. Обработка результатов поиска
Перебрать результаты поиска и отобразить найденный текст вместе с выделенными фрагментами:
```csharp
if (searchResults != null)
{
    foreach (SearchResult result in searchResults)
    {
        Console.WriteLine($"{result.LeftHighlightItem.Text}{result.Text}{result.RightHighlightItem.Text}");
    }
}
else
{
    Console.WriteLine("Search isn't supported");
}
```

## Заключение
В этом руководстве вы узнали, как использовать GroupDocs.Parser для .NET для поиска текста в документах и выделения результатов поиска. Эта функциональность может быть чрезвычайно полезна для извлечения и анализа текста в ваших .NET-приложениях.

## Часто задаваемые вопросы
### Подходит ли GroupDocs.Parser для обработки документов различных форматов?
Да, GroupDocs.Parser поддерживает широкий спектр форматов документов, включая PDF, DOCX, XLSX, PPTX и другие.
### Могу ли я использовать GroupDocs.Parser для извлечения метаданных из документов?
Абсолютно! GroupDocs.Parser позволяет извлекать метаданные, текст и структурированные данные из документов.
### Где я могу найти поддержку или задать вопросы о GroupDocs.Parser?
 Вы можете посетить[Форум GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) по любым вопросам, связанным с поддержкой.
### Доступна ли бесплатная пробная версия GroupDocs.Parser?
 Да, вы можете получить доступ к[бесплатная пробная версия](https://releases.groupdocs.com/) GroupDocs.Parser, чтобы оценить его возможности.
### Как я могу приобрести лицензию на GroupDocs.Parser?
 Вы можете приобрести лицензию у[здесь](https://purchase.groupdocs.com/buy) а также получить временные лицензии[здесь](https://purchase.groupdocs.com/temporary-license/).