---
title: استخراج الرموز الشريطية من المستند مع الخيارات
linktitle: استخراج الرموز الشريطية من المستند مع الخيارات
second_title: GroupDocs.Parser .NET API
description: تعرف على كيفية استخراج الرموز الشريطية من المستندات باستخدام GroupDocs.Parser لـ .NET. برنامج تعليمي شامل مع أمثلة التعليمات البرمجية والأسئلة الشائعة.
weight: 14
url: /ar/net/barcode-extraction/extract-barcodes-from-document-with-options/
type: docs
---
# استخراج الرموز الشريطية من المستند مع الخيارات

## مقدمة
في هذا البرنامج التعليمي، سنتعرف على عملية استخراج الرموز الشريطية من مستند باستخدام GroupDocs.Parser لـ .NET. GroupDocs.Parser هي مكتبة قوية تسمح لك باستخراج النصوص وبيانات التعريف والرموز الشريطية من تنسيقات المستندات المختلفة مثل PDF وMicrosoft Word وExcel والمزيد.
## المتطلبات الأساسية
قبل البدء، تأكد من توفر المتطلبات الأساسية التالية:
1. بيئة التطوير: تأكد من تثبيت Visual Studio على جهازك.
2.  مكتبة GroupDocs.Parser: قم بتنزيل وتثبيت GroupDocs.Parser لمكتبة .NET من[هنا](https://releases.groupdocs.com/parser/net/).
3. نموذج مستند: قم بإعداد مستند نموذجي (على سبيل المثال، PDF، DOCX) يحتوي على رموز شريطية لاستخراجها.

## استيراد مساحات الأسماء
أولاً، تحتاج إلى استيراد مساحات الأسماء الضرورية إلى مشروع C# الخاص بك للاستفادة من وظائف GroupDocs.Parser.
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using System;
using System.Collections.Generic;
```
## الخطوة 1: إنشاء مثيل لفئة المحلل اللغوي
 للبدء، قم بإنشاء مثيل لـ`Parser` class عن طريق تمرير المسار إلى نموذج المستند الخاص بك.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // الكود المراد إضافته في الخطوات التالية
}
```
## الخطوة 2: التحقق من دعم استخراج الباركود
 بعد ذلك، تحقق مما إذا كان المستند يدعم استخراج الرمز الشريطي باستخدام الملف`Features` ملكية`Parser` مثال.
```csharp
if (!parser.Features.Barcodes)
{
    Console.WriteLine("Document doesn't support barcode extraction.");
    return;
}
```
## الخطوة 3: تحديد خيارات استخراج الباركود
 الآن قم بتحديد خيارات استخراج الباركود باستخدام`BarcodeOptions`. يمكنك تعيين معلمات مثل أوضاع الجودة وأنواع الباركود.
```csharp
BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```
## الخطوة 4: استخراج الرموز الشريطية من المستند
 استخدم ال`GetBarcodes` طريقة`Parser` فئة لاستخراج الرموز الشريطية بناءً على الخيارات المحددة.
```csharp
IEnumerable<PageBarcodeArea> barcodes = parser.GetBarcodes(options);
```
## الخطوة 5: تكرار وعرض الرموز الشريطية المستخرجة
وأخيرًا، قم بالتكرار عبر الرموز الشريطية المستخرجة وعرض فهرس الصفحات وقيمها.
```csharp
foreach (PageBarcodeArea barcode in barcodes)
{
    Console.WriteLine("Page: " + barcode.Page.Index.ToString());
    Console.WriteLine("Value: " + barcode.Value);
}
```

## خاتمة
 في هذا البرنامج التعليمي، تعلمنا كيفية استخراج الرموز الشريطية من مستند باستخدام GroupDocs.Parser لـ .NET. تتضمن هذه العملية إنشاء ملف`Parser` على سبيل المثال، تحديد خيارات الاستخراج، والتكرار من خلال الرموز الشريطية المستخرجة. يعمل GroupDocs.Parser على تبسيط مهمة استخراج الرمز الشريطي من تنسيقات المستندات المختلفة، مما يتيح معالجة المستندات بكفاءة داخل تطبيقات .NET الخاصة بك.

## الأسئلة الشائعة
### هل يستطيع GroupDocs.Parser استخراج الرموز الشريطية من مستندات PDF؟
نعم، يدعم GroupDocs.Parser استخراج الرمز الشريطي من مستندات PDF إلى جانب التنسيقات الأخرى مثل DOCX وXLSX وما إلى ذلك.
### ما هي أنواع الرموز الشريطية التي يدعمها GroupDocs.Parser؟
يدعم GroupDocs.Parser أنواعًا مختلفة من الرموز الشريطية بما في ذلك رموز QR وCode 39 وCode 128 والمزيد.
### هل يحتاج GroupDocs.Parser إلى ترخيص للاستخدام التجاري؟
 نعم، مطلوب ترخيص ساري المفعول للاستخدام التجاري. يمكنك الحصول على ترخيص من[هنا](https://purchase.groupdocs.com/buy).
### هل GroupDocs.Parser مناسب لمعالجة المستندات دفعة واحدة؟
نعم، يمكن لـ GroupDocs.Parser التعامل بكفاءة مع المعالجة المجمعة للمستندات لاستخراج النص، واسترجاع بيانات التعريف، واستخراج الرمز الشريطي.
### أين يمكنني العثور على الدعم الفني لـ GroupDocs.Parser؟
 يمكنك الحصول على الدعم الفني أو طرح الأسئلة على[منتدى مستندات المجموعة](https://forum.groupdocs.com/c/parser/17).