---
title: استخراج النص حسب عنصر جدول المحتويات (TOC).
linktitle: استخراج النص حسب عنصر جدول المحتويات (TOC).
second_title: GroupDocs.Parser .NET API
description: قم باستخراج النص حسب جدول المحتويات (TOC) باستخدام GroupDocs.Parser لـ .NET. تعلم تقنيات تحليل المستندات الفعالة لاستخراج البيانات المنظمة.
weight: 15
url: /ar/net/text-extraction/extract-text-by-toc-item/
---
## مقدمة
في هذا البرنامج التعليمي، سوف نستكشف كيفية استخدام GroupDocs.Parser لـ .NET لاستخراج النص بناءً على عناصر جدول المحتويات (TOC) من المستندات. GroupDocs.Parser هي أداة قوية تسمح بتحليل المستندات واستخراجها بكفاءة.
## المتطلبات الأساسية
قبل متابعة هذا البرنامج التعليمي، تأكد من أن لديك المتطلبات الأساسية التالية:
1. Visual Studio: قم بتثبيت Visual Studio IDE على نظامك.
2.  GroupDocs.Parser لـ .NET: قم بتنزيل وتثبيت GroupDocs.Parser لـ .NET من[هنا](https://releases.groupdocs.com/parser/net/).
3. نموذج مستند مع TOC: قم بإعداد مستند (على سبيل المثال، PDF، DOCX) يحتوي على جدول المحتويات.

## استيراد مساحات الأسماء
أولاً، قم بتضمين مساحات الأسماء الضرورية في مشروع C# الخاص بك:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## الخطوة 1: إنشاء مثيل لفئة المحلل اللغوي
 إنشاء مثيل`Parser` فئة مع المسار إلى نموذج المستند الخاص بك:
```csharp
using (Parser parser = new Parser("YourSampleFileWithToc"))
{
    // تابع الخطوات التالية هنا...
}
```
## الخطوة 2: استخراج جدول المحتويات (TOC)
احصل على عناصر جدول المحتويات (TOC) من المستند:
```csharp
IEnumerable<TocItem> tocItems = parser.GetToc();
if (tocItems == null)
{
    Console.WriteLine("Table of contents extraction isn't supported");
    return;
}
```
## الخطوة 3: التكرار على عناصر جدول المحتويات واستخراج النص
قم بالتكرار خلال كل عنصر من عناصر جدول المحتويات واستخرج النص المقابل:
```csharp
foreach (TocItem tocItem in tocItems)
{
    using (TextReader reader = tocItem.ExtractText())
    {
        Console.WriteLine("----");
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## خاتمة
لقد أوضح هذا البرنامج التعليمي كيفية استخراج النص من مستند استنادًا إلى عناصر جدول المحتويات (TOC) باستخدام GroupDocs.Parser لـ .NET. باتباع الخطوات الموضحة، يمكنك تحليل محتوى محدد واستخراجه من مستنداتك بشكل برمجي.

## الأسئلة الشائعة
### ما هي تنسيقات الملفات التي يدعمها GroupDocs.Parser؟
يدعم GroupDocs.Parser مجموعة واسعة من تنسيقات المستندات، بما في ذلك PDF وMicrosoft Word (DOC/DOCX) وExcel (XLS/XLSX) وPowerPoint (PPT/PPTX) والمزيد.
### هل يمكنني استخراج البيانات المنظمة مثل الجداول أو الصور باستخدام GroupDocs.Parser؟
نعم، يوفر GroupDocs.Parser واجهات برمجة التطبيقات لاستخراج البيانات المنظمة مثل الجداول والصور وبيانات التعريف من أنواع المستندات المختلفة.
### هل GroupDocs.Parser مناسب للمستندات الكبيرة؟
تم تحسين GroupDocs.Parser للتعامل مع المستندات الكبيرة بكفاءة، مما يتيح الاستخراج السلس للمحتوى من الملفات الشاملة.
### كيف يمكنني الحصول على الدعم الفني لـ GroupDocs.Parser؟
 يمكنك طلب الدعم الفني والتفاعل مع المجتمع على[GroupDocs.منتدى المحلل](https://forum.groupdocs.com/c/parser/17).
### هل تقدم GroupDocs نسخة تجريبية مجانية للتقييم؟
نعم، يمكنك تنزيل نسخة تجريبية مجانية من GroupDocs.Parser من[هنا](https://releases.groupdocs.com/).