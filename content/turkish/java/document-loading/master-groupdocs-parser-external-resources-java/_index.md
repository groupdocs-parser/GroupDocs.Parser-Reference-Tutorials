---
date: '2025-12-29'
description: GroupDocs.Parser for Java kullanarak belgelerden resim çıkarma ve kaynakları
  filtreleme yöntemlerini öğrenin. Bu kılavuz, yapılandırma, özel işleyiciler ve pratik
  örnekleri kapsamaktadır.
keywords:
- GroupDocs.Parser for Java
- external resource loading in Java
- custom handlers in GroupDocs
title: GroupDocs.Parser Java ile Belgelerden Görüntüleri Çıkarma – Bir Kılavuz
type: docs
url: /tr/java/document-loading/master-groupdocs-parser-external-resources-java/
weight: 1
---

# Belgelerden Görüntüleri Çıkarma ve GroupDocs.Parser Java ile Kaynakları Filtreleme

Belgelerden görüntüleri çıkarmak, belge‑işleme hatları oluştururken yaygın bir gereksinimdir. Bu öğreticide GroupDocs.Parser for Java kullanarak **belgelerden görüntüleri nasıl çıkaracağınızı** keşfedecek ve **kaynakları nasıl filtreleyeceğinizi** öğrenecek, böylece yalnızca ihtiyacınız olan dosyalar yüklenir. Kütüphaneyi kurma, özel bir `ExternalResourceHandler` oluşturma ve uygulamanızı hızlı ve güvenli tutmak için filtreleme mantığını uygulama adımlarını göstereceğiz.

## Hızlı Yanıtlar
- **GroupDocs.Parser ne yapar?** Çeşitli belge formatlarını ayrıştırır ve size metin, görüntü ve diğer gömülü kaynaklara erişim sağlar.  
- **İstenmeyen görüntüleri atlayabilir miyim?** Evet—özel bir `ExternalResourceHandler` uygulayarak hangi kaynakların yükleneceğine karar verebilirsiniz.  
- **Hangi Maven sürümü gerekiyor?** GroupDocs.Parser Java 25.5 veya daha yenisini kullanın.  
- **Lisans gerekir mi?** Değerlendirme için ücretsiz deneme çalışır; üretim için kalıcı bir lisans gereklidir.  
- **Bu yaklaşım çoklu iş parçacığı güvenli mi?** Ayrıştırma nesneleri iş parçacıkları arasında paylaşılmaz; her iş parçacığı için yeni bir `Parser` örneği oluşturun.

## “Belgelerden görüntüleri çıkarmak” ne demektir?
Bir belge gömülü resimler, grafikler veya diğer medya öğeleri içerdiğinde, “belgelerden görüntüleri çıkarmak”, bu ikili dosyaları programlı olarak alarak orijinal dosyanın dışına depolamanızı, görüntülemenizi veya daha fazla işlem yapmanızı sağlar.

## Görüntüleri çıkarırken neden kaynakları filtrelemelisiniz?
- Büyük veya alakasız dosyaları göz ardı ederek bellek tüketimini azaltın.  
- Potansiyel olarak güvensiz içeriğin yüklenmesini engelleyerek güvenliği artırın.  
- Özellikle çok sayıda gömülü nesne içeren büyük belgelerde işleme hızını artırın.

## Önkoşullar

- **Java Development Kit (JDK)** – sürüm 8 veya üzeri.  
- **Maven** – bağımlılık yönetimi için.  
- Java I/O ve istisna yönetimi konusunda temel bilgi.

## GroupDocs.Parser for Java Kurulumu

`pom.xml` dosyanıza GroupDocs deposunu ve parser bağımlılığını ekleyin:

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

Alternatif olarak, en son sürümü [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/) adresinden indirin.

### Lisans Edinme
- **Free Trial** – temel özellikleri ücretsiz keşfedin.  
- **Temporary License** – değerlendirme sırasında tam işlevselliği açın.  
- **Purchased License** – ticari dağıtım için gereklidir.

## Görüntüleri çıkarırken kaynakları nasıl filtrelersiniz

### Adım 1: Özel bir işleyici oluşturun
`ExternalResourceHandler` sınıfını genişleten bir sınıf tanımlayın. `onLoading` metodunun içinde hangi kaynakların tutulacağına karar verirsiniz.

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

### Adım 2: İşleyiciyle `ParserSettings` yapılandırın
`Handler` örneğinizi `ParserSettings`e geçirin ve belge açarken kullanın.

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

### Adım 3: Filtreleme mantığını ince ayar yapın
Daha karmaşık kurallara ihtiyacınız varsa—örneğin görüntü boyutu, formatı veya URI deseniyle filtreleme—`onLoading` metodunu buna göre genişletin:

```java
@Override
public void onLoading(ExternalResourceLoadingArgs args) {
    if (!args.getUri().endsWith("installation.png")) {
        args.setSkipped(true);
    }
}
```

## Pratik Uygulamalar

1. **Document Management Systems** – Taranmış sözleşmelerden yalnızca gerekli görüntüleri çekerek küçük resimler oluşturun.  
2. **Data Extraction Services** – Dekoratif grafikleri atlayın ve değerli veri içeren grafiklere odaklanın.  
3. **Web Scraping Tools** – HTML‑tabanlı belgelerden anlamlı medyayı alırken izleme piksellerini filtreleyin.

## Performans Düşünceleri
- **Erken filtreleme**: Kaynaklar üzerinde döngü yapmadan önce özel işleyicinizi uygulayarak istenmeyen verilerin belleğe yüklenmesini önleyin.  
- **Hemen serbest bırakma**: Yerel kaynakları serbest bırakmak için try‑with‑resources (`try (Parser parser = …)`) kullanın.  
- **Asenkron işleme**: Büyük toplular için belgeleri paralel akışlarda işleyin ve her `Parser` örneğini tek bir iş parçacığına sınırlı tutun.

## Yaygın Sorunlar ve Çözümler

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| Görüntü bulunamadı | İşleyici, tüm kaynakları istemeden atlıyor | `if` koşulunu doğrulayın ve `args.setSkipped(true)` yalnızca istenmeyen URI'ler için çağrıldığından emin olun. |
| Büyük dosyalarda `IOException` | Yetersiz yığın belleği | JVM yığın boyutunu artırın (`-Xmx2g`) veya sayfaları daha küçük parçalar halinde işleyin. |
| Lisans tanınmadı | Üretim kodunda deneme DLL'si kullanmak | `License.setLicense("path/to/license")` ile doğru lisans dosyası yolunu uygulayın. |

## Sıkça Sorulan Sorular

**Q:** Özel bir `ExternalResourceHandler` kullanmanın temel amacı nedir?  
**A:** Hangi dış kaynakların yükleneceğini kontrol etmenizi sağlar, gereksiz dosyaları filtreleyerek güvenliği ve performansı artırır.

**Q:** GroupDocs.Parser for Java'ı lisans olmadan kullanabilir miyim?  
**A:** Evet, ücretsiz bir deneme mevcuttur, ancak bazı gelişmiş özellikler geçici veya satın alınmış bir lisans alana kadar sınırlı olabilir.

**Q:** GroupDocs.Parser ile ayrıştırma sırasında istisnaları nasıl ele alırım?  
**A:** `IOException` ve diğer belirli istisnalar için try‑catch bloklarıyla ayrıştırma çağrılarını sararak hataları nazikçe ele alın.

**Q:** Kaynakları filtrelerken yaygın tuzaklar nelerdir?  
**A:** Yanlış URI kontrolleri gerekli dosyaları atlayabilir; koşullarınızı doğrulamak için günlükleme veya breakpoint kullanın.

**Q:** GroupDocs.Parser for Java ile HTML dışı belgeler ayrıştırılabilir mi?  
**A:** Kesinlikle—GroupDocs.Parser PDF, Word, Excel, PowerPoint ve birçok diğer formatı destekler.

## Sonraki Adımlar
Kütüphaneyi daha derinlemesine keşfetmek için [API Reference](https://reference.groupdocs.com/parser/java) adresini inceleyin veya tablo çıkarımı için `ParserSettings.setDetectTables(true)` gibi ek ayarlarla deney yapın.

---

**Last Updated:** 2025-12-29  
**Tested With:** GroupDocs.Parser 25.5 for Java  
**Author:** GroupDocs  

**Resources**  
- **Dokümantasyon:** [GroupDocs.Parser Documentation](https://docs.groupdocs.com/parser/java/)  
- **API Referansı:** [API Details](https://reference.groupdocs.com/parser/java)  
- **İndirmeler:** [Latest Versions](https://releases.groupdocs.com/parser/java/)