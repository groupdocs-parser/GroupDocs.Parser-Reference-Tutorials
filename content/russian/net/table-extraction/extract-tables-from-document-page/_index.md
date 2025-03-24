---
title: Извлечь таблицы со страницы документа
linktitle: Извлечь таблицы со страницы документа
second_title: GroupDocs.Parser .NET API
description: Узнайте, как программно извлекать таблицы из документов с помощью GroupDocs.Parser для .NET. Это подробное руководство содержит пошаговые инструкции.
weight: 11
url: /ru/net/table-extraction/extract-tables-from-document-page/
---

# Извлечь таблицы со страницы документа

## Введение
В этом руководстве мы рассмотрим, как извлекать таблицы со страницы документа с помощью GroupDocs.Parser для .NET. GroupDocs.Parser — это мощная библиотека, которая позволяет разработчикам работать с различными форматами документов, такими как PDF, DOCX, XLSX и другими. Используя его функции, мы можем эффективно извлекать из этих документов структурированные данные, такие как таблицы, что позволяет нам программно манипулировать и анализировать информацию.
## Предварительные условия
Прежде чем приступить к работе, убедитесь, что у вас есть следующее:
- Visual Studio установлена на вашем компьютере.
- Базовое понимание разработки на C# и .NET.
-  GroupDocs.Parser для библиотеки .NET. Вы можете скачать его с[здесь](https://releases.groupdocs.com/parser/net/).
- Доступ к образцу документа (PDF, DOCX и т. д.), содержащему таблицы для извлечения.

## Импортировать пространства имен
Сначала начните с импорта необходимых пространств имен в проект C#:
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
 Создайте экземпляр`Parser` класс, указав путь к образцу документа:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //Ваш код продолжается здесь...
}
```
## Шаг 2. Проверьте поддержку извлечения таблицы документов
Прежде чем продолжить, проверьте, поддерживает ли документ извлечение таблиц:
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document does not support table extraction.");
    return;
}
```
## Шаг 3. Определите макет таблицы
Определите макет таблиц, которые будут извлечены из документа. Укажите ширину столбцов и высоту строк в соответствии со структурой вашего документа:
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },  // Ширина столбцов
    new double[] { 325, 340, 365, 395 });         // Высота строк
```
## Шаг 4. Настройте параметры извлечения таблиц
Создайте параметры извлечения таблицы, используя указанный макет:
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Шаг 5: Получите информацию о документе
Получите информацию о документе, включая количество страниц:
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Шаг 6. Перебор страниц документа
Перейдите по каждой странице документа, чтобы извлечь таблицы:
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Извлечь таблицы с текущей страницы
    IEnumerable<PageTableArea> tables = parser.GetTables(pageIndex, options);
    // Перебирать извлеченные таблицы
    foreach (PageTableArea table in tables)
    {
        // Перебирать строки таблицы
        for (int row = 0; row < table.RowCount; row++)
        {
            // Перебирать столбцы таблицы
            for (int column = 0; column < table.ColumnCount; column++)
            {
                // Получить ячейку таблицы
                PageTableAreaCell cell = table[row, column];
                if (cell != null)
                {
                    // Распечатать текст ячейки таблицы
                    Console.Write(cell.Text);
                    Console.Write(" | ");
                }
            }
            Console.WriteLine();
        }
        Console.WriteLine();
    }
}
```

## Заключение
В этом руководстве мы рассмотрели процесс извлечения таблиц со страниц документа с помощью GroupDocs.Parser для .NET. Следуя предоставленным инструкциям, вы сможете легко интегрировать функцию извлечения таблиц в свои приложения .NET, обеспечивая эффективную обработку и манипулирование структурированными данными в документах.

## Часто задаваемые вопросы
### Может ли GroupDocs.Parser извлекать таблицы из всех типов документов?
GroupDocs.Parser поддерживает различные форматы документов, такие как PDF, DOCX, XLSX и другие, позволяя извлекать таблицы из совместимых типов файлов.
### Подходит ли GroupDocs.Parser для .NET для крупномасштабной обработки документов?
Да, GroupDocs.Parser предназначен для эффективной обработки больших документов, что делает его пригодным для обработки обширных наборов данных.
### Сохраняет ли GroupDocs.Parser форматирование во время извлечения таблицы?
Да, GroupDocs.Parser сохраняет детали форматирования, такие как границы ячеек, стили текста и выравнивание, во время извлечения таблицы.
### Могу ли я извлечь определенные таблицы на основе критериев содержания?
GroupDocs.Parser предлагает гибкие возможности выбора конкретных таблиц на основе шаблонов макета или условий содержимого для извлечения.
### Совместим ли GroupDocs.Parser с .NET Core?
Да, GroupDocs.Parser совместим со средами .NET Framework и .NET Core.