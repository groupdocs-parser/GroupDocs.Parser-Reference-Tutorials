---
date: '2026-01-19'
description: تعلم كيفية استخراج الصور من ملفات PDF وحفظها بصيغة PNG باستخدام GroupDocs.Parser
  للغة Java. دليل خطوة بخطوة مع أمثلة على الشيفرة.
keywords:
- Java image extraction
- GroupDocs.Parser for Java
- image saving in Java
title: استخراج الصور من PDF وحفظها كـ PNG باستخدام GroupDocs.Parser – دليل Java كامل
type: docs
url: /ar/java/image-extraction/java-image-extraction-saving-groupdocs-parser/
weight: 1
---

# إتقان استخراج الصور في Java وحفظها باستخدام GroupDocs.Parser

في بيئة الأعمال سريعة الحركة اليوم، القدرة على **استخراج الصور من PDF** برمجيًا توفر ساعات لا تحصى من العمل اليدوي. سواء كنت بحاجة إلى سحب صور المنتجات من كتالوجات PDF، أو سحب الشعارات من العقود، أو جمع لقطات الشاشة من التقارير، فإن أتمتة العملية باستخدام Java وGroupDocs.Parser يمنحك حلاً موثوقًا وقابلًا للتوسع. في هذا الدليل سنستعرض سير العمل الكامل: إعداد المكتبة، استخراج الصور من PDF (وباقي الصيغ)، و**حفظ الصور كملفات PNG** جاهزة للاستخدام لاحقًا.

## إجابات سريعة
- **ماذا يعني “استخراج الصور من PDF”?** إنه عملية قراءة PDF برمجيًا واستخراج كل صورة نقطية مدمجة.  
- **أي مكتبة تتعامل مع ذلك في Java؟** GroupDocs.Parser for Java توفر API بسيط لاستخراج الصور عبر العديد من أنواع المستندات.  
- **هل يمكنني حفظ الملفات المستخرجة كـ PNG؟** نعم – استخدم `ImageOptions(ImageFormatدعاء `image.save()`.  
- **هل أحتاج إلى ترخيص؟** الإصدار التجريبي المجاني يعمل للتطوير؛ الترخيص التجاري مطلوب للإنتاج. نفس استدعاء `parser.getImages()` يعمل لتلك الصيغ أيضًا.

## ما هو “استخراج الصور من PDF”؟
استخراج الصور من PDF يعني تحديد كل كائن صورة نقطية مدمج في مستندرجاع بياناته الثنائية. يتيح لك ذلك إعادة استخدام الصور أو تحليلها أو أرشفتها دون الحاجة إلى فتح PDF يدويًا.

## لماذا استخراج الصور من PDF باستخدام GroupDocs.Parser؟
- **دعم متعدد الصيغ** – نفس الـ API يعمل مع Word وExcel وZIP والعديد من أنواع الملفات الأخرى.  
- **أداء عالي** – الكود الأصلي المُحسّن يتعامل مع المستندات الكبيرة بكفاءة.  
- **تكامل Java بسيط** – بضع أسطر من الكود تنقلك من الملف إلى ملفات الصور.  
- **تحكم كامل في الناتج** – أنت تقرر صيغة الصورة (PNG، JPEG، إلخ) واتفاقيات التسمية.

## المتطلبات المسبقة
- مجموعة تطوير Java (JDK) 8 أو أعلى مثبتة.  
- إلمام أساسي بـ Java I/O ومعالجة الاستثناءات.  
- Maven أو القدرة على إضافة ملفات JAR الخارجية إلى مشروعك.

### المكتبات والاعتمادات المطلوبة
للعمل مع GroupDocs.Parser لـ Java، أدرجه في مشروعك باستخدام Maven أو بتحميل المكتبة مباشرة.

### متطلبات إعداد البيئة
تأكد من أن بيئة التطوير المتكاملة (IntelliJ IDEA، Eclipse، VS Code) مُكوَّنة مع JDK وMaven (إذا اخترت مسار Maven).

### المتطلبات المعرفية
فهم تدفقات الملفات، try‑with‑resources، وأساسيّات Java الكائنية سيجعل التنفيذ أسهل.

## إعداد GroupDocs.Parser لـ Java
لاستخدام GroupDocs.Parser، أضفه إلى مشروعك باستخدام Maven أو حمّل المكتبة من صفحة الإصدارات الرسمية.

### إعداد Maven
أضف التكوين التالي إلى ملف `pom.xml` الخاص بك:

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
بدلاً من ذلك، حمّل أحدث نسخة من [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

### الحصول على الترخيص
ابدأ بنسخة تجريبية مجانية عن طريق تحميل المكتبة. للاستخدام المطول، فكر في شراء ترخيص أو الحصول على ترخيص مؤقت من [GroupDocs](https://purchase.groupdocs.com/temporary-license/).

#### التهيئة الأساسية والإعداد
لبدء استخدام GroupDocs.Parser في تطبيق Java الخاص بك، قم بتهيئته كما يلي:

```java
import com.groupdocs.parser.Parser;

public class InitializeParser {
    public static void main(String[] args) {
        // Initialize the Parser object with a document path
        try (Parser parser = new Parser("path/to/your/document")) {
            System.out.println("Parser initialized successfully.");
        } catch (Exception e) {
            System.err.println("Error initializing parser: " + e.getMessage());
        }
    }
}
```

## كيفية استخراج الصور من PDF باستخدام GroupDocs.Parser
الآن بعد أن أصبحت المكتبة جاهزة، دعنا نتعمق في الوظيفة الأساسية: استخراج الصور من PDF (أو أي مستند مدعوم).

### دليل التنفيذ
سنقسم التنفيذ إلى أقسام منطقية لتتمكن من متابعة كل خطوة بوضوح.

### الميزة 1: استخراج الصور من مستند
توضح هذه الميزة كيفية استخراج الصور باستخدام GroupDocs.Parser لـ Java.

#### نظرة عامة
سنقوم بإنشاء طريقة تستخرج جميع الصور من مستند محدد وتتحقق مما إذا كان استخراج الصور مدعومًا.

#### خطوات التنفيذ

##### الخطوة 1: إعداد الـ Parser
قم بتهيئة كائن `Parser` باستخدام مسار المستند الخاص بك:

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.data.PageImageArea;
import com.groupdocs.parser.exceptions.UnsupportedDocumentFormatException;

public class ExtractImagesFeature {
    public static void extractImages() throws UnsupportedDocumentFormatException, IOException {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/document.zip";
        
        try (Parser parser = new Parser(documentPath)) {
            Iterable<PageImageArea> images = parser.getImages();
            if (images == null) {
                throw new UnsupportedDocumentFormatException("Page images extraction isn't supported.");
            }
        }
    }
}
```

##### شرح
- **`parser.getImages()`**: يستخرج جميع مناطق الصور من المستند، سواء كان PDF أو Word أو Excel أو حتى أرشيف ZIP يحتوي على ملفات مدعومة.  
- **Error Handling**: يرمي استثناءً إذا كان تنسيق المستند لا يدعم استخراج الصور.

### الميزة 2: حفظ الصور المستخرجة إلى ملفات
بعد حصولك على كائنات الصورة، الخطوة التالية هي كتابتها إلى القرص كملفات PNG.

#### نظرة عامة
سنقوم بالتكرار على كل صورة مستخرجة وحفظها كملف PNG.

#### خطوات التنفيذ

##### الخطوة 1: حفظ كل صورة
قم بالتكرار عبر الصور واحفظها:

```java
import com.groupdocs.parser.data.PageImageArea;
import com.groupdocs.parser.options.ImageOptions;
import com.groupdocs.parser.options.ImageFormat;

import java.io.FileOutputStream;
import java.io.IOException;
import java.io.OutputStream;

public class SaveImagesFeature {
    public static void saveExtractedImages(Iterable<PageImageArea> images) throws IOException {
        String outputPath = "YOUR_OUTPUT_DIRECTORY/";
        int imageNumber = 0;
        
        ImageOptions options = new ImageOptions(ImageFormat.Png);

        for (PageImageArea image : images) {
            String outputFilePath = outputPath + String.format("%d.png", imageNumber++);
            
            try (OutputStream outputStream = new FileOutputStream(outputFilePath)) {
                image.save(outputStream, options);
            }
        }
    }
}
```

##### شرح
- **`ImageOptions(ImageFormat.Png)`**: يحدد الصيغة لحفظ الصور، مستوفيًا متطلب “حفظ الصور كـ png”.  
- **`image.save()`**: يكتب كل صورة إلى نظام الملفات باستخدام تدفق الإخراج المقدم.

#### نصائح استكشاف الأخطاء وإصلاحها
- تحقق من أن **document path** يشير إلى ملف موجود وأن التطبيق يمتلك أذونات القراءة.  
- تأكد من أن **output directory** موجود وأن العملية تمتلك أذونات الكتابة.  
- بالنسبة لملفات PDF الكبيرة جدًا، فكر في معالجة الصفحات على دفعات لتقليل استهلاك الذاكرة.

## كيفية حفظ الصور كـ PNG
المقتطف البرمجي أعلاه يوضح بالفعل حفظ الصور كـ PNG، لكن تذكر أنه يمكنك أيضًا اختيار JPEG أو BMP أو TIFF عن طريق استبدال `ImageFormat.Png` بالصيغ المطلوبة. PNG غير مضغوط، مما يجعله مثاليًا لقطات الشاشة والرسومات التي تحتاج إلى الحفاظ على الجودة.

## استخراج الصور من Word وExcel وملفات ZIP
دالة `getImages()` في GroupDocs.Parser تعمل عبر العديد من الصيغ:

- **Word (`.docx`)** – يستخرج الصور والرسومات المدمجة.  
- **Excel (`.xlsx`)** – يستخرج المخططات والصور المُدرجة.  
- **ZIP** – إذا كان الأرشيف يحتوي على مستندات مدعومة، سيقوم الـ parser بمعالجة كل إدخال وإرجاع صوره.

فقط استبدل المتغير `documentPath` بالمسار إلى ملف `.docx` أو `.xlsx` أو `.zip` الخاص بك وأعد استخدام نفس منطق الاستخراج والحفظ.

## تطبيقات عملية
يمكن دمج GroupDocs.Parser في أنظمة متعددة، مما يعزز الوظائف:

1. **Automated Document Processing** – استخراج الصور من الفواتير أو العقود لإدخال البيانات تلقائيًا.  
2. **Archiving Systems** – تخزين صور المستندات مركزيًا لاسترجاع بصري سريع.  
3. **Content Management Systems (CMS)** – سحب أصول الوسائط تلقائيًا من المستندات المرفوعة.  

## اعتبارات الأداء
للحفاظ على استجابة تطبيق Java الخاص بك عند معالجة دفعات كبيرة:

- **Close streams promptly** باستخدام try‑with‑resources (كما هو موضح).  
- **Reuse `ImageOptions`** بدلاً من إنشاء نسخة جديدة لكل صورة.  
- **Process documents sequentially or in a controlled thread pool** لتجنب ارتفاع الذاكرة.

## الخلاصة
في هذا الدرس تعلمت كيفية إعداد GroupDocs.Parser لـ Java، **استخراج الصور من PDF** (وباقي الصيغ)، و**حفظ الصور كملفات PNG**. هذه القدرة يمكن أن تسرّع بشكل كبير سير العمل المرتكز على المستندات في أي حل مبني على Java.

### الخطوات التالية
استكشف [GroupDocs documentation](https://docs.groupdocs.com/parser/java/) لاكتشاف ميزات إضافية مثل استخراج النص، تحليل الجداول، ودعم OCR.

### دعوة إلى اتخاذ الإجراء
ابدأ بتنفيذ هذه المقاطع في مشروعك اليوم—خط أنابيب استخراج الصور الآلي الخاص بك على بعد بضع أسطر من الكود فقط!

## الأسئلة المتكررة

**س: ما الصيغ التي يدعمها GroupDocs.Parser لاستخراج الصور؟**  
ج: PDFs، Word (`.docx`)، Excel (`.xlsx`)، PowerPoint، أرشيفات ZIP التي تحتوي على ملفات مدعومة، والعديد غيرها.

**س: هل يمكن استخراج الصور من ملفات PDF محمية بكلمة مرور؟**  
ج: نعم. قدم كلمة المرور عند إنشاء كائن `Parser`.

**س: كيف يجب أن أتعامل مع المستندات الكبيرة جدًا؟**  
ج: عالجها صفحة بصفحة، حرّر الموارد بعد كل دفعة، وفكّر في زيادة حجم heap الخاص بـ JVM إذا لزم الأمر.

**س: هل يمكن استخراج أنواع بيانات أخرى غير الصور؟**  
ج: بالتأكيد. GroupDocs.Parser يستخرج أيضًا النصوص، الجداول، والبيانات الوصفية.

**س: ماذا لو لم يكن استخراج الصور مدعومًا لملف معين؟**  
ج: سيعيد الـ API `null` أو يرمي `UnsupportedDocumentFormatException`؛ يمكنك التقاط ذلك واللجوء إلى استراتيجية بديلة (مثل تحويل الملف أولاً).

## الموارد
- [GroupDocs Documentation](https://docs.groupdocs.com/parser/java/)
- [API Reference](https://apireference.groupdocs.com/parser/java)

---

**آخر تحديث:** 2026-01-19  
**تم الاختبار مع:** GroupDocs.Parser 25.5 for Java  
**المؤلف:** Group