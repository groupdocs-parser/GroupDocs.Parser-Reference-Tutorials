---
date: '2025-12-29'
description: تعلم كيفية استخراج الصور من المستندات وكيفية تصفية الموارد باستخدام GroupDocs.Parser
  للغة Java. يغطي هذا الدليل التكوين، ومعالجات مخصصة، وأمثلة عملية.
keywords:
- GroupDocs.Parser for Java
- external resource loading in Java
- custom handlers in GroupDocs
title: استخراج الصور من المستندات باستخدام GroupDocs.Parser Java – دليل
type: docs
url: /ar/java/document-loading/master-groupdocs-parser-external-resources-java/
weight: 1
---

# استخراج الصور من المستندات وتصفية الموارد باستخدام GroupDocs.Parser Java

استخراج الصور من المستندات هو طلب شائع عند بناء خطوط معالجة المستندات. في هذا الدرس ستكتشف **كيفية استخراج الصور من المستندات** باستخدام GroupDocs.Parser للـ Java، وستتعلم أيضًا **كيفية تصفية الموارد** بحيث يتم تحميل الملفات التي تحتاجها فقط. سنستعرض إعداد المكتبة، إنشاء معالج مخصص `ExternalResourceHandler`، وتطبيق منطق التصفية للحفاظ على تطبيقك سريعًا وآمنًا.

## إجابات سريعة
- **ماذا يفعل GroupDocs.Parser؟** يقوم بتحليل مجموعة واسعة من صيغ المستندات ويمنحك الوصول إلى النصوص، الصور، وغيرها من الموارد المدمجة.  
- **هل يمكنني تخطي الصور غير المرغوب فيها؟** نعم—من خلال تنفيذ `ExternalResourceHandler` مخصص يمكنك تحديد الموارد التي تريد تحميلها.  
- **ما نسخة Maven المطلوبة؟** استخدم GroupDocs.Parser Java 25.5 أو أحدث.  
- **هل أحتاج إلى ترخيص؟** نسخة تجريبية مجانية تكفي للتقييم؛ الترخيص الدائم مطلوب للإنتاج.  
- **هل هذا النهج آمن للاستخدام متعدد الخيوط؟** كائنات التحليل لا تُشارك بين الخيوط؛ أنشئ نسخة جديدة من `Parser` لكل خيط.

## ما معنى “استخراج الصور من المستندات”؟
عندما يحتوي المستند على صور مدمجة، مخططات، أو وسائط أخرى، يعني “استخراج الصور من المستندات” استرجاع تلك الملفات الثنائية برمجيًا حتى تتمكن من تخزينها أو عرضها أو معالجتها خارج الملف الأصلي.

## لماذا تصفية الموارد أثناء استخراج الصور؟
تساعدك تصفية الموارد على:
- تقليل استهلاك الذاكرة بتجاهل الملفات الكبيرة أو غير ذات الصلة.  
- تحسين الأمان بمنع تحميل المحتوى الذي قد يكون غير آمن.  
- تسريع المعالجة، خاصةً مع المستندات الضخمة التي تحتوي على العديد من الكائنات المدمجة.

## المتطلبات المسبقة

- **مجموعة تطوير جافا (JDK)** – الإصدار 8 أو أعلى.  
- **Maven** – لإدارة التبعيات.  
- إلمام أساسي بـ Java I/O ومعالجة الاستثناءات.

## إعداد GroupDocs.Parser للـ Java

أضف مستودع GroupDocs وتبعيات الـ parser إلى ملف `pom.xml` الخاص بك:

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

بدلاً من ذلك، حمّل أحدث نسخة من [إصدارات GroupDocs.Parser للـ Java](https://releases.groupdocs.com/parser/java/).

### الحصول على الترخيص
- **نسخة تجريبية مجانية** – استكشف الميزات الأساسية دون تكلفة.  
- **ترخيص مؤقت** – يفتح جميع الوظائف أثناء فترة التقييم.  
- **ترخيص مُشتَرٍ** – مطلوب للنشر التجاري.

## كيفية تصفية الموارد أثناء استخراج الصور

### الخطوة 1: إنشاء معالج مخصص
عرّف فئة تمتد من `ExternalResourceHandler`. داخل طريقة `onLoading` تقرّر أي الموارد تحتفظ بها.

```java
import com.groupdocs.parser.options.ExternalResourceHandler;
import com.groupdocs.parser.data.ExternalResourceLoadingArgs;

class Handler extends ExternalResourceHandler {
    @Override
    public void onLoading(ExternalResourceLoadingArgs args) {
        if (!args.getUri().endsWith("installation.png")) {
            args.setSkipped(true);
        }
        super.onLoading(args);
    }
}
```

### الخطوة 2: تكوين `ParserSettings` باستخدام المعالج
مرّر نسخة الـ `Handler` إلى `ParserSettings` واستخدمها عند فتح المستند.

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.data.PageImageArea;
import com.groupdocs.parser.exceptions.IOException;
import com.groupdocs.parser.options.ParserSettings;

public class LoadExternalResources {
    public static void run() throws IOException {
        ParserSettings settings = new ParserSettings(new Handler());
        
        try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY", settings)) {
            Iterable<PageImageArea> images = parser.getImages();
            
            for (PageImageArea image : images) {
                System.out.println(image.getFileType());
            }
        }
    }
}
```

### الخطوة 3: ضبط منطق التصفية بدقة
إذا احتجت قواعد أكثر تعقيدًا—مثل التصفية حسب حجم الصورة، الصيغة، أو نمط الـ URI—قم بتمديد طريقة `onLoading` وفقًا لذلك:

```java
@Override
public void onLoading(ExternalResourceLoadingArgs args) {
    if (!args.getUri().endsWith("installation.png")) {
        args.setSkipped(true);
    }
}
```

## تطبيقات عملية

1. **أنظمة إدارة المستندات** – استخراج الصور الضرورية فقط من العقود الممسوحة لإنشاء صور مصغرة.  
2. **خدمات استخراج البيانات** – تخطي الرسومات الزخرفية والتركيز على المخططات التي تحتوي على بيانات قيمة.  
3. **أدوات استخراج الويب** – تصفية بكسلات التتبع أثناء جلب الوسائط المفيدة من المستندات القائمة على HTML.

## اعتبارات الأداء
- **التصفيةًا**: طبّق المعالج المخصص قبل iterating على الموارد لتجنب تحميل بيانات غير مرغوب فيها إلى الذاكرة.  
- **تحرير الموارد فورًا**: استخدم `try‑with‑resources` (`try (Parser parser = …)`) لتحرير الموارد الأصلية.  
- **المعالجة غير المتزامنة**: للدفعات الكبيرة، عالج المستندات في تدفقات متوازية مع الحفاظ على كل نسخة `Parser` محصورة في خيط واحد.

## المشكلات الشائعة والحلول
| المشكلة | السبب | الحل |
|-------|--------|------|
| عدم إرجاع أي صور | المعالج يتخطى جميع الموارد عن غير قصد | تحقق من شرط `if` وتأكد أن `args.setSkipped(true)` يُستدعى فقط للـ URIs غير المطلوبة. |
| `IOException` عند ملفات كبيرة | نقص في ذاكرة الـ heap | زد حجم heap للـ JVM (`-Xmx2g`) أو عالج الصفحات على دفعات أصغر. |
| عدم التعرف على الترخيص | استخدام ملف DLL تجريبي مع كود الإنتاج | عيّن مسار ملف الترخيص الصحيح عبر `License.setLicense("path/to/license")`. |

## الأسئلة المتكررة

**س: ما هو الهدف الأساسي من استخدام `ExternalResourceHandler` مخصص؟**  
ج: يتيح لك التحكم في الموارد الخارجية التي يتم تحميلها، مما يعزز الأمان والأداء عبر تصفية الملفات غير الضرورية.

**س: هل يمكنني استخدام GroupDocs.Parser للـ Java بدون ترخيص؟**  
ج: نعم، تتوفر نسخة تجريبية مجانية، لكن بعض الميزات المتقدمة قد تكون محدودة حتى تحصل على ترخيص مؤقت أو دائم.

**س: كيف أتعامل مع الاستثناءات أثناء التحليل باستخدام GroupDocs.Parser؟**  
ج: غلف استدع التحليل بكتل `try‑catch` للـ `IOException` وغيرها من الاستثناءات المحددة للتعامل مع الأخطاء بشكل سلس.

**س: ما هي الأخطاء الشائعة عند تصفية الموارد؟**  
ج: فحص URI غير الصحيح قد يتسبب في تخطي الملفات المطلوبة؛ استخدم السجلات أو نقاط التوقف للتحقق من الشروط.

**س: هل يمكن تحليل مستندات غير HTML باستخدام GroupDocs.Parser للـ Java؟**  
ج: بالتأكيد—يدعم GroupDocs.Parser ملفات PDF، Word، Excel، PowerPoint، والعديد من الصيغ الأخرى.

## الخطوات التالية
تعمق أكثر في المكتبة عبر استكشاف [مرجع الـ API](https://reference.groupdocs.com/parser/java) أو تجربة إعدادات إضافية مثل `ParserSettings.setDetectTables(true)` لاستخراج الجداول.

---

**آخر تحديث:** 2025-12-29  
**تم الاختبار مع:** GroupDocs.Parser 25.5 للـ Java  
**المؤلف:** GroupDocs  

**الموارد**  
- **التوثيق:** [توثيق GroupDocs.Parser](https://docs.groupdocs.com/parser/java/)  
- **مرجع الـ API:** [تفاصيل الـ API](https://reference.groupdocs.com/parser/java)  
- **التنزيلات:** [أحدث الإصدارات](https://releases.groupdocs.com/parser/java/)