---
title: استخراج الارتباطات التشعبية من صفحة المستند
linktitle: استخراج الارتباطات التشعبية من صفحة المستند
second_title: GroupDocs.Parser .NET API
description: تعرف على كيفية استخراج الارتباطات التشعبية من المستندات باستخدام GroupDocs.Parser لـ .NET. دليل خطوة بخطوة لاستخراج الارتباط التشعبي في C#.
weight: 11
url: /ar/net/hyperlink-extraction/extract-hyperlinks-from-document-page/
---
## مقدمة
في هذا البرنامج التعليمي، سنستكشف كيفية استخدام GroupDocs.Parser لـ .NET لاستخراج الارتباطات التشعبية من المستندات خطوة بخطوة. GroupDocs.Parser هي مكتبة قوية تمكن المطورين من تحليل تنسيقات المستندات المختلفة واستخراج النص وبيانات التعريف والعناصر الأخرى.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك ما يلي:
- Visual Studio: قم بتثبيت Visual Studio على جهاز التطوير الخاص بك.
-  مكتبة GroupDocs.Parser: قم بتنزيل مكتبة GroupDocs.Parser والإشارة إليها. يمكنك الحصول عليه من[هنا](https://releases.groupdocs.com/parser/net/).
- نموذج مستند: قم بإعداد مستند نموذجي (على سبيل المثال، DOCX، PDF) يحتوي على ارتباطات تشعبية للاختبار.

## استيراد مساحات الأسماء
أولاً، قم بتضمين مساحات الأسماء اللازمة لاستخدام وظائف GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## الخطوة 1: إنشاء مثيل المحلل اللغوي
 إنشاء مثيل`Parser` class مع المسار إلى مستند العينة الخاص بك.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // الكود يذهب هنا...
}
```
## الخطوة 2: التحقق من دعم استخراج الارتباط التشعبي
تأكد من أن المستند يدعم استخراج الارتباط التشعبي قبل المتابعة.
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
## الخطوة 3: استرجاع معلومات الوثيقة
احصل على معلومات أساسية حول المستند وتحقق مما إذا كان يحتوي على صفحات.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## الخطوة 4: التكرار على صفحات المستند
قم بالتكرار خلال كل صفحة من المستند.
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // استخراج الارتباطات التشعبية من الصفحة الحالية
    IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks(pageIndex);
    // التكرار على الارتباطات التشعبية المستخرجة
    foreach (PageHyperlinkArea hyperlink in hyperlinks)
    {
        Console.WriteLine($"Hyperlink Text: {hyperlink.Text}");
        Console.WriteLine($"Hyperlink URL: {hyperlink.Url}");
        Console.WriteLine(); // سطر فارغ لسهولة القراءة
    }
}
```

## خاتمة
في هذا البرنامج التعليمي، قمنا بتغطية أساسيات استخدام GroupDocs.Parser لـ .NET لاستخراج الارتباطات التشعبية من المستندات. لقد تعلمت كيفية تهيئة المحلل اللغوي والتحقق من دعم الارتباط التشعبي واسترداد معلومات المستند والتكرار عبر صفحات المستند لاستخراج الارتباطات التشعبية بكفاءة.

## الأسئلة الشائعة
### هل يمكنني استخراج الارتباطات التشعبية من تنسيقات المستندات المختلفة؟
نعم، يدعم GroupDocs.Parser تنسيقات مختلفة مثل DOCX وPDF وPPTX وما إلى ذلك لاستخراج الارتباط التشعبي.
### هل من السهل دمج GroupDocs.Parser في تطبيقات .NET الموجودة؟
بالتأكيد، تم تصميم GroupDocs.Parser ليكون مباشرًا ويمكن دمجه بسهولة في مشاريع .NET الخاصة بك.
### هل يمكنني استخراج بيانات التعريف الأخرى مع الارتباطات التشعبية باستخدام GroupDocs.Parser؟
نعم، إلى جانب الارتباطات التشعبية، يمكنك استخراج النصوص والصور وبيانات التعريف من المستندات باستخدام هذه المكتبة.
### هل يتعامل GroupDocs.Parser مع المستندات المشفرة أو المحمية بكلمة مرور؟
يمكن لـ GroupDocs.Parser تحليل المستندات المحمية بكلمة مرور إذا تم توفير كلمة المرور.
### هل هناك نسخة تجريبية متاحة للاختبار قبل الشراء؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية[هنا](https://releases.groupdocs.com/).