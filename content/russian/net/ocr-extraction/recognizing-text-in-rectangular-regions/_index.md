---
title: Распознавание текста в прямоугольных областях
linktitle: Распознавание текста в прямоугольных областях
second_title: GroupDocs.Parser .NET API
description: Узнайте, как распознавать текст в определенных областях документов с помощью GroupDocs.Parser для .NET с возможностями OCR.
weight: 14
url: /ru/net/ocr-extraction/recognizing-text-in-rectangular-regions/
type: docs
---
# Распознавание текста в прямоугольных областях

## Введение
В этом руководстве мы рассмотрим, как использовать GroupDocs.Parser для .NET для распознавания текста в определенных прямоугольных областях документов. GroupDocs.Parser — это мощная библиотека, которая позволяет разработчикам извлекать текст, метаданные и многое другое из файлов различных форматов, включая PDF, Word, Excel и PowerPoint.
## Предварительные условия
Прежде чем мы начнем, убедитесь, что у вас установлены следующие настройки:
-  GroupDocs.Parser для .NET: загрузите и установите библиотеку с сайта[здесь](https://releases.groupdocs.com/parser/net/).
- Среда разработки: Visual Studio или любая другая .NET IDE.
- Образец документа. Имейте образец файла (например, PDF, DOCX), содержащий текст, который необходимо распознать.

## Импортировать пространства имен
Сначала вам нужно импортировать необходимые пространства имен в ваш код C#:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using System.Linq;
using System.Text;
using Aspose.OCR;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Шаг 1. Инициализируйте настройки парсера
 Начните с настройки`ParserSettings` с разъемом OCR. Здесь мы будем использовать локальный коннектор Aspose OCR:
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## Шаг 2. Создайте экземпляр парсера
 Далее создайте экземпляр`Parser` класс с ранее определенными настройками:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // Код продолжается здесь
}
```
 Заменять`"YourSampleFile.pdf"` с путем к вашему документу.
## Шаг 3. Определите прямоугольник OCR
 Определите прямоугольник внутри документа, где будет выполняться распознавание текста. Например, прямоугольник, начинающийся с`(0, 0)` с шириной`400` и высота`200`:
```csharp
OcrOptions ocrOptions = new OcrOptions(new Data.Rectangle(0, 0, 400, 200));
```
## Шаг 4. Настройте параметры распознавания текста
 Создавать`TextOptions` чтобы указать использование OCR вместе с определенным прямоугольником:
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## Шаг 5. Извлеките текст с помощью OCR
 Использовать`GetText` метод`Parser` экземпляр с настроенным`TextOptions`:
```csharp
using (TextReader reader = parser.GetText(options))
{
    // Прочитайте извлеченный текст или обработайте случай «не поддерживается»
    Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
}
```

## Заключение
В этом руководстве мы продемонстрировали, как использовать GroupDocs.Parser для .NET для извлечения текста из определенных прямоугольных областей документов с помощью OCR. Этот процесс можно дополнительно настроить и интегрировать в различные приложения для задач автоматического извлечения текста.

## Часто задаваемые вопросы
### Может ли GroupDocs.Parser извлекать текст из отсканированных документов?
Да, GroupDocs.Parser поддерживает OCR (оптическое распознавание символов) для извлечения текста из отсканированных документов.
### Какие форматы файлов поддерживает GroupDocs.Parser?
GroupDocs.Parser поддерживает широкий спектр форматов файлов, включая PDF, DOCX, XLSX, PPTX и другие.
### Как я могу обрабатывать документы, из которых не поддерживается извлечение текста?
 Вы можете проверить, поддерживается ли извлечение текста, используя`TextReader` экземпляр, возвращенный`parser.GetText(options)`.
### Подходит ли GroupDocs.Parser для крупномасштабных задач извлечения текста?
Да, GroupDocs.Parser предназначен для эффективного решения крупномасштабных задач по извлечению текста.
### Где я могу получить поддержку по вопросам, связанным с GroupDocs.Parser?
 Для поддержки и обсуждения посетите[Форум GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).