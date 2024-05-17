---
title: التعرف على النص في مناطق محددة
linktitle: التعرف على النص في مناطق محددة
second_title: GroupDocs.Parser .NET API
description: تعرف على كيفية استخدام GroupDocs.Parser لـ .NET لاستخراج النص من مناطق محددة في المستندات التي تتمتع بإمكانيات التعرف الضوئي على الحروف.
type: docs
weight: 13
url: /ar/net/ocr-extraction/recognizing-text-in-specific-areas/
---
## مقدمة
في هذا البرنامج التعليمي، سنستكشف كيفية استخدام GroupDocs.Parser لـ .NET للتعرف على النص واستخراجه من مناطق معينة داخل المستند. GroupDocs.Parser عبارة عن مكتبة قوية لتحليل المستندات تتيح للمطورين العمل مع تنسيقات المستندات المختلفة، بما في ذلك PDF وWord وExcel وPowerPoint والمزيد. على وجه التحديد، سنركز على الاستفادة من إمكانات التعرف الضوئي على الحروف (OCR) الخاصة بـ GroupDocs.Parser لاستخراج النص من مناطق محددة داخل المستند.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من إعداد المتطلبات الأساسية التالية:
1. Visual Studio IDE: تأكد من تثبيت Visual Studio على جهازك.
2.  GroupDocs.Parser لـ .NET: قم بتنزيل وتثبيت GroupDocs.Parser لـ .NET من[رابط التحميل](https://releases.groupdocs.com/parser/net/).
3. عينات المستندات: قم بإعداد ملفات العينات (مثل PDF وDOCX) التي تريد استخراج النص منها.

## استيراد مساحات الأسماء
للبدء، قم باستيراد مساحات الأسماء الضرورية إلى مشروعك:
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using System.Linq;
using System.Text;
using Aspose.OCR;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```

دعونا نقسم العملية إلى خطوات تفصيلية باستخدام GroupDocs.Parser لـ .NET:
## الخطوة 1: إنشاء إعدادات المحلل اللغوي باستخدام موصل OCR
 أولاً، قم بإنشاء مثيل لـ`ParserSettings`فئة وتهيئتها باستخدام موصل التعرف الضوئي على الحروف، مثل`AsposeOcrOnPremise`:
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## الخطوة 2: إنشاء مثيل للمحلل باستخدام الإعدادات
 بعد ذلك، قم بإنشاء مثيل لـ`Parser` الفصل عن طريق تمرير ما تم إنشاؤه مسبقًا`ParserSettings`:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // يستمر مقتطف الكود...
}
```
 يستبدل`"YourSampleFile.pdf"` مع المسار إلى المستند المستهدف.
## الخطوة 3: تكوين خيارات استخراج منطقة النص
 إنشاء مثيل ل`PageTextAreaOptions` لتمكين استخراج النص القائم على التعرف الضوئي على الحروف:
```csharp
PageTextAreaOptions options = new PageTextAreaOptions(true);
```
 تعيين`true` لتمكين التعرف الضوئي على الحروف (OCR) للتعرف بشكل أفضل على النص.
## الخطوة 4: استخراج مناطق النص
 يستحضر`parser.GetTextAreas(options)` لاستخراج مناطق النص من المستند:
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## الخطوة 5: معالجة مناطق النص المستخرجة
قم بالتكرار على مناطق النص المستخرجة واسترجاع معلومات النص والموضع والحجم:
```csharp
foreach (PageTextArea area in areas)
{
    Console.WriteLine(area.Text);
    Console.WriteLine($"\tPosition: ({area.Rectangle.Left}; {area.Rectangle.Top})");
    Console.WriteLine($"\tSize: ({area.Rectangle.Size.Width}; {area.Rectangle.Size.Height})");
}
```

## خاتمة
في هذا البرنامج التعليمي، قمنا بتغطية عملية استخراج النص من مناطق محددة داخل المستند باستخدام GroupDocs.Parser لـ .NET مع إمكانيات التعرف الضوئي على الحروف. باتباع هذه الخطوات، يمكنك الاستفادة بشكل فعال من وظائف التحليل الخاصة بـ GroupDocs.Parser للتعامل مع مهام استخراج النص برمجيًا.

## الأسئلة الشائعة
### هل يمكن لـ GroupDocs.Parser استخراج النص من المستندات الممسوحة ضوئيًا؟
نعم، يدعم GroupDocs.Parser تقنية التعرف الضوئي على الحروف (OCR) لاستخراج النص من الصور الممسوحة ضوئيًا داخل المستندات.
### ما تنسيقات المستندات التي يدعمها GroupDocs.Parser؟
يدعم GroupDocs.Parser مجموعة واسعة من التنسيقات، بما في ذلك PDF وDOCX وXLSX وPPTX وTXT والمزيد.
### هل GroupDocs.Parser مناسب لمعالجة المستندات دفعة واحدة؟
نعم، يمكن لـ GroupDocs.Parser التعامل بكفاءة مع مهام المعالجة المجمعة لتحليل المستندات واستخراجها.
### هل يمكنني تخصيص خيارات استخراج النص باستخدام GroupDocs.Parser؟
نعم، يقدم GroupDocs.Parser خيارات متنوعة لتخصيص استخراج النص بناءً على متطلبات محددة.
### هل يوفر GroupDocs.Parser الدعم لاستخراج بيانات التعريف من المستندات؟
نعم، يسمح GroupDocs.Parser باستخراج بيانات التعريف مثل المؤلف وتاريخ الإنشاء والمزيد من تنسيقات المستندات المدعومة.