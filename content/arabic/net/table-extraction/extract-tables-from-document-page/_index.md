---
title: استخراج الجداول من صفحة الوثيقة
linktitle: استخراج الجداول من صفحة الوثيقة
second_title: GroupDocs.Parser .NET API
description: تعرف على كيفية استخراج الجداول من المستندات برمجياً باستخدام GroupDocs.Parser لـ .NET. يوفر هذا البرنامج التعليمي الشامل إرشادات خطوة بخطوة.
weight: 11
url: /ar/net/table-extraction/extract-tables-from-document-page/
type: docs
---
# استخراج الجداول من صفحة الوثيقة

## مقدمة
في هذا البرنامج التعليمي، سنستكشف كيفية استخراج الجداول من صفحة المستند باستخدام GroupDocs.Parser لـ .NET. GroupDocs.Parser هي مكتبة قوية تتيح للمطورين العمل مع تنسيقات المستندات المختلفة مثل PDF وDOCX وXLSX والمزيد. ومن خلال الاستفادة من ميزاته، يمكننا استخراج البيانات المنظمة مثل الجداول من هذه المستندات بكفاءة، مما يمكننا من معالجة المعلومات وتحليلها برمجيًا.
## المتطلبات الأساسية
قبل البدء، تأكد من أن لديك ما يلي:
- تم تثبيت Visual Studio على جهازك.
- الفهم الأساسي لتطوير C# و.NET.
-  GroupDocs.Parser لمكتبة .NET. يمكنك تنزيله من[هنا](https://releases.groupdocs.com/parser/net/).
- الوصول إلى نموذج مستند (PDF، DOCX، إلخ) يحتوي على جداول لاستخراجها.

## استيراد مساحات الأسماء
أولاً، ابدأ باستيراد مساحات الأسماء الضرورية في مشروع C# الخاص بك:
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
 إنشاء مثيل`Parser` فئة عن طريق توفير المسار إلى نموذج المستند الخاص بك:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //يستمر الرمز الخاص بك هنا ...
}
```
## الخطوة 2: التحقق من دعم استخراج جدول المستندات
قبل المتابعة، تحقق مما إذا كانت الوثيقة تدعم استخراج الجدول:
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document does not support table extraction.");
    return;
}
```
## الخطوة 3: تحديد تخطيط الجدول
تحديد تخطيط الجداول التي سيتم استخراجها من الوثيقة. حدد عرض الأعمدة وارتفاعات الصفوف وفقًا لبنية المستند:
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },  // عرض العمود
    new double[] { 325, 340, 365, 395 });         // ارتفاعات الصف
```
## الخطوة 4: تكوين خيارات استخراج الجدول
قم بإنشاء خيارات لاستخراج الجدول باستخدام التخطيط المحدد:
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## الخطوة 5: استرجاع معلومات الوثيقة
جلب معلومات حول المستند، بما في ذلك عدد الصفحات:
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## الخطوة 6: التكرار على صفحات المستند
كرر خلال كل صفحة من المستند لاستخراج الجداول:
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // استخراج الجداول من الصفحة الحالية
    IEnumerable<PageTableArea> tables = parser.GetTables(pageIndex, options);
    // التكرار على الجداول المستخرجة
    foreach (PageTableArea table in tables)
    {
        // التكرار على صفوف الجدول
        for (int row = 0; row < table.RowCount; row++)
        {
            // التكرار على أعمدة الجدول
            for (int column = 0; column < table.ColumnCount; column++)
            {
                // الحصول على خلية الجدول
                PageTableAreaCell cell = table[row, column];
                if (cell != null)
                {
                    // طباعة نص خلية الجدول
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

## خاتمة
في هذا البرنامج التعليمي، قمنا بتغطية عملية استخراج الجداول من صفحات المستندات باستخدام GroupDocs.Parser لـ .NET. باتباع الخطوات المقدمة، يمكنك دمج وظيفة استخراج الجدول بسلاسة في تطبيقات .NET الخاصة بك، مما يتيح المعالجة والمعالجة الفعالة للبيانات المنظمة داخل المستندات.

## الأسئلة الشائعة
### هل يستطيع GroupDocs.Parser استخراج الجداول من كافة أنواع المستندات؟
يدعم GroupDocs.Parser تنسيقات المستندات المختلفة مثل PDF وDOCX وXLSX والمزيد، مما يتيح استخراج الجدول من أنواع الملفات المتوافقة.
### هل GroupDocs.Parser for .NET مناسب لمعالجة المستندات على نطاق واسع؟
نعم، تم تصميم GroupDocs.Parser للتعامل مع المستندات الكبيرة بكفاءة، مما يجعله مناسبًا لمعالجة مجموعات البيانات الشاملة.
### هل يحتفظ GroupDocs.Parser بالتنسيق أثناء استخراج الجدول؟
نعم، يحتفظ GroupDocs.Parser بتفاصيل التنسيق مثل حدود الخلايا وأنماط النص والمحاذاة أثناء استخراج الجدول.
### هل يمكنني استخراج جداول محددة بناءً على معايير المحتوى؟
يوفر GroupDocs.Parser خيارات مرنة لاستهداف جداول محددة بناءً على قوالب التخطيط أو شروط المحتوى للاستخراج.
### هل GroupDocs.Parser متوافق مع .NET Core؟
نعم، GroupDocs.Parser متوافق مع كل من بيئات .NET Framework و.NET Core.