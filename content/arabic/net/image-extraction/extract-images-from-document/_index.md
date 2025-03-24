---
title: استخراج الصور من الوثيقة
linktitle: استخراج الصور من الوثيقة
second_title: GroupDocs.Parser .NET API
description: قم باستخراج الصور من المستندات بسهولة باستخدام GroupDocs.Parser لـ .NET. قدرات معالجة المستندات لديك وتبسيط مهام استخراج الصور بكفاءة.
weight: 11
url: /ar/net/image-extraction/extract-images-from-document/
---

# استخراج الصور من الوثيقة

## مقدمة
في هذا البرنامج التعليمي، سنستكشف كيفية استخراج الصور من المستندات باستخدام GroupDocs.Parser لـ .NET. GroupDocs.Parser هي مكتبة قوية تمكن المطورين من استخراج النصوص وبيانات التعريف والصور والمزيد من تنسيقات المستندات المختلفة.
## المتطلبات الأساسية
قبل البدء، تأكد من إعداد المتطلبات الأساسية التالية:
- Visual Studio: قم بتثبيت Visual Studio على جهازك.
-  GroupDocs.Parser لـ .NET: قم بتنزيل وتثبيت GroupDocs.Parser من[صفحة التحميل](https://releases.groupdocs.com/parser/net/).
- نموذج مستند: قم بإعداد نموذج مستند (PDF، DOCX، إلخ) الذي تريد استخراج الصور منه.

## استيراد مساحات الأسماء
ابدأ باستيراد مساحات الأسماء الضرورية في مشروع C# الخاص بك:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## الخطوة 1: إنشاء مثيل لفئة المحلل اللغوي
 أولاً، قم بإنشاء مثيل لـ`Parser` فئة عن طريق توفير المسار إلى نموذج المستند الخاص بك.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // الكود الخاص بك يذهب هنا
}
```
 يستبدل`"YourSampleFile.pdf"` مع المسار إلى ملف المستند الخاص بك.
## الخطوة 2: استخراج الصور من المستند
 بعد ذلك، قم باستخراج الصور من المستند باستخدام الملف`GetImages()` طريقة.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
 ال`GetImages()` تقوم الطريقة بإرجاع مجموعة من`PageImageArea` كائنات تمثل الصور الموجودة في المستند.
## الخطوة 3: التحقق من دعم استخراج الصور
قبل التكرار على الصور، تحقق مما إذا كان استخراج الصور مدعومًا للمستند.
```csharp
if (images == null)
{
    Console.WriteLine("Images extraction isn't supported");
    return;
}
```
تضمن هذه الخطوة أن المستند يحتوي على صور قابلة للاستخراج.
## الخطوة 4: التكرار على الصور المستخرجة
الآن، قم بالتكرار على الصور المستخرجة للوصول إلى معلومات مفصلة حول كل صورة، مثل فهرس الصفحة، وإحداثيات المستطيل، ونوع الصورة.
```csharp
foreach (PageImageArea image in images)
{
    Console.WriteLine($"Page: {image.Page.Index}, Rectangle: {image.Rectangle}, Type: {image.FileType}");
}
```
تقوم هذه الحلقة بطباعة معلومات حول كل صورة مستخرجة، بما في ذلك موقعها ونوعها.

## خاتمة
في هذا البرنامج التعليمي، تعلمنا كيفية استخدام GroupDocs.Parser لـ .NET لاستخراج الصور من المستندات برمجيًا. باتباع هذه الخطوات، يمكنك دمج وظيفة استخراج صور المستندات في تطبيقات .NET الخاصة بك بسلاسة.

## الأسئلة الشائعة
### هل يستطيع GroupDocs.Parser استخراج الصور من كافة تنسيقات المستندات؟
يدعم GroupDocs.Parser استخراج الصور من تنسيقات مختلفة، بما في ذلك PDF وDOCX وXLSX والمزيد.
### هل هناك نسخة تجريبية مجانية متاحة لـ GroupDocs.Parser؟
 نعم، يمكنك الوصول إلى النسخة التجريبية المجانية من GroupDocs.Parser من[موقع إلكتروني](https://releases.groupdocs.com/).
### أين يمكنني العثور على وثائق GroupDocs.Parser؟
 يمكن العثور على الوثائق التفصيلية لـ GroupDocs.Parser[هنا](https://tutorials.groupdocs.com/parser/net/).
### كيف يمكنني الحصول على ترخيص مؤقت لـ GroupDocs.Parser؟
 يمكنك الحصول على ترخيص مؤقت من[صفحة الترخيص المؤقتة](https://purchase.groupdocs.com/temporary-license/).
### أين يمكنني الحصول على الدعم لـ GroupDocs.Parser؟
 للحصول على الدعم الفني والمساعدة، قم بزيارة[منتدى GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).