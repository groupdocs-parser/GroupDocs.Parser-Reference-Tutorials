---
title: استخراج النص من مستند Excel بتنسيق HTML
linktitle: استخراج النص من مستند Excel بتنسيق HTML
second_title: GroupDocs.Parser .NET API
description: تعرف على كيفية استخراج النص من مستندات Excel وتحويله إلى HTML باستخدام GroupDocs.Parser لـ .NET.
type: docs
weight: 13
url: /ar/net/excel-document-processing/extract-text-from-excel-document-as-html/
---
## مقدمة
في هذا البرنامج التعليمي، سوف نستكشف كيفية استخدام GroupDocs.Parser لـ .NET لاستخراج النص من مستند Excel وتحويله إلى تنسيق HTML. GroupDocs.Parser هي مكتبة قوية تتيح للمطورين العمل مع تنسيقات المستندات المختلفة، واستخراج النص وبيانات التعريف بكفاءة.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك الإعداد التالي:
- تم تثبيت Visual Studio على نظامك.
- الفهم الأساسي للبرمجة C#.
-  مكتبة GroupDocs.Parser لـ .NET. يمكنك تنزيله من[هنا](https://releases.groupdocs.com/parser/net/).
## استيراد مساحات الأسماء
ابدأ بتضمين مساحات الأسماء الضرورية في مشروع C# الخاص بك للوصول إلى وظائف GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## الخطوة 1: إنشاء مثيل لفئة المحلل اللغوي
 أولاً، قم بإنشاء مثيل`Parser` فئة عن طريق توفير المسار إلى مستند Excel الخاص بك.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // مزيد من التعليمات البرمجية سوف تذهب هنا
}
```
 يستبدل`"YourSampleFile.xlsx"` مع المسار إلى ملف Excel الخاص بك.
## الخطوة 2: استخراج النص بصيغة HTML
 في حدود`using` كتلة من`Parser` على سبيل المثال، استخدم`GetFormattedText` طريقة لاستخراج النص المنسق في وضع HTML.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // مزيد من التعليمات البرمجية سوف تذهب هنا
    }
}
```
## الخطوة 3: قراءة وطباعة نص HTML المستخرج
 بعد ذلك، اقرأ نص HTML المستخرج من ملف`TextReader` وطباعته على وحدة التحكم.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
بمجرد تنفيذه، سيقوم هذا الرمز باستخراج النص من مستند Excel وعرضه بتنسيق HTML في وحدة التحكم.
## خاتمة
في هذا البرنامج التعليمي، تعلمنا كيفية استخدام GroupDocs.Parser لـ .NET لاستخراج النص من مستند Excel وتحويله إلى تنسيق HTML. توفر هذه المكتبة طريقة مباشرة للعمل مع تنسيقات المستندات المختلفة، مما يتيح للمطورين التعامل بكفاءة مع مهام استخراج النص في تطبيقاتهم.

## الأسئلة الشائعة
### هل يستطيع GroupDocs.Parser التعامل مع تنسيقات المستندات الأخرى إلى جانب Excel؟
نعم، يدعم GroupDocs.Parser مجموعة واسعة من تنسيقات الملفات بما في ذلك PDF وWord وPowerPoint والمزيد.
### هل GroupDocs.Parser متوافق مع .NET Core؟
نعم، GroupDocs.Parser متوافق مع كل من .NET Framework و.NET Core.
### هل يحتفظ GroupDocs.Parser بالتنسيق أثناء استخراج النص؟
نعم، يمكن لـ GroupDocs.Parser الحفاظ على التنسيق مثل الخطوط والأنماط والتخطيط أثناء استخراج النص.
### هل يمكنني استخراج بيانات التعريف من المستندات باستخدام GroupDocs.Parser؟
نعم، يسمح GroupDocs.Parser باستخراج البيانات التعريفية مثل المؤلف وتاريخ الإنشاء والمزيد من أنواع المستندات المدعومة.
### هل هناك نسخة تجريبية مجانية متاحة لـ GroupDocs.Parser؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية من[هنا](https://releases.groupdocs.com/).