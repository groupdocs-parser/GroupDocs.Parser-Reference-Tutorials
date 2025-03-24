---
title: استخراج النص من الصفحة في الوضع الخام
linktitle: استخراج النص من الصفحة في الوضع الخام
second_title: GroupDocs.Parser .NET API
description: تعلم استخراج النص بكفاءة من صفحات المستندات باستخدام Groupdocs.Parser لـ .NET في هذا البرنامج التعليمي الشامل.
weight: 17
url: /ar/net/text-extraction/extract-text-from-page-in-raw-mode/
---
## مقدمة
ستتعلم في هذا البرنامج التعليمي كيفية استخدام Groupdocs.Parser لـ .NET لاستخراج النص من صفحات المستندات في الوضع الأولي. توفر هذه المكتبة أدوات فعالة لتحليل واستخراج المحتوى من تنسيقات الملفات المختلفة، مما يتيح للمطورين دمج استخراج نص المستند في تطبيقات .NET الخاصة بهم.
## المتطلبات الأساسية
قبل البدء، تأكد من توفر المتطلبات الأساسية التالية:
- المعرفة الأساسية ببرمجة C# و.NET
- تم تثبيت Visual Studio على جهازك
- الوصول إلى Groupdocs.Parser لمكتبة .NET
- نموذج ملف الوثيقة للاختبار

## استيراد مساحات الأسماء
ابدأ بتضمين مساحات الأسماء الضرورية في مشروع C# الخاص بك:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## الخطوة 1: تهيئة المحلل اللغوي
 أولاً، قم بإنشاء مثيل لـ`Parser` فئة عن طريق توفير المسار إلى ملف المستند النموذجي الخاص بك.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // الرمز الخاص بك هنا
}
```
## الخطوة 2: استرجاع معلومات المستند
 استرجاع المعلومات حول الوثيقة باستخدام`GetDocumentInfo()` طريقة.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## الخطوة 3: التكرار على الصفحات واستخراج النص
قم بالتكرار خلال كل صفحة من المستند واستخرج محتوى النص.
```csharp
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // استخراج النص من الصفحة
    using (TextReader reader = parser.GetText(p, new TextOptions(true)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## خاتمة
لقد تعلمت الآن كيفية استخدام Groupdocs.Parser لـ .NET لاستخراج النص من صفحات المستندات في الوضع الأولي. يمكن أن تكون هذه ميزة قوية للتطبيقات التي تحتاج إلى تحليل محتوى النص أو معالجته من تنسيقات ملفات مختلفة.

## الأسئلة الشائعة
### هل Groupdocs.Parser for .NET متوافق مع كافة تنسيقات الملفات؟
يدعم Groupdocs.Parser مجموعة واسعة من تنسيقات الملفات بما في ذلك PDF وDOCX وXLSX وPPTX وEPUB والمزيد.
### هل يمكنني استخراج البيانات الوصفية مع النص باستخدام هذه المكتبة؟
نعم، يتيح لك Groupdocs.Parser استخراج النص وبيانات التعريف من المستندات.
### هل هناك نسخة تجريبية متاحة للاختبار؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية من[هنا](https://releases.groupdocs.com/).
### كيف يمكنني الحصول على الدعم الفني لـ Groupdocs.Parser؟
 للحصول على المساعدة الفنية، قم بزيارة[Groupdocs.منتدى المحلل](https://forum.groupdocs.com/c/parser/17).
### أين يمكنني شراء ترخيص Groupdocs.Parser لـ .NET؟
 يمكنك شراء ترخيص[هنا](https://purchase.groupdocs.com/buy).