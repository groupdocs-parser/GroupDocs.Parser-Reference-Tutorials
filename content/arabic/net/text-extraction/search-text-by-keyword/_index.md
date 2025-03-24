---
title: بحث النص عن طريق الكلمة الرئيسية
linktitle: بحث النص عن طريق الكلمة الرئيسية
second_title: GroupDocs.Parser .NET API
description: تعرف على كيفية البحث عن النص باستخدام الكلمة الرئيسية في المستندات باستخدام GroupDocs.Parser لـ .NET. استخراج المحتوى ذي الصلة بكفاءة وبسهولة.
weight: 21
url: /ar/net/text-extraction/search-text-by-keyword/
---

# بحث النص عن طريق الكلمة الرئيسية

## مقدمة
في هذا البرنامج التعليمي، سوف نتعمق في استخدام GroupDocs.Parser لـ .NET للبحث عن النص حسب الكلمة الرئيسية داخل المستندات. GroupDocs.Parser هي مكتبة قوية تمكن المطورين من استخراج النصوص وبيانات التعريف والمعلومات الأخرى من تنسيقات الملفات المختلفة، مثل ملفات PDF ومستندات Microsoft Office والمزيد. يمكن أن يكون البحث عن كلمات رئيسية محددة داخل هذه المستندات أمرًا ضروريًا للتطبيقات التي تتعامل مع كميات كبيرة من البيانات النصية.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك الإعداد التالي:
1. بيئة التطوير: Visual Studio أو أي برنامج .NET IDE مفضل.
2.  GroupDocs.Parser لـ .NET: قم بتنزيل المكتبة من[هنا](https://releases.groupdocs.com/parser/net/).
3. الوصول إلى نماذج الملفات: قم بإعداد ملف نموذجي (مثل PDF وDOCX) لاختبار وظيفة البحث عن الكلمات الرئيسية.

## استيراد مساحات الأسماء
أولاً، عليك تضمين مساحات الأسماء الضرورية في مشروعك.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## الخطوة 1: إنشاء مثيل لفئة المحلل اللغوي
 ابدأ بإنشاء مثيل لـ`Parser` class وقم بتوفير المسار إلى ملف العينة الخاص بك.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // ابحث عن كلمة رئيسية
    IEnumerable<SearchResult> searchResults = parser.Search("test");
    // التكرار على نتائج البحث
    foreach (SearchResult result in searchResults)
    {
        //قم بطباعة الفهرس والنص الذي تم العثور عليه
        Console.WriteLine($"At {result.Position}: {result.Text}");
    }
}
```
## الخطوة 2: البحث عن كلمة رئيسية
 في حدود`using` كتلة، اتصل ب`Search` الطريقة على`parser` كائن، وتمرير الكلمة الأساسية المطلوبة كوسيطة.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("test");
```
 يستبدل`"test"` بالكلمة الأساسية التي ترغب في البحث عنها داخل المستند.
## الخطوة 3: التكرار على نتائج البحث
 بعد ذلك، قم بالتكرار على نتائج البحث التي تم الحصول عليها من`Search` طريقة باستخدام أ`foreach` حلقة.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
 لكل`SearchResult` هدف`result` ، يمكنك الوصول إليه`Position` (الفهرس) و`Text` (النص الموجود).

## خاتمة
 في هذا البرنامج التعليمي، اكتشفنا كيفية استخدام GroupDocs.Parser لـ .NET للبحث عن النص حسب الكلمة الرئيسية داخل المستندات دون عناء. الاستفادة من`Search` طريقة`Parser` تسمح الفئة باسترجاع مقتطفات النص ذات الصلة بشكل فعال بناءً على مصطلحات بحث محددة.

## الأسئلة الشائعة
### هل GroupDocs.Parser متوافق مع تنسيقات المستندات المختلفة؟
نعم، يدعم GroupDocs.Parser مجموعة واسعة من تنسيقات الملفات، بما في ذلك PDF وDOCX وXLSX وPPTX والمزيد.
### هل يمكنني إجراء عمليات استخراج النص المتقدمة باستخدام GroupDocs.Parser؟
قطعاً! وبصرف النظر عن البحث عن النص، يتيح GroupDocs.Parser استخراج البيانات التعريفية واستخراج النص المنظم والمزيد.
### أين يمكنني العثور على وثائق مفصلة عن GroupDocs.Parser؟
استكشاف الوثائق الكاملة[هنا](https://tutorials.groupdocs.com/parser/net/).
### كيف يمكنني الحصول على الدعم أو المساعدة فيما يتعلق بالاستعلامات المتعلقة بـ GroupDocs.Parser؟
 قم بزيارة منتدى GroupDocs للحصول على الدعم والمناقشات[هنا](https://forum.groupdocs.com/c/parser/17).
### هل هناك نسخة تجريبية متاحة لتقييم GroupDocs.Parser قبل الشراء؟
 نعم، يمكنك الوصول إلى النسخة التجريبية المجانية[هنا](https://releases.groupdocs.com/).