---
title: البحث عن نص في مستند Word عن طريق الكلمة الأساسية
linktitle: البحث عن نص في مستند Word عن طريق الكلمة الأساسية
second_title: GroupDocs.Parser .NET API
description: تعرف على كيفية البحث عن نص في مستندات Word باستخدام GroupDocs.Parser لـ .NET. استخراج كلمات رئيسية محددة بكفاءة.
type: docs
weight: 18
url: /ar/net/word-document-processing/search-text-in-word-document-by-keyword/
---
## مقدمة
في هذا البرنامج التعليمي، سوف نستكشف كيفية استخدام GroupDocs.Parser لـ .NET للبحث عن نص محدد داخل مستند Word باستخدام C#. GroupDocs.Parser هي مكتبة قوية تسمح للمطورين باستخراج النصوص وبيانات التعريف من تنسيقات المستندات المختلفة، بما في ذلك مستندات Word.
## المتطلبات الأساسية
قبل البدء، تأكد من توفر المتطلبات الأساسية التالية:
1. بيئة التطوير: قم بتثبيت Visual Studio أو بيئة تطوير متكاملة أخرى متوافقة.
2.  مكتبة GroupDocs.Parser: قم بتنزيل وتثبيت GroupDocs.Parser لمكتبة .NET من[موقع إلكتروني](https://releases.groupdocs.com/parser/net/).
3. نموذج مستند Word: قم بإعداد نموذج مستند Word لاستخدامه في البحث عن النص.

## استيراد مساحات الأسماء
ابدأ باستيراد مساحات الأسماء الضرورية في مشروع C# الخاص بك:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## الخطوة 1: إنشاء مثيل لفئة المحلل اللغوي
 أولاً، قم بإنشاء مثيل لـ`Parser` فئة عن طريق تمرير المسار إلى مستند Word النموذجي الخاص بك.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // الكود يذهب هنا
}
```
## الخطوة 2: البحث عن كلمة رئيسية
 بعد ذلك، استخدم`Search` طريقة`Parser` class للبحث عن كلمة رئيسية محددة داخل المستند.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword");
```
 يستبدل`"keyword"` بالنص الذي تريد البحث عنه داخل المستند.
## الخطوة 3: التكرار على نتائج البحث
 قم بالتكرار على نتائج البحث باستخدام أ`foreach` حلقة للوصول إلى كل منهما`SearchResult` هدف.
```csharp
foreach (SearchResult result in searchResults)
{
    //كود للتعامل مع كل نتيجة بحث
}
```
## الخطوة 4: الوصول إلى تفاصيل نتائج البحث
 داخل الحلقة، يمكنك الوصول إلى موضع ونص كل نتيجة بحث باستخدام الملف`Position` و`Text` خصائص`SearchResult` هدف.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
يقوم مقتطف الكود هذا بطباعة الفهرس (`Position`) والنص الموجود (`Text`) لكل نتيجة بحث إلى وحدة التحكم.

## خاتمة
في هذا البرنامج التعليمي، تعلمت كيفية استخدام GroupDocs.Parser لـ .NET للبحث عن نص محدد داخل مستند Word. توفر هذه المكتبة طريقة مناسبة لاستخراج المحتوى ومعالجته من تنسيقات المستندات المختلفة برمجيًا.

## الأسئلة الشائعة
### هل يستطيع GroupDocs.Parser التعامل مع تنسيقات المستندات الأخرى إلى جانب Word؟
نعم، يدعم GroupDocs.Parser مجموعة واسعة من التنسيقات، بما في ذلك PDF وExcel وPowerPoint والمزيد.
### هل GroupDocs.Parser متوافق مع .NET Core؟
نعم، GroupDocs.Parser متوافق مع كل من .NET Framework و.NET Core.
### كيف يمكنني الحصول على ترخيص مؤقت لـ GroupDocs.Parser؟
 يمكنك طلب ترخيص مؤقت من[صفحة شراء GroupDocs](https://purchase.groupdocs.com/temporary-license/).
### أين يمكنني العثور على دعم إضافي أو طرح أسئلة حول GroupDocs.Parser؟
 قم بزيارة[منتدى GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) لدعم المجتمع والمناقشات.
### هل يمكنني تجربة GroupDocs.Parser مجانًا قبل الشراء؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية من[صفحة إصدارات GroupDocs](https://releases.groupdocs.com/).