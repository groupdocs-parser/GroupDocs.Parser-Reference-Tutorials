---
date: '2026-10-12'
description: Java kullanarak PDF'den QR kodunu nasıl çıkaracağınızı ve GroupDocs.Parser
  ile barkod verilerini sonraki işlemler için XML'e nasıl dışa aktaracağınızı öğrenin.
keywords:
- extract QR from PDF
- how to read QR
- read QR codes Java
- parse QR codes Java
- PDF QR code extraction
lastmod: '2026-10-12'
og_description: Java kullanarak PDF'den QR kodunu nasıl çıkaracağınızı ve GroupDocs.Parser
  ile barkod verilerini sonraki işlemler için XML'e nasıl dışa aktaracağınızı öğrenin.
og_image_alt: Guide showing Java code that extracts QR codes from PDF files with GroupDocs.Parser
  and saves results as XML
og_title: Java'da PDF'den QR kodu nasıl çıkarılır? GroupDocs.Parser
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
title: Java'da PDF'den QR kodu nasıl çıkarılır? GroupDocs.Parser
type: docs
url: /tr/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Java'da GroupDocs.Parser ile PDF'den QR Nasıl Çıkarılır

Modern iş akışlarında, **PDF'den QR çıkarma** dosyaları manuel veri girişi darboğazını tam otomatik bir boru hattına dönüştürebilir. Gönderi manifestoları, perakende makbuzları veya ürün kataloglarıyla çalışıyor olun, QR bilgilerini hızlı ve güvenilir bir şekilde çekmek, sonraki sistemler için hayati öneme sahiptir. Bu öğretici, **GroupDocs.Parser for Java** kullanarak PDF'lerden QR kodlarını (ve diğer barkodları) okumanızı ve sonuçları ERP, envanter veya analiz platformunuzun tüketebileceği temiz bir XML dosyasına dışa aktarmanızı adım adım gösterir.

## Hızlı cevaplar
- **GroupDocs.Parser for Java ne yapar?** PDF dosyalarını okur ve barkodlar, tablolar ve metin gibi yapılandırılmış verileri çıkarır.  
- **QR kodları nasıl çıkarılır?** `BarcodeOptions`'ı QR türüyle yapılandırın ve `parser.getBarcodes()`'ı çağırın.  
- **Java'da QR kodlarını okuyabilir miyim?** Evet—seçeneklerde barkod türünü `"QR"` olarak ayarlayın.  
- **Lisans gerekir mi?** Test için bir deneme sürümü çalışır; üretim için ticari bir lisans gereklidir.  
- **Hangi Java sürümü gereklidir?** Java 8 veya üzeri önerilir.

## PDF işleme bağlamında “PDF'den QR çıkarma” nedir?
PDF'den QR çıkarma, her sayfayı QR kodlu grafikler için taramak, gömülü veriyi çözmek ve bunu program dostu bir formatta döndürmek anlamına gelir. GroupDocs.Parser, düşük seviyeli görüntü analizini soyutlayarak piksel manipülasyonu yerine iş mantığına odaklanmanızı sağlar.

## QR çıkarımı için neden GroupDocs.Parser kullanılmalı?
GroupDocs.Parser **30'dan fazla giriş formatını** destekler ve **500 MB**'a kadar PDF'leri tüm dosyayı belleğe yüklemeden işleyebilir, düşük çözünürlüklü taramalarda bile yüksek doğruluk sonuçları sunar. Hız için `QualityMode.Low`, maksimum hassasiyet için `QualityMode.High` seçebilirsiniz ve aynı API PDF'ler, görüntüler ve Office belgeleri için çalışır, birden fazla kütüphane ihtiyacını ortadan kaldırır.

## Önkoşullar
- **GroupDocs.Parser for Java** (sürüm 25.5 veya sonrası).  
- Maven veya manuel JAR indirme.  
- Java 8+ geliştirme ortamı (IntelliJ IDEA, Eclipse veya herhangi bir editör).  

## GroupDocs.Parser for Java Kurulumu
### Maven Kullanarak
`pom.xml` dosyanıza GroupDocs deposunu ve bağımlılığı ekleyin:

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

### Doğrudan indirme
Alternatif olarak, en son JAR'ı [GroupDocs.Parser for Java sürümleri](https://releases.groupdocs.com/parser/java/) adresinden indirin.

#### Lisans edinme adımları
- **Ücretsiz deneme:** Tam özellik setiyle 30‑günlük deneme.  
- **Geçici lisans:** Uzatılmış değerlendirme için geçici bir anahtar isteyin.  
- **Satın al:** Üretim dağıtımları için ticari bir lisans edinin.

### Temel başlatma ve kurulum
Analiz etmek istediğiniz PDF'ye işaret eden bir `Parser` örneği oluşturun:

`Parser`, GroupDocs.Parser içinde bir belgeyi temsil eden ve metin, tablo ve barkod gibi içerikleri çıkarmak için yöntemler sağlayan temel sınıftır.  

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

## GroupDocs.Parser ile Java PDF'lerinde QR kodlarını nasıl okuyabilirsiniz
GroupDocs.Parser ile Java PDF'lerinde QR kodlarını okumak, bir parser örneği oluşturmayı, QR türlerini hedeflemek için barkod seçeneklerini yapılandırmayı, barkod çıkarma yöntemini çağırmayı ve ardından dönen barkod nesnelerini işlemeyi içerir. İşlem basittir, herhangi bir PDF sayfasında çalışır ve çözülen değerleri, sonraki işleme yönelik konumsal meta verilerle birlikte döndürür.

### Adım 1: barkod desteğini doğrula
Çıkarma işlemine başlamadan önce, belge formatının barkod taramayı desteklediğini doğrulayın:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*Açıklama:* Bu koruma, desteklenmeyen dosya türlerinde çalışma zamanı hatalarını önler.

### Adım 2: barkod seçeneklerini yapılandır (Java'da QR kodlarını oku)
`BarcodeOptions`, hangi barkod sembollerinin algılanacağını belirlemenizi, tarama kalite modunu ayarlamanızı ve tespit eşik değerleri gibi parametreleri ince ayar yapmanızı sağlayan bir yapılandırma nesnesidir; bu, hedef QR kodları için optimum performans sağlar.

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*Açıklama:* `QualityMode.Low` işleme hızını artırır; ekstra doğruluk gerekiyorsa `High`'a geçin. `"QR"` argümanı, motorun yalnızca QR‑tipi barkodları aramasını söyler.

### Adım 3: QR verisini çıkar
`parser.getBarcodes(options)`, verilen `BarcodeOptions` ile belgeyi tarar ve her biri çözülen QR değerini, sayfa numarasını ve barkodun sayfa içindeki tam koordinatlarını kapsayan `PageBarcodeArea` nesnelerinin bir koleksiyonunu döndürür; bu, kesin sonraki işlemeyi mümkün kılar.

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*Açıklama:* `parser.getBarcodes`, her biri çözülen QR değerini ve sayfadaki konumunu içeren `PageBarcodeArea` nesnelerinin yinelemeli bir koleksiyonunu döndürür.

## Çıkarılan veriyi XML'e Dışa Aktarma
### Adım 4: XML dışa aktarıcısını başlat
`XmlExporter`, barkod nesnelerinin bir koleksiyonunu iyi yapılandırılmış bir XML belgesine dönüştüren bir yardımcı sınıftır; her barkod için sayfa indeksi, konum ve çözülen değer gibi özniteliklerle öğeler otomatik olarak oluşturur ve ardından diğer sistemlere kaydedilebilir veya akışa gönderilebilir.

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*Açıklama:* `XmlExporter`, barkod nesnelerinin standart XML'e serileştirilmesini yönetir ve ERP veya envanter sistemleriyle entegrasyona hazır hale getirir.

### Adım 5: XML dosyasını yaz
Çıkarılan QR bilgilerini diske kaydedin:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*Açıklama:* Oluşan `data.xml`, her QR kodu için bir `<Barcode>` öğesi içerir; öğeler sayfa numarası, koordinatlar ve çözülen değer özniteliklerine sahiptir.

## Pratik uygulamalar
1. **Envanter yönetimi:** Gelen gönderi PDF'lerindeki QR etiketlerini okuyarak stok veritabanlarını otomatik doldurun.  
2. **Tedarik zinciri görünürlüğü:** Lojistik belgelerde gömülü QR tanımlayıcıları çıkararak paketleri gerçek zamanlı izleyin.  
3. **Perakende makbuzları:** Dijital makbuzlarda basılmış QR kodlarından promosyon veya garanti bilgilerini çekin.

## Performans değerlendirmeleri
- **Bellek yönetimi:** Çok büyük PDF'lerde, tüm dosyayı belleğe yüklemek yerine sayfaları akış biçiminde işleyin.  
- **QualityMode seçimi:** Toplu işleme için `Low`, düşük çözünürlüklü taramalarla çalışırken `High`'a geçin.  
- **Kütüphane güncellemeleri:** En son performans iyileştirmelerinden ve hata düzeltmelerinden yararlanmak için GroupDocs.Parser'ı güncel tutun.

## Yaygın sorunlar ve sorun giderme
| Sorun | Muhtemel neden | Çözüm |
|---------|--------------|-----|
| Barkod bulunamadı | Yanlış barkod türü belirtildi | `"QR"`'yi uygun türle (ör. `"CODE_128"`) değiştirin. |
| Büyük PDF'lerde bellek yetersizliği hatası | Tüm belge bir kerede yüklendi | Sayfaları tek tek işleyin veya JVM yığın boyutunu artırın (`-Xmx2g`). |
| Boş XML dosyası | `exportBarcodes` çıkarma işleminden önce çağrıldı | Dışa aktarmadan önce `parser.getBarcodes(options)`'ın veri döndürdüğünden emin olun. |

## Sıkça Sorulan Sorular
**Q:** GroupDocs.Parser ile görüntü dosyalarından barkod çıkarabilir miyim?  
**A:** Evet, kütüphane yaygın görüntü formatlarından (PNG, JPEG, TIFF) barkod çıkarımını destekler.

**Q:** Hangi barkod formatları tanınır?  
**A:** QR, Code 39, Code 128, DataMatrix, PDF417 ve daha birçokları. Tam liste için API belgelerine bakın.

**Q:** Şifre korumalı PDF'leri nasıl ele almalı?  
**A:** Şifreyi `Parser` yapıcısına geçirin: `new Parser(filePath, "password")`.

**Q:** Deneme sürümü üretim testi için yeterli mi?  
**A:** Deneme sürümü tam işlevsellik sağlar ancak çıkarılan verilere bir filigran ekler. Üretim için ticari bir lisans edinin.

**Q:** PDF'im hem QR hem de doğrusal barkodlar içeriyorsa ne yapmalıyım?  
**A:** Birden fazla `BarcodeOptions` örneği oluşturun veya tüm gerekli formatları tek geçişte taramak için bir dizi tür geçirin.

---

**Son Güncelleme:** 2026-10-12  
**Test Edilen Versiyon:** GroupDocs.Parser 25.5  
**Yazar:** GroupDocs  

## Kaynaklar
- [GroupDocs.Parser Java belgeleri](https://docs.groupdocs.com/parser/java/)
- [API referansı](https://reference.groupdocs.com/parser/java)
- [GroupDocs.Parser'ı İndir](https://releases.groupdocs.com/parser/java/)
- [GitHub deposu](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Ücretsiz destek forumu](https://forum.groupdocs.com/c/parser)
- [Geçici lisans başvurusu](https://purchase.groupdocs.com/temporary-license/)

## İlgili Eğitimler

- [PDF'den Barkod Çıkarma GroupDocs Parser Java](/parser/java/barcode-extraction/extract-barcode-pdf-groupdocs-parser-java/)
- [GroupDocs.Parser for Java ile URL'den PDF Yükleme](/parser/java/document-loading/)
- [Java'da GroupDocs.Parser ile PDF Form Verilerini Çıkarma](/parser/java/form-extraction/groupdocs-parser-java-pdf-form-extraction/)