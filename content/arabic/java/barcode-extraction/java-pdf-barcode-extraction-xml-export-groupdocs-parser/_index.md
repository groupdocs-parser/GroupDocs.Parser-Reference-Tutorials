---
date: '2026-10-12'
description: تعلم كيفية استخراج QR من PDF في Java باستخدام GroupDocs.Parser وتصدير
  بيانات الباركود إلى XML للمعالجة اللاحقة.
keywords:
- extract QR from PDF
- how to read QR
- read QR codes Java
- parse QR codes Java
- PDF QR code extraction
lastmod: '2026-10-12'
og_description: تعلم كيفية استخراج QR من PDF في Java باستخدام GroupDocs.Parser وتصدير
  بيانات الباركود إلى XML للمعالجة اللاحقة.
og_image_alt: Guide showing Java code that extracts QR codes from PDF files with GroupDocs.Parser
  and saves results as XML
og_title: كيفية استخراج QR من PDF في Java باستخدام GroupDocs.Parser
schemas:
- author: GroupDocs
  dateModified: '2026-10-12'
  description: Learn how to extract QR from PDF in Java using GroupDocs.Parser and
    export the barcode data to XML for downstream processing.
  headline: How to extract QR from PDF in Java with GroupDocs.Parser
  type: TechArticle
- description: Learn how to extract QR from PDF in Java using GroupDocs.Parser and
    export the barcode data to XML for downstream processing.
  name: How to extract QR from PDF in Java with GroupDocs.Parser
  steps:
  - name: verify barcode support
    text: 'Before attempting extraction, confirm that the document format supports
      barcode scanning: *Explanation:* This guard prevents runtime errors on unsupported
      file types.'
  - name: configure barcode options (read QR codes Java)
    text: '`BarcodeOptions` is a configuration object that lets you specify which
      barcode symbologies to detect, set the scanning quality mode, and fine‑tune
      parameters such as detection thresholds, ensuring optimal performance for the
      target QR codes. *Explanation:* `QualityMode.Low` speeds up processing; swi'
  - name: extract the QR data
    text: '`parser.getBarcodes(options)` scans the document using the provided `BarcodeOptions`
      and returns a collection of `PageBarcodeArea` objects, each encapsulating the
      decoded QR value, the page number, and the exact coordinates of the barcode
      within the page, allowing precise downstream handling. *Expla'
  - name: initialise the XML exporter
    text: '`XmlExporter` is a utility class that transforms a collection of barcode
      objects into a well‑structured XML document, automatically generating elements
      for each barcode with attributes for page index, position, and decoded value,
      which can then be saved or streamed to other systems. *Explanation:* T'
  - name: write the XML file
    text: 'Save the extracted QR information to disk: *Explanation:* The resulting
      `data.xml` contains one `<Barcode>` element per QR code, with attributes for
      page number, coordinates, and decoded value.'
  type: HowTo
- questions:
  - answer: Yes, the library supports barcode extraction from common image formats
      (PNG, JPEG, TIFF).
    question: Can I extract barcodes from image files using GroupDocs.Parser?
  - answer: QR, Code 39, Code 128, DataMatrix, PDF417, and many more. Refer to the
      API docs for the full list.
    question: What barcode formats are recognized?
  - answer: 'Pass the password to the `Parser` constructor: `new Parser(filePath,
      "password")`.'
    question: How should I handle password‑protected PDFs?
  - answer: The trial provides full functionality but adds a watermark to extracted
      data. For production, acquire a commercial license.
    question: Is the trial version sufficient for production testing?
  - answer: Create multiple `BarcodeOptions` instances or pass an array of types to
      scan for all needed formats in one pass.
    question: What if my PDF contains both QR and linear barcodes?
  type: FAQPage
tags:
- extract QR
- GroupDocs.Parser
- Java PDF processing
- barcode extraction
- XML export
title: كيفية استخراج QR من PDF في Java باستخدام GroupDocs.Parser
type: docs
url: /ar/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# كيفية استخراج QR من PDF باستخدام Java وGroupDocs.Parser

في سير عمل الأعمال الحديثة، **استخراج QR من PDF** يمكن أن يحول عنق زجاجة الإدخال اليدوي للبيانات إلى خط أنابيب مؤتمت بالكامل. سواء كنت تتعامل مع قوائم الشحن، أو إيصالات التجزئة، أو كتالوجات المنتجات، فإن سحب معلومات QR بسرعة وبشكل موثوق أمر أساسي للأنظمة اللاحقة. يشرح هذا الدليل كيفية استخدام **GroupDocs.Parser for Java** لقراءة رموز QR (وبقية الباركود) من ملفات PDF وتصدير النتائج إلى ملف XML نظيف يمكن لنظام ERP أو المخزون أو منصة التحليل الخاصة بك استهلاكه.

## إجابات سريعة
- **ما الذي يفعله GroupDocs.Parser for Java؟** يقوم بقراءة ملفات PDF واستخراج البيانات المهيكلة مثل الباركود والجداول والنص.  
- **كيف يتم استخراج رموز QR؟** قم بتكوين `BarcodeOptions` بنوع QR واستدعِ `parser.getBarcodes()`.  
- **هل يمكنني قراءة رموز QR في Java؟** نعم—قم بتعيين نوع الباركود إلى `"QR"` في الخيارات.  
- **هل أحتاج إلى ترخيص؟** الإصدار التجريبي يعمل للاختبار؛ يتطلب الترخيص التجاري للإنتاج.  
- **ما نسخة Java المطلوبة؟** يوصى باستخدام Java 8 أو أعلى.

## ما هو “استخراج QR من PDF” في سياق معالجة PDF؟
يعني استخراج QR من PDF مسح كل صفحة للبحث عن الرسومات المشفرة بـ QR، وفك تشفير البيانات المضمنة، وإرجاعها بصيغة صديقة للبرامج. يقوم GroupDocs.Parser بتجريد تحليل الصورة منخفض المستوى حتى تتمكن من التركيز على منطق الأعمال بدلاً من معالجة البكسل.

## لماذا استخدام GroupDocs.Parser لاستخراج QR؟
يدعم GroupDocs.Parser **أكثر من 30 تنسيق إدخال** ويمكنه معالجة ملفات PDF حتى **500 MB** دون تحميل الملف بالكامل إلى الذاكرة، مما يوفر نتائج عالية الدقة حتى على المسحات منخفضة الدقة. يمكنك اختيار `QualityMode.Low` للسرعة أو `QualityMode.High` للدقة القصوى، وتعمل نفس الـ API مع ملفات PDF والصور ومستندات Office، مما يلغي الحاجة إلى مكتبات متعددة.

## المتطلبات المسبقة
- **GroupDocs.Parser for Java** (الإصدار 25.5 أو أحدث).  
- Maven أو تحميل JAR يدويًا.  
- بيئة تطوير Java 8+ (IntelliJ IDEA، Eclipse، أو أي محرر).  

## إعداد GroupDocs.Parser للـ Java
### استخدام Maven
أضف مستودع GroupDocs والاعتماد إلى ملف `pom.xml` الخاص بك:

```xml
<repositories>
    <repository>
        <id>repository.groupdocs.com</id>
        <name>GroupDocs Repository</name>
        <url>https://releases.groupdocs.com/parser/java/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-parser</artifactId>
        <version>25.5</version>
    </dependency>
</dependencies>
```

```xml
<repositories>
    <repository>
        <id>repository.groupdocs.com</id>
        <name>GroupDocs Repository</name>
        <url>https://releases.groupdocs.com/parser/java/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-parser</artifactId>
        <version>25.5</version>
    </dependency>
</dependencies>
```

### التحميل المباشر
بدلاً من ذلك، قم بتحميل أحدث JAR من [توثيق GroupDocs.Parser Java](https://releases.groupdocs.com/parser/java/).

#### خطوات الحصول على الترخيص
- **إصدار تجريبي مجاني:** تجربة لمدة 30 يومًا مع مجموعة كاملة من الميزات.  
- **ترخيص مؤقت:** طلب مفتاح مؤقت لتقييم ممتد.  
- **شراء:** الحصول على ترخيص تجاري للنشر في بيئة الإنتاج.

### التهيئة الأساسية والإعداد
إنشاء مثال `Parser` يشير إلى ملف PDF الذي تريد تحليله:

`Parser` هو الفئة الأساسية في GroupDocs.Parser التي تمثل مستندًا وتوفر طرقًا لاستخراج المحتوى مثل النصوص والجداول والباركود.  

```java
import com.groupdocs.parser.Parser;

class BarcodeExtractor {
    public static void main(String[] args) {
        // Initialize Parser object with the path to your PDF document.
        try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY")) {
            // Additional setup and usage will follow in the next sections.
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## كيفية قراءة رموز QR في ملفات PDF باستخدام Java وGroupDocs.Parser
يتضمن قراءة رموز QR في ملفات PDF باستخدام Java وGroupDocs.Parser إنشاء مثال parser، وتكوين خيارات الباركود لاستهداف أنواع QR، واستدعاء طريقة استخراج الباركود، ثم معالجة كائنات الباركود المرتجعة. العملية بسيطة، تعمل على أي صفحة PDF، وتعيد القيم المفكوكة مع بيانات ميتا موقعية لمزيد من المعالجة.

### الخطوة 1: التحقق من دعم الباركود
قبل محاولة الاستخراج، تأكد من أن تنسيق المستند يدعم مسح الباركود:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*شرح:* هذا الحارس يمنع أخطاء وقت التشغيل على أنواع الملفات غير المدعومة.

### الخطوة 2: تكوين خيارات الباركود (قراءة رموز QR في Java)
`BarcodeOptions` هو كائن تكوين يتيح لك تحديد أي رموز باركود تريد اكتشافها، وتعيين وضع جودة المسح، وضبط المعلمات مثل عتبات الكشف، لضمان أداء مثالي لرموز QR المستهدفة.  

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*شرح:* `QualityMode.Low` يسرّع المعالجة؛ قم بالتبديل إلى `High` إذا كنت تحتاج إلى دقة إضافية. المعامل `"QR"` يخبر المحرك بالبحث عن باركود من نوع QR فقط.

### الخطوة 3: استخراج بيانات QR
`parser.getBarcodes(options)` يمسح المستند باستخدام `BarcodeOptions` المقدمة ويعيد مجموعة من كائنات `PageBarcodeArea`، كل منها يحتوي على قيمة QR المفكوكة، ورقم الصفحة، والإحداثيات الدقيقة للباركود داخل الصفحة، مما يسمح بمعالجة دقيقة لاحقة.  

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*شرح:* `parser.getBarcodes` يعيد مجموعة قابلة للتكرار من كائنات `PageBarcodeArea`، كل منها يحتوي على قيمة QR المفكوكة وموقعها على الصفحة.

## تصدير البيانات المستخرجة إلى XML
### الخطوة 4: تهيئة مُصدّر XML
`XmlExporter` هو فئة مساعدة تحول مجموعة من كائنات الباركود إلى مستند XML منظم جيدًا، وتولد تلقائيًا عناصر لكل باركود مع سمات لفهرس الصفحة، والموقع، والقيمة المفكوكة، والتي يمكن بعدها حفظها أو بثها إلى أنظمة أخرى.  

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*شرح:* `XmlExporter` يتعامل مع تسلسل كائنات الباركود إلى XML قياسي، جاهز للتكامل مع أنظمة ERP أو المخزون.

### الخطوة 5: كتابة ملف XML
احفظ معلومات QR المستخرجة إلى القرص:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*شرح:* الملف الناتج `data.xml` يحتوي على عنصر `<Barcode>` واحد لكل رمز QR، مع سمات لرقم الصفحة، والإحداثيات، والقيمة المفكوكة.

## تطبيقات عملية
1. **إدارة المخزون:** ملء قواعد بيانات المخزون تلقائيًا بقراءة علامات QR على ملفات PDF الخاصة بالشحن الوارد.  
2. **رؤية سلسلة الإمداد:** تتبع الطرود في الوقت الحقيقي عن طريق استخراج معرفات QR المدمجة في مستندات اللوجستيات.  
3. **إيصالات التجزئة:** استخراج معلومات ترويجية أو ضمان من رموز QR المطبوعة على الإيصالات الرقمية.

## اعتبارات الأداء
- **إدارة الذاكرة:** بالنسبة لملفات PDF الكبيرة جدًا، عالج الصفحات بطريقة تدفقية بدلاً من تحميل الملف بالكامل إلى الذاكرة.  
- **اختيار QualityMode:** استخدم `Low` للمعالجة الجماعية؛ وانتقل إلى `High` عند التعامل مع مسحات منخفضة الدقة.  
- **تحديثات المكتبة:** حافظ على تحديث GroupDocs.Parser للاستفادة من أحدث تحسينات الأداء وإصلاحات الأخطاء.

## المشكلات الشائعة & استكشاف الأخطاء
| العَرَض | السبب المحتمل | الحل |
|---------|--------------|-----|
| لم يتم إرجاع أي باركود | تم تحديد نوع باركود غير صحيح | غيّر `"QR"` إلى النوع المناسب (مثال: `"CODE_128"`). |
| خطأ نفاد الذاكرة على ملفات PDF الكبيرة | تم تحميل المستند بالكامل مرة واحدة | عالج الصفحات بشكل فردي أو زد حجم كومة JVM (`-Xmx2g`). |
| ملف XML فارغ | `exportBarcodes` تم استدعاؤه قبل الاستخراج | تأكد من أن `parser.getBarcodes(options)` يعيد بيانات قبل التصدير. |

## الأسئلة المتكررة
**س: هل يمكنني استخراج الباركود من ملفات الصور باستخدام GroupDocs.Parser؟**  
ج: نعم، تدعم المكتبة استخراج الباركود من صيغ الصور الشائعة (PNG، JPEG، TIFF).

**س: ما هي صيغ الباركود التي يتم التعرف عليها؟**  
ج: QR، Code 39، Code 128، DataMatrix، PDF417، والعديد غيرها. راجع وثائق الـ API للقائمة الكاملة.

**س: كيف يجب أن أتعامل مع ملفات PDF المحمية بكلمة مرور؟**  
ج: مرّر كلمة المرور إلى مُنشئ `Parser`: `new Parser(filePath, "password")`.

**س: هل النسخة التجريبية كافية لاختبار الإنتاج؟**  
ج: النسخة التجريبية توفر جميع الوظائف لكنها تضيف علامة مائية إلى البيانات المستخرجة. للإنتاج، احصل على ترخيص تجاري.

**س: ماذا لو كان ملف PDF يحتوي على كل من رموز QR والباركود الخطية؟**  
ج: أنشئ عدة مثيلات من `BarcodeOptions` أو مرّر مصفوفة من الأنواع للمسح عن جميع الصيغ المطلوبة في تمريرة واحدة.

---

**آخر تحديث:** 2026-10-12  
**تم الاختبار مع:** GroupDocs.Parser 25.5  
**المؤلف:** GroupDocs  

## الموارد
- [توثيق GroupDocs.Parser Java](https://docs.groupdocs.com/parser/java/)
- [مرجع API](https://reference.groupdocs.com/parser/java)
- [تحميل GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [مستودع GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [منتدى الدعم المجاني](https://forum.groupdocs.com/c/parser)
- [طلب ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/)

## دروس ذات صلة
- [استخراج باركود PDF باستخدام GroupDocs Parser Java](/parser/java/barcode-extraction/extract-barcode-pdf-groupdocs-parser-java/)
- [كيفية تحميل PDF من URL باستخدام GroupDocs.Parser للـ Java](/parser/java/document-loading/)
- [استخراج بيانات نموذج PDF باستخدام GroupDocs.Parser في Java](/parser/java/form-extraction/groupdocs-parser-java-pdf-form-extraction/)