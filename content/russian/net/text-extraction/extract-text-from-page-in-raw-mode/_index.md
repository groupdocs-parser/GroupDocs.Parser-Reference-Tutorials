---
title: Извлечь текст со страницы в режиме Raw
linktitle: Извлечь текст со страницы в режиме Raw
second_title: GroupDocs.Parser .NET API
description: Изучите эффективное извлечение текста из страниц документов с помощью Groupdocs.Parser для .NET в этом подробном руководстве.
type: docs
weight: 17
url: /ru/net/text-extraction/extract-text-from-page-in-raw-mode/
---
## Введение
В этом руководстве вы узнаете, как использовать Groupdocs.Parser для .NET для извлечения текста со страниц документа в необработанном режиме. Эта библиотека предоставляет эффективные инструменты для анализа и извлечения содержимого из файлов различных форматов, что позволяет разработчикам включать извлечение текста документов в свои .NET-приложения.
## Предварительные условия
Прежде чем начать, убедитесь, что у вас есть следующие предварительные условия:
- Базовые знания программирования на C# и .NET.
- Visual Studio установлена на вашем компьютере
- Доступ к библиотеке Groupdocs.Parser for .NET.
- Образец файла документа для тестирования

## Импортировать пространства имен
Начните с включения необходимых пространств имен в проект C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Шаг 1: Инициализируйте парсер
 Сначала создайте экземпляр`Parser` class, указав путь к файлу образца документа.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Ваш код здесь
}
```
## Шаг 2. Получите информацию о документе
 Получить информацию о документе с помощью`GetDocumentInfo()` метод.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## Шаг 3. Перебор страниц и извлечение текста
Перебирайте каждую страницу документа и извлекайте текстовое содержимое.
```csharp
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Извлечь текст со страницы
    using (TextReader reader = parser.GetText(p, new TextOptions(true)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Заключение
Теперь вы узнали, как использовать Groupdocs.Parser для .NET для извлечения текста со страниц документа в необработанном режиме. Это может быть мощной функцией для приложений, которым необходимо анализировать или обрабатывать текстовое содержимое файлов различных форматов.

## Часто задаваемые вопросы
### Совместим ли Groupdocs.Parser для .NET со всеми форматами файлов?
Groupdocs.Parser поддерживает широкий спектр форматов файлов, включая PDF, DOCX, XLSX, PPTX, EPUB и другие.
### Могу ли я извлечь метаданные вместе с текстом, используя эту библиотеку?
Да, Groupdocs.Parser позволяет извлекать из документов как текст, так и метаданные.
### Доступна ли пробная версия для тестирования?
 Да, вы можете скачать бесплатную пробную версию с сайта[здесь](https://releases.groupdocs.com/).
### Как я могу получить техническую поддержку для Groupdocs.Parser?
 Для получения технической помощи посетите[Форум Groupdocs.Parser](https://forum.groupdocs.com/c/parser/17).
### Где я могу приобрести лицензию на Groupdocs.Parser для .NET?
 Вы можете приобрести лицензию[здесь](https://purchase.groupdocs.com/buy).