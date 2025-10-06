---
title: البحث عن النص بالتعبير العادي (Regex)
linktitle: البحث عن النص بالتعبير العادي (Regex)
second_title: GroupDocs.Parser .NET API
description: تعرف على كيفية البحث عن نص باستخدام التعبيرات العادية في المستندات باستخدام GroupDocs.Parser لـ .NET. استخراج محتوى معين دون عناء.
weight: 23
url: /ar/net/text-extraction/search-text-by-regex/
type: docs
---
# البحث عن النص بالتعبير العادي (Regex)

## مقدمة
في هذا البرنامج التعليمي، سوف نتعمق في استخدام GroupDocs.Parser لـ .NET للبحث عن النص باستخدام التعبير العادي (Regex) داخل المستندات. GroupDocs.Parser هي مكتبة قوية تسمح للمطورين باستخراج النصوص والبيانات التعريفية من تنسيقات ملفات مختلفة مثل PDF وDOCX وXLSX والمزيد. يعد البحث عن النص باستخدام التعبيرات العادية مفيدًا بشكل خاص للعثور على أنماط أو محتوى محدد داخل المستندات بكفاءة.
## المتطلبات الأساسية
قبل الغوص في هذا البرنامج التعليمي، تأكد من أن لديك ما يلي:
1. Visual Studio: قم بتثبيت Visual Studio IDE لتطوير .NET.
2.  GroupDocs.Parser لـ .NET: قم بتنزيل وتثبيت GroupDocs.Parser لـ .NET من[هنا](https://releases.groupdocs.com/parser/net/).
3. ملف نموذجي: قم بإعداد مستند نموذجي (PDF، DOCX، إلخ) لاختبار وظيفة البحث.

## استيراد مساحات الأسماء
أولاً، ابدأ بتضمين مساحات الأسماء الضرورية في كود C# الخاص بك:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## الخطوة 1: إنشاء مثيل لفئة المحلل اللغوي
 إنشاء مثيل`Parser` فئة عن طريق توفير المسار إلى ملف العينة الخاص بك:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // الكود يذهب هنا
}
```
 يستبدل`"YourSampleFile.pdf"` مع المسار إلى الملف الفعلي الخاص بك.
## الخطوة 2: البحث باستخدام التعبير العادي
تحديد وتنفيذ البحث باستخدام نمط التعبير العادي. على سبيل المثال، للعثور على تسلسلات رقمية (على سبيل المثال، الأعداد الصحيحة) داخل المستند:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("[0-9]+", new SearchOptions(true, false, true));
```
 في هذا المثال،`[0-9]+` هو نمط تعبير عادي يطابق رقمًا واحدًا أو أكثر.
## الخطوة 3: التحقق من دعم البحث
تحقق مما إذا كانت عملية البحث مدعومة لنوع المستند:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported");
    return;
}
```
## الخطوة 4: التكرار على نتائج البحث
قم بالتكرار من خلال نتائج البحث ومعالجة كل تطابق:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
ستقوم هذه الحلقة بطباعة الموضع والنص المطابق الموجود داخل المستند.

## خاتمة
في الختام، الاستفادة من GroupDocs.Parser لـ .NET تسمح بالبحث الفعال عن النص باستخدام التعبيرات العادية عبر تنسيقات المستندات المختلفة. باتباع هذا الدليل، يمكن للمطورين دمج تحليل المستندات واستخراج النص المستند إلى regex بسلاسة في تطبيقات .NET الخاصة بهم.

## الأسئلة الشائعة
### هل يمكن لـ GroupDocs.Parser البحث ضمن المستندات المشفرة؟
لا، لا يمكن لـ GroupDocs.Parser البحث ضمن المستندات المشفرة أو المحمية بكلمة مرور.
### هل يدعم GroupDocs.Parser التعرف الضوئي على الحروف (OCR)؟
لا، لا يقوم GroupDocs.Parser بإجراء التعرف الضوئي على الحروف. يعتمد على استخراج النص من البنية الداخلية للوثيقة.
### هل يمكنني البحث عن أنماط معقدة باستخدام التعبيرات العادية؟
نعم، يدعم GroupDocs.Parser التعبيرات العادية الكاملة، مما يتيح مطابقة الأنماط المعقدة داخل المستندات.
### ما هي تنسيقات المستندات المدعومة لاستخراج النص؟
يدعم GroupDocs.Parser مجموعة واسعة من التنسيقات، بما في ذلك PDF وDOCX وXLSX وPPTX والمزيد.
### هل GroupDocs.Parser متوافق مع .NET Core؟
نعم، GroupDocs.Parser متوافق مع .NET Core للتطوير عبر الأنظمة الأساسية.