---
title: Работа с полями в связанных позициях в шаблонах
linktitle: Работа с полями в связанных позициях в шаблонах
second_title: GroupDocs.Parser .NET API
description: Узнайте, как эффективно извлекать данные из документов с помощью GroupDocs.Parser для .NET. Пошаговое руководство с примерами кода.
type: docs
weight: 12
url: /ru/net/document-template-processing/working-with-fields-at-linked-positions-in-templates/
---
## Введение
GroupDocs.Parser для .NET — это надежная библиотека, предназначенная для облегчения задач анализа документов и извлечения данных. Он поддерживает широкий спектр форматов файлов, включая PDF, DOCX, XLSX и другие. Одной из его ключевых функций является извлечение данных на основе шаблонов, которое позволяет определять поля в документе и извлекать определенные данные на основе этих предопределенных шаблонов.
## Предварительные условия
Прежде чем мы начнем, убедитесь, что у вас есть следующее:
- Базовое понимание программирования на C#.
- Visual Studio установлена в вашей системе
-  GroupDocs.Parser для библиотеки .NET (скачать с сайта[здесь](https://releases.groupdocs.com/parser/net/))
- Примеры файлов документов для работы

## Импорт пространств имен
Начните с включения необходимых пространств имен в проект C#:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Шаг 1. Определите поля шаблона
Сначала определите поля шаблона, используя регулярные выражения и связанные позиции:
```csharp
// Определить поле с помощью регулярного выражения
TemplateField field = new TemplateField(
    new TemplateRegexPosition("Tax"),
    "Tax");
// Определите связанное поле с определенными настройками позиции
TemplateField linkedField = new TemplateField(
    new TemplateLinkedPosition(
        "Tax",
        new Size(100, 20),
        new TemplateLinkedPositionEdges(false, false, true, false)),
    "TaxValue");
```
## Шаг 2: Создайте шаблон
Затем создайте шаблон, содержащий определенные поля:
```csharp
// Создайте шаблон с определенными полями
Template template = new Template(new TemplateItem[] { field, linkedField });
```
## Шаг 3. Анализ документа с помощью шаблона
 Теперь инициализируйте`Parser` class и проанализируйте документ, используя шаблон:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Разобрать документ по шаблону
    DocumentData data = parser.ParseByTemplate(template);
    // Перебирать извлеченные данные и распечатывать результаты.
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

## Заключение
GroupDocs.Parser для .NET упрощает процесс извлечения структурированных данных из документов с помощью шаблонов. Определив поля и применив шаблоны, вы можете эффективно извлекать соответствующую информацию, повышая автоматизацию и производительность задач обработки документов.

## Часто задаваемые вопросы
### Может ли GroupDocs.Parser извлекать данные из зашифрованных PDF-файлов?
Да, GroupDocs.Parser поддерживает анализ зашифрованных PDF-файлов, предоставляя пароль во время анализа.
### Какие форматы файлов поддерживаются для извлечения на основе шаблонов?
GroupDocs.Parser поддерживает широкий спектр форматов файлов, включая PDF, DOCX, XLSX, PPTX, TXT и другие.
### Доступна ли пробная версия для GroupDocs.Parser?
 Да, вы можете скачать бесплатную пробную версию с сайта[здесь](https://releases.groupdocs.com/).
### Могу ли я использовать GroupDocs.Parser для пакетной обработки документов?
Да, GroupDocs.Parser позволяет пакетную обработку одновременно анализировать несколько документов.
### Где я могу получить техническую поддержку для GroupDocs.Parser?
 Вы можете обратиться за технической поддержкой и пообщаться с сообществом по адресу[Форум групповых документов](https://forum.groupdocs.com/c/parser/17).