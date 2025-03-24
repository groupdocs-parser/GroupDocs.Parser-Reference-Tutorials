---
title: Извлечь текст со страницы в PDF в режиме Raw
linktitle: Извлечь текст со страницы в PDF в режиме Raw
second_title: GroupDocs.Parser .NET API
description: Извлекайте текст из PDF-файлов с помощью GroupDocs.Parser на C#. Научитесь эффективному извлечению текста из PDF-файлов с помощью этой мощной библиотеки .NET.
weight: 16
url: /ru/net/pdf-processing/extract-text-from-page-in-pdf-in-raw-mode/
---
## Введение
В этом руководстве мы рассмотрим, как использовать GroupDocs.Parser для .NET для извлечения текста со страниц PDF-документов в необработанном режиме. GroupDocs.Parser — мощный инструмент, позволяющий разработчикам программно работать с документами различных форматов.
## Предварительные условия
Прежде чем приступить к этому уроку, убедитесь, что у вас есть следующее:
- Visual Studio установлена на вашем компьютере.
- Базовые знания программирования на C#.
- GroupDocs.Parser для библиотеки .NET, которую вы можете[Скачать здесь](https://releases.groupdocs.com/parser/net/).
- Образец PDF-файла для тестирования.

## Импортировать пространства имен
Сначала обязательно импортируйте необходимые пространства имен в свой проект C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Шаг 1. Создайте экземпляр класса парсера
 Для начала создайте экземпляр`Parser`class, указав путь к образцу PDF-файла.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Ваш код находится здесь
}
```
## Шаг 2. Получите информацию о документе и перебирайте страницы
Затем извлеките информацию о документе и пройдитесь по каждой странице, чтобы извлечь текст.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Здесь находится ваш код для извлечения текста
}
```
## Шаг 3. Извлеките текст с каждой страницы
 Внутри цикла используйте`GetText` метод для извлечения текста с каждой страницы и его печати.
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## Заключение
 В этом уроке мы научились извлекать текст из страниц PDF в необработанном режиме с помощью GroupDocs.Parser для .NET. Этот процесс предполагает создание`Parser` экземпляр, получая информацию о документе, перебирая каждую страницу и извлекая текст с помощью`GetText` метод.

## Часто задаваемые вопросы
### Что такое GroupDocs.Parser для .NET?
GroupDocs.Parser для .NET — это API анализа документов, который позволяет разработчикам программно извлекать текст, метаданные и другую информацию из файлов различных форматов.
### Как загрузить GroupDocs.Parser для .NET?
 Вы можете скачать библиотеку с сайта[Веб-сайт ГруппДокс](https://releases.groupdocs.com/parser/net/).
### Доступна ли бесплатная пробная версия?
 Да, вы можете получить доступ к бесплатной пробной версии GroupDocs.Parser для .NET на сайте[здесь](https://releases.groupdocs.com/).
### Где я могу найти поддержку GroupDocs.Parser для .NET?
 Для получения технической помощи и поддержки сообщества посетите[Форум групповых документов](https://forum.groupdocs.com/c/parser/17).
### Как я могу приобрести лицензию на GroupDocs.Parser для .NET?
 Вы можете приобрести лицензию на сайте[страница покупки](https://purchase.groupdocs.com/buy) или получить временную лицензию[здесь](https://purchase.groupdocs.com/temporary-license/).