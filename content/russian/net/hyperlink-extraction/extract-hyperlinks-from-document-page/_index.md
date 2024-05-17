---
title: Извлечь гиперссылки со страницы документа
linktitle: Извлечь гиперссылки со страницы документа
second_title: GroupDocs.Parser .NET API
description: Узнайте, как извлекать гиперссылки из документов с помощью GroupDocs.Parser для .NET. Пошаговое руководство по извлечению гиперссылок в C#.
type: docs
weight: 11
url: /ru/net/hyperlink-extraction/extract-hyperlinks-from-document-page/
---
## Введение
В этом руководстве мы рассмотрим, как шаг за шагом использовать GroupDocs.Parser для .NET для извлечения гиперссылок из документов. GroupDocs.Parser — это мощная библиотека, которая позволяет разработчикам анализировать различные форматы документов и извлекать текст, метаданные и другие элементы.
## Предварительные условия
Прежде чем мы начнем, убедитесь, что у вас есть следующее:
- Visual Studio: установите Visual Studio на свой компьютер для разработки.
-  Библиотека GroupDocs.Parser: загрузите и используйте библиотеку GroupDocs.Parser. Вы можете получить его от[здесь](https://releases.groupdocs.com/parser/net/).
- Образец документа: подготовьте образец документа (например, DOCX, PDF), содержащий гиперссылки для тестирования.

## Импортировать пространства имен
Сначала включите необходимые пространства имен для использования функций GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Шаг 1. Создайте экземпляр парсера
 Создайте экземпляр`Parser` class с путем к вашему образцу документа.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Код идет сюда...
}
```
## Шаг 2. Проверьте поддержку извлечения гиперссылок
Прежде чем продолжить, убедитесь, что документ поддерживает извлечение гиперссылок.
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
## Шаг 3. Получите информацию о документе
Получите основную информацию о документе и проверьте, есть ли в нем страницы.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Шаг 4. Перебор страниц документа
Пройдитесь по каждой странице документа.
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Извлечь гиперссылки с текущей страницы
    IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks(pageIndex);
    // Перебирать извлеченные гиперссылки
    foreach (PageHyperlinkArea hyperlink in hyperlinks)
    {
        Console.WriteLine($"Hyperlink Text: {hyperlink.Text}");
        Console.WriteLine($"Hyperlink URL: {hyperlink.Url}");
        Console.WriteLine(); // Пустая строка для удобства чтения.
    }
}
```

## Заключение
В этом руководстве мы рассмотрели основы использования GroupDocs.Parser для .NET для извлечения гиперссылок из документов. Вы узнали, как инициализировать анализатор, проверять поддержку гиперссылок, получать информацию о документе и перебирать страницы документа для эффективного извлечения гиперссылок.

## Часто задаваемые вопросы
### Могу ли я извлечь гиперссылки из документов разных форматов?
Да, GroupDocs.Parser поддерживает различные форматы, такие как DOCX, PDF, PPTX и т. д., для извлечения гиперссылок.
### Легко ли интегрировать GroupDocs.Parser в существующие приложения .NET?
Конечно, GroupDocs.Parser спроектирован так, чтобы быть простым и может быть легко интегрирован в ваши проекты .NET.
### Могу ли я извлечь другие метаданные вместе с гиперссылками с помощью GroupDocs.Parser?
Да, помимо гиперссылок, с помощью этой библиотеки вы можете извлекать из документов текст, изображения и метаданные.
### Обрабатывает ли GroupDocs.Parser зашифрованные или защищенные паролем документы?
GroupDocs.Parser может анализировать документы, защищенные паролем, если указан пароль.
### Есть ли пробная версия, которую можно протестировать перед покупкой?
 Да, вы можете скачать бесплатную пробную версию[здесь](https://releases.groupdocs.com/).