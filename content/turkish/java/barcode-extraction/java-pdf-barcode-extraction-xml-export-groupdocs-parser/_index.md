---
date: '2026-02-19'
description: GroupDocs.Parser kullanarak Java PDF'lerinde QR kodlarını nasıl okuyacağınızı
  öğrenin ve barkod verilerini XML'e dışa aktarın.
keywords:
- Java PDF barcode extraction
- GroupDocs.Parser for Java
- XML export from PDF
title: GroupDocs.Parser ile Java PDF'lerinde QR Kodlarını Okuma
type: docs
url: /tr/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Java PDF'lerde QR Kodlarını Okuma - GroupDocs.Parser ile

## Hızlı Yanıtlar
- **GroupDocs.Parser for Java ne yapar?** PDF dosyalarını okur ve barkod gibi yapılandırılmış verileri çıkarır.  
- **QR kodları nasıl çıkarılır?** `BarcodeOptions`ı QR tipiyle yapılandırıp `parser.getBarcodes()` çağırarak.  
- **Java'da QR kodları okuyabilir miyim?** Evet—seçeneklerde barkod tipini `"QR"` olarak ayarlayın.  
- **Lisans gerekli mi?** Test için deneme sürümü çalışır; üretim için ticari lisans gerekir.  
- **Hangi Java sürümü gerekiyor?** Java 8 veya üzeri önerilir.

## “how to read QR” ifadesi PDF işleme bağlamında ne anlama geliyor?
PDF'lerden QR kodlarını okumak, her sayfayı QR‑kodlu grafikler için taramak, gömülü veriyi çözmek ve bunu program dostu bir formatta döndürmek anlamına gelir. GroupDocs.Parser düşük seviyeli görüntü analizini soyutlayarak piksel manipülasyonu yerine iş mantığına odaklanmanızı sağlar.

## QR Çıkarma için neden GroupDocs.Parser kullanılmalı?
- **Yüksek doğruluk:** Yerleşik görüntü işleme algoritmaları düşük çözünürlüklü taramaları işler.  
- **Performans seçenekleri:** Hız için `QualityMode.Low`, maksimum hassasiyet için `QualityMode.High` seçin.  
- **Çapraz format desteği:** PDF'ler, görüntüler ve hatta Office belgeleriyle çalışır, böylece farklı dosya tipleri için aynı kod tabanını yeniden kullanabilirsiniz.

## Önkoşullar
- **GroupDocs.Parser for Java** (sürüm 25.5 veya üzeri).  
- Maven veya manuel JAR indirme.  
- Java 8+ geliştirme ortamı (IntelliJ IDEA, Eclipse veya herhangi bir editör).  

## GroupDocs.Parser for Java Kurulumu
### Maven Kullanarak
Add the GroupDocs repository and dependency to your `pom.xml`:

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

### Doğrudan İndirme
Alternatif olarak, en son JAR dosyasını [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/) adresinden indirin.

#### Lisans Edinme Adımları
- **Ücretsiz Deneme:** Tam özellik setiyle 30‑günlük deneme.  
- **Geçici Lisans:** Uzatılmış değerlendirme için geçici anahtar isteyin.  
- **Satın Alma:** Üretim dağıtımları için ticari lisans edinin.

### Temel Başlatma ve Kurulum
Create a `Parser` instance that points to the PDF you want to analyze:

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

## Java PDF'lerde QR Kodlarını Okuma - GroupDocs.Parser Kullanarak
### Adım 1: Barkod Desteğini Doğrula
Before attempting extraction, confirm that the document format supports barcode scanning:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*Açıklama:* Bu kontrol, desteklenmeyen dosya tiplerinde çalışma zamanı hatalarını önler.

### Adım 2: Barkod Seçeneklerini Yapılandır (Java'da QR Kodlarını Okuma)
Set the scanning quality and specify that you’re interested in QR codes:

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*Açıklama:* `QualityMode.Low` işleme hızını artırır; ekstra doğruluk gerekiyorsa `High`'a geçin. `"QR"` argümanı, motorun yalnızca QR tipi barkodları aramasını sağlar.

### Adım 3: QR Verisini Çıkar
Pull the barcode information from every page of the PDF:

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*Açıklama:* `parser.getBarcodes` `PageBarcodeArea` nesnelerinin yinelemeli bir koleksiyonunu döndürür; her biri çözülen QR değerini ve sayfadaki konumunu içerir.

## Çıkarılan Veriyi XML'e Aktarma
### Adım 4: XML Dışa Aktarıcıyı Başlat
Create an exporter that will transform the barcode collection into a well‑structured XML file:

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*Açıklama:* `XmlExporter`, barkod nesnelerinin standart XML'e serileştirilmesini yönetir ve ERP ya da envanter sistemleriyle entegrasyon için hazır bir dosya oluşturur.

### Adım 5: XML Dosyasını Yaz
Save the extracted QR information to disk:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*Açıklama:* Oluşan `data.xml`, her QR kodu için bir `<Barcode>` öğesi içerir; öğe sayfa numarası, koordinatlar ve çözülen değer gibi özniteliklere sahiptir.

## Pratik Uygulamalar
1. **Envanter Yönetimi:** Gelen sevkiyat PDF'lerindeki QR etiketlerini okuyarak stok veritabanlarını otomatik doldurun.  
2. **Tedarik Zinciri Görünürlüğü:** Lojistik belgelerde gömülü QR tanımlayıcıları çıkararak paketleri gerçek zamanlı izleyin.  
3. **Perakende Makbuzları:** Dijital makbuzlarda basılmış QR kodlarından promosyon veya garanti bilgilerini alın.

## Performans Düşünceleri
- **Bellek Yönetimi:** Çok büyük PDF'lerde tüm dosyayı belleğe yüklemek yerine sayfaları akış şeklinde işleyin.  
- **QualityMode Seçimi:** Toplu işleme için `Low`, düşük çözünürlüklü taramalarla çalışırken `High`'a geçin.  
- **Kütüphane Güncellemeleri:** En son performans iyileştirmeleri ve hata düzeltmelerinden yararlanmak için GroupDocs.Parser'ı güncel tutun.

## Yaygın Sorunlar ve Çözümleme
| Semptom | Muhtemel Neden | Çözüm |
|---------|----------------|-------|
| Barkod bulunamadı | Yanlış barkod tipi belirtildi | Uygun tipe (ör. `"CODE_128"`) `"QR"` yerine değiştirin. |
| Büyük PDF'lerde bellek yetersizliği hatası | Tüm belge bir kerede yüklendi | Sayfaları tek tek işleyin veya JVM yığın boyutunu artırın (`-Xmx2g`). |
| Boş XML dosyası | `exportBarcodes` çıkarımdan önce çağrıldı | Dışa aktarmadan önce `parser.getBarcodes(options)` veri döndürdüğünden emin olun. |

## Sıkça Sorulan Sorular
**S: GroupDocs.Parser ile görüntü dosyalarından barkod çıkarabilir miyim?**  
C: Evet, kütüphane yaygın görüntü formatlarından (PNG, JPEG, TIFF) barkod çıkarımını destekler.

**S: Hangi barkod formatları tanınır?**  
C: QR, Code 39, Code 128, DataMatrix, PDF417 ve daha fazlası. Tam liste için API belgelerine bakın.

**S: Şifre korumalı PDF'leri nasıl ele almalı?**  
C: Şifreyi `Parser` yapıcısına geçirin: `new Parser(filePath, "password")`.

**S: Deneme sürümü üretim testi için yeterli mi?**  
C: Deneme sürümü tam işlevsellik sağlar ancak çıkarılan verilere bir filigran ekler. Üretim için ticari lisans edinin.

**S: PDF'im hem QR hem de doğrusal barkodlar içeriyorsa ne yapmalıyım?**  
C: Birden fazla `BarcodeOptions` örneği oluşturun veya tüm gerekli formatları tek seferde taramak için tip dizisi geçirin.

---

**Son Güncelleme:** 2026-02-19  
**Test Edilen Sürüm:** GroupDocs.Parser 25.5  
**Yazar:** GroupDocs  

## Kaynaklar
- [GroupDocs.Parser Java Dokümantasyonu](https://docs.groupdocs.com/parser/java/)
- [API Referansı](https://reference.groupdocs.com/parser/java)
- [GroupDocs.Parser İndir](https://releases.groupdocs.com/parser/java/)
- [GitHub Deposu](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Ücretsiz Destek Forumu](https://forum.groupdocs.com/c/parser)
- [Geçici Lisans Başvurusu](https://purchase.groupdocs.com/temporary-license/)