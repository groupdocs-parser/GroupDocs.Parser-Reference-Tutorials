---
date: '2026-02-19'
description: تعرّف على كيفية قراءة رموز QR في ملفات PDF بلغة Java باستخدام GroupDocs.Parser
  وتصدير بيانات الباركود إلى XML.
keywords:
- Java PDF barcode extraction
- GroupDocs.Parser for Java
- XML export from PDF
title: كيفية قراءة رموز QR في ملفات PDF بلغة Java باستخدام GroupDocs.Parser
type: docs
url: /ar/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# كيفية قراءة رموز QR في ملفات PDF باستخدام Java و GroupDocs.Parser

في سير عمل الأعمال الحديثة، **كيفية قراءة رموز QR** من مستندات PDF يمكن أن تكون الفارق بين عنق زجاجة إدخال بيانات يدوي وخط أنابيب مؤتمت بالكامل. سواء كنت تتعامل مع قوائم الشحن، أو إيصالات التجزئة، أو كتالوجات المنتجات، فإن استخراج معلومات QR بسرعة وبشكل موثوق أمر أساسي. يشرح هذا الدليل كيفية استخدام **GroupDocs.Parser for Java** لقراءة رموز QR (وبطاقات باركود أخرى) من ملفات PDF وتصدير النتائج إلى ملف XML نظيف يمكن للأنظمة اللاحقة استهلاكه.

## إجابات سريعة
- **ماذا يفعل GroupDocs.Parser for Java؟** يقرأ ملفات PDF ويستخرج البيانات المهيكلة مثل الباركود.  
- **كيف يتم استخراج رموز QR؟** عن طريق تكوين `BarcodeOptions` بنوع QR واستدعاء `parser.getBarcodes()`.  
- **هل يمكنني قراءة رموز QR في Java؟** نعم—قم بتعيين نوع الباركود إلى `"QR"` في الخيارات.  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية تعمل للاختبار؛ يلزم ترخيص تجاري للإنتاج.  
- **ما نسخة Java المطلوبة؟** يوصى بـ Java 8 أو أعلى.

## ما هو “كيفية قراءة QR” في سياق معالجة PDF؟
قراءة رموز QR من ملفات PDF تعني مسح كل صفحة للرسومات المشفرة بـ QR، فك تشفير البيانات المضمنة، وإرجاعها بتنسيق مناسب للبرامج. يقوم GroupDocs.Parser بتجريد تحليل الصورة منخفض المستوى حتى تتمكن من التركيز على منطق الأعمال بدلاً من معالجة البكسلات.

## لماذا تستخدم GroupDocs.Parser لاستخراج QR؟
- **دقة عالية:** الخوارزميات المدمجة لمعالجة الصور تتعامل مع المسحات منخفضة الدقة.  
- **خيارات الأداء:** اختر `QualityMode.Low` للسرعة أو `QualityMode.High` للدقة القصوى.  
- **دعم صيغ متعددة:** يعمل مع ملفات PDF، الصور، وحتى مستندات Office، بحيث يمكنك إعادة استخدام قاعدة الشيفرة نفسها لأنواع ملفات مختلفة.

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

### التحميل المباشر
بدلاً من ذلك، قم بتحميل أحدث JAR من [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

#### خطوات الحصول على الترخيص
- **نسخة تجريبية مجانية:** نسخة تجريبية لمدة 30 يومًا مع مجموعة كاملة من الميزات.  
- **ترخيص مؤقت:** طلب مفتاح مؤقت لتقييم ممتد.  
- **شراء:** الحصول على ترخيص تجاري للنشر في بيئات الإنتاج.

### التهيئة الأساسية والإعداد
أنشئ كائن `Parser` يشير إلى ملف PDF الذي تريد تحليله:

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

## كيفية قراءة رموز QR في ملفات PDF باستخدام Java و GroupDocs.Parser
### الخطوة 1: التحقق من دعم الباركود
قبل محاولة الاستخراج، تأكد من أن صيغة المستند تدعم مسح الباركود:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*شرح:* هذا الفحص يمنع حدوث أخطاء وقت التشغيل على الأنواع غير المدعومة.

### الخطوة 2: تكوين خيارات الباركود (قراءة رموز QR في Java)
حدد جودة المسح وحدد أنك مهتم برموز QR:

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*شرح:* `QualityMode.Low` يسرّع المعالجة؛ غير إلى `High` إذا كنت تحتاج إلى دقة إضافية. المعامل `"QR"` يخبر المحرك بالبحث عن بطاقات باركود من نوع QR فقط.

### الخطوة 3: استخراج بيانات QR
احصل على معلومات الباركود من كل صفحة في ملف PDF:

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*شرح:* `parser.getBarcodes` تُعيد مجموعة قابلة للتكرار من كائنات `PageBarcodeArea`، كل منها يحتوي على قيمة QR المفكوكة وموقعها على الصفحة.

## تصدير البيانات المستخرجة إلى XML
### الخطوة 4: تهيئة مُصدّر XML
أنشئ مُصدّرًا سيحوّل مجموعة الباركود إلى ملف XML منظم جيدًا:

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

*شرح:* ملف `data.xml` الناتج يحتوي على عنصر `<Barcode>` واحد لكل رمز QR، مع سمات لرقم الصفحة، الإحداثيات، والقيمة المفكوكة.

## تطبيقات عملية
1. **إدارة المخزون:** تعبئة قواعد بيانات المخزون تلقائيًا بقراءة علامات QR على ملفات PDF الخاصة بالشحن الوارد.  
2. **رؤية سلسلة التوريد:** تتبع الطرود في الوقت الحقيقي عن طريق استخراج معرفات QR المدمجة في مستندات اللوجستيات.  
3. **إيصالات التجزئة:** استخراج معلومات ترويجية أو ضمان من رموز QR المطبوعة على الإيصالات الرقمية.

## اعتبارات الأداء
- **إدارة الذاكرة:** بالنسبة لملفات PDF الكبيرة جدًا، عالج الصفحات بطريقة تدفقية بدلاً من تحميل الملف بالكامل في الذاكرة.  
- **اختيار QualityMode:** استخدم `Low` للمعالجة الجماعية؛ غير إلى `High` عند التعامل مع مسحات منخفضة الدقة.  
- **تحديثات المكتبة:** حافظ على تحديث GroupDocs.Parser للاستفادة من أحدث تحسينات الأداء وإصلاحات الأخطاء.

## المشكلات الشائعة & استكشاف الأخطاء
| العَرَض | السبب المحتمل | الحل |
|---------|--------------|-----|
| لا يتم إرجاع أي باركود | تم تحديد نوع باركود غير صحيح | غيّر `"QR"` إلى النوع المناسب (مثال: `"CODE_128"`). |
| خطأ نفاد الذاكرة في ملفات PDF الكبيرة | تم تحميل المستند بالكامل مرة واحدة | عالج الصفحات بشكل فردي أو زد حجم ذاكرة JVM (`-Xmx2g`). |
| ملف XML فارغ | `exportBarcodes` تم استدعاؤه قبل الاستخراج | تأكد من أن `parser.getBarcodes(options)` تُعيد بيانات قبل التصدير. |

## الأسئلة المتكررة
**س: هل يمكنني استخراج الباركود من ملفات الصور باستخدام GroupDocs.Parser؟**  
ج: نعم، المكتبة تدعم استخراج الباركود من صيغ الصور الشائعة (PNG، JPEG، TIFF).

**س: ما صيغ الباركود التي يتم التعرف عليها؟**  
ج: QR، Code 39، Code 128، DataMatrix، PDF417، والعديد غيرها. راجع وثائق API للقائمة الكاملة.

**س: كيف يجب أن أتعامل مع ملفات PDF المحمية بكلمة مرور؟**  
ج: مرّر كلمة المرور إلى مُنشئ `Parser`: `new Parser(filePath, "password")`.

**س: هل النسخة التجريبية كافية لاختبار الإنتاج؟**  
ج: النسخة التجريبية توفر جميع الوظائف ولكنها تضيف علامة مائية إلى البيانات المستخرجة. للإنتاج، احصل على ترخيص تجاري.

**س: ماذا لو كان ملف PDF يحتوي على كل من رموز QR والباركود الخطي؟**  
ج: أنشئ عدة مثيلات من `BarcodeOptions` أو مرّر مصفوفة من الأنواع للمسح عن جميع الصيغ المطلوبة في تمريرة واحدة.

---

**آخر تحديث:** 2026-02-19  
**تم الاختبار مع:** GroupDocs.Parser 25.5  
**المؤلف:** GroupDocs  

## الموارد
- [توثيق GroupDocs.Parser Java](https://docs.groupdocs.com/parser/java/)
- [مرجع API](https://reference.groupdocs.com/parser/java)
- [تحميل GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [مستودع GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [منتدى الدعم المجاني](https://forum.groupdocs.com/c/parser)
- [طلب ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/)

---