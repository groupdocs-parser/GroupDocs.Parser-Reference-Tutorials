---
title: البحث عن نص في مستند Excel عن طريق التعبير العادي
linktitle: البحث عن نص في مستند Excel عن طريق التعبير العادي
second_title: GroupDocs.Parser .NET API
description: تعرف على كيفية البحث عن نص في مستندات Excel باستخدام التعبيرات العادية باستخدام GroupDocs.Parser لـ .NET. إجراء عمليات البحث النصية المتقدمة بكفاءة.
weight: 17
url: /ar/net/excel-document-processing/search-text-in-excel-document-by-regular-expression/
---
## مقدمة
في هذا البرنامج التعليمي، سوف نستكشف كيفية استخدام GroupDocs.Parser لـ .NET للبحث عن أنماط نصية محددة داخل مستندات Excel باستخدام التعبيرات العادية. GroupDocs.Parser هي مكتبة قوية تسمح للمطورين باستخراج النصوص وبيانات التعريف من تنسيقات المستندات المختلفة، بما في ذلك جداول البيانات مثل Excel. ومن خلال الاستفادة من التعبيرات العادية، يمكننا إجراء عمليات بحث نصية متقدمة بكفاءة.
## المتطلبات الأساسية
قبل البدء، تأكد من أن لديك الإعداد التالي:
1. Visual Studio: قم بتثبيت Visual Studio أو بيئة تطوير متكاملة أخرى متوافقة لتطوير .NET.
2.  GroupDocs.Parser لـ .NET: قم بتنزيل المكتبة وتثبيتها من[هنا](https://releases.groupdocs.com/parser/net/).
3. نموذج ملف Excel: قم بإعداد نموذج ملف Excel الذي يحتوي على النص الذي تريد البحث فيه.

## استيراد مساحات الأسماء
أولاً، قم بتضمين مساحات الأسماء اللازمة لاستخدام GroupDocs.Parser في مشروعك:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## الخطوة 1: إنشاء مثيل لفئة المحلل اللغوي
 ابدأ بإنشاء مثيل لـ`Parser` فئة، وتمرير المسار إلى مستند Excel الخاص بك كمعلمة.
```csharp
// إنشاء مثيل لفئة المحلل اللغوي
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // يستمر الكود هنا ...
}
```
## الخطوة 2: إجراء بحث التعبير العادي
 في حدود`using` كتلة، قم بإجراء بحث نصي باستخدام نمط التعبير العادي.
```csharp
//البحث باستخدام تعبير عادي مع مطابقة حالة الأحرف
IEnumerable<SearchResult> searchResults = parser.Search("\\sthe\\s", new SearchOptions(true, false, true));
```
- شرح نمط Regex:
  - `\\sthe\\s`: يبحث هذا النمط العادي عن الكلمة "the" (حساسة لحالة الأحرف) محاطة بمسافة بيضاء.
## الخطوة 3: التكرار على نتائج البحث
بعد ذلك، قم بالتكرار خلال نتائج البحث للوصول إلى كل تكرار مطابق.
```csharp
// التكرار على نتائج البحث
foreach (SearchResult result in searchResults)
{
    // طباعة الموقف والنص الموجود
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
- انتاج:
  - ستقوم هذه الحلقة بطباعة كل تكرار لنمط النص المحدد مع موضعه داخل المستند.

## خاتمة
في هذا البرنامج التعليمي، تعلمنا كيفية استخدام GroupDocs.Parser لـ .NET لإجراء بحث تعبير عادي داخل مستندات Excel. باتباع هذه الخطوات، يمكنك دمج إمكانيات البحث عن النص المتقدمة في تطبيقات .NET الخاصة بك بكفاءة.

## الأسئلة الشائعة
### هل يستطيع GroupDocs.Parser استخراج البيانات من تنسيقات المستندات الأخرى إلى جانب Excel؟
نعم، يدعم GroupDocs.Parser تنسيقات المستندات المختلفة، بما في ذلك Word وPDF وPowerPoint والمزيد.
### هل هناك نسخة تجريبية مجانية متاحة لـ GroupDocs.Parser؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية من[هنا](https://releases.groupdocs.com/).
### أين يمكنني العثور على الدعم أو طرح الأسئلة حول GroupDocs.Parser؟
 قم بزيارة[منتدى GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17)للدعم والمناقشات.
### كيف يمكنني شراء ترخيص GroupDocs.Parser؟
 يمكنك شراء ترخيص من[هنا](https://purchase.groupdocs.com/buy).
### هل يمكنني الحصول على ترخيص مؤقت لأغراض الاختبار؟
 نعم، يمكنك الحصول على ترخيص مؤقت[هنا](https://purchase.groupdocs.com/temporary-license/).