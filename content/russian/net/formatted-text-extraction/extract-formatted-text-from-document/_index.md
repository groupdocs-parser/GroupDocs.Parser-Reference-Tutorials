---
title: Извлечь форматированный текст из документа
linktitle: Извлечь форматированный текст из документа
second_title: GroupDocs.Parser .NET API
description: Узнайте, как извлечь форматированный текст из документов с помощью GroupDocs.Parser для .NET. Простое и эффективное извлечение текста для ваших приложений.
weight: 10
url: /ru/net/formatted-text-extraction/extract-formatted-text-from-document/
---

# Извлечь форматированный текст из документа

## Введение
В этом руководстве мы рассмотрим, как использовать GroupDocs.Parser для .NET для извлечения форматированного текста из различных типов документов. GroupDocs.Parser — мощная библиотека, позволяющая разработчикам работать с документами упрощенно и эффективно. К концу этого руководства вы сможете легко интегрировать возможности извлечения текста в свои .NET-приложения.
## Предварительные условия
Прежде чем мы начнем, убедитесь, что у вас есть следующее:
- Visual Studio: убедитесь, что в вашей системе установлена Visual Studio.
-  GroupDocs.Parser для .NET: загрузите и установите библиотеку GroupDocs.Parser с сайта[здесь](https://releases.groupdocs.com/parser/net/).
- Образцы документов: подготовьте образцы документов (например, PDF, DOCX) для извлечения текста.
## Импортировать пространства имен
Сначала включите необходимые пространства имен в свой код C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Шаг 1. Создайте экземпляр класса парсера
 Начните с инициализации`Parser` объект с путем к вашему образцу документа.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Здесь находится код извлечения текста
}
```
 Заменять`"YourSampleFile.pdf"` с путем к файлу вашего документа.

## Шаг 2. Извлечение форматированного текста
 В рамках`using` блок, используйте`GetFormattedText` метод извлечения форматированного текста из документа. Укажите желаемый формат вывода (например, HTML), используя`FormattedTextOptions`.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Извлечение форматированного текста в программу чтения
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Проверьте, поддерживается ли извлечение
        if (reader == null)
        {
            Console.WriteLine("Formatted text extraction isn't supported.");
        }
        else
        {
            // Прочитайте и отобразите извлеченный текст
            Console.WriteLine(reader.ReadToEnd());
        }
    }
}
```

## Заключение
Поздравляем! Вы узнали, как извлекать форматированный текст из документов с помощью GroupDocs.Parser для .NET. Эта универсальная библиотека открывает возможности для обработки и анализа текста в ваших приложениях.

## Часто задаваемые вопросы
### Вопрос: Может ли GroupDocs.Parser извлекать текст из документов, защищенных паролем?
О: Да, GroupDocs.Parser поддерживает извлечение текста из документов, защищенных паролем.
### Вопрос: Какие форматы документов поддерживаются GroupDocs.Parser?
О: GroupDocs.Parser поддерживает широкий спектр форматов, включая PDF, DOCX, XLSX, PPTX и другие.
### Вопрос: Как получить временную лицензию на GroupDocs.Parser?
 О: Вы можете получить временную лицензию на[здесь](https://purchase.groupdocs.com/temporary-license/).
### Вопрос: Предоставляет ли GroupDocs.Parser поддержку извлечения изображений из документов?
О: Да, GroupDocs.Parser поддерживает извлечение изображений наряду с извлечением текста.
### Вопрос: Где я могу найти дополнительную поддержку или задать вопросы о GroupDocs.Parser?
 А: Посетите[Форум GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17)за поддержку и обсуждения.