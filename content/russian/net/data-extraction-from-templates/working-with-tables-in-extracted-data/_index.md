---
title: Работа с таблицами в извлеченных данных
linktitle: Работа с таблицами в извлеченных данных
second_title: GroupDocs.Parser .NET API
description: Узнайте, как извлечь данные таблицы из документов с помощью GroupDocs.Parser для .NET. Эффективно анализируйте структурированный контент с помощью предопределенных шаблонов.
type: docs
weight: 12
url: /ru/net/data-extraction-from-templates/working-with-tables-in-extracted-data/
---
## Введение
В этом руководстве мы рассмотрим, как использовать GroupDocs.Parser для .NET для извлечения данных из таблиц в документах. GroupDocs.Parser — это мощный инструмент, который позволяет разработчикам анализировать и извлекать текст, метаданные и структурированный контент из различных форматов файлов, таких как PDF, DOCX, XLSX и других. В частности, мы сосредоточимся на эффективном извлечении данных таблиц с использованием предопределенных шаблонов.
## Предварительные условия
Прежде чем начать, убедитесь, что у вас есть следующее:
- Visual Studio установлена на вашем компьютере.
- Базовое понимание C# и .NET framework.
- Библиотека GroupDocs.Parser устанавливается через менеджер пакетов NuGet.

## Импортировать пространства имен
Начните с импорта необходимых пространств имен для работы с GroupDocs.Parser и связанными с ним функциями.
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Шаг 1. Создайте шаблон таблицы
Чтобы извлечь данные из таблиц, сначала определите шаблон, представляющий структуру таблицы, которую вы хотите извлечь. Укажите расположение и размеры таблицы в документе.
```csharp
// Определить параметры таблицы (расположение и размер)
TemplateTableParameters parameters = new TemplateTableParameters(new Rectangle(new Point(35, 320), new Size(530, 55)), null);
// Создайте шаблон таблицы с параметрами
TemplateTable table = new TemplateTable(parameters, "Details", null);
```
## Шаг 2. Определите шаблон
Создайте шаблон, включающий определенный вами шаблон таблицы. Этот шаблон поможет синтаксическому анализатору понять, на что следует обращать внимание при извлечении данных таблицы.
```csharp
// Создайте шаблон с таблицей
Template template = new Template(new TemplateItem[] { table });
```
## Шаг 3. Анализ документа и извлечение данных таблицы
Используйте класс Parser из GroupDocs.Parser для анализа определенного документа с использованием определенного вами шаблона.
```csharp
// Укажите путь к файлу примера
string filePath = "YourSampleFile.pdf";
// Создайте экземпляр класса Parser
using (Parser parser = new Parser(filePath))
{
    // Разобрать документ по шаблону
    DocumentData data = parser.ParseByTemplate(template);
    // Перебрать все извлеченные данные
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        // Проверьте, является ли извлеченное поле таблицей
        PageTableArea area = data[i].PageArea as PageTableArea;
        if (area == null)
        {
            continue;
        }
        // Перебирать строки таблицы
        for (int row = 0; row < area.RowCount; row++)
        {
            // Перебирать столбцы таблицы
            for (int column = 0; column < area.ColumnCount; column++)
            {
                // Получить значение ячейки
                PageTextArea cellValue = area[row, column].PageArea as PageTextArea;
                // Распечатайте значение ячейки (или пустую строку, если значение равно нулю)
                Console.Write(cellValue == null ? "" : cellValue.Text);
                // Печать табуляции между столбцами
                if (column > 0)
                {
                    Console.Write("\t");
                }
            }
            // Переход к следующей строке после печати каждой строки
            Console.WriteLine();
        }
    }
}
```

## Заключение
В этом руководстве мы рассмотрели, как использовать GroupDocs.Parser для .NET для извлечения табличных данных из документов. Определяя шаблоны и используя методы анализа, разработчики могут эффективно извлекать структурированные данные, такие как таблицы, из файлов различных форматов.

## Часто задаваемые вопросы
### Совместим ли GroupDocs.Parser со всеми форматами документов?
Да, GroupDocs.Parser поддерживает широкий спектр форматов файлов, включая PDF, DOCX, XLSX, PPTX и другие.
### Могу ли я извлечь данные из определенных областей документа?
Конечно, вы можете определить шаблоны, предназначенные для извлечения определенных областей (например, таблиц) внутри документа.
### Подходит ли GroupDocs.Parser для больших документов?
Да, GroupDocs.Parser оптимизирован для эффективной обработки больших документов, что позволяет разработчикам беспрепятственно извлекать данные.
### Поддерживает ли GroupDocs.Parser извлечение текста вместе со структурированными данными?
Да, помимо извлечения структурированных данных (например, таблиц), GroupDocs.Parser может извлекать из документов простой текст и метаданные.
### Как я могу получить поддержку или помощь по интеграции GroupDocs.Parser?
 Для поддержки и обсуждения посетите форум сообщества GroupDocs.[здесь](https://forum.groupdocs.com/c/parser/17).