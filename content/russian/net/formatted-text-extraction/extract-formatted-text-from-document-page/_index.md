---
title: Извлечь форматированный текст со страницы документа
linktitle: Извлечь форматированный текст со страницы документа
second_title: GroupDocs.Parser .NET API
description: Извлекайте форматированный текст со страниц документа с помощью GroupDocs.Parser для .NET. Эффективное и надежное решение для извлечения текста.
weight: 11
url: /ru/net/formatted-text-extraction/extract-formatted-text-from-document-page/
---
## Введение
В этом руководстве мы покажем вам процесс извлечения форматированного текста со страниц документа с помощью GroupDocs.Parser для .NET. Эта библиотека позволяет эффективно анализировать и извлекать текст из различных форматов документов, таких как PDF, Word, Excel и других.
## Предварительные условия
Прежде чем мы начнем, убедитесь, что у вас есть следующее:
- Visual Studio установлена в вашей системе.
- Базовые знания программирования на C#.
-  GroupDocs.Parser для библиотеки .NET. Вы можете скачать его[здесь](https://releases.groupdocs.com/parser/net/).

## Импортировать пространства имен
Сначала начните с импорта необходимых пространств имен в проект C#.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Шаг 1. Создайте экземпляр класса парсера
 Начните с создания экземпляра`Parser` class, указав путь к файлу примера.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Код будет здесь
}
```
## Шаг 2. Проверьте, поддерживается ли извлечение форматированного текста
Прежде чем приступить к извлечению текста, проверьте, поддерживает ли документ извлечение форматированного текста.
```csharp
if (!parser.Features.FormattedText)
{
    Console.WriteLine("Document does not support formatted text extraction.");
    return;
}
```
## Шаг 3. Получите информацию о документе
Получите информацию о документе, например количество страниц.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Шаг 4. Перебор страниц документа и извлечение форматированного текста
Перебирайте каждую страницу документа и извлекайте форматированный текст, используя заданные параметры (например, формат Markdown).
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    
    using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Markdown)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Заключение
Теперь вы знаете, как извлечь форматированный текст со страниц документа с помощью GroupDocs.Parser для .NET. Эта библиотека предоставляет мощное и простое в использовании решение для извлечения текста из файлов различных форматов.

## Часто задаваемые вопросы
### Может ли GroupDocs.Parser обрабатывать файлы разных форматов?
Да, GroupDocs.Parser поддерживает широкий спектр форматов документов, включая PDF, DOCX, XLSX, PPTX и другие.
### Совместим ли GroupDocs.Parser с .NET Core?
Да, GroupDocs.Parser поддерживает .NET Core и .NET Framework.
### Сохраняет ли GroupDocs.Parser форматирование текста во время извлечения?
Да, GroupDocs.Parser может сохранять форматирование, например стили и шрифты, при извлечении текста.
### Могу ли я извлечь изображения и метаданные с помощью GroupDocs.Parser?
Да, GroupDocs.Parser позволяет извлекать изображения, метаданные и текст из документов.
### Как я могу получить поддержку для GroupDocs.Parser?
 Вы можете получить поддержку от[Форум GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).