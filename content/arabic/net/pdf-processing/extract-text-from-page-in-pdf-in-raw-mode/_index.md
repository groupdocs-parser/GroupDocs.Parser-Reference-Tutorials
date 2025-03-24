---
title: استخراج النص من الصفحة في PDF في الوضع الخام
linktitle: استخراج النص من الصفحة في PDF في الوضع الخام
second_title: GroupDocs.Parser .NET API
description: استخرج النص من ملفات PDF باستخدام GroupDocs.Parser في C#. تعلم استخراج نص PDF بكفاءة باستخدام مكتبة .NET القوية هذه.
weight: 16
url: /ar/net/pdf-processing/extract-text-from-page-in-pdf-in-raw-mode/
---

# استخراج النص من الصفحة في PDF في الوضع الخام

## مقدمة
في هذا البرنامج التعليمي، سوف نستكشف كيفية استخدام GroupDocs.Parser لـ .NET لاستخراج النص من الصفحات في مستندات PDF باستخدام الوضع الأولي. تعد GroupDocs.Parser أداة قوية تمكن المطورين من العمل مع تنسيقات المستندات المختلفة برمجيًا.
## المتطلبات الأساسية
قبل البدء في هذا البرنامج التعليمي، تأكد من أن لديك ما يلي:
- تم تثبيت Visual Studio على جهازك.
- المعرفة الأساسية ببرمجة C#.
- GroupDocs.Parser لمكتبة .NET، والتي يمكنك ذلك[حمل هنا](https://releases.groupdocs.com/parser/net/).
- نموذج لملف PDF لأغراض الاختبار.

## استيراد مساحات الأسماء
أولاً، تأكد من استيراد مساحات الأسماء الضرورية في مشروع C# الخاص بك:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## الخطوة 1: إنشاء مثيل لفئة المحلل اللغوي
 للبدء، قم بإنشاء مثيل`Parser`فئة من خلال توفير المسار إلى ملف PDF النموذجي الخاص بك.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // الكود الخاص بك يذهب هنا
}
```
## الخطوة 2: الحصول على معلومات المستند والتكرار عبر الصفحات
بعد ذلك، قم باسترداد معلومات المستند وتكرارها على كل صفحة لاستخراج النص.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // الكود الخاص بك لاستخراج النص موجود هنا
}
```
## الخطوة 3: استخراج النص من كل صفحة
 داخل الحلقة، استخدم`GetText` طريقة استخراج النص من كل صفحة وطباعته.
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## خاتمة
 في هذا البرنامج التعليمي، تعلمنا كيفية استخراج النص من صفحات PDF في الوضع الأولي باستخدام GroupDocs.Parser لـ .NET. تتضمن هذه العملية إنشاء ملف`Parser` على سبيل المثال، الحصول على معلومات المستند، والتكرار على كل صفحة، واستخراج النص باستخدام`GetText` طريقة.

## الأسئلة الشائعة
### ما هو GroupDocs.Parser لـ .NET؟
GroupDocs.Parser for .NET عبارة عن واجهة برمجة تطبيقات لتحليل المستندات تسمح للمطورين باستخراج النص وبيانات التعريف والمعلومات الأخرى من تنسيقات الملفات المختلفة برمجيًا.
### كيف يمكنني تنزيل GroupDocs.Parser لـ .NET؟
 يمكنك تحميل المكتبة من[موقع مستندات المجموعة](https://releases.groupdocs.com/parser/net/).
### هل هناك نسخة تجريبية مجانية متاحة؟
 نعم، يمكنك الوصول إلى النسخة التجريبية المجانية من GroupDocs.Parser لـ .NET من[هنا](https://releases.groupdocs.com/).
### أين يمكنني العثور على دعم لـ GroupDocs.Parser لـ .NET؟
 للحصول على المساعدة الفنية ودعم المجتمع، قم بزيارة[منتدى مستندات المجموعة](https://forum.groupdocs.com/c/parser/17).
### كيف يمكنني شراء ترخيص GroupDocs.Parser لـ .NET؟
 يمكنك شراء ترخيص من[صفحة الشراء](https://purchase.groupdocs.com/buy) أو الحصول على ترخيص مؤقت[هنا](https://purchase.groupdocs.com/temporary-license/).