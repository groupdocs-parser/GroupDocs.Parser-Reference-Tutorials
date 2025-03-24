---
title: Работа с полями в фиксированных позициях в шаблонах
linktitle: Работа с полями в фиксированных позициях в шаблонах
second_title: GroupDocs.Parser .NET API
description: Узнайте, как извлекать данные из документов с помощью GroupDocs.Parser для .NET. Подробное руководство с примерами кода.
weight: 11
url: /ru/net/document-template-processing/working-with-fields-at-fixed-positions-in-templates/
---
## Введение
В этом руководстве мы рассмотрим, как работать с полями в фиксированных позициях в шаблонах с помощью GroupDocs.Parser для .NET. GroupDocs.Parser — это мощная библиотека анализа документов, которая позволяет разработчикам извлекать данные из различных форматов документов, таких как PDF, Word, Excel и других. В частности, мы сосредоточимся на определении и использовании полей шаблона для извлечения целевой информации на основе их фиксированных позиций.
## Предварительные условия
Прежде чем мы начнем, убедитесь, что у вас есть следующее:
- Базовое понимание разработки на C# и .NET.
- Visual Studio установлена в вашей системе.
- Установлена библиотека GroupDocs.Parser для .NET. Вы можете скачать его с[здесь](https://releases.groupdocs.com/parser/net/).
- Примеры файлов документов для тестирования.

## Импортировать пространства имен
Начните с включения необходимых пространств имен в проект C#:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Шаг 1. Определите поле шаблона
Сначала определите поле с фиксированной позицией в шаблоне. Это поле представляет область, из которой будут извлечены данные.
```csharp
TemplateField field = new TemplateField(
    new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))),
    "FromCompany");
```
Здесь:
- `Rectangle` определяет положение и размер поля.
- `Point(35, 135)` представляет координаты верхнего левого угла.
- `Size(100, 10)` определяет ширину и высоту поля.
- `"FromCompany"` — это имя, присвоенное этому полю.
## Шаг 2: Создайте шаблон
Создайте шаблон, используя определенное поле.
```csharp
Template template = new Template(new TemplateItem[] { field });
```
`Template` объект содержит определенные поля.
## Шаг 3. Анализ документа с использованием шаблона
 Создайте экземпляр`Parser` class с указанием пути к целевому документу, а затем проанализируйте документ, используя созданный шаблон.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    // Перебирать извлеченные данные
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
Здесь:
- `Parser` инициализируется с использованием пути к файлу образца документа.
- `ParseByTemplate` Метод используется для извлечения данных на основе предоставленного шаблона.
-  Доступ к извлеченным данным осуществляется с помощью`DocumentData`где каждый элемент соответствует определенному полю.

## Заключение
В этом руководстве мы рассмотрели процесс работы с полями в фиксированных позициях в шаблонах с использованием GroupDocs.Parser для .NET. Определяя шаблоны с конкретными позициями полей, разработчики могут точно извлекать нужные данные из документов различных форматов.

## Часто задаваемые вопросы
### Совместим ли GroupDocs.Parser со всеми форматами документов?
 GroupDocs.Parser поддерживает широкий спектр форматов файлов, включая PDF, Microsoft Word, Excel, PowerPoint и другие. Обратитесь к[документация](https://tutorials.groupdocs.com/parser/net/) для подробного списка.
### Как получить временную лицензию на GroupDocs.Parser?
 Вы можете получить временную лицензию для целей тестирования на сайте[здесь](https://purchase.groupdocs.com/temporary-license/).
### Где я могу найти поддержку GroupDocs.Parser?
 Для получения технической помощи и обсуждений посетите[Форум GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).
### Могу ли я попробовать GroupDocs.Parser перед покупкой?
 Да, вы можете изучить библиотеку, воспользовавшись бесплатной пробной версией.[здесь](https://releases.groupdocs.com/).
### Как приобрести лицензию на GroupDocs.Parser?
 Чтобы купить лицензию, посетите сайт[страница покупки](https://purchase.groupdocs.com/buy).