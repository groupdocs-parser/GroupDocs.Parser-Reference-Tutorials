---
title: البحث في النص مع النقاط البارزة
linktitle: البحث في النص مع النقاط البارزة
second_title: GroupDocs.Parser .NET API
description: تعرف على كيفية البحث عن النص وتمييزه في المستندات باستخدام GroupDocs.Parser لـ .NET. استخراج رؤى قيمة بكفاءة.
weight: 24
url: /ar/net/text-extraction/search-text-with-highlights/
---

# البحث في النص مع النقاط البارزة

## مقدمة
في هذا البرنامج التعليمي، سوف نستكشف كيفية استخدام GroupDocs.Parser لـ .NET للبحث عن نص داخل مستند وتمييز نتائج البحث. GroupDocs.Parser هي مكتبة قوية تتيح لك العمل مع تنسيقات المستندات المختلفة واستخراج النص وبيانات التعريف والمزيد.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك ما يلي:
1.  GroupDocs.Parser لـ .NET: قم بتنزيل المكتبة وتثبيتها من[هنا](https://releases.groupdocs.com/parser/net/).
2. IDE: استخدم Visual Studio أو أي IDE مفضل لتطوير .NET.
3. ملف نموذجي: قم بإعداد مستند نموذجي (على سبيل المثال، PDF، DOCX) للبحث عن النص.

## استيراد مساحات الأسماء
أولاً، ابدأ باستيراد مساحات الأسماء الضرورية في مشروع .NET الخاص بك:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## الخطوة 1: إنشاء مثيل المحلل اللغوي
 ابدأ بإنشاء مثيل لـ`Parser` فئة مع المسار إلى ملف العينة الخاص بك:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // الرمز الخاص بك هنا
}
```
## الخطوة 2: تحديد خيارات التمييز
 حدد ال`HighlightOptions` لتكوين كيفية إبراز نتائج البحث. على سبيل المثال، تعيين نافذة سياق مكونة من 15 حرفًا:
```csharp
HighlightOptions highlightOptions = new HighlightOptions(15);
```
## الخطوة 3: البحث عن النص
الآن، قم بإجراء بحث نصي داخل المستند. قم بتوفير الكلمة الأساسية التي تريد البحث عنها (على سبيل المثال، "lorem"):
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("lorem", new SearchOptions(true, false, false, highlightOptions));
```
## الخطوة 4: معالجة نتائج البحث
كرر نتائج البحث واعرض النص الذي تم العثور عليه مع النقاط البارزة:
```csharp
if (searchResults != null)
{
    foreach (SearchResult result in searchResults)
    {
        Console.WriteLine($"{result.LeftHighlightItem.Text}{result.Text}{result.RightHighlightItem.Text}");
    }
}
else
{
    Console.WriteLine("Search isn't supported");
}
```

## خاتمة
في هذا البرنامج التعليمي، تعلمت كيفية استخدام GroupDocs.Parser لـ .NET للبحث عن نص داخل المستندات وتمييز نتائج البحث. يمكن أن تكون هذه الوظيفة مفيدة جدًا لاستخراج النص وتحليله في تطبيقات .NET الخاصة بك.

## الأسئلة الشائعة
### هل GroupDocs.Parser مناسب لمعالجة تنسيقات المستندات المختلفة؟
نعم، يدعم GroupDocs.Parser مجموعة واسعة من تنسيقات المستندات بما في ذلك PDF وDOCX وXLSX وPPTX والمزيد.
### هل يمكنني استخدام GroupDocs.Parser لاستخراج بيانات التعريف من المستندات؟
قطعاً! يسمح لك GroupDocs.Parser باستخراج بيانات التعريف والنص والبيانات المنظمة من المستندات.
### أين يمكنني العثور على الدعم أو طرح الأسئلة حول GroupDocs.Parser؟
 يمكنك زيارة[منتدى GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) لأية استفسارات متعلقة بالدعم.
### هل هناك نسخة تجريبية مجانية متاحة لـ GroupDocs.Parser؟
 نعم يمكنك الوصول إلى[تجربة مجانية](https://releases.groupdocs.com/) من GroupDocs.Parser لتقييم ميزاته.
### كيف يمكنني شراء ترخيص GroupDocs.Parser؟
 يمكنك شراء ترخيص من[هنا](https://purchase.groupdocs.com/buy) وكذلك الحصول على تراخيص مؤقتة[هنا](https://purchase.groupdocs.com/temporary-license/).