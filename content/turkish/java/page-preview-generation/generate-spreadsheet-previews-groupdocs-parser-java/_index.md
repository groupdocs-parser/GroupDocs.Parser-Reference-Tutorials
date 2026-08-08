---
date: '2026-07-16'
description: GroupDocs.Parser ile Java kullanarak elektronik tablo küçük resmi oluşturmayı,
  Office olmadan Excel'i preview etmeyi ve Excel sayfalarını images olarak render
  etmeyi öğrenin. Bu guide, setup, implementation ve practical use cases'ı kapsar.
keywords:
- create spreadsheet thumbnail java
- preview excel without office
- render excel sheets as images
lastmod: '2026-07-16'
og_description: GroupDocs.Parser ile Java kullanarak elektronik tablo küçük resmi
  oluşturun—Office olmadan Excel'i preview edin ve Excel sayfalarını images olarak
  render edin. Bu step‑by‑step guide'ı izleyerek PNG preview'larını verimli bir şekilde
  oluşturun.
og_image_alt: 'Developer guide: Create spreadsheet thumbnail Java using GroupDocs.Parser'
og_title: GroupDocs.Parser Kullanarak Java ile Elektronik Tablo Küçük Resmi Oluşturma
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
title: GroupDocs.Parser Kullanarak Java ile Elektronik Tablo Küçük Resmi Oluşturma
type: docs
url: /tr/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# GroupDocs.Parser Kullanarak Java'da Elektronik Tablo Küçük Resmi Oluştur

Eğer **Java'da elektronik tablo küçük resmi oluştur** programları arıyorsanız, doğru yerdesiniz. Bu rehberde, GroupDocs.Parser for Java kullanarak `.xlsx` çalışma kitaplarından yüksek kaliteli PNG önizlemeleri oluşturmayı adım adım göstereceğiz—hızlı küçük resimler, anlık görüntüler paylaşmak veya uygulamanızda bir belge önizleme özelliği oluşturmak için mükemmeldir. Çözüm Microsoft Office kurulumu olmadan çalışır ve büyük çalışma kitaplarıyla ölçeklenebilir, bellek kullanımını düşük tutar.

## Hızlı Yanıtlar
- **“preview Excel” ne anlama geliyor?** Her çalışma sayfasını temsil eden görüntü dosyaları (ör. PNG) oluşturmak.  
- **Hangi format önerilir?** PNG, kayıpsız kalite sağlar ve web küçük resimleri için iyi çalışır.  
- **Bir lisansa ihtiyacım var mı?** Geliştirme için ücretsiz deneme sürümü çalışır; üretim için ticari lisans gereklidir.  
- **Görüntü çözünürlüğünü değiştirebilir miyim?** Evet—`PreviewOptions` içinde DPI'yi ayarlayın.  
- **Diğer formatları önizlemek mümkün mü?** GroupDocs.Parser ayrıca PDF, Word ve birçok görüntü türünü destekler.

## GroupDocs.Parser ile “Excel önizleme” nasıl yapılır?
Excel çalışma kitabınızı yükleyin ve her sayfayı Microsoft Office gerektirmeden PNG görüntüsü olarak render edin. GroupDocs.Parser sayfaları tek tek akıtarak kayıpsız küçük resimler üretir; bu resimler diske kaydedilebilir veya HTTP üzerinden döndürülebilir, bu da web tabanlı önizleme hizmetleri için idealdir.

GroupDocs.Parser Excel çalışma kitaplarını okur, her sayfayı görsel bir sayfa olarak render eder ve bu sayfaları görüntü dosyalarına akıtmanıza olanak tanır. Bu, Office interop veya üçüncü taraf dönüştürücülere ihtiyaç duyulmasını ortadan kaldırır.

## Excel önizlemeleri için GroupDocs.Parser neden kullanılmalı?
GroupDocs.Parser'ı kullanmalısınız çünkü herhangi bir Java sunucusunda çalışır, Office kurulumu gerektirmez, büyük çalışma kitaplarını düşük bellekle işler ve yapılandırılabilir DPI ile kayıpsız PNG görüntüleri üretir. SDK **100'den fazla giriş ve çıkış formatını** destekler, 200 sayfalık bir çalışma kitabını 3 saniyeden kısa sürede işleyebilir ve sayfa başına bellek kullanımını 50 MB'nin altında tutar.

- **Office kurulumu gerekmez** – herhangi bir sunucu‑tarafı Java ortamında çalışır.  
- **Büyük dosyaları destekler** – sayfaları tek tek akıtarak bellek kullanımını düşük tutar.  
- **Yüksek kalite çıktı** – DPI, format ve render seçenekleri üzerinde kontrol.  
- **Çapraz format esnekliği** – aynı API PDF'ler, Word belgeleri ve daha fazlası için çalışır.

## Ön Koşullar
- **Java Development Kit** (8 +).  
- **IDE** (IntelliJ IDEA veya Eclipse gibi).  
- **GroupDocs.Parser for Java SDK** – [buradan](https://releases.groupdocs.com/parser/java/) indirin.  
- **Dokümantasyon** – resmi [dokümantasyon](https://docs.groupdocs.com/parser/java/) sayfasına bakın.  
- **Örnek Excel dosyası** (`.xlsx`) önizlemek istediğiniz.  
- **Maven veya Gradle** (isteğe bağlı) bağımlılık yönetimi için.

## Paketleri İçe Aktarma
Bu içe aktarmalar, parser, önizleme seçenekleri ve akış yönetimi yardımcı programlarına erişim sağlar.

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

## Sayfa Önizlemeleri Oluşturmak için Adım‑Adım Kılavuz

### Adım 1: Parser Örneğini Başlatma
`Parser`, GroupDocs.Parser'ın elektronik tablo dosyalarına okuma erişimi sağlayan ve sayfa‑sayfa render etmeyi mümkün kılan çekirdek sınıfıdır.  
Excel çalışma kitabınızı gösteren bir `Parser` nesnesi oluşturun. *try‑with‑resources* bloğu parser'ın otomatik olarak kapanmasını sağlar.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **İpucu:** `FileNotFoundException` hatasından kaçınmak için mutlak bir yol kullanın veya bir kaynak klasörü yapılandırın.

### Adım 2: Önizleme Seçeneklerinizi Hazırlayın
`PreviewOptions`, çıktı formatı ve DPI gibi render parametrelerini yapılandırır.  
`ICreatePageStream`, oluşturulan her sayfa için bir çıktı akışı sağlayan bir geri çağırma arayüzüdür. Her sayfanın nasıl kaydedileceğini tanımlayın. `ICreatePageStream` uygulaması, her çalışma sayfası için yeni bir `FileOutputStream` döndürür.

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

> Bu adım, **xlsx'i png'ye dönüştürdüğünüz** yerdir—akış PNG verisini diske yazar.

### Adım 3: Render Bilgilerini Yakalamak İçin Bir Delegasyon Ekleyin
Render edilen her sayfa hakkında (ör. boyutlar, sayfa adı) detaylara ihtiyacınız varsa, bir geri çağırma kaydedin.

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### Adım 4: Çıktı Formatını ve DPI'yi Belirleyin
Görüntü formatı olarak PNG'yi seçin ve kalite ile dosya boyutunu dengeleyen bir DPI ayarlayın.

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> Daha küçük küçük resimler (ör. 96) veya yüksek çözünürlüklü baskılar (ör. 300) için DPI'yi ayarlayın.

### Adım 5: Önizlemeleri Oluşturun
Her şey yapılandırıldıktan sonra `generatePreview` metodunu çağırın. SDK, her çalışma sayfası üzerinde dönecek ve sağladığınız akışı çağıracaktır.

```java
parser.generatePreview(previewOptions);
```

### Adım 6: `getOutputPath()` Yardımcısını Tanımlayın
`getOutputPath()`, sayfa (çalışma sayfası) numarasına dayalı bir dosya adı oluşturur ve çıktı görüntüsü için tam yolu döndürür. Klasör yapısını istediğiniz gibi özelleştirebilirsiniz.

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **Yaygın tuzak:** `output` dizinini önceden oluşturmayı unutmak bir `IOException` hatasına yol açar. Dizini programlı olarak oluşturun veya var olduğundan emin olun.

## Tam Çalışan Örnek (Basitleştirilmiş)

Aşağıda, tüm parçaları bir araya getiren kompakt bir sürüm bulunmaktadır. **Java'da elektronik tablo küçük resmi oluşturma** iş akışını baştan sona gösterir.

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

Bu kodu çalıştırdığınızda, `output` klasöründe `preview_page_1.png`, `preview_page_2.png`, … gibi bir dizi dosya bulacaksınız—her biri orijinal Excel çalışma kitabının bir sayfasını temsil eder.

## Yaygın Sorunlar ve Çözümler
| Sorun | Neden | Çözüm |
|-------|-------|-----|
| **Görüntü oluşturulmadı** | `getOutputPath` geçersiz bir dizin döndürüyor | Hedef klasörün var olduğundan emin olun veya `new File("output").mkdirs();` ile oluşturun |
| **Büyük dosyalarda bellek yetersizliği hatası** | Tüm çalışma kitabını bir kerede yüklemek | Akış yaklaşımını (gösterildiği gibi) kullanın ve sayfaları tek tek işleyin |
| **Yanlış DPI** | `setDpi` çağrılmadı veya varsayılan (96) olarak ayarlandı | `generatePreview`'den önce `previewOptions.setDpi(istenenDeğer);` çağırın |
| **Desteklenmeyen format** | Bozuk bir `.xlsx` dosyasını önizlemeye çalışmak | Dosyayı Excel ile doğrulayın veya işlemden önce `Parser.isSupported` kullanın |

## Sıkça Sorulan Sorular

**S: GroupDocs.Parser kullanarak PDF ve görüntü önizlemeleri oluşturabilir miyim?**  
A: Evet, aynı API PDF'ler, Word belgeleri ve birçok görüntü formatı için çalışır.

**S: Çıktı görüntü formatını nasıl değiştiririm?**  
A: `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (veya `Gif`, `Bmp`, vb.) metodunu çağırın.

**S: Çok büyük çalışma kitaplarında performans bir sorun mu?**  
A: SDK sayfaları akıtarak bellek kullanımını düşük tutar. Çok büyük dosyalar için paralel toplu işlemeyi düşünün.

**S: Önizleme oluşturma sırasında hataları nasıl yönetebilirim?**  
A: Kodları (gösterildiği gibi) try‑catch bloklarıyla sarın ve istisna detaylarını kaydedin. try‑with‑resources kullanmıyorsanız akışların `finally` bloğunda kapatıldığından emin olun.

**S: Kütüphane Microsoft Office kurulumunu gerektiriyor mu?**  
A: Hayır. GroupDocs.Parser saf bir Java çözümüdür ve Java 8+ destekleyen herhangi bir platformda çalışır.

**Son Güncelleme:** 2026-07-16  
**Test Edilen Versiyon:** GroupDocs.Parser 23.11 (yazım zamanı en son sürüm)  
**Yazar:** GroupDocs

## İlgili Öğreticiler

- [Önizleme Oluşturma – GroupDocs.Parser Java için Belge Sayfa Önizleme Oluşturma Öğreticileri](/parser/java/page-preview-generation/)
- [GroupDocs.Parser ile Java'da Excel Ayrıştırma: Tam Kılavuz](/parser/java/getting-started/mastering-document-parsing-java-groupdocs-parser/)
- [GroupDocs.Parser for Java kullanarak Excel Sayfalarından Ham Metin Çıkarma: Adım‑Adım Kılavuz](/parser/java/text-extraction/extract-raw-text-excel-groupdocs-parser-java/)