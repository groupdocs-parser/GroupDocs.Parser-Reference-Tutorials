---
title: استخراج الجداول من الوثيقة
linktitle: استخراج الجداول من الوثيقة
second_title: GroupDocs.Parser .NET API
description: تعرف على كيفية استخراج الجداول من المستندات باستخدام Groupdocs.Parser لـ .NET. تابع للحصول على دليل مفصل حول دمج هذه الوظيفة.
weight: 10
url: /ar/net/table-extraction/extract-tables-from-document/
---

# استخراج الجداول من الوثيقة

## مقدمة
Groupdocs.Parser for .NET عبارة عن مكتبة شاملة تسهل تحليل المستندات، مما يسمح لك باستخراج معلومات قيمة مثل الجداول والنصوص وبيانات التعريف والمزيد من المستندات. في هذا البرنامج التعليمي، نركز بشكل خاص على استخراج الجداول من المستندات باستخدام Groupdocs.Parser API.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك ما يلي:
- تم تثبيت Visual Studio على نظامك.
- تم تثبيت .NET Framework أو .NET Core.
- المعرفة الأساسية ببرمجة C#.

## استيراد مساحات الأسماء
أولاً، تحتاج إلى استيراد مساحات الأسماء الضرورية للوصول إلى فئات وأساليب Groupdocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using GroupDocs.Parser.Templates;
```
## الخطوة 1: إنشاء مثيل لفئة المحلل اللغوي
 تهيئة مثيل جديد لـ`Parser` فئة عن طريق توفير المسار إلى نموذج المستند الخاص بك.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // الكود الخاص بك يذهب هنا
}
```
## الخطوة 2: التحقق من دعم استخراج الجدول
 تحقق مما إذا كانت الوثيقة تدعم استخراج الجدول باستخدام ملف`Features` ملكية`Parser` فصل.
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document doesn't support table extraction.");
    return;
}
```
## الخطوة 3: تحديد تخطيط الجدول
حدد تخطيط الجداول التي تريد استخراجها باستخدام`TemplateTableLayout`. حدد عرض الأعمدة وارتفاعات الصفوف بناءً على بنية المستند.
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },
    new double[] { 325, 340, 365, 395 });
```
## الخطوة 4: ضبط خيارات استخراج الجدول
 يخلق`PageTableAreaOptions` مع التخطيط المحدد لتحديد كيفية استخراج الجداول.
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## الخطوة 5: استخراج الجداول
 الاستفادة من`GetTables` طريقة`Parser` فئة لاستخراج الجداول من المستند بناءً على الخيارات المحددة.
```csharp
IEnumerable<PageTableArea> tables = parser.GetTables(options);
```
## الخطوة 6: تكرار بيانات الجدول والوصول إليها
قم بالتكرار من خلال الجداول المستخرجة والصفوف والأعمدة الخاصة بها للوصول إلى بيانات الخلية.
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
## خاتمة
في هذا البرنامج التعليمي، تناولنا كيفية استخدام Groupdocs.Parser لـ .NET لاستخراج الجداول من المستندات بكفاءة. من خلال الاستفادة من إمكانيات هذه المكتبة، يمكنك دمج استخراج الجدول في تطبيقات .NET الخاصة بك بسلاسة.

## الأسئلة الشائعة
### هل يستطيع Groupdocs.Parser التعامل مع تنسيقات المستندات المختلفة؟
نعم، يدعم Groupdocs.Parser مجموعة واسعة من تنسيقات المستندات بما في ذلك DOCX وPDF وXLSX والمزيد.
### هل هناك إصدار تجريبي متاح لـ Groupdocs.Parser لـ .NET؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية من[هنا](https://releases.groupdocs.com/).
### كيف يمكنني الحصول على دعم للاستفسارات ذات الصلة بـ Groupdocs.Parser؟
 يمكنك زيارة[Groupdocs.منتدى المحلل](https://forum.groupdocs.com/c/parser/17) للمساعدة.
### أين يمكنني شراء ترخيص Groupdocs.Parser؟
 يمكنك شراء ترخيص من[هنا](https://purchase.groupdocs.com/buy).
### كيف يمكنني الحصول على ترخيص مؤقت لأغراض التقييم؟
 يمكنك الحصول على ترخيص مؤقت[هنا](https://purchase.groupdocs.com/temporary-license/).