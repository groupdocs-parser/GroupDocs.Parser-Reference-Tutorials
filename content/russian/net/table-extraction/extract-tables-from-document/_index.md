---
title: Извлечь таблицы из документа
linktitle: Извлечь таблицы из документа
second_title: GroupDocs.Parser .NET API
description: Узнайте, как извлекать таблицы из документов с помощью Groupdocs.Parser для .NET. Следуйте инструкциям по интеграции этой функции.
type: docs
weight: 10
url: /ru/net/table-extraction/extract-tables-from-document/
---
## Введение
Groupdocs.Parser для .NET — это комплексная библиотека, которая упрощает анализ документов и позволяет извлекать из документов ценную информацию, такую как таблицы, текст, метаданные и многое другое. В этом руководстве мы сосредоточимся конкретно на извлечении таблиц из документов с помощью API Groupdocs.Parser.
## Предварительные условия
Прежде чем мы начнем, убедитесь, что у вас есть следующее:
- Visual Studio установлена в вашей системе.
- Установлен .NET Framework или .NET Core.
- Базовые знания программирования на C#.

## Импортировать пространства имен
Во-первых, вам необходимо импортировать необходимые пространства имен для доступа к классам и методам Groupdocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using GroupDocs.Parser.Templates;
```
## Шаг 1. Создайте экземпляр класса парсера
 Инициализировать новый экземпляр`Parser` class, указав путь к образцу документа.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Ваш код находится здесь
}
```
## Шаг 2. Проверьте поддержку извлечения таблиц
 Убедитесь, что документ поддерживает извлечение таблицы с помощью`Features` собственность`Parser` сорт.
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document doesn't support table extraction.");
    return;
}
```
## Шаг 3. Определите макет таблицы
Определите макет таблиц, которые вы хотите извлечь, используя`TemplateTableLayout`. Укажите ширину столбцов и высоту строк в зависимости от структуры вашего документа.
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },
    new double[] { 325, 340, 365, 395 });
```
## Шаг 4. Установите параметры извлечения таблицы
 Создавать`PageTableAreaOptions` с определенным макетом, чтобы указать, как следует извлекать таблицы.
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Шаг 5: Извлечение таблиц
 Используйте`GetTables` метод`Parser` класс для извлечения таблиц из документа на основе заданных параметров.
```csharp
IEnumerable<PageTableArea> tables = parser.GetTables(options);
```
## Шаг 6. Итерация и доступ к данным таблицы
Перебирайте извлеченные таблицы и соответствующие им строки и столбцы, чтобы получить доступ к данным ячеек.
```csharp
foreach (PageTableArea table in tables)
{
    for (int row = 0; row < table.RowCount; row++)
    {
        for (int column = 0; column < table.ColumnCount; column++)
        {
            PageTableAreaCell cell = table[row, column];
            if (cell != null)
            {
                Console.Write(cell.Text);
                Console.Write(" | ");
            }
        }
        Console.WriteLine();
    }
    Console.WriteLine();
}
```
## Заключение
В этом руководстве мы рассмотрели, как использовать Groupdocs.Parser для .NET для эффективного извлечения таблиц из документов. Используя возможности этой библиотеки, вы можете легко интегрировать извлечение таблиц в свои приложения .NET.

## Часто задаваемые вопросы
### Может ли Groupdocs.Parser обрабатывать документы разных форматов?
Да, Groupdocs.Parser поддерживает широкий спектр форматов документов, включая DOCX, PDF, XLSX и другие.
### Доступна ли пробная версия Groupdocs.Parser для .NET?
 Да, вы можете загрузить бесплатную пробную версию с сайта[здесь](https://releases.groupdocs.com/).
### Как я могу получить поддержку по запросам, связанным с Groupdocs.Parser?
 Вы можете посетить[Форум Groupdocs.Parser](https://forum.groupdocs.com/c/parser/17) для оказания помощи.
### Где я могу приобрести лицензию на Groupdocs.Parser?
 Вы можете купить лицензию у[здесь](https://purchase.groupdocs.com/buy).
### Как я могу получить временную лицензию для ознакомительных целей?
 Вы можете получить временную лицензию[здесь](https://purchase.groupdocs.com/temporary-license/).