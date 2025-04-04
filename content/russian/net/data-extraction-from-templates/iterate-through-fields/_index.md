---
title: Перебор полей
linktitle: Перебор полей
second_title: GroupDocs.Parser .NET API
description: Узнайте, как извлекать структурированные данные из документов с помощью GroupDocs.Parser для .NET. Расширьте возможности своих .NET-приложений с помощью возможностей извлечения данных из документов.
weight: 11
url: /ru/net/data-extraction-from-templates/iterate-through-fields/
---

# Перебор полей

## Введение
GroupDocs.Parser для .NET — это мощная библиотека, которая позволяет разработчикам извлекать данные из различных форматов документов, таких как PDF, Microsoft Word, Excel и PowerPoint. Это руководство проведет вас через процесс использования GroupDocs.Parser для перебора полей документа и извлечения определенных данных с помощью шаблонов. К концу этого руководства вы сможете эффективно извлекать структурированные данные из документов в своих приложениях .NET.
## Предварительные условия
Прежде чем мы начнем, убедитесь, что у вас настроены следующие предварительные условия:
- Базовые знания программирования на C#.
- Visual Studio установлена на вашем компьютере.
- GroupDocs.Parser для библиотеки .NET, установленной и указанной в вашем проекте.

## Импортировать пространства имен
Для начала добавьте необходимые пространства имен в файл C#:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
Разобьем процесс на пошаговые инструкции.
## Шаг 1. Определите поля шаблона
Сначала определите поля, которые вы хотите извлечь из документа, с помощью регулярных выражений.
```csharp
// Определите поле «цена»
TemplateField priceField = new TemplateField(
    new TemplateRegexPosition("\\$\\d+(.\\d+)?"),
    "Price");
// Определите поле «электронная почта»
TemplateField emailField = new TemplateField(
    new TemplateRegexPosition("[a-z]+\\@[a-z]+\\.[a-z]+"),
    "Email");
// Создайте шаблон с определенными полями
Template template = new Template(new TemplateItem[] { priceField, emailField });
```
На этом этапе мы определили два поля: одно для извлечения цен (обозначаемых знаком доллара и цифрами), а другое — для извлечения адресов электронной почты.
## Шаг 2. Анализ документа
 Далее используйте`Parser` класс для анализа документа с использованием определенного шаблона.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Разобрать документ по шаблону
    DocumentData data = parser.ParseByTemplate(template);
    // Перебирать извлеченные данные
    for (int i = 0; i < data.Count; i++)
    {
        // Распечатать имя поля
        Console.Write(data[i].Name + ": ");
        // Проверьте, является ли извлеченная область текстом
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
 Здесь мы инициализируем`Parser` указав путь к образцу документа, а затем проанализируйте документ, используя определенный шаблон. Затем мы перебираем извлеченные данные и печатаем имена полей вместе с извлеченным текстом.
## Заключение
В этом руководстве мы рассмотрели, как использовать GroupDocs.Parser для .NET для извлечения определенных данных из документов с помощью шаблонов. Используя регулярные выражения и шаблоны, вы можете эффективно извлекать структурированную информацию из документов различных форматов. Поэкспериментируйте с различными шаблонами и типами документов в соответствии с вашими конкретными потребностями в извлечении.

## Часто задаваемые вопросы
### Может ли GroupDocs.Parser извлекать данные из отсканированных документов?
Да, GroupDocs.Parser может извлекать текст и метаданные как из отсканированных PDF-документов, так и из доступных для поиска PDF-документов.
### Совместим ли GroupDocs.Parser с приложениями .NET Core?
Да, GroupDocs.Parser поддерживает .NET Core наряду с .NET Framework.
### Какие форматы документов поддерживает GroupDocs.Parser?
GroupDocs.Parser поддерживает широкий спектр форматов, включая PDF, Microsoft Word, Excel, PowerPoint и другие.
### Как я могу обрабатывать большие документы с помощью GroupDocs.Parser?
GroupDocs.Parser предоставляет возможности для извлечения данных из определенных страниц или разделов больших документов, обеспечивая эффективную обработку.
### Могу ли я использовать GroupDocs.Parser только для извлечения текста?
Да, вы можете извлечь обычный текстовый контент из документов с помощью GroupDocs.Parser без необходимости сложного форматирования.