---
title: العمل مع الحقول في المواضع الثابتة في القوالب
linktitle: العمل مع الحقول في المواضع الثابتة في القوالب
second_title: GroupDocs.Parser .NET API
description: تعرف على كيفية استخراج البيانات من المستندات باستخدام GroupDocs.Parser لـ .NET. برنامج تعليمي شامل مع أمثلة التعليمات البرمجية.
type: docs
weight: 11
url: /ar/net/document-template-processing/working-with-fields-at-fixed-positions-in-templates/
---
## مقدمة
في هذا البرنامج التعليمي، سوف نستكشف كيفية التعامل مع الحقول الموجودة في مواضع ثابتة داخل القوالب باستخدام GroupDocs.Parser لـ .NET. GroupDocs.Parser هي مكتبة قوية لتحليل المستندات تمكن المطورين من استخراج البيانات من تنسيقات المستندات المختلفة مثل PDF وWord وExcel والمزيد. على وجه التحديد، سنركز على تحديد واستخدام حقول القالب لاستخراج المعلومات المستهدفة بناءً على مواضعها الثابتة.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك ما يلي:
- الفهم الأساسي لتطوير C# و.NET.
- تم تثبيت Visual Studio على نظامك.
- تم تثبيت GroupDocs.Parser لمكتبة .NET. يمكنك تنزيله من[هنا](https://releases.groupdocs.com/parser/net/).
- نماذج من ملفات المستندات للاختبار.

## استيراد مساحات الأسماء
ابدأ بتضمين مساحات الأسماء الضرورية في مشروع C# الخاص بك:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## الخطوة 1: تحديد حقل القالب
أولاً، قم بتعريف حقل بموضع ثابت داخل القالب. يمثل هذا الحقل المنطقة التي سيتم استخراج البيانات منها.
```csharp
TemplateField field = new TemplateField(
    new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))),
    "FromCompany");
```
هنا:
- `Rectangle` يحدد موضع وحجم الحقل.
- `Point(35, 135)` يمثل إحداثيات الزاوية العلوية اليسرى.
- `Size(100, 10)` يحدد عرض وارتفاع الحقل.
- `"FromCompany"` هو الاسم المخصص لهذا الحقل.
## الخطوة 2: إنشاء قالب
إنشاء قالب باستخدام الحقل المحدد.
```csharp
Template template = new Template(new TemplateItem[] { field });
```
 ال`Template` الكائن يحمل الحقول المحددة.
## الخطوة 3: تحليل المستند باستخدام القالب
 إنشاء مثيل`Parser` فئة مع مسار المستند الهدف ثم قم بتحليل المستند باستخدام القالب الذي تم إنشاؤه.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    // التكرار من خلال البيانات المستخرجة
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
هنا:
- `Parser` تتم تهيئته باستخدام مسار ملف المستند النموذجي.
- `ParseByTemplate` يتم استخدام الطريقة لاستخراج البيانات بناءً على القالب المقدم.
-  يتم الوصول إلى البيانات المستخرجة باستخدام`DocumentData`، حيث يتوافق كل عنصر مع حقل محدد.

## خاتمة
في هذا البرنامج التعليمي، قمنا بتغطية عملية العمل مع الحقول في المواضع الثابتة في القوالب باستخدام GroupDocs.Parser لـ .NET. من خلال تحديد القوالب بمواضع ميدانية محددة، يمكن للمطورين استخراج البيانات المستهدفة بدقة من تنسيقات المستندات المختلفة.

## الأسئلة الشائعة
### هل GroupDocs.Parser متوافق مع كافة تنسيقات المستندات؟
 يدعم GroupDocs.Parser مجموعة واسعة من تنسيقات الملفات، بما في ذلك PDF وMicrosoft Word وExcel وPowerPoint والمزيد. الرجوع إلى[توثيق](https://reference.groupdocs.com/parser/net/) للحصول على قائمة مفصلة.
### كيف يمكنني الحصول على ترخيص مؤقت لـ GroupDocs.Parser؟
 يمكنك الحصول على ترخيص مؤقت لأغراض الاختبار من[هنا](https://purchase.groupdocs.com/temporary-license/).
### أين يمكنني العثور على الدعم لـ GroupDocs.Parser؟
 للحصول على المساعدة الفنية والمناقشات، قم بزيارة[منتدى GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).
### هل يمكنني تجربة GroupDocs.Parser قبل الشراء؟
 نعم، يمكنك استكشاف المكتبة من خلال النسخة التجريبية المجانية المتاحة[هنا](https://releases.groupdocs.com/).
### كيف يمكنني شراء ترخيص GroupDocs.Parser؟
 لشراء ترخيص، قم بزيارة[صفحة الشراء](https://purchase.groupdocs.com/buy).