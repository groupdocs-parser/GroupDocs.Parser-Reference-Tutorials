---
date: '2026-02-06'
description: GroupDocs.Parser for Java kullanarak Excel dosyalarını önizlemeyi ve
  xlsx dosyalarını png'ye dönüştürmeyi öğrenin. Bu öğreticide kurulum, uygulama ve
  pratik uygulamalar ele alınmaktadır.
keywords:
- GroupDocs.Parser
- Java
- Document Processing
title: Java'da GroupDocs.Parser ile Excel Dosyalarını Önizleme
type: docs
url: /tr/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# Java'da GroupDocs.Parser ile Excel Dosyalarını Önizleme

Programlı olarak **Excel önizleme** nasıl yapılır** arıyorsanız, doğru yere geldiniz. Bu rehberde GroupDocs.Parser for Java kullanarak `.xlsx` çalışma kitaplarından görüntü önizlemeleri (PNG) oluşturmayı adım adım göstereceğiz—hızlı küçük resimler oluşturmak, anlık görüntüler paylaşmak veya uygulamanızda bir belge‑önizleme özelliği oluşturmak için mükemmeldir.

## Hızlı Yanıtlar
- **“Excel önizleme” ne anlama geliyor?** Her çalışma sayfasını temsil eden görüntü dosyaları (örn. PNG) oluşturmak.  
- **Hangi format önerilir?** PNG kayıpsız kalite sunar ve web küçük resimleri için iyidir.  
- **Lisans gerekli mi?** Geliştirme için ücretsiz deneme sürümü yeterlidir; üretim için ticari lisans gerekir.  
- **Görüntü çözünürlüğünü değiştirebilir miyim?** Evet—`PreviewOptions` içinde DPI'yi ayarlayın.  
- **Diğer formatları önizlemek mümkün mü?** GroupDocs.Parser ayrıca PDF, Word ve birçok görüntü tipini destekler.

## GroupDocs.Parser ile “Excel önizleme” nedir?
GroupDocs.Parser Excel çalışma kitaplarını okur, her sayfayı görsel bir sayfa olarak oluşturur ve bu sayfaları görüntü dosyalarına akıtmanıza olanak tanır. Bu sayede Office interop veya üçüncü‑taraf dönüştürücülere ihtiyaç kalmaz.

## Excel önizlemeleri için neden GroupDocs.Parser kullanmalı?
- **Office kurulumu gerekmez** – herhangi bir sunucu‑tarafı Java ortamında çalışır.  
- **Büyük dosyaları destekler** – sayfaları tek tek akıtarak bellek kullanımını düşük tutar.  
- **Yüksek‑kaliteli çıktı** – DPI, format ve render seçenekleri üzerinde kontrol.  
- **Çapraz‑format esnekliği** – aynı API PDF, Word belgeleri ve daha fazlası için çalışır.

## Önkoşullar
- **Java Development Kit** (8 +).  
- **IDE** (IntelliJ IDEA veya Eclipse gibi).  
- **GroupDocs.Parser for Java SDK** – [buradan](https://releases.groupdocs.com/parser/java/) indirin.  
- **Önizlemek istediğiniz örnek Excel dosyası** (`.xlsx`).  
- **Maven veya Gradle** (isteğe bağlı) bağımlılık yönetimi için.

## Paketleri İçe Aktarma
Bu içe aktarmalar, parser, önizleme seçenekleri ve akış yönetimi yardımcı sınıflarına erişim sağlar.

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

## Elektronik Tablo Sayfa Önizlemeleri Oluşturmak için Adım‑Adım Kılavuz

### Adım 1: Parser Örneğini Başlatma
`Parser` nesnesini Excel çalışma kitabınıza işaret edecek şekilde oluşturun. *try‑with‑resources* bloğu parser'ın otomatik olarak kapatılmasını sağlar.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **Pro ipucu:** `FileNotFoundException` hatasından kaçınmak için mutlak bir yol kullanın veya bir kaynak klasörü yapılandırın.

### Adım 2: Önizleme Seçeneklerinizi Hazırlama
Her sayfanın nasıl kaydedileceğini tanımlayın. `ICreatePageStream` uygulaması, her çalışma sayfası için yeni bir `FileOutputStream` döndürür.

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

### Adım 3: Render Bilgilerini Yakalamak için Bir Delegasyon Ekleyin
Her render edilen sayfa hakkında (ör. boyutlar, sayfa adı) detaylara ihtiyacınız varsa, bir geri çağırma (callback) kaydedin.

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### Adım 4: Çıktı Formatını ve DPI'yi Belirleme
Görüntü formatı olarak PNG'yi seçin ve kalite ile dosya boyutunu dengeleyen bir DPI ayarlayın.

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> Daha küçük küçük resimler (ör. 96) veya yüksek çözünürlüklü baskılar (ör. 300) için DPI'yi ayarlayın.

### Adım 5: Önizlemeleri Oluşturma
Her şey yapılandırıldıktan sonra `generatePreview` metodunu çağırın. SDK, her çalışma sayfasını dolaşacak ve sağladığınız akışı (stream) çağıracaktır.

```java
parser.generatePreview(previewOptions);
```

### Adım 6: `getOutputPath()` Yardımcısını Tanımlama
Bu yöntem, sayfa (sayfa) numarasına göre bir dosya adı oluşturur. Klasör yapısını istediğiniz gibi özelleştirebilirsiniz.

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **Yaygın tuzak:** `output` dizinini önceden oluşturmamayı unutmak bir `IOException` hatasına yol açar. Dizini programlı olarak oluşturun veya var olduğundan emin olun.

## Tam Çalışan Örnek (Basitleştirilmiş)

Aşağıda tüm parçaları bir araya getiren kompakt bir sürüm bulunmaktadır. **Excel sayfa önizleme oluşturma** iş akışını baştan sona gösterir.

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

Bu kodu çalıştırdığınızda, `output` klasöründe `preview_page_1.png`, `preview_page_2.png`, … dosyalar serisini bulacaksınız—her biri orijinal Excel çalışma kitabındaki bir sayfayı temsil eder.

## Yaygın Sorunlar ve Çözümler
| Sorun | Sebep | Çözüm |
|-------|-------|-----|
| **Görüntü oluşturulmadı** | `getOutputPath` geçersiz bir dizin döndürüyor | Hedef klasörün var olduğundan emin olun veya `new File("output").mkdirs();` ile oluşturun |
| **Büyük dosyalarda bellek dışı hata** | Tüm çalışma kitabını bir seferde yüklemek | Gösterildiği gibi akış (streaming) yaklaşımını kullanın ve sayfaları tek tek işleyin |
| **Yanlış DPI** | `setDpi` çağrılmadı veya varsayılan (96) olarak ayarlandı | `generatePreview`'den önce `previewOptions.setDpi(istediğinizDeğer);` çağırın |
| **Desteklenmeyen format** | Bozuk bir `.xlsx` dosyasını önizlemeye çalışmak | Dosyayı Excel ile doğrulayın veya işlemden önce `Parser.isSupported` kullanın |

## Sıkça Sorulan Sorular

**S: GroupDocs.Parser kullanarak PDF ve görüntü önizlemeleri oluşturabilir miyim?**  
C: Evet, aynı API PDF, Word belgeleri ve birçok görüntü formatı için çalışır.

**S: Çıktı görüntü formatını nasıl değiştiririm?**  
C: `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (veya `Gif`, `Bmp`, vb.) metodunu çağırın.

**S: Çok büyük çalışma kitaplarında performans bir sorun mu?**  
C: SDK sayfaları akıtarak bellek kullanımını düşük tutar. Çok büyük dosyalar için paralel toplu işleme düşünün.

**S: Önizleme oluşturma sırasında hataları nasıl yönetebilirim?**  
C: Kodu (gösterildiği gibi) try‑catch bloklarıyla sarın ve istisna detaylarını kaydedin. try‑with‑resources kullanmıyorsanız akışların `finally` bloğunda kapatıldığından emin olun.

**S: Kütüphane Microsoft Office'in kurulu olmasını gerektiriyor mu?**  
C: Hayır. GroupDocs.Parser saf bir Java çözümüdür ve Java 8+ destekleyen herhangi bir platformda çalışır.

## Sonuç
Artık GroupDocs.Parser kullanarak **Excel önizleme** çalışma kitapları ve **xlsx'i png'ye dönüştürme** için tam, üretim‑hazır bir yönteme sahipsiniz. DPI, çıktı klasörü veya görüntü formatını projenizin ihtiyaçlarına göre ayarlayın ve bu kodu daha büyük belge‑yönetim iş akışlarına entegre edin.

Bir sonraki adıma hazır mısınız? Gelişmiş render seçenekleri, şifre korumalı dosyalar ve toplu işleme teknikleri için resmi [belgelere](https://docs.groupdocs.com/parser/java/) göz atın.

---

**Son Güncelleme:** 2026-02-06  
**Test Edilen Versiyon:** GroupDocs.Parser 23.11 (yazım anındaki en son)  
**Yazar:** GroupDocs