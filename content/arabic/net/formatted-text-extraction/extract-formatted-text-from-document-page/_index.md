---
title: استخراج النص المنسق من صفحة المستند
linktitle: استخراج النص المنسق من صفحة المستند
second_title: GroupDocs.Parser .NET API
description: قم باستخراج النص المنسق من صفحات المستندات باستخدام GroupDocs.Parser لـ .NET. حل فعال وموثوق لاستخراج النص.
weight: 11
url: /ar/net/formatted-text-extraction/extract-formatted-text-from-document-page/
type: docs
---
# استخراج النص المنسق من صفحة المستند

## مقدمة
في هذا البرنامج التعليمي، سنرشدك خلال عملية استخراج النص المنسق من صفحات المستندات باستخدام GroupDocs.Parser لـ .NET. تتيح لك هذه المكتبة تحليل النص واستخراجه بكفاءة من تنسيقات المستندات المختلفة مثل PDF وWord وExcel والمزيد.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك ما يلي:
- تم تثبيت Visual Studio على نظامك.
- المعرفة الأساسية ببرمجة C#.
-  GroupDocs.Parser لمكتبة .NET. يمكنك تنزيله[هنا](https://releases.groupdocs.com/parser/net/).

## استيراد مساحات الأسماء
أولاً، ابدأ باستيراد مساحات الأسماء الضرورية إلى مشروع C# الخاص بك.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## الخطوة 1: إنشاء مثيل لفئة المحلل اللغوي
 ابدأ بإنشاء مثيل لـ`Parser` فئة من خلال توفير المسار إلى ملف العينة الخاص بك.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // سوف يذهب الرمز هنا
}
```
## الخطوة 2: التحقق من دعم استخراج النص المنسق
قبل متابعة استخراج النص، تحقق مما إذا كان المستند يدعم استخراج النص المنسق.
```csharp
if (!parser.Features.FormattedText)
{
    Console.WriteLine("Document does not support formatted text extraction.");
    return;
}
```
## الخطوة 3: الحصول على معلومات المستند
استرجاع معلومات حول المستند، مثل عدد الصفحات.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## الخطوة 4: التكرار على صفحات المستند واستخراج النص المنسق
قم بالتكرار خلال كل صفحة من المستند واستخرج النص المنسق باستخدام خيارات محددة (على سبيل المثال، تنسيق Markdown).
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    
    using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Markdown)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## خاتمة
الآن أنت تعرف كيفية استخراج النص المنسق من صفحات المستندات باستخدام GroupDocs.Parser لـ .NET. توفر هذه المكتبة حلاً قويًا وسهل الاستخدام لاستخراج النص من تنسيقات الملفات المختلفة.

## الأسئلة الشائعة
### هل يستطيع GroupDocs.Parser التعامل مع تنسيقات الملفات المختلفة؟
نعم، يدعم GroupDocs.Parser مجموعة واسعة من تنسيقات المستندات، بما في ذلك PDF وDOCX وXLSX وPPTX والمزيد.
### هل GroupDocs.Parser متوافق مع .NET Core؟
نعم، يدعم GroupDocs.Parser .NET Core و.NET Framework.
### هل يحافظ GroupDocs.Parser على تنسيق النص أثناء الاستخراج؟
نعم، يمكن لـ GroupDocs.Parser الاحتفاظ بالتنسيق مثل الأنماط والخطوط عند استخراج النص.
### هل يمكنني استخراج الصور والبيانات التعريفية باستخدام GroupDocs.Parser؟
نعم، يسمح GroupDocs.Parser باستخراج الصور وبيانات التعريف والنص من المستندات.
### كيف يمكنني الحصول على الدعم لـ GroupDocs.Parser؟
 يمكنك الحصول على الدعم من[منتدى GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).