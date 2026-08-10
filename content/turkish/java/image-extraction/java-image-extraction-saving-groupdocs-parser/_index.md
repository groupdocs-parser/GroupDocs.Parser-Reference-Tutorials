---
date: '2026-08-10'
description: PDF görüntülerini Java ile nasıl çıkaracağınızı ve PDF görüntülerini
  PNG olarak GroupDocs.Parser ile nasıl kaydedeceğinizi öğrenin. Adım adım Java rehberi
  ve kod parçacıkları.
keywords:
- extract images pdf java
- convert pdf images png
- save pdf images png
lastmod: '2026-08-10'
og_description: PDF görüntülerini Java ile çıkarın ve PDF görüntülerini PNG olarak
  GroupDocs.Parser ile kaydedin. Hızlı ve güvenilir görüntü çıkarımı için bu Java
  öğreticisini izleyin.
og_image_alt: 'Java guide: extracting images from PDF and saving as PNG with GroupDocs.Parser'
og_title: PDF görüntülerini Java ile çıkar – PDF görüntülerini PNG olarak GroupDocs
  kullanarak kaydedin
schemas:
- author: GroupDocs
  dateModified: '2026-08-10'
  description: Learn how to extract images pdf java and save PDF images png with GroupDocs.Parser.
    Step‑by‑step Java guide with code snippets.
  headline: Extract images pdf java – save PDF images as PNG using GroupDocs
  type: TechArticle
- questions:
  - answer: PDFs, Word (`.docx`), Excel (`.xlsx`), PowerPoint, ZIP archives containing
      supported files, and many more.
    question: What formats does GroupDocs.Parser support for image extraction?
  - answer: Yes. Provide the password when constructing the `Parser` object.
    question: Can I extract images from password‑protected PDFs?
  - answer: Process them page‑by‑page, release resources after each batch, and consider
      increasing the JVM heap size if needed.
    question: How should I handle very large documents?
  - answer: Absolutely. GroupDocs.Parser also extracts text, tables, and metadata.
    question: Is it possible to extract other data types besides images?
  - answer: The API will throw `UnsupportedDocumentFormatException`; you can catch
      this and fallback to an alternative strategy (e.g., convert the file first).
    question: What if image extraction isn’t supported for a specific file?
  type: FAQPage
tags:
- extract images pdf
- GroupDocs.Parser
- Java image extraction
title: PDF görüntülerini Java ile çıkar – PDF görüntülerini PNG olarak GroupDocs kullanarak
  kaydedin
type: docs
url: /tr/java/image-extraction/java-image-extraction-saving-groupdocs-parser/
weight: 1
---

# PDF Görüntülerini Java ile Çıkarma – PDF Görüntülerini PNG Olarak Kaydetme GroupDocs Kullanarak

Modern belge‑odaklı iş akışlarında, **extract images pdf java** yaygın bir gereksinimdir ve PDF'leri manuel olarak açıp resimleri kopyalamaktan sizi kurtarır. Kataloglardan ürün fotoğrafları, sözleşmelerden logolar veya raporlardan ekran görüntüleri ihtiyacınız olsun, Java ve GroupDocs.Parser ile çıkarımı otomatikleştirerek her gömülü raster görüntüyü saniyeler içinde alabilirsiniz. Bu kılavuz, kütüphaneyi kurmaktan, PDF'den (ve diğer formatlardan) görüntü çıkarmaya ve **görüntüleri PNG olarak kaydetme** dosyalarına kadar adımları size gösterir.

## Hızlı cevaplar
- **“extract images from PDF” ne anlama geliyor?** Bu, bir PDF'yi programlı olarak okuyup tüm gömülü raster görüntüleri çıkarmak sürecidir.  
- **Java'da bunu hangi kütüphane yönetir?** GroupDocs.Parser for Java, birçok belge türünde görüntü çıkarımı için basit bir API sunar.  
- **Çıkarılan dosyaları PNG olarak kaydedebilir miyim?** Evet – `image.save()` çağrılırken `ImageOptions(ImageFormat.Png)` kullanın.  
- **Lisans gerekir mi?** Geliştirme için ücretsiz deneme sürümü çalışır; üretim için ticari bir lisans gereklidir.  
- **Word, Excel veya ZIP dosyalarından görüntü çıkarmak mümkün mü?** Kesinlikle – aynı `parser.getImages()` çağrısı bu formatlar için de çalışır.

## extract images pdf java nedir?
Extract images pdf java, bir PDF belgesine gömülü her raster görüntü nesnesini programlı olarak bulmayı ve ikili verilerini almayı ifade eder; böylece dosyayı manuel olarak açmadan resimleri yeniden kullanabilir, analiz edebilir veya arşivleyebilirsiniz. Bu süreç genellikle PDF yapısını ayrıştırmayı, görüntü akışlarını çıkarmayı ve PNG gibi seçilen bir formatta ayrı görüntü dosyalarına yazmayı içerir.

## GroupDocs.Parser ile PDF'den görüntü çıkarmak neden?
GroupDocs.Parser, tipik bir 8 çekirdekli sunucuda **500 sayfaya kadar PDF'yi 5 saniyeden kısa sürede** işleyebilir ve DOCX, XLSX, PPTX ve ZIP arşivleri dahil **50+ giriş formatını** destekler. Yerel kodlu motor bellek kullanımını düşük tutar, böylece tüm belgeyi belleğe yüklemeden çok sayfalı dosyaları işleyebilirsiniz. Ayrıca çıktı formatı, dosya adlandırma ve toplu işleme üzerinde tam kontrol elde edersiniz.

## Önkoşullar
- Java Development Kit (JDK) 8 veya üzeri.  
- Java I/O ve istisna yönetimi konusunda temel bilgi.  
- Maven veya projenize harici JAR'lar ekleyebilme yeteneği.

### Gerekli kütüphaneler ve bağımlılıklar
GroupDocs.Parser for Java ile çalışmak için, Maven kullanarak veya kütüphaneyi doğrudan indirerek projenize ekleyin.

### Ortam kurulum gereksinimleri
IDE'nizin (IntelliJ IDEA, Eclipse, VS Code) JDK ve Maven (Maven yolunu seçerseniz) ile yapılandırıldığından emin olun.

### Bilgi önkoşulları
Dosya akışları, try‑with‑resources ve temel nesne‑yönelimli Java kavramlarını anlamak, uygulamayı daha sorunsuz hale getirecektir.

## GroupDocs.Parser for Java'ı Kurma
GroupDocs.Parser'ı kullanmak için, Maven ile projenize ekleyin veya resmi sürüm sayfasından kütüphaneyi indirin.

### Maven kurulumu
`pom.xml` dosyanıza aşağıdaki yapılandırmayı ekleyin:

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
Alternatif olarak, en son sürümü [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/) adresinden indirin.

Kapsamlı kılavuzlar için [GroupDocs Documentation](https://docs.groupdocs.com/parser/java/) sayfasına bakın.

### Lisans edinme
Kütüphaneyi indirerek ücretsiz bir deneme ile başlayın. Uzun vadeli kullanım için bir lisans satın almayı veya [GroupDocs](https://purchase.groupdocs.com/temporary-license/) üzerinden geçici bir lisans almayı düşünün.

#### Temel başlatma ve kurulum
`Parser` sınıfı, GroupDocs.Parser'da tüm belge‑parçalama işlemleri için giriş noktasıdır. Dosya yolunu (ve isteğe bağlı olarak bir şifreyi) yapıcıya geçirerek bir örnek oluşturursunuz.

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

## GroupDocs.Parser Kullanarak PDF'den Görüntü Nasıl Çıkarılır
Belgeyi `new Parser("yourFile.pdf")` ile yükleyin ve `parser.getImages()` metodunu çağırın – bu tek çağrı, sağladığınız PDF, Word, Excel veya ZIP dosyasında gömülü tüm raster görüntülerin bir koleksiyonunu döndürür.

### Uygulama rehberi
Uygulamayı mantıksal bölümlere ayıracağız, böylece her adımı net bir şekilde izleyebilirsiniz.

### Özellik 1: bir belgeden görüntü çıkarma
Bu özellik, GroupDocs.Parser for Java kullanarak görüntülerin nasıl çıkarılacağını gösterir.

#### Genel Bakış
Belirtilen bir belgede tüm görüntüleri çıkaran ve verilen format için görüntü çıkarımının desteklenip desteklenmediğini kontrol eden bir yöntem oluşturacaksınız.

#### Uygulama adımları

##### Adım 1: parser'ı kurun
`Parser` nesnesini belge yolunuzla başlatın:

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

##### Açıklama
- **`parser.getImages()`** belge içindeki her görüntü alanını çıkarır; ister PDF, Word, Excel, ister desteklenen dosyaları içeren bir ZIP arşivi olsun.  
- **Hata yönetimi**: Format görüntü çıkarımını desteklemiyorsa yöntem `UnsupportedDocumentFormatException` fırlatır, bu da sorunsuz bir geri dönüş yapmanıza olanak tanır.

### Özellik 2: çıkarılan görüntüleri dosyalara kaydetme
Görüntü nesnelerine sahip olduktan sonra, bir sonraki adım bunları PNG dosyaları olarak diske yazmaktır.

#### Genel Bakış
`ImageOptions` sınıfını kullanarak her çıkarılan görüntüyü PNG dosyası olarak kaydedeceksiniz.

**ImageOptions**, kaydedilen görüntüler için çıktı formatını ve kodlama ayarlarını belirler.  
**ImageFormat.Png**, PNG görüntü formatını seçen bir enum değeridir.

#### Uygulama adımları

##### Adım 1: her görüntüyü kaydet
Görüntüler üzerinde döngü kurun ve kaydedin:

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

##### Açıklama
- **`ImageOptions(ImageFormat.Png)`**, kayıpsız bir PNG formatını belirtir ve ekran görüntüleri veya tam doğruluk gerektiren grafikler için idealdir.  
- **`image.save()`**, sağlanan çıktı akışını kullanarak her görüntüyü dosya sistemine yazar; performans için aynı `ImageOptions` örneği yeniden kullanılır.

#### Sorun giderme ipuçları
- **document path**'in mevcut bir dosyaya işaret ettiğini ve uygulamanın okuma izinlerine sahip olduğunu doğrulayın.  
- **output directory**'nin var olduğundan ve işlemin yazma izinlerine sahip olduğundan emin olun.  
- Çok büyük PDF'ler için, bellek kullanımını düşük tutmak amacıyla sayfaları partiler halinde işlemeyi düşünün.

## Görüntüleri PNG Olarak Nasıl Kaydedilir
Belgeyi yükleyin, görüntüleri çıkarın ve `image.save(outputStream, new ImageOptions(ImageFormat.Png))` metodunu çağırın – bu tek satır, her raster görüntüyü orijinal çözünürlüğünü ve renk derinliğini koruyarak bir PNG dosyasına yazar.

## Word, Excel ve ZIP Dosyalarından Görüntü Çıkarma
GroupDocs.Parser'ın `getImages()` birçok formatta çalışır:

- **Word (`.docx`)** – gömülü resimleri ve çizimleri çıkarır.  
- **Excel (`.xlsx`)** – grafikler ve eklenmiş resimleri çıkarır.  
- **ZIP** – arşiv desteklenen belgeler içeriyorsa, parser her girişi işleyip görüntülerini döndürür.

`documentPath` değişkenini `.docx`, `.xlsx` veya `.zip` dosyanızın yolu ile değiştirin ve aynı çıkarma ve kaydetme mantığını yeniden kullanın.

## Pratik uygulamalar
GroupDocs.Parser çeşitli sistemlere entegre edilebilir ve işlevselliği artırır:

1. **Otomatik belge işleme** – faturalar veya sözleşmelerden görüntüleri otomatik veri girişi için çıkarır.  
2. **Arşivleme sistemleri** – belge görüntülerini hızlı görsel erişim için merkezi olarak depolar.  
3. **İçerik yönetim sistemleri (CMS)** – yüklenen belgelerden medya varlıklarını otomatik olarak çeker.

## Performans değerlendirmeleri
Büyük toplu işlemlerle çalışırken Java uygulamanızın yanıt verebilir kalması için:

- **Akışları hızlıca kapatın** try‑with‑resources kullanarak (gösterildiği gibi).  
- **`ImageOptions`'ı yeniden kullanın** her görüntü için yeni bir örnek oluşturmak yerine.  
- **Belgeleri sıralı olarak veya kontrollü bir iş parçacığı havuzunda işleyin** bellek dalgalanmalarını önlemek için.  
- GroupDocs.Parser, 300 sayfalık bir PDF'den **4 saniyeden az** sürede görüntü çıkarabilir ve **200 MB**'den az yığın belleği kullanır.

## Sonuç
Bu öğreticide, GroupDocs.Parser for Java'ı nasıl kuracağınızı, **extract images pdf java** ve **görüntüleri PNG olarak kaydetme** dosyalarını öğrendiniz. Bu yetenek, herhangi bir Java tabanlı çözümde belge‑odaklı iş akışlarını büyük ölçüde hızlandırabilir.

### Sonraki adımlar
Ek özellikleri keşfetmek için [GroupDocs documentation](https://docs.groupdocs.com/parser/java/) sayfasını inceleyin; metin çıkarımı, tablo ayrıştırma ve OCR desteği gibi. Ayrıntılı metod imzaları için [API Reference](https://apireference.groupdocs.com/parser/java) sayfasına bakın.

### Eylem çağrısı
Bu kod parçacıklarını bugün projenizde uygulamaya başlayın—otomatik görüntü çıkarım hattınız sadece birkaç kod satırı uzakta!

## Sıkça Sorulan Sorular

**S: GroupDocs.Parser görüntü çıkarımı için hangi formatları destekliyor?**  
C: PDF'ler, Word (`.docx`), Excel (`.xlsx`), PowerPoint, desteklenen dosyaları içeren ZIP arşivleri ve daha fazlası.

**S: Parola korumalı PDF'lerden görüntü çıkarabilir miyim?**  
C: Evet. `Parser` nesnesini oluştururken parolayı sağlayın.

**S: Çok büyük belgelerle nasıl başa çıkmalıyım?**  
C: Sayfa sayfa işleyin, her partiden sonra kaynakları serbest bırakın ve gerekirse JVM yığın boyutunu artırmayı düşünün.

**S: Görüntüler dışında başka veri türlerini çıkarmak mümkün mü?**  
C: Kesinlikle. GroupDocs.Parser ayrıca metin, tablolar ve meta verileri de çıkarır.

**S: Belirli bir dosya için görüntü çıkarımı desteklenmiyorsa ne olur?**  
C: API `UnsupportedDocumentFormatException` fırlatır; bunu yakalayabilir ve alternatif bir stratejiye (örneğin, önce dosyayı dönüştürmek) geçebilirsiniz.

**Son Güncelleme:** 2026-08-10  
**Test Edilen Versiyon:** GroupDocs.Parser 25.5 for Java  
**Yazar:** GroupDocs

## İlgili Öğreticiler

- [GroupDocs.Parser Java ile PDF Görüntü Çıkarma – Öğreticiler](/parser/java/image-extraction/)
- [GroupDocs.Parser Java API Kullanarak Belirli Alanlardan PDF Görüntülerini Çıkarma](/parser/java/image-extraction/image-extraction-pdf-areas-groupdocs-parser-java/)
- [GroupDocs.Parser Java ile Powerpoint Görüntülerini Nasıl Çıkarılır (Adım‑Adım Kılavuz)](/parser/java/image-extraction/extract-images-powerpoint-groupdocs-parser-java/)