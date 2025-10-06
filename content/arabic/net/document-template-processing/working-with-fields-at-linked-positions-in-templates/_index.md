---
title: العمل مع الحقول في المواضع المرتبطة في القوالب
linktitle: العمل مع الحقول في المواضع المرتبطة في القوالب
second_title: GroupDocs.Parser .NET API
description: تعرف على كيفية استخراج البيانات بكفاءة من المستندات باستخدام GroupDocs.Parser لـ .NET. برنامج تعليمي خطوة بخطوة مع أمثلة التعليمات البرمجية.
weight: 12
url: /ar/net/document-template-processing/working-with-fields-at-linked-positions-in-templates/
type: docs
---
# العمل مع الحقول في المواضع المرتبطة في القوالب

## مقدمة
تعد GroupDocs.Parser for .NET مكتبة قوية مصممة لتسهيل مهام تحليل المستندات واستخراج البيانات. وهو يدعم مجموعة واسعة من تنسيقات الملفات، بما في ذلك PDF وDOCX وXLSX والمزيد. إحدى ميزاته الرئيسية هي استخراج البيانات المستندة إلى القالب، والذي يسمح لك بتحديد الحقول داخل المستند واستخراج بيانات محددة بناءً على هذه القوالب المحددة مسبقًا.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك ما يلي:
- الفهم الأساسي للبرمجة C#
- تم تثبيت Visual Studio على نظامك
-  GroupDocs.Parser لمكتبة .NET (التنزيل من[هنا](https://releases.groupdocs.com/parser/net/))
- نماذج من ملفات المستندات للعمل معها

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
## الخطوة 1: تحديد حقول القالب
أولاً، حدد حقول القالب باستخدام التعبيرات العادية والمواضع المرتبطة:
```csharp
// تحديد حقل بتعبير عادي
TemplateField field = new TemplateField(
    new TemplateRegexPosition("Tax"),
    "Tax");
// حدد حقلاً مرتبطًا بإعدادات موضع محددة
TemplateField linkedField = new TemplateField(
    new TemplateLinkedPosition(
        "Tax",
        new Size(100, 20),
        new TemplateLinkedPositionEdges(false, false, true, false)),
    "TaxValue");
```
## الخطوة 2: إنشاء قالب
بعد ذلك، قم بإنشاء قالب يحتوي على الحقول المحددة:
```csharp
// إنشاء قالب مع الحقول المحددة
Template template = new Template(new TemplateItem[] { field, linkedField });
```
## الخطوة 3: تحليل المستند باستخدام القالب
 الآن، قم بتهيئة`Parser` فئة وتحليل المستند باستخدام القالب:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // تحليل المستند حسب القالب
    DocumentData data = parser.ParseByTemplate(template);
    // التكرار من خلال البيانات المستخرجة ونتائج الطباعة
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

## خاتمة
يعمل GroupDocs.Parser for .NET على تبسيط عملية استخراج البيانات المنظمة من المستندات باستخدام القوالب. من خلال تحديد الحقول وتطبيق القوالب، يمكنك استخراج المعلومات ذات الصلة بكفاءة، وتعزيز الأتمتة والإنتاجية في مهام معالجة المستندات.

## الأسئلة الشائعة
### هل يمكن لـ GroupDocs.Parser استخراج البيانات من ملفات PDF المشفرة؟
نعم، يدعم GroupDocs.Parser تحليل ملفات PDF المشفرة من خلال توفير كلمة المرور أثناء التحليل.
### ما هي تنسيقات الملفات المدعومة للاستخراج القائم على القالب؟
يدعم GroupDocs.Parser مجموعة واسعة من تنسيقات الملفات بما في ذلك PDF وDOCX وXLSX وPPTX وTXT والمزيد.
### هل هناك نسخة تجريبية متاحة لـ GroupDocs.Parser؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية من[هنا](https://releases.groupdocs.com/).
### هل يمكنني استخدام GroupDocs.Parser لمعالجة المستندات دفعة واحدة؟
نعم، يسمح GroupDocs.Parser بالمعالجة المجمعة لتحليل مستندات متعددة بشكل متزامن.
### أين يمكنني الحصول على الدعم الفني لـ GroupDocs.Parser؟
 يمكنك طلب الدعم الفني والتفاعل مع المجتمع على[منتدى مستندات المجموعة](https://forum.groupdocs.com/c/parser/17).