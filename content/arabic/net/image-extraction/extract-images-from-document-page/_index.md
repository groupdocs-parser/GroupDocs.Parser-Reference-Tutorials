---
title: استخراج الصور من صفحة الوثيقة
linktitle: استخراج الصور من صفحة الوثيقة
second_title: GroupDocs.Parser .NET API
description: تعرف على كيفية استخراج الصور من المستندات باستخدام GroupDocs.Parser لـ .NET. تعزيز قدرات معالجة المستندات الخاصة بك.
weight: 12
url: /ar/net/image-extraction/extract-images-from-document-page/
---
## مقدمة
في هذا البرنامج التعليمي، سوف نتعلم كيفية استخراج الصور من صفحة المستند باستخدام GroupDocs.Parser لـ .NET. GroupDocs.Parser هي مكتبة قوية تسمح لك باستخراج النصوص وبيانات التعريف والصور والمزيد من تنسيقات المستندات المختلفة مثل PDF وMicrosoft Word وExcel وPowerPoint وغيرها. سنتعرف على الخطوات اللازمة لاستخراج الصور من صفحة المستند باستخدام هذه المكتبة.
## المتطلبات الأساسية
قبل أن تبدأ، تأكد من أن لديك ما يلي:
- تم تثبيت Visual Studio على جهازك.
- الفهم الأساسي لبرمجة C# و.NET.
- تم تثبيت GroupDocs.Parser لمكتبة .NET. يمكنك تنزيله من[هنا](https://releases.groupdocs.com/parser/net/).

## استيراد مساحات الأسماء
ابدأ باستيراد مساحات الأسماء الضرورية في مشروع C# الخاص بك للاستفادة من وظائف GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## الخطوة 1: إنشاء مثيل لفئة المحلل اللغوي
 ابدأ بإنشاء مثيل لـ`Parser` class وحدد المسار إلى مستند العينة الخاص بك.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // الرمز الخاص بك هنا
}
```
## الخطوة 2: التحقق من المستند لدعم استخراج الصور
 بعد ذلك، تحقق مما إذا كان المستند يدعم استخراج الصور باستخدام الملف`Features.Images` ملكية.
```csharp
if (!parser.Features.Images)
{
    Console.WriteLine("Document doesn't support image extraction.");
    return;
}
```
## الخطوة 3: الحصول على معلومات المستند
 احصل على معلومات حول المستند باستخدام`GetDocumentInfo()` طريقة.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## الخطوة 4: التكرار على صفحات المستند
تحقق مما إذا كان المستند يحتوي على صفحات، ثم قم بالتكرار على كل صفحة لاستخراج الصور.
```csharp
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // الكود الخاص بك لاستخراج الصور من الصفحة
}
```
## الخطوة 5: استخراج الصور من كل صفحة
 ضمن حلقة تكرار الصفحة، استخدم`GetImages(pageIndex)` طريقة استرجاع الصور من كل صفحة.
```csharp
foreach (PageImageArea image in parser.GetImages(pageIndex))
{
    Console.WriteLine($"Rectangle: {image.Rectangle}, FileType: {image.FileType}");
    // رمز إضافي لحفظ الصورة أو معالجتها
}
```

## خاتمة
في هذا البرنامج التعليمي، اكتشفنا كيفية استخراج الصور من صفحة المستند باستخدام GroupDocs.Parser لـ .NET. لقد قمنا بتغطية الخطوات الأساسية مثل إنشاء مثيل محلل، والتحقق من دعم استخراج الصور، واسترداد معلومات المستند، والتكرار على الصفحات، واستخراج الصور من كل صفحة. الآن، يمكنك دمج وظيفة استخراج الصور في تطبيقات .NET الخاصة بك بكفاءة.

## الأسئلة الشائعة
### هل يستطيع GroupDocs.Parser استخراج الصور من مستندات PDF؟
نعم، يدعم GroupDocs.Parser استخراج الصور من تنسيقات المستندات المختلفة بما في ذلك PDF.
### هل GroupDocs.Parser مناسب لمعالجة المستندات دفعة واحدة؟
قطعاً! يمكنك استخدام GroupDocs.Parser لمعالجة مستندات متعددة واستخراج المحتوى المطلوب بكفاءة.
### أين يمكنني العثور على المزيد من الموارد والدعم لـ GroupDocs.Parser؟
 يمكنك زيارة[منتدى GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) لدعم المجتمع والمناقشات.
### هل يمكنني تجربة GroupDocs.Parser قبل الشراء؟
 نعم يمكنك الحصول على[نسخة تجريبية مجانية](https://releases.groupdocs.com/) لتقييم إمكانيات المكتبة.
### كيف يمكنني الحصول على ترخيص مؤقت لـ GroupDocs.Parser؟
 يمكنك الحصول على[ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/) لأغراض الاختبار والتطوير.