---
date: '2026-04-21'
description: GroupDocs.Parser for Java kullanarak PDF'de birden fazla anahtar kelimeyi
  nasıl arayacağınızı ve PDF'yi sayfa numarasına göre nasıl arayacağınızı öğrenin.
  Adım adım kod, hata yönetimi ve performans ipuçlarını alın.
keywords:
- search multiple keywords in pdf
- search pdf by page number
- GroupDocs.Parser for Java
title: Java için GroupDocs.Parser kullanarak PDF'de birden fazla anahtar kelimeyi
  arama – Kapsamlı Rehber
type: docs
url: /tr/java/text-search/groupdocs-parser-java-pdf-text-search-guide/
weight: 1
---

# PDF'de birden fazla anahtar kelime arama - GroupDocs.Parser for Java kullanarak

PDF belgelerinde belirli metni bulmak zor olabilir, özellikle büyük dosyalar veya çok sayıda sayfa ile çalışırken. **PDF'de birden fazla anahtar kelime aramanız** gerekiyorsa, GroupDocs.Parser for Java kütüphanesi temiz, yüksek performanslı bir çözüm sunar. Bu öğreticide kütüphaneyi kurma, sayfa numarasına göre arama ve desteklenmeyen formatları ele alma konularını adım adım gösteriyoruz—projeye kopyalayabileceğiniz gerçek dünya örnekleriyle.

## Hızlı Yanıtlar
- **PDF'de birden fazla anahtar kelime aramanıza yardımcı olan kütüphane nedir?** GroupDocs.Parser for Java.  
- **Sonuçları belirli sayfa numaralarına sınırlayabilir misiniz?** Evet, `SearchOptions` kullanarak her eşleşme için sayfa indeksini alabilirsiniz.  
- **Geliştirme için lisansa ihtiyacım var mı?** Test için ücretsiz deneme çalışır; üretim için ücretli lisans gereklidir.  
- **Regex destekleniyor mu?** Kesinlikle – `SearchOptions` içinde etkinleştirin.  
- **Hangi Java sürümü gereklidir?** Maven veya Gradle yapı araçlarıyla Java 8 veya üzeri.

## “PDF'de birden fazla anahtar kelime arama” nedir?
Büyük bir PDF'de “invoice”, “due date” veya “total” gibi birden fazla terimi bulmanız gerektiğinde, her eşleşme için sayfa numaralarını döndüren tek geçişli bir arama zaman ve kod karmaşıklığını azaltır. GroupDocs.Parser düşük seviyeli PDF ayrıştırmayı soyutlayarak bu çoklu‑anahtar kelime sorgularını gerçekleştirmek için basit bir API sunar.

## Neden GroupDocs.Parser for Java kullanmalısınız?
- **Tarama veya karmaşık PDF'lerden bile doğru metin çıkarma**.  
- **Yerleşik sayfa indeksleme** sayesinde her anahtar kelimenin tam olarak nerede göründüğünü bilirsiniz.  
- **Desteklenmeyen formatlar, şifreli dosyalar ve bellek yoğun belgeler** için istisna yönetimi.  
- **Sıfır bağımlılık Maven entegrasyonu** hızlı proje kurulumunu sağlar.

## Önkoşullar
- **Java 8+** ve Maven uyumlu bir IDE (IntelliJ IDEA, Eclipse vb.).  
- **GroupDocs.Parser for Java** (sürüm 25.5 veya üzeri).  
- Java istisna yönetimi ve dosya I/O hakkında temel bilgi.

## GroupDocs.Parser for Java Kurulumu
Kütüphaneyi Maven üzerinden ekleyebilir veya doğrudan indirebilirsiniz.

### Maven Kullanarak
Depoyu ve bağımlılığı `pom.xml` dosyanıza ekleyin:
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
Alternatif olarak, en son sürümü [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/) adresinden indirin.  
**Lisans Alımı**: GroupDocs.Parser'ı test etmek için ücretsiz deneme ile başlayın veya geçici bir lisans isteyin. Uzun vadeli kullanım için lisans satın almayı düşünün.

#### Temel Başlatma ve Kurulum
Kütüphane erişilebilir olduğunda, başlatması oldukça basittir:
```java
import com.groupdocs.parser.Parser;

String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.pdf";
try (Parser parser = new Parser(filePath)) {
    // Your parsing logic here
} catch (Exception e) {
    System.err.println("An error occurred: " + e.getMessage());
}
```

## Uygulama Kılavuzu
Uygulamayı iki pratik özelliğe ayıracağız:

1. **PDF'de birden fazla anahtar kelime arama ve sayfa numaralarını alma** – “pdf'yi sayfa numarasına göre arama” için ideal.  
2. **Desteklenmeyen belge formatları için sorunsuz hata yönetimi**.

### Özellik 1: PDF'de birden fazla anahtar kelime arama ve sayfa indekslerini alma
#### Genel Bakış
GroupDocs.Parser'ın `search` yöntemi, `SearchOptions` ile birleştirildiğinde, herhangi bir terimi (veya düzenli ifade desenini) bulmanızı sağlar ve hem karakter konumunu hem de sayfa indeksini döndürür.

#### Adım‑adım
**Adım 1 – Gerekli sınıfları içe aktarın**  
```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.data.SearchResult;
import com.groupdocs.parser.options.SearchOptions;
import com.groupdocs.parser.exceptions.UnsupportedDocumentFormatException;
```

**Adım 2 – Parser'ı başlatın ve `SearchOptions`'ı yapılandırın**  
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.pdf"; // Replace with actual document path

try (Parser parser = new Parser(filePath)) {
    if (!parser.getFeatures().isText()) {
        throw new UnsupportedDocumentFormatException("Text extraction isn't supported.");
    }

    // false = case‑insensitive, false = not whole‑word, false = regex disabled, true = return page index
    SearchOptions options = new SearchOptions(false, false, false, true);
    Iterable<SearchResult> results = parser.search("invoice|due date|total", options);
    
    for (SearchResult result : results) {
        System.out.println(String.format("Found at position %d on page %d: %s", 
                                         result.getPosition(), 
                                         result.getPageIndex() + 1, // pages are zero‑based
                                         result.getText()));
    }
} catch (UnsupportedDocumentFormatException e) {
    System.err.println(e.getMessage());
}
```

**Anahtar parametrelerin açıklaması**
- `filePath`: Aramak istediğiniz PDF'nin yolu.  
- `SearchOptions(false, false, false, true)`:  
  * **Büyük/küçük harfe duyarlı** – `false` aramayı büyük/küçük harfe duyarsız yapar.  
  * **Tam kelime** – `false` kısmi eşleşmelere izin verir.  
  * **Regex** – `false` düzenli ifade ayrıştırmayı devre dışı bırakır; regex gerekiyorsa `true` yapın.  
  * **Sayfa indeksini döndür** – `true` her `SearchResult`'un sayfa numarasını içerdiğini garantiler.  

**İpucu:** Arama dizesi `"invoice|due date|total"` tek bir çağrıda *birden fazla anahtar kelime* aramak için boru (`|`) operatörünü kullanır.

#### Sorun Giderme
- **Boş sonuçlar:** PDF'nin seçilebilir metin içerdiğini (sadece görüntü olmadığını) doğrulayın.  
- **Yanlış sayfa numaraları:** `getPageIndex()` sıfır‑tabanlıdır; insan okuyuşu için `+1` ekleyin.

### Özellik 2: Desteklenmeyen belge formatları için hata yönetimi
#### Genel Bakış
Her dosya metin için ayrıştırılamaz (örneğin, bazı şifreli veya yalnızca görüntü PDF'leri). `UnsupportedDocumentFormatException` yakalamak uygulamanızın sorunsuz bir şekilde başarısız olmasını sağlar.

#### Uygulama
**Adım 1 – Parser oluşturmayı try‑catch bloğuna sarın**  
```java
try (Parser parser = new Parser(filePath)) {
    if (!parser.getFeatures().isText()) {
        throw new UnsupportedDocumentFormatException("Text extraction isn't supported.");
    }
} catch (UnsupportedDocumentFormatException e) {
    System.err.println(e.getMessage());
}
```

**Neden önemli**  
Desteklenmeyen formatları erken tespit ederek kullanıcıları bilgilendirebilir, sorunu kaydedebilir veya tüm süreci çökertmek yerine OCR çözümüne geçebilirsiniz.

## Pratik Uygulamalar
Aşağıda **PDF'de birden fazla anahtar kelime arama**'nın öne çıktığı üç yaygın senaryo bulunmaktadır:

1. **Hukuki Belge İncelemesi** – Yüzlerce sayfa boyunca “force majeure”, “termination” veya “confidentiality” gibi maddeleri bulun.  
2. **Fatura İşleme** – Otomatik muhasebe için “invoice number”, “due date” ve “total amount” değerlerini tek geçişte çıkarın.  
3. **Akademik Araştırma** – Araştırma makalelerinde birden fazla terminoloji varyasyonunu tarayın (ör. “machine learning”, “deep learning”, “neural network”).

## Performans Düşünceleri
- **Yalnızca gerekli sayfaları ayrıştırın**: İlgili bölümleri biliyorsanız, bellek kullanımını azaltmak için arama aralığını sınırlayın.  
- **try‑with‑resources kullanın** (gösterildiği gibi) parser'ların hızlıca kapatılmasını sağlayarak bellek sızıntılarını önleyin.  
- **Tam PDF'yi belleğe yüklemekten kaçının** çok büyük dosyalarla çalışırken; mümkünse parçalar halinde işleyin.

## Sonuç
Artık **PDF'de birden fazla anahtar kelime arama** belgeleri için tam, üretim‑hazır bir yaklaşıma sahipsiniz; tam sayfa numaralarını alabilir ve GroupDocs.Parser for Java kullanarak desteklenmeyen formatları sorunsuz bir şekilde yönetebilirsiniz. Bu kod parçacıklarını daha büyük iş akışlarına—toplu işleme, web servisleri veya masaüstü yardımcı programlara—entegre ederek belge analizini ölçekli bir şekilde otomatikleştirebilirsiniz.

**Sonraki Adımlar**  
- Daha karmaşık aramalar için regex desenleriyle deney yapın.  
- Arama sonuçlarını bir PDF yazıcı (ör. GroupDocs.Conversion) ile birleştirerek eşleşmeleri vurgulayın.  
- PDF klasörünü dolaşarak ve sonuçları bir veritabanına kaydederek toplu işleme keşfedin.

## Sıkça Sorulan Sorular
**S: Aynı anda birden fazla anahtar kelime arayabilir miyim?**  
C: Evet. Boru ile ayrılmış bir dize (ör. `"invoice|due date|total"`) kullanın veya `SearchOptions` içinde regex'i etkinleştirin.

**S: Belgem şifreli olursa ne olur?**  
C: `Parser` oluştururken şifreyi sağlayın. Şifre yoksa, kütüphane yakalayabileceğiniz bir istisna fırlatır.

**S: Çok büyük PDF dosyalarını verimli bir şekilde nasıl yönetirim?**  
C: Dosyayı sayfa‑sayfa işleyin veya `SearchOptions` ile kapsamı belirli sayfa aralıklarıyla sınırlayın.

**S: GroupDocs.Parser tüm PDF sürümleriyle uyumlu mu?**  
C: Çoğu PDF standardını (1.4‑1.7, PDF/A, PDF/X) destekler. Her zaman kendi dosyalarınızla test edin.

**S: Bu belge toplu işleme için kullanılabilir mi?**  
C: Kesinlikle. Bir dizini döngüye alıp aynı arama mantığını uygulayarak her dosyanın sonuçlarını saklayabilirsiniz.

## Kaynaklar
- **Dokümantasyon**: [GroupDocs.Parser Java Documentation](https://docs.groupdocs.com/parser/java/)  
- **API Referansı**: [GroupDocs API Reference](https://reference.groupdocs.com/parser/java/)

---

**Son Güncelleme:** 2026-04-21  
**Test Edilen Versiyon:** GroupDocs.Parser for Java 25.5  
**Yazar:** GroupDocs  

{< /blocks/products/pf/tutorial-page-section >}
{< /blocks/products/pf/main-container >}
{< /blocks/products/pf/main-wrap-class >}
{< blocks/products/products-backtop-button >}