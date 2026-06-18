---
date: '2026-01-27'
description: تعلم كيفية استخراج المرفقات من ملفات msg وطباعة بيانات التعريف الخاصة
  بها باستخدام GroupDocs.Parser للغة Java. يوضح هذا الدليل خطوةً بخطوة كيفية استخراج
  المرفقات، وتحليل ملفات msg في Java، ومعالجة بيانات التعريف بكفاءة.
keywords:
- GroupDocs.Parser for Java
- email attachment extraction
- metadata printing
title: استخراج المرفقات من ملف MSG باستخدام GroupDocs.Parser للغة Java
type: docs
url: /ar/java/metadata-extraction/extract-print-email-attachments-metadata-groupdocs-parser-java/
weight: 1
---

# استخراج المرفقات من ملفات msg باستخدام GroupDocs.Parser للغة Java

إدارة مرفقات البريد الإلكتروني برمجياً هي حاجة شائعة لمطوري Java الذين يعملون على الأرشفة الآلية، أو فحص الأمان، أو خطوط استخراج البيانات. في هذا البرنامج التعليمي ستتعلم **كيفية استخراج المرفقات من ملفات msg**، وطباعة بيانات التعريف الخاصة بها، وفهم لماذا هذه الطريقة ذات قيمة للمشاريع الواقعية.

## إجابات سريعة
- **ما المكتبة التي يجب أن أستخدمها؟** GroupDocs.Parser للغة Java.  
- **هل يمكنني استخراج المرفقات من ملفات .msg؟** نعم، توفر API وصولاً مباشراً إلى كل مرفق.  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية تعمل للتقييم؛ الترخيص الكامل مطلوب للإنتاج.  
- **ما نسخة Java المدعومة؟** Java 8 أو أعلى.  
- **هل المعالجة الجماعية ممكنة؟** بالتأكيد – اجمع كود العينة مع الحلقات أو التدفقات المتوازية.  

## ما هو “استخراج المرفقات من msg”؟
عند استلامك لملف Outlook `.msg`، يتم تخزين محتوى البريد الإلكتروني والملفات المرفقة معه معًا. “استخراج المرفقات من msg” يعني فصل كل ملف مرفق برمجياً بحيث يمكنك تخزينه أو تحليله أو تحويله بشكل مستقل.

## لماذا تستخدم GroupDocs.Parser للغة Java؟
- **دعم صيغ قوي** – يتعامل مع `.msg`، `.eml` والعديد من صيغ البريد الإلكتروني الأخرى.  
- **الوصول إلى بيانات التعريف** – استرجاع مسارات الملفات، الأحجام، والخصائص المخصصة دون الحاجة إلى التحليل اليدوي.  
- **API بسيط** – يتطلب أقل قدر من الكود لفتح رسالة، وتكرار المرفقات، وقراءة المحتوى.  
- **مركز على الأداء** – يستخدم البث و`try‑with‑resources` للحفاظ على استهلاك الذاكرة منخفضًا.  

## المتطلبات المسبقة
- **Java Development Kit (JDK):** الإصدار 8 أو أحدث.  
- **IDE:** IntelliJ IDEA، Eclipse، أو أي محرر متوافق مع Java.  
- **مكتبة GroupDocs.Parser:** مضافة عبر Maven أو إدراج JAR يدويًا (انظر أدناه).  

## إعداد GroupDocs.Parser للغة Java

### إعداد Maven
أضف التكوينات التالية إلى ملف `pom.xml` الخاص بك لدمج GroupDocs.Parser عبر Maven:

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
بدلاً من ذلك، قم بتحميل أحدث نسخة من [صفحة إصدارات GroupDocs.Parser للغة Java](https://releases.groupdocs.com/parser/java/). أضف ملف JAR إلى مسار الفئة (classpath) الخاص بمشروعك يدويًا.

#### الحصول على الترخيص
توفر GroupDocs عدة خيارات للترخيص:
- **نسخة تجريبية مجانية:** تقييم بميزات محدودة.  
- **ترخيص مؤقت:** وصول كامل خلال فترة تقييم قصيرة.  
- **ترخيص تجاري:** مطلوب للنشر في بيئة الإنتاج.  

قم بإدراج ملف الترخيص المكتسب كما هو موضح في الوثائق الرسمية لفتح جميع الميزات.

### التهيئة الأساسية
فيما يلي مثال بسيط يثبت أن المكتبة تم الإشارة إليها بشكل صحيح:

```java
import com.groupdocs.parser.Parser;

public class SetupExample {
    public static void main(String[] args) {
        // Initialize the Parser object with an email file path.
        try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY/sample.msg")) {
            System.out.println("GroupDocs.Parser is set up successfully!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

الآن بعد أن أصبح المحلل جاهزًا، دعنا نغوص في المهمة الأساسية: **كيفية استخراج المرفقات من msg** وطباعة بيانات التعريف الخاصة بها.

## كيفية استخراج المرفقات من msg باستخدام GroupDocs.Parser؟

### الخطوة 1: تهيئة كائن Parser
أنشئ مثالًا من `Parser` يشير إلى ملف `.msg` الذي تريد معالجته:

```java
try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY/sample.msg")) {
    // Proceed with attachment extraction.
}
```

### الخطوة 2: استخراج المرفقات
استخدم API الحاوية لاسترجاع كل مرفق مدمج في البريد الإلكتروني:

```java
Iterable<ContainerItem> attachments = parser.getContainer();
if (attachments == null) {
    System.out.println("No attachments found.");
    return;
}

for (ContainerItem item : attachments) {
    // Continue to parse each attachment.
}
```

### الخطوة 3: تحليل كل مرفق (java parse email attachments)
لكل `ContainerItem`، افتح مثالًا مخصصًا من المحلل. هذا يتيح لك قراءة محتوى المرفق إذا كان بصيغة نصية:

```java
try (Parser attachmentParser = item.openParser()) {
    try (TextReader reader = attachmentParser.getText()) {
        String attachmentText = reader == null ? "No text" : reader.readToEnd();
        // Handle or process the extracted text as needed.
    }
} catch (UnsupportedDocumentFormatException ex) {
    System.out.println("Unsupported document format.");
}
```

### الخطوة 4: طباعة بيانات تعريف المرفق
الآن بعد أن لديك كل كائن مرفق، يمكنك عرض بيانات تعريفه — مسار الملف، الحجم، وأي خصائص مخصصة:

```java
for (ContainerItem item : attachments) {
    System.out.println("File Path: " + item.getFilePath());

    // Proceed to retrieve metadata.
}
```

```java
for (MetadataItem metadata : item.getMetadata()) {
    System.out.println(String.format("%s: %s", metadata.getName(), metadata.getValue()));
}
```

## المشكلات الشائعة والحلول
- **صيغ غير مدعومة:** قم بالترقية إلى أحدث نسخة من GroupDocs.Parser إذا صادفت `UnsupportedDocumentFormatException`.  
- **مرفقات فارغة:** تحقق من أن ملف `.msg` المصدر يحتوي فعليًا على مرفقات؛ بعض الرسائل تحتوي على النص فقط.  
- **استهلاك الذاكرة:** عند معالجة صناديق بريد كبيرة، عالج المرفقات على دفعات وأغلق المحللات فورًا (نمط `try‑with‑resources` يساعد بالفعل).  

## التطبيقات العملية
استخراج وطباعة بيانات تعريف المرفقات مفيد لـ:
1. **أرشفة البيانات:** خزن المرفقات مع بيانات تعريفها لتدقيق الامتثال.  
2. **تصفية البريد الإلكتروني:** توجيه الرسائل تلقائيًا بناءً على نوع المرفق أو حجمه.  
3. **فحص الأمان:** إدخال بيانات التعريف إلى خطوط اكتشاف البرمجيات الخبيثة قبل الفحص العميق للمحتوى.  

## نصائح الأداء
- **إدارة الموارد:** استخدم دائمًا `try‑with‑resources` لتحرير المقابض الأصلية.  
- **المعالجة على دفعات:** عالج عددًا محدودًا من الرسائل لكل خيط للحفاظ على استهلاك الذاكرة متوقعًا.  
- **التنفيذ المتوازي:** استفد من `ExecutorService` في Java لتحليل عدة ملفات `.msg` بشكل متزامن.  

## الأسئلة المتكررة

**س: كيف يمكنني التعامل مع عدد كبير من ملفات .msg بكفاءة؟**  
ج: اجمع كود العينة مع مجموعة من الخيوط (مثل `Executors.newFixedThreadPool`) وعالج كل ملف في مهمته الخاصة. تذكر أن تجعل كائنات المحلل قصيرة العمر لتجنب تسرب الذاكرة.

**س: هل يمكنني استخراج المرفقات من رسائل مشفرة أو محمية بكلمة مرور؟**  
ج: يدعم GroupDocs.Parser ملفات `.msg` المشفرة عندما تزود كلمة المرور الصحيحة عبر تحميل مُنشئ `Parser`.

**س: ما هي حقول بيانات التعريف المتاحة لكل مرفق؟**  
ج: تشمل الحقول النموذجية `FilePath`، `Size`، `CreationTime`، وأي خصائص مخصصة يخزنها Outlook (مثل `ContentId`).

**س: هل هناك طريقة لتصفية المرفقات حسب نوع الملف قبل التحليل؟**  
ج: نعم، افحص `item.getFilePath()` أو `metadata.getName()` للحصول على امتداد الملف وتجاوز الأنواع غير المرغوبة.

**س: هل تعمل المكتبة على أنظمة غير Windows؟**  
ج: GroupDocs.Parser متعدد المنصات؛ يعمل على أي نظام تشغيل يدعم Java 8+.  

## الخلاصة
أنت الآن تمتلك سير عمل كامل وجاهز للإنتاج لـ **استخراج المرفقات من msg** وطباعة بيانات التعريف الخاصة بها باستخدام GroupDocs.Parser للغة Java. هذه الأساسيات تتيح لك بناء حلول أكثر غنىً—مثل خطوط الأرشفة، فاحصات الأمان، أو معالجات البريد الإلكتروني المخصصة—مع الحفاظ على نظافة الكود وأدائه.

استكشف قدرات إضافية مثل استخراج النص الكامل، تحليل البيانات المهيكلة، أو تحويل المرفقات إلى صيغ أخرى. توفر [وثائق GroupDocs](https://docs.groupdocs.com/parser/java/) أمثلة أعمق ومراجع API لمساعدتك على توسيع هذا الدرس أكثر.

---

**آخر تحديث:** 2026-01-27  
**تم الاختبار مع:** GroupDocs.Parser 25.5  
**المؤلف:** GroupDocs