---
date: '2026-07-16'
description: تعرف على كيفية إنشاء صورة مصغرة لجدول البيانات باستخدام Java وGroupDocs.Parser،
  ومعاينة ملفات Excel دون الحاجة إلى Office، وتحويل أوراق Excel إلى صور. يغطي هذا
  الدليل الإعداد، والتنفيذ، وحالات الاستخدام العملية.
keywords:
- create spreadsheet thumbnail java
- preview excel without office
- render excel sheets as images
lastmod: '2026-07-16'
og_description: إنشاء صورة مصغرة لجدول البيانات باستخدام Java وGroupDocs.Parser —
  معاينة ملفات Excel دون Office وتحويل أوراق Excel إلى صور. اتبع هذا الدليل خطوة بخطوة
  لتوليد معاينات PNG بكفاءة.
og_image_alt: 'Developer guide: Create spreadsheet thumbnail Java using GroupDocs.Parser'
og_title: إنشاء صورة مصغرة لجدول البيانات باستخدام Java وGroupDocs.Parser
schemas:
- author: GroupDocs
  dateModified: '2026-07-16'
  description: Learn how to create spreadsheet thumbnail Java with GroupDocs.Parser,
    preview Excel without Office, and render Excel sheets as images. This guide covers
    setup, implementation, and practical use cases.
  headline: Create Spreadsheet Thumbnail Java Using GroupDocs.Parser
  type: TechArticle
- description: Learn how to create spreadsheet thumbnail Java with GroupDocs.Parser,
    preview Excel without Office, and render Excel sheets as images. This guide covers
    setup, implementation, and practical use cases.
  name: Create Spreadsheet Thumbnail Java Using GroupDocs.Parser
  steps:
  - name: Initialize the Parser Instance
    text: '`Parser` is GroupDocs.Parser''s core class that provides read access to
      spreadsheet files and enables page‑wise rendering. Create a `Parser` object
      pointing at your Excel workbook. The *try‑with‑resources* block ensures the
      parser is closed automatically. > **Pro tip:** Use an absolute path or config'
  - name: Prepare Your Preview Options
    text: '`PreviewOptions` configures rendering parameters such as output format
      and DPI. `ICreatePageStream` is a callback interface that supplies an output
      stream for each generated page. Define how each page will be saved. The `ICreatePageStream`
      implementation returns a fresh `FileOutputStream` for every '
  - name: Attach a Delegate to Capture Render Info
    text: If you need details about each rendered sheet (e.g., dimensions, sheet name),
      register a callback.
  - name: Specify Output Format and DPI
    text: Select PNG as the image format and set a DPI that balances quality and file
      size. > Adjust the DPI if you need smaller thumbnails (e.g., 96) or high‑resolution
      prints (e.g., 300).
  - name: Generate the Previews
    text: With everything configured, call `generatePreview`. The SDK will iterate
      over each worksheet and invoke the stream you supplied.
  - name: Define the `getOutputPath()` Helper
    text: '`getOutputPath()` builds a file name based on the page (sheet) number and
      returns the full path for the output image. Feel free to customize the folder
      structure. > **Common pitfall:** Forgetting to create the `output` directory
      beforehand will cause an `IOException`. Create it programmatically or e'
  type: HowTo
- questions:
  - answer: Yes, the same API works for PDFs, Word documents, and many image formats.
    question: Can I generate previews for PDFs and images using GroupDocs.Parser?
  - answer: Call `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (or `Gif`,
      `Bmp`, etc.).
    question: How do I change the output image format?
  - answer: The SDK streams pages, which keeps memory usage low. For massive files,
      consider processing in parallel batches.
    question: Is performance a concern with very large workbooks?
  - answer: Wrap the code in try‑catch blocks (as shown) and log the exception details.
      Ensure streams are closed in the `finally` block if you’re not using try‑with‑resources.
    question: How can I handle errors during preview generation?
  - answer: No. GroupDocs.Parser is a pure Java solution and works on any platform
      that supports Java 8+.
    question: Does the library require Microsoft Office to be installed?
  type: FAQPage
tags:
- create spreadsheet thumbnail
- GroupDocs.Parser
- Java preview excel
- excel to png
- document processing
title: إنشاء صورة مصغرة لجدول البيانات باستخدام Java وGroupDocs.Parser
type: docs
url: /ar/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# إنشاء صورة مصغرة لجدول بيانات Java باستخدام GroupDocs.Parser

إذا كنت تبحث عن **إنشاء صورة مصغرة لجدول بيانات Java**، فقد وصلت إلى المكان الصحيح. في هذا الدليل سنستعرض كيفية إنشاء معاينات PNG عالية الجودة من دفاتر العمل `.xlsx` باستخدام GroupDocs.Parser للـ Java — مثالي للصور المصغرة السريعة، مشاركة اللقطات، أو بناء ميزة معاينة المستندات في تطبيقك. يعمل الحل دون الحاجة إلى تثبيت Microsoft Office ويتعامل مع دفاتر عمل كبيرة مع الحفاظ على استهلاك الذاكرة منخفضًا.

## إجابات سريعة
- **ماذا يعني “preview Excel”؟** إنشاء ملفات صور (مثل PNG) تمثل كل صفحة من ورقة العمل.  
- **ما الصيغة الموصى بها؟** PNG توفر جودة غير مضغوطة وتعمل جيدًا للصور المصغرة على الويب.  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية المجانية تكفي للتطوير؛ يتطلب الترخيص التجاري للإنتاج.  
- **هل يمكنني تغيير دقة الصورة؟** نعم — اضبط DPI في `PreviewOptions`.  
- **هل يمكن معاينة صيغ أخرى؟** GroupDocs.Parser يدعم أيضًا PDF و Word والعديد من أنواع الصور.

## ما هو “كيفية معاينة Excel” باستخدام GroupDocs.Parser؟
حمّل دفتر عمل Excel الخاص بك وقم بعرض كل ورقة كصورة PNG دون الحاجة إلى Microsoft Office. يقوم GroupDocs.Parser ببث الصفحات واحدة تلو الأخرى، منتجًا صورًا مصغرة غير مضغوطة يمكن حفظها على القرص أو إرجاعها عبر HTTP، مما يجعلها مثالية لخدمات المعاينة عبر الويب.

يقوم GroupDocs.Parser بقراءة دفاتر عمل Excel، ويعرض كل ورقة كصفحة بصرية، ويسمح لك ببث تلك الصفحات إلى ملفات صور. هذا يلغي الحاجة إلى تفاعل Office أو محولات الطرف الثالث.

## لماذا نستخدم GroupDocs.Parser لمعالجة معاينات Excel؟
يجب عليك استخدام GroupDocs.Parser لأنه يعمل على أي خادم Java، ولا يحتاج إلى تثبيت Office، ويتعامل مع دفاتر عمل كبيرة بذاكرة منخفضة، وينتج صور PNG غير مضغوطة مع DPI قابل للتكوين. يدعم SDK **أكثر من 100 صيغة إدخال وإخراج**، ويمكنه معالجة دفتر عمل مكوّن من 200 صفحة في أقل من 3 ثوانٍ، ويحافظ على استهلاك الذاكرة أقل من 50 ميغابايت لكل ورقة.

- **لا يتطلب تثبيت Office** – يعمل على أي بيئة Java من جانب الخادم.  
- **يدعم الملفات الكبيرة** – يبث الصفحات واحدة تلو الأخرى، مما يحافظ على انخفاض استهلاك الذاكرة.  
- **إخراج عالي الجودة** – تحكم في DPI، الصيغة، وخيارات العرض.  
- **مرونة متعددة الصيغ** – نفس الـ API يعمل مع PDF، مستندات Word، وأكثر.

## المتطلبات المسبقة
- **مجموعة تطوير Java** (8 +).  
- **بيئة تطوير متكاملة (IDE)** مثل IntelliJ IDEA أو Eclipse.  
- **GroupDocs.Parser for Java SDK** – حمّل من [here](https://releases.groupdocs.com/parser/java/).  
- **الوثائق** – راجع [documentation](https://docs.groupdocs.com/parser/java/).  
- **ملف Excel تجريبي** (`.xlsx`) الذي تريد معاينته.  
- **Maven أو Gradle** (اختياري) لإدارة التبعيات.

## استيراد الحزم
تتيح لك هذه الاستيرادات الوصول إلى المحلل، خيارات المعاينة، وأدوات معالجة التدفقات.

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.options.PreviewOptions;
import com.groupdocs.parser.options.PreviewFormats;
import com.groupdocs.parser.options.ICreatePageStream;
import com.groupdocs.parser.options.IPreviewPageRender;
import com.groupdocs.parser.results.PageRenderInfo;
import java.io.FileOutputStream;
import java.io.OutputStream;
import java.io.IOException;
```

## دليل خطوة بخطوة لإنشاء معاينات صفحات جدول البيانات

### الخطوة 1: تهيئة كائن Parser
`Parser` هو الفئة الأساسية في GroupDocs.Parser التي توفر وصول قراءة إلى ملفات جداول البيانات وتمكن من العرض حسب الصفحات.  
أنشئ كائن `Parser` يشير إلى دفتر عمل Excel الخاص بك. يضمن كتلة *try‑with‑resources* إغلاق المحلل تلقائيًا.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **نصيحة احترافية:** استخدم مسارًا مطلقًا أو قم بتهيئة مجلد موارد لتجنب `FileNotFoundException`.

### الخطوة 2: إعداد خيارات المعاينة الخاصة بك
`PreviewOptions` يضبط معلمات العرض مثل صيغة الإخراج و DPI.  
`ICreatePageStream` هي واجهة رد نداء توفر تدفق إخراج لكل صفحة مُولدة. حدد كيفية حفظ كل صفحة. تُعيد تنفيذ `ICreatePageStream` كائن `FileOutputStream` جديد لكل صفحة من أوراق العمل.

```java
PreviewOptions previewOptions = new PreviewOptions(new ICreatePageStream() {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        try {
            String outputPath = getOutputPath(pageNumber); // define this method later
            return new FileOutputStream(outputPath);
        } catch (IOException ex) {
            throw new RuntimeException("Error creating output stream", ex);
        }
    }
});
```

> هذه هي الخطوة التي **تحول xlsx إلى png** — يقوم التدفق بكتابة بيانات PNG إلى القرص.

### الخطوة 3: إرفاق مندوب لالتقاط معلومات العرض
إذا كنت بحاجة إلى تفاصيل حول كل ورقة مُعروضة (مثل الأبعاد، اسم الورقة)، سجّل رد نداء.

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### الخطوة 4: تحديد صيغة الإخراج و DPI
اختر PNG كصيغة الصورة واضبط DPI بحيث يوازن بين الجودة وحجم الملف.

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> اضبط DPI إذا كنت تحتاج إلى صور مصغرة أصغر (مثلاً 96) أو طباعة عالية الدقة (مثلاً 300).

### الخطوة 5: إنشاء المعاينات
بعد ضبط جميع الإعدادات، استدعِ `generatePreview`. سيقوم SDK بتكرار كل ورقة عمل واستدعاء التدفق الذي قدمته.

```java
parser.generatePreview(previewOptions);
```

### الخطوة 6: تعريف الدالة المساعدة `getOutputPath()`
`getOutputPath()` يبني اسم ملف بناءً على رقم الصفحة (الورقة) ويعيد المسار الكامل لصورة الإخراج. يمكنك تعديل بنية المجلد حسب رغبتك.

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **مشكلة شائعة:** نسيان إنشاء مجلد `output` مسبقًا سيسبب `IOException`. أنشئه برمجيًا أو تأكد من وجوده.

## مثال عملي كامل (مبسط)

فيما يلي نسخة مختصرة تجمع جميع الأجزاء معًا. تُظهر سير عمل **إنشاء صورة مصغرة لجدول بيانات Java** من البداية إلى النهاية.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    final PageRenderInfo[] renderInfoHolder = {null};

    PreviewOptions options = new PreviewOptions(new ICreatePageStream() {
        @Override
        public OutputStream createPageStream(int pageNumber) {
            try {
                return new FileOutputStream(getOutputPath(pageNumber));
            } catch (IOException e) {
                throw new RuntimeException(e);
            }
        }
    });

    options.setPreviewPageRender(pageRenderInfo -> {
        renderInfoHolder[0] = pageRenderInfo;
    });
    options.setPreviewFormat(PreviewFormats.Png);
    options.setDpi(150);

    parser.generatePreview(options);
} catch (Exception e) {
    e.printStackTrace();
}
```

شغّل هذا المقتطف، وستجد سلسلة من الملفات `preview_page_1.png`, `preview_page_2.png`, … في مجلد `output` — كل منها يمثل ورقة من دفتر عمل Excel الأصلي.

## المشكلات الشائعة والحلول

| المشكلة | السبب | الحل |
|-------|-------|-----|
| **لم يتم إنشاء صور** | `getOutputPath` يُعيد دليلًا غير صالح | تأكد من وجود المجلد الهدف أو أنشئه باستخدام `new File("output").mkdirs();` |
| **خطأ نفاد الذاكرة على ملفات ضخمة** | تحميل دفتر العمل بالكامل مرة واحدة | استخدم نهج البث (كما هو موضح) وعالج الصفحات واحدة تلو الأخرى |
| **DPI غير صحيح** | `setDpi` لم يتم استدعاؤه أو تم تعيينه إلى القيمة الافتراضية (96) | استدعِ `previewOptions.setDpi(yourDesiredValue);` قبل `generatePreview` |
| **صيغة غير مدعومة** | محاولة معاينة ملف `.xlsx` تالف | تحقق من صحة الملف باستخدام Excel أو استخدم `Parser.isSupported` قبل المعالجة |

## الأسئلة المتكررة

**س: هل يمكنني إنشاء معاينات لملفات PDF والصور باستخدام GroupDocs.Parser؟**  
ج: نعم، نفس الـ API يعمل مع PDF، مستندات Word، والعديد من صيغ الصور.

**س: كيف يمكنني تغيير صيغة صورة الإخراج؟**  
ج: استدعِ `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (أو `Gif`، `Bmp`، إلخ).

**س: هل الأداء يمثل مشكلة مع دفاتر عمل كبيرة جدًا؟**  
ج: يقوم SDK ببث الصفحات، مما يحافظ على انخفاض استهلاك الذاكرة. للملفات الضخمة، فكر في المعالجة على دفعات متوازية.

**س: كيف يمكنني التعامل مع الأخطاء أثناء إنشاء المعاينات؟**  
ج: غلف الكود بكتل try‑catch (كما هو موضح) وسجّل تفاصيل الاستثناء. تأكد من إغلاق التدفقات في كتلة `finally` إذا لم تستخدم try‑with‑resources.

**س: هل تتطلب المكتبة تثبيت Microsoft Office؟**  
ج: لا. GroupDocs.Parser حل Java نقي ويعمل على أي منصة تدعم Java 8+.

---

**آخر تحديث:** 2026-07-16  
**تم الاختبار مع:** GroupDocs.Parser 23.11 (أحدث نسخة عند كتابة هذا)  
**المؤلف:** GroupDocs

## دروس ذات صلة

- [كيفية إنشاء معاينة – دروس توليد معاينة صفحات المستند لـ GroupDocs.Parser Java](/parser/java/page-preview-generation/)
- [تحليل Excel Java باستخدام GroupDocs.Parser: دليل كامل](/parser/java/getting-started/mastering-document-parsing-java-groupdocs-parser/)
- [كيفية استخراج النص الخام من أوراق Excel باستخدام GroupDocs.Parser للـ Java: دليل خطوة بخطوة](/parser/java/text-extraction/extract-raw-text-excel-groupdocs-parser-java/)