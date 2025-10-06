---
title: العمل مع الجداول في البيانات المستخرجة
linktitle: العمل مع الجداول في البيانات المستخرجة
second_title: GroupDocs.Parser .NET API
description: تعرف على كيفية استخراج بيانات الجدول من المستندات باستخدام GroupDocs.Parser لـ .NET. تحليل المحتوى المنظم بكفاءة باستخدام قوالب محددة مسبقًا.
weight: 12
url: /ar/net/data-extraction-from-templates/working-with-tables-in-extracted-data/
type: docs
---
# العمل مع الجداول في البيانات المستخرجة

## مقدمة
في هذا البرنامج التعليمي، سوف نستكشف كيفية استخدام GroupDocs.Parser لـ .NET لاستخراج البيانات من الجداول في المستندات. تعد GroupDocs.Parser أداة قوية تمكن المطورين من تحليل واستخراج النص وبيانات التعريف والمحتوى المنظم من تنسيقات ملفات مختلفة مثل PDF وDOCX وXLSX والمزيد. وعلى وجه التحديد، سنركز على استخراج بيانات الجدول بكفاءة باستخدام قوالب محددة مسبقًا.
## المتطلبات الأساسية
قبل البدء، تأكد من توفر ما يلي:
- تم تثبيت Visual Studio على جهازك.
- الفهم الأساسي لـ C# و.NET Framework.
- تم تثبيت مكتبة GroupDocs.Parser عبر مدير الحزم NuGet.

## استيراد مساحات الأسماء
ابدأ باستيراد مساحات الأسماء الضرورية للعمل مع GroupDocs.Parser والوظائف ذات الصلة.
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## الخطوة 1: إنشاء قالب جدول
لاستخراج البيانات من الجداول، قم أولاً بتحديد قالب يمثل بنية الجدول الذي تريد استخراجه. حدد موقع الجدول وأبعاده داخل المستند.
```csharp
// تحديد معلمات الجدول (الموقع والحجم)
TemplateTableParameters parameters = new TemplateTableParameters(new Rectangle(new Point(35, 320), new Size(530, 55)), null);
// إنشاء قالب جدول مع المعلمات
TemplateTable table = new TemplateTable(parameters, "Details", null);
```
## الخطوة 2: تحديد القالب
قم بإنشاء قالب يتضمن قالب الجدول الذي حددته. سيرشد هذا القالب المحلل اللغوي إلى ما يجب البحث عنه عند استخراج بيانات الجدول.
```csharp
// إنشاء قالب مع الجدول
Template template = new Template(new TemplateItem[] { table });
```
## الخطوة 3: تحليل المستند واستخراج بيانات الجدول
استخدم فئة Parser من GroupDocs.Parser لتحليل مستند محدد باستخدام القالب الذي حددته.
```csharp
// حدد المسار إلى ملف العينة الخاص بك
string filePath = "YourSampleFile.pdf";
// إنشاء مثيل لفئة المحلل اللغوي
using (Parser parser = new Parser(filePath))
{
    // تحليل المستند حسب القالب
    DocumentData data = parser.ParseByTemplate(template);
    // التكرار على كافة البيانات المستخرجة
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        // تحقق مما إذا كان الحقل المستخرج عبارة عن جدول
        PageTableArea area = data[i].PageArea as PageTableArea;
        if (area == null)
        {
            continue;
        }
        // التكرار على صفوف الجدول
        for (int row = 0; row < area.RowCount; row++)
        {
            // التكرار على أعمدة الجدول
            for (int column = 0; column < area.ColumnCount; column++)
            {
                // احصل على قيمة الخلية
                PageTextArea cellValue = area[row, column].PageArea as PageTextArea;
                // اطبع قيمة الخلية (أو سلسلة فارغة إذا كانت فارغة)
                Console.Write(cellValue == null ? "" : cellValue.Text);
                // طباعة مسافة علامة تبويب بين الأعمدة
                if (column > 0)
                {
                    Console.Write("\t");
                }
            }
            // انتقل إلى السطر التالي بعد طباعة كل صف
            Console.WriteLine();
        }
    }
}
```

## خاتمة
في هذا البرنامج التعليمي، اكتشفنا كيفية استخدام GroupDocs.Parser لـ .NET لاستخراج بيانات الجدول من المستندات. من خلال تحديد القوالب واستخدام أساليب التحليل، يمكن للمطورين استخراج البيانات المنظمة بكفاءة مثل الجداول من تنسيقات الملفات المختلفة.

## الأسئلة الشائعة
### هل GroupDocs.Parser متوافق مع كافة تنسيقات المستندات؟
نعم، يدعم GroupDocs.Parser مجموعة واسعة من تنسيقات الملفات بما في ذلك PDF وDOCX وXLSX وPPTX والمزيد.
### هل يمكنني استخراج البيانات من مناطق محددة داخل المستند؟
بالتأكيد، يمكنك تحديد القوالب التي تستهدف مناطق معينة (مثل الجداول) داخل المستند لاستخراجها.
### هل GroupDocs.Parser مناسب للمستندات الكبيرة؟
نعم، تم تحسين GroupDocs.Parser للتعامل مع المستندات الكبيرة بكفاءة، مما يسمح للمطورين باستخراج البيانات بسلاسة.
### هل يدعم GroupDocs.Parser استخراج النص إلى جانب البيانات المنظمة؟
نعم، بالإضافة إلى استخراج البيانات المنظمة (مثل الجداول)، يستطيع GroupDocs.Parser استخراج النص العادي وبيانات التعريف من المستندات.
### كيف يمكنني الحصول على الدعم أو المساعدة فيما يتعلق بتكامل GroupDocs.Parser؟
 للحصول على الدعم والمناقشات، تفضل بزيارة منتدى مجتمع GroupDocs[هنا](https://forum.groupdocs.com/c/parser/17).