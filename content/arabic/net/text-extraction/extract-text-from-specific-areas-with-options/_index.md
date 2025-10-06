---
title: استخراج النص من مناطق محددة مع الخيارات
linktitle: استخراج النص من مناطق محددة مع الخيارات
second_title: GroupDocs.Parser .NET API
description: تعرف على كيفية استخراج النص من مناطق معينة في المستندات باستخدام GroupDocs.Parser لـ .NET. استكشف خيارات استخراج النص المتقدمة باستخدام هذا البرنامج التعليمي.
weight: 14
url: /ar/net/text-extraction/extract-text-from-specific-areas-with-options/
type: docs
---
# استخراج النص من مناطق محددة مع الخيارات

## مقدمة
في هذا البرنامج التعليمي، سوف نستكشف كيفية استخدام GroupDocs.Parser لـ .NET لاستخراج النص من مناطق محددة داخل المستند باستخدام خيارات قابلة للتخصيص. GroupDocs.Parser هي مكتبة قوية تمكن المطورين من تحليل النص واستخراجه من تنسيقات المستندات المختلفة دون عناء.
## المتطلبات الأساسية
قبل أن نتعمق في عملية الترميز، تأكد من أن لديك ما يلي:
1. بيئة التطوير: قم بتثبيت Visual Studio أو أي بيئة تطوير IDE أخرى.
2.  مكتبة GroupDocs.Parser: قم بتنزيل وتثبيت GroupDocs.Parser لـ .NET من[هنا](https://releases.groupdocs.com/parser/net/).
3. ملف نموذجي: قم بإعداد مستند نموذجي (على سبيل المثال، PDF، DOCX، وما إلى ذلك) لاستخراج النص منه.

## استيراد مساحات الأسماء
أولاً، ستحتاج إلى استيراد مساحات الأسماء الضرورية للوصول إلى فئات وأساليب GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## الخطوة 1: إنشاء مثيل لفئة المحلل اللغوي
 تهيئة مثيل لـ`Parser` فئة من خلال توفير المسار إلى ملف العينة الخاص بك.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // سيتم وضع رمز استخراج منطقة النص هنا
}
```
## الخطوة 2: تحديد خيارات استخراج منطقة النص
 يخلق`PageTextAreaOptions` تحديد معايير استخراج النص.
```csharp
PageTextAreaOptions options = new PageTextAreaOptions("\\s[a-z]{2}\\s", new Rectangle(new Point(0, 0), new Size(300, 100)));
```
في هذا المثال:
- `"\\s[a-z]{2}\\s"` هو نمط تعبير عادي لمطابقة مناطق النص التي تحتوي على أحرف صغيرة فقط.
- `new Rectangle(new Point(0, 0), new Size(300, 100))` يحدد المستطيل (الموضع والحجم) على الصفحة التي سيتم استخراج النص منها.
## الخطوة 3: استخراج مناطق النص
استخدم الخيارات المحددة لاستخراج مناطق النص التي تلبي المعايير المحددة.
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## الخطوة 4: التحقق والتكرار على مناطق النص المستخرجة
تحقق مما إذا كان استخراج منطقة النص مدعومًا ثم كرر ذلك على المناطق المستخرجة.
```csharp
if (areas == null)
{
    Console.WriteLine("Page text areas extraction isn't supported");
    return;
}
foreach (PageTextArea a in areas)
{
    Console.WriteLine(string.Format("Page: {0}, R: {1}, Text: {2}", a.Page.Index, a.Rectangle, a.Text));
}
```

## خاتمة
في هذا البرنامج التعليمي، تناولنا كيفية استخراج النص من مناطق محددة داخل المستند باستخدام GroupDocs.Parser لـ .NET. توفر هذه المكتبة إمكانات واسعة النطاق لتحليل تنسيقات المستندات المختلفة، مما يجعلها أداة قيمة لمهام استخراج النص.

## الأسئلة الشائعة
### هل يمكن لـ GroupDocs.Parser استخراج النص من المستندات الممسوحة ضوئيًا؟
نعم، يدعم GroupDocs.Parser استخراج النص المستند إلى OCR للمستندات الممسوحة ضوئيًا.
### هل GroupDocs.Parser متوافق مع تنسيقات المستندات المتعددة؟
نعم، يمكنه تحليل النص واستخراجه من تنسيقات PDF وDOCX وXLSX وPPTX وغيرها من التنسيقات الشائعة.
### هل يوفر GroupDocs.Parser الدعم لـ .NET Core؟
نعم، GroupDocs.Parser متوافق مع .NET Core بالإضافة إلى .NET Framework.
### هل يمكنني استخراج بيانات التعريف مع النص باستخدام GroupDocs.Parser؟
نعم، يمكنك استخراج كل من المحتوى النصي والبيانات الوصفية من المستندات.
### هل هناك نسخة تجريبية متاحة لـ GroupDocs.Parser؟
 نعم، يمكنك الحصول على نسخة تجريبية مجانية من[هنا](https://releases.groupdocs.com/).