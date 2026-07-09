---
date: '2026-02-06'
description: تعلم كيفية معاينة ملفات Excel وتحويل ملفات xlsx إلى png باستخدام GroupDocs.Parser
  للغة Java. يغطي هذا الدرس الإعداد والتنفيذ والتطبيقات العملية.
keywords:
- GroupDocs.Parser
- Java
- Document Processing
title: كيفية معاينة ملفات Excel باستخدام GroupDocs.Parser في Java
type: docs
url: /ar/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# كيفية معاينة ملفات Excel باستخدام GroupDocs.Parser في Java

إذا كنت تبحث عن **كيفية معاينة ملفات Excel** برمجياً، فقد وصلت إلى المكان الصحيح. في هذا الدليل سنستعرض إنشاء معاينات صور (PNG) من ملفات `.xlsx` باستخدام GroupDocs.Parser للـ Java — مثالي لإنشاء صور مصغرة سريعة، مشاركة لقطات، أو بناء ميزة معاينة المستندات في تطبيقك.

## إجابات سريعة
- **ماذا يعني “معاينة Excel”؟** إنشاء ملفات صورة (مثل PNG) تمثل كل صفحة من أوراق العمل.  
- **أي صيغة يُنصح بها؟** PNG توفر جودة غير مضغوطة وتعمل جيداً للصور المصغرة على الويب.  
- **هل أحتاج إلى ترخيص؟** نسخة تجريبية مجانية تكفي للتطوير؛ يُطلب ترخيص تجاري للإنتاج.  
- **هل يمكنني تغيير دقة الصورة؟** نعم — اضبط DPI في `PreviewOptions`.  
- **هل يمكن معاينة صيغ أخرى؟** GroupDocs.Parser يدعم أيضاً PDF، Word، والعديد من صيغ الصور.

## ما هو “كيفية معاينة Excel” باستخدام GroupDocs.Parser؟
GroupDocs.Parser يقرأ ملفات Excel، يُظهر كل ورقة كصفحة بصرية، ويسمح لك بتدفق تلك الصفحات إلى ملفات صورة. هذا يلغي الحاجة إلى تكامل Office أو محولات طرف ثالث.

## لماذا نستخدم GroupDocs.Parser لمعالجة معاينات Excel؟
- **لا حاجة لتثبيت Office** – يعمل على أي بيئة Java من جانب الخادم.  
- **يدعم الملفات الكبيرة** – يَتَدَفَّق الصفحات واحدةً تلو الأخرى، مما يحافظ على استهلاك الذاكرة منخفضاً.  
- **إخراج عالي الجودة** – تحكم في DPI، الصيغة، وخيارات العرض.  
- **مرونة عبر الصيغ** – نفس الـ API يعمل مع PDFs، مستندات Word، وأكثر.

## المتطلبات المسبقة
- **مجموعة تطوير جافا (JDK)** (8 +).  
- **بيئة تطوير متكاملة** مثل IntelliJ IDEA أو Eclipse.  
- **GroupDocs.Parser للـ Java SDK** – حمّله من [هنا](https://releases.groupdocs.com/parser/java/).  
- **ملف Excel تجريبي** (`.xlsx`) تريد معاينته.  
- **Maven أو Gradle** (اختياري) لإدارة الاعتمادات.

## استيراد الحزم
هذه الاستيرادات تمنحك الوصول إلى المحلل، خيارات المعاينة، وأدوات التعامل مع التدفقات.

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

## دليل خطوة بخطوة لإنشاء معاينات صفحات جداول البيانات

### الخطوة 1: تهيئة كائن Parser
أنشئ كائن `Parser` يشير إلى ملف Excel الخاص بك. يضمن بلوك *try‑with‑resources* إغلاق المحلل تلقائياً.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **نصيحة احترافية:** استخدم مسارًا مطلقًا أو اضبط مجلد الموارد لتجنب `FileNotFoundException`.

### الخطوة 2: إعداد خيارات المعاينة
حدد كيف سيتم حفظ كل صفحة. تنفيذ `ICreatePageStream` يُعيد `FileOutputStream` جديد لكل ورقة عمل.

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

> هذه الخطوة هي حيث **تحول xlsx إلى png** — يكتب التدفق بيانات PNG إلى القرص.

### الخطوة 3: إرفاق مُفوض لالتقاط معلومات العرض
إذا كنت بحاجة إلى تفاصيل حول كل ورقة مُعرضة (مثل الأبعاد، اسم الورقة)، سجِّل رد نداء (callback).

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### الخطوة 4: تحديد صيغة الإخراج وDPI
اختر PNG كصيغة الصورة واضبط DPI بحيث يوازن بين الجودة وحجم الملف.

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> عدّل DPI إذا كنت تحتاج إلى صور مصغرة أصغر (مثلاً 96) أو طباعة عالية الدقة (مثلاً 300).

### الخطوة 5: توليد المعاينات
بعد ضبط جميع الإعدادات، استدعِ `generatePreview`. سيقوم الـ SDK بتكرار كل ورقة عمل ويستدعي التدفق الذي قدمته.

```java
parser.generatePreview(previewOptions);
```

### الخطوة 6: تعريف الدالة المساعدة `getOutputPath()`
هذه الطريقة تُنشئ اسم ملف بناءً على رقم الصفحة (الورقة). يمكنك تعديل بنية المجلد حسب رغبتك.

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **خطأ شائع:** نسيان إنشاء مجلد `output` مسبقًا سيسبب `IOException`. أنشئه برمجيًا أو تأكد من وجوده.

## مثال كامل يعمل (مبسط)

فيما يلي نسخة مختصرة تجمع كل الأجزاء معًا. تُظهر سير عمل **إنشاء معاينة صفحة Excel** من البداية حتى النهاية.

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

شغّل هذا المقتطف، وستجد سلسلة من الملفات `preview_page_1.png`, `preview_page_2.png`, … داخل مجلد `output` — كل ملف يمثل ورقة من ملف Excel الأصلي.

## المشكلات الشائعة والحلول
| المشكلة | السبب | الحل |
|-------|-------|-----|
| **لم يتم إنشاء أي صور** | `getOutputPath` يُعيد مسار دليل غير صالح | تأكد من وجود المجلد الهدف أو أنشئه باستخدام `new File("output").mkdirs();` |
| **خطأ نفاد الذاكرة على ملفات ضخمة** | تحميل ملف العمل بالكامل مرة واحدة | استخدم نهج التدفق (كما هو موضح) وعالج الصفحات واحدةً تلو الأخرى |
| **DPI غير صحيح** | عدم استدعاء `setDpi` أو تركه على القيمة الافتراضية (96) | استدعِ `previewOptions.setDpi(القيمة_المطلوبة);` قبل `generatePreview` |
| **صيغة غير مدعومة** | محاولة معاينة ملف `.xlsx` تالف | تحقق من صحة الملف باستخدام Excel أو استعمل `Parser.isSupported` قبل المعالجة |

## الأسئلة المتكررة

**س: هل يمكنني توليد معاينات لملفات PDF والصور باستخدام GroupDocs.Parser؟**  
ج: نعم، نفس الـ API يعمل مع PDFs، مستندات Word، والعديد من صيغ الصور.

**س: كيف أغيّر صيغة الصورة الناتجة؟**  
ج: استدعِ `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (أو `Gif`, `Bmp`, إلخ).

**س: هل الأداء مشكلة مع ملفات Excel الضخمة؟**  
ج: الـ SDK يَتَدَفَّق الصفحات، مما يحافظ على استهلاك الذاكرة منخفضًا. للملفات الضخمة جدًا، فكر في المعالجة المتوازية على دفعات.

**س: كيف أتعامل مع الأخطاء أثناء توليد المعاينات؟**  
ج: غلف الكود بكتل `try‑catch` (كما هو موضح) وسجِّل تفاصيل الاستثناء. تأكد من إغلاق التدفقات في كتلة `finally` إذا لم تستخدم `try‑with‑resources`.

**س: هل تحتاج المكتبة إلى تثبيت Microsoft Office؟**  
ج: لا. GroupDocs.Parser حل Java نقي يعمل على أي منصة تدعم Java 8+.

## الخلاصة
أصبح لديك الآن طريقة جاهزة للإنتاج **لمعاينة ملفات Excel** و**تحويل xlsx إلى png** باستخدام GroupDocs.Parser. اضبط DPI، مجلد الإخراج، أو صيغة الصورة لتتناسب مع احتياجات مشروعك، ودمج هذا المقتطف في سير عمل إدارة المستندات الأكبر.

هل أنت مستعد للخطوة التالية؟ استكشف الوثائق الرسمية [هنا](https://docs.groupdocs.com/parser/java/) للحصول على خيارات عرض متقدمة، ملفات محمية بكلمة مرور، وتقنيات المعالجة الدفعة.

---

**آخر تحديث:** 2026-02-06  
**تم الاختبار مع:** GroupDocs.Parser 23.11 (أحدث نسخة وقت الكتابة)  
**المؤلف:** GroupDocs