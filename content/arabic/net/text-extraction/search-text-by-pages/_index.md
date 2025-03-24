---
title: البحث عن النص حسب الصفحات
linktitle: البحث عن النص حسب الصفحات
second_title: GroupDocs.Parser .NET API
description: تعرف على كيفية البحث عن النص حسب الصفحات باستخدام GroupDocs.Parser لـ .NET. قم باستخراج محتوى محدد بكفاءة من المستندات الموجودة في تطبيقات .NET الخاصة بك.
weight: 22
url: /ar/net/text-extraction/search-text-by-pages/
---

# البحث عن النص حسب الصفحات

## مقدمة
في عالم تطوير .NET، يعد تحليل النص واستخراجه من المستندات بكفاءة مهمة بالغة الأهمية. يوفر GroupDocs.Parser for .NET إمكانات قوية للعمل مع تنسيقات المستندات المختلفة، مما يسمح للمطورين بالبحث عن محتوى محدد واستخراجه بسلاسة. سيرشدك هذا البرنامج التعليمي خلال عملية الاستفادة من GroupDocs.Parser للبحث في النص حسب الصفحات في تطبيقات .NET الخاصة بك.
## المتطلبات الأساسية
قبل الغوص في هذا البرنامج التعليمي، تأكد من أن لديك المتطلبات الأساسية التالية:
- الفهم الأساسي لـ C# و.NET Framework
- تم تثبيت Visual Studio على نظامك
-  تم تثبيت GroupDocs.Parser لمكتبة .NET (التنزيل من[هنا](https://releases.groupdocs.com/parser/net/))
- نموذج ملف (ملفات) لاختبار وظيفة البحث
## استيراد مساحات الأسماء
أولاً، قم بتضمين مساحات الأسماء الضرورية في مشروعك للوصول إلى وظائف GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## الخطوة 1: إنشاء مثيل لفئة المحلل اللغوي
 ابدأ بإنشاء مثيل لـ`Parser` فئة مع المسار إلى ملف العينة الخاص بك:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // الكود الخاص بك يذهب هنا
}
```
## الخطوة 2: البحث عن النص باستخدام أرقام الصفحات
 الاستفادة من`Search` طريقة للبحث عن كلمات رئيسية محددة داخل المستند مع أرقام الصفحات:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword", new SearchOptions(false, false, false, true));
```
## الخطوة 3: التحقق من دعم البحث
تحقق مما إذا كانت عملية البحث مدعومة لنوع المستند:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported for this document type.");
    return;
}
```
## الخطوة 4: التكرار على نتائج البحث
كرر نتائج البحث لاسترداد المواضع المفهرسة وأرقام الصفحات والنص الذي تم العثور عليه:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position} (page {result.PageIndex}): {result.Text}");
}
```
## خاتمة
في هذا البرنامج التعليمي، اكتشفنا كيفية تنفيذ البحث عن النص حسب الصفحات باستخدام GroupDocs.Parser لـ .NET. باتباع هذه الخطوات، يمكنك دمج وظائف تحليل المستندات والبحث فيها بكفاءة في تطبيقات .NET الخاصة بك.

## الأسئلة الشائعة
### هل GroupDocs.Parser متوافق مع تنسيقات المستندات المختلفة؟
نعم، يدعم GroupDocs.Parser مجموعة واسعة من تنسيقات المستندات بما في ذلك DOCX وPDF وXLSX وPPTX والمزيد.
### هل يمكنني استخراج الصور وبيانات التعريف من المستندات باستخدام GroupDocs.Parser؟
بالتأكيد، يسمح GroupDocs.Parser باستخراج الصور وبيانات التعريف والنص من المستندات.
### أين يمكنني العثور على وثائق مفصلة عن GroupDocs.Parser؟
 يمكنك الوصول إلى الوثائق[هنا](https://tutorials.groupdocs.com/parser/net/).
### كيف يمكنني الحصول على ترخيص مؤقت لـ GroupDocs.Parser؟
 يمكنك طلب ترخيص مؤقت[هنا](https://purchase.groupdocs.com/temporary-license/).
### أين يمكنني الحصول على الدعم أو المساعدة فيما يتعلق بـ GroupDocs.Parser؟
 للحصول على الدعم والمناقشات، قم بزيارة منتدى GroupDocs.Parser[هنا](https://forum.groupdocs.com/c/parser/17).