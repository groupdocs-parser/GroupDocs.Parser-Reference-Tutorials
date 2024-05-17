---
title: استخراج الصور من مستند Excel
linktitle: استخراج الصور من مستند Excel
second_title: GroupDocs.Parser .NET API
description: تعرف على كيفية استخراج الصور من مستندات Excel باستخدام GroupDocs.Parser لـ .NET. دليل خطوة بخطوة مع أمثلة التعليمات البرمجية.
type: docs
weight: 10
url: /ar/net/excel-document-processing/extract-images-from-excel-document/
---
## مقدمة
ستتعلم في هذا البرنامج التعليمي كيفية استخراج الصور من مستند Excel باستخدام GroupDocs.Parser لـ .NET. GroupDocs.Parser هي مكتبة قوية تسمح لك بتحليل واستخراج النصوص وبيانات التعريف والصور من تنسيقات المستندات المختلفة بما في ذلك ملفات Excel.
## المتطلبات الأساسية
قبل البدء، تأكد من إعداد المتطلبات الأساسية التالية:
1. بيئة التطوير: قم بتثبيت Visual Studio أو أي بيئة تطوير .NET مفضلة.
2.  مكتبة GroupDocs.Parser: قم بتنزيل مكتبة GroupDocs.Parser والإشارة إليها. يمكنك الحصول على المكتبة من[هنا](https://releases.groupdocs.com/parser/net/).
3. نموذج ملف Excel: قم بإعداد نموذج ملف Excel الذي تريد استخراج الصور منه.
## استيراد مساحات الأسماء
قم بتضمين مساحات الأسماء الضرورية في مشروعك:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
اتبع هذه الخطوات لاستخراج الصور من مستند Excel:
## الخطوة 1: إنشاء مثيل لفئة المحلل اللغوي
 أولاً، قم بإنشاء مثيل لـ`Parser` فئة عن طريق توفير المسار إلى ملف Excel الخاص بك.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // الكود الخاص بك هنا...
}
```
## الخطوة 2: استرداد الصور من مستند Excel
 استخدم ال`GetImages()` طريقة استخراج الصور من ملف اكسيل.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## الخطوة 3: تحديد خيارات استخراج الصور
حدد تنسيق الصورة والخيارات الأخرى لحفظ الصور المستخرجة. على سبيل المثال، لحفظ الصور بتنسيق PNG:
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## الخطوة 4: تكرار الصور وحفظها
قم بالتكرار على الصور المستخرجة واحفظ كل صورة في ملف.
```csharp
int imageNumber = 0;
foreach (PageImageArea image in images)
{
    // احفظ الصورة في ملف PNG
    image.Save(imageNumber.ToString() + ".png", options);
    imageNumber++;
}
```
## خاتمة
لقد تعلمت في هذا البرنامج التعليمي كيفية استخدام GroupDocs.Parser لـ .NET لاستخراج الصور من مستند Excel. باتباع هذه الخطوات، يمكنك دمج إمكانيات استخراج الصور في تطبيقات .NET الخاصة بك بكفاءة.

## الأسئلة الشائعة
### س: هل يمكن لـ GroupDocs.Parser استخراج الصور من تنسيقات المستندات الأخرى إلى جانب Excel؟
ج: نعم، يدعم GroupDocs.Parser مجموعة واسعة من تنسيقات المستندات بما في ذلك Word وPowerPoint وPDF والمزيد.
### س: كيف يمكنني الحصول على الدعم أو المساعدة فيما يتعلق بتكامل GroupDocs.Parser؟
 ج: للحصول على الدعم والمساعدة، قم بزيارة[منتدى GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).
### س: هل GroupDocs.Parser مجاني للاستخدام؟
 ج: يقدم GroupDocs.Parser نسخة تجريبية مجانية، ولكن لمواصلة الاستخدام، قد تحتاج إلى شراء ترخيص. افحص ال[التسعير والترخيص](https://purchase.groupdocs.com/buy)تفاصيل.
### س: هل يمكنني تجربة GroupDocs.Parser قبل شراء الترخيص؟
 ج: نعم، يمكنك الحصول على[تجربة مجانية](https://releases.groupdocs.com/) لتقييم GroupDocs.Parser.
### س: أين يمكنني العثور على الوثائق التفصيلية الخاصة بـ GroupDocs.Parser؟
 ج: راجع الشامل[توثيق](https://reference.groupdocs.com/parser/net/) للحصول على معلومات مفصلة حول استخدام GroupDocs.Parser.