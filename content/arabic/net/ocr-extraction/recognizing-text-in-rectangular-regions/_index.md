---
title: التعرف على النص في المناطق المستطيلة
linktitle: التعرف على النص في المناطق المستطيلة
second_title: GroupDocs.Parser .NET API
description: تعرف على كيفية التعرف على النص في مناطق معينة من المستندات باستخدام GroupDocs.Parser لـ .NET مع إمكانيات التعرف الضوئي على الحروف.
weight: 14
url: /ar/net/ocr-extraction/recognizing-text-in-rectangular-regions/
---
## مقدمة
في هذا البرنامج التعليمي، سوف نستكشف كيفية استخدام GroupDocs.Parser لـ .NET للتعرف على النص داخل مناطق مستطيلة محددة من المستندات. GroupDocs.Parser هي مكتبة قوية تسمح للمطورين باستخراج النصوص وبيانات التعريف والمزيد من تنسيقات الملفات المختلفة، بما في ذلك PDF وWord وExcel وPowerPoint.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك الإعداد التالي:
-  GroupDocs.Parser لـ .NET: قم بتنزيل المكتبة وتثبيتها من[هنا](https://releases.groupdocs.com/parser/net/).
- بيئة التطوير: Visual Studio أو أي برنامج .NET IDE آخر.
- مستند نموذجي: احصل على ملف نموذجي (على سبيل المثال، PDF، DOCX) يحتوي على نص ليتم التعرف عليه.

## استيراد مساحات الأسماء
أولاً، ستحتاج إلى استيراد مساحات الأسماء الضرورية إلى كود C# الخاص بك:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using System.Linq;
using System.Text;
using Aspose.OCR;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## الخطوة 1: تهيئة إعدادات المحلل اللغوي
 ابدأ بإعداد`ParserSettings` مع موصل التعرف الضوئي على الحروف. سنستخدم هنا موصل Aspose OCR الداخلي:
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## الخطوة 2: إنشاء مثيل المحلل اللغوي
 بعد ذلك، قم بإنشاء مثيل`Parser` فئة مع الإعدادات المحددة مسبقا:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // يستمر الكود هنا
}
```
 يستبدل`"YourSampleFile.pdf"` مع المسار إلى المستند الخاص بك.
## الخطوة 3: تحديد مستطيل التعرف الضوئي على الحروف
 حدد مستطيلاً داخل المستند حيث سيتم تنفيذ التعرف على النص. على سبيل المثال، مستطيل يبدأ بـ`(0, 0)` مع العرض`400` والارتفاع`200`:
```csharp
OcrOptions ocrOptions = new OcrOptions(new Data.Rectangle(0, 0, 400, 200));
```
## الخطوة 4: تكوين خيارات التعرف على النص
 يخلق`TextOptions` لتحديد استخدام التعرف الضوئي على الحروف (OCR) مع المستطيل المحدد:
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## الخطوة 5: استخراج النص باستخدام التعرف الضوئي على الحروف
 استخدم ال`GetText` طريقة`Parser` المثال مع تكوينه`TextOptions`:
```csharp
using (TextReader reader = parser.GetText(options))
{
    // اقرأ النص المستخرج أو تعامل مع حالة "غير مدعوم".
    Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
}
```

## خاتمة
في هذا البرنامج التعليمي، أوضحنا كيفية الاستفادة من GroupDocs.Parser لـ .NET لاستخراج النص من مناطق مستطيلة محددة في المستندات باستخدام OCR. يمكن تخصيص هذه العملية بشكل أكبر ودمجها في التطبيقات المختلفة لمهام استخراج النص الآلي.

## الأسئلة الشائعة
### هل يمكن لـ GroupDocs.Parser استخراج النص من المستندات الممسوحة ضوئيًا؟
نعم، يدعم GroupDocs.Parser OCR (التعرف البصري على الأحرف) لاستخراج النص من المستندات الممسوحة ضوئيًا.
### ما هي تنسيقات الملفات التي يدعمها GroupDocs.Parser؟
يدعم GroupDocs.Parser مجموعة واسعة من تنسيقات الملفات، بما في ذلك PDF وDOCX وXLSX وPPTX والمزيد.
### كيف يمكنني التعامل مع المستندات غير المدعومة لاستخراج النص؟
 يمكنك التحقق مما إذا كان استخراج النص مدعومًا باستخدام`TextReader` تم إرجاع المثيل بواسطة`parser.GetText(options)`.
### هل GroupDocs.Parser مناسب لمهام استخراج النصوص واسعة النطاق؟
نعم، تم تصميم GroupDocs.Parser للتعامل مع مهام استخراج النص واسعة النطاق بكفاءة.
### أين يمكنني الحصول على الدعم للمشكلات المتعلقة بـ GroupDocs.Parser؟
 للحصول على الدعم والمناقشات، قم بزيارة[منتدى GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).