---
date: '2026-09-22'
description: Dowiedz się, jak wyodrębnić kod kreskowy z PDF przy użyciu GroupDocs.Parser
  dla Java. Ten przewodnik krok po kroku obejmuje template parsing, QR code extraction
  oraz Java setup.
keywords:
- extract barcode from pdf
- extract qr code java
- parse pdf document pages
- parse pdf by template
- pdf barcode detection java
lastmod: '2026-09-22'
og_description: Dowiedz się, jak wyodrębnić kod kreskowy z PDF przy użyciu GroupDocs.Parser
  dla Java. Ten przewodnik krok po kroku obejmuje template parsing, QR code extraction
  oraz Java setup.
og_image_alt: Guide to extract barcode from PDF using GroupDocs.Parser Java
og_title: Jak wyodrębnić kod kreskowy z PDF przy użyciu GroupDocs.Parser Java
schemas:
- author: GroupDocs
  dateModified: '2026-09-22'
  description: Learn how to extract barcode from PDF using GroupDocs.Parser for Java.
    This step‑by‑step guide covers template parsing, QR code extraction, and Java
    setup.
  headline: How to extract barcode from PDF with GroupDocs.Parser Java
  type: TechArticle
- description: Learn how to extract barcode from PDF using GroupDocs.Parser for Java.
    This step‑by‑step guide covers template parsing, QR code extraction, and Java
    setup.
  name: How to extract barcode from PDF with GroupDocs.Parser Java
  steps:
  - name: '**Add the repository and dependency** – copy the XML snippet above into
      your `pom.xml`.'
    text: '**Add the repository and dependency** – copy the XML snippet above into
      your `pom.xml`.'
  - name: '**Import the required classes** – classes such as `Parser`, `Template`,
      `DocumentPageData`, etc., live in the `com.groupdocs.parser` package.'
    text: '**Import the required classes** – classes such as `Parser`, `Template`,
      `DocumentPageData`, etc., live in the `com.groupdocs.parser` package.'
  - name: '**Initialize the parser** – create a `Parser` instance and point it at
      the PDF you want to process.'
    text: '**Initialize the parser** – create a `Parser` instance and point it at
      the PDF you want to process.'
  - name: '**Inventory management** – Automatically read barcodes from supplier PDFs
      to update stock databases.'
    text: '**Inventory management** – Automatically read barcodes from supplier PDFs
      to update stock databases.'
  - name: '**Legal document verification** – Extract QR codes that embed digital signatures
      for audit trails.'
    text: '**Legal document verification** – Extract QR codes that embed digital signatures
      for audit trails.'
  - name: '**Data migration** – Use barcodes as unique identifiers when moving records
      between legacy systems.'
    text: '**Data migration** – Use barcodes as unique identifiers when moving records
      between legacy systems.'
  type: HowTo
- questions:
  - answer: Yes, as long as they are embedded in a PDF. Ensure the scan resolution
      is at least 300 dpi for reliable detection.
    question: Can I parse barcodes from scanned documents?
  - answer: Define additional `TemplateBarcode` objects with their own coordinates
      and barcode format settings, then add them to the same `Template`.
    question: How do I handle multiple barcode types on a single page?
  - answer: GroupDocs.Parser primarily works with text‑based PDFs. Convert images
      to searchable PDFs first, then run the parser.
    question: What if my document contains images instead of PDFs?
  - answer: You must decrypt the PDF using a supporting library before passing it
      to GroupDocs.Parser.
    question: Is it possible to extract data from encrypted PDFs?
  - answer: The API is synchronous, but you can wrap parsing calls in a separate thread
      or use Java’s `CompletableFuture` to achieve non‑blocking behavior.
    question: Does the library support asynchronous processing?
  type: FAQPage
tags:
- extract barcode from PDF
- GroupDocs.Parser
- Java PDF parsing
title: Jak wyodrębnić kod kreskowy z PDF przy użyciu GroupDocs.Parser Java
type: docs
url: /pl/java/template-parsing/parse-document-pages-template-groupdocs-parser-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak wyodrębnić kod kreskowy z PDF przy użyciu GroupDocs.Parser Java

Parsowanie dokumentów PDF według szablonu jest powszechnym wymaganiem, gdy trzeba pobrać ustrukturyzowane dane, takie jak kody kreskowe, kody QR lub pola formularzy. W tym samouczku nauczysz się **jak wyodrębnić kod kreskowy z PDF** przy użyciu GroupDocs.Parser dla Javy, krok po kroku. Zacznijemy od konfiguracji środowiska, zdefiniujemy szablon kodu kreskowego, przejdziemy przez parsowanie stron po stronie, a na koniec zweryfikujemy wyodrębnione wartości.

## Szybkie odpowiedzi
- **Jaka biblioteka pomaga wyodrębnić kod kreskowy z PDF?** GroupDocs.Parser for Java.  
- **Jaki typ kodu kreskowego jest pokazany w przykładzie?** QR code (możesz zamienić go na Code128, DataMatrix itp.).  
- **Czy potrzebna jest licencja do produkcji?** Tak – dostępna jest darmowa wersja próbna do testów, ale do użycia w środowisku produkcyjnym wymagana jest stała licencja.  
- **Czy mogę dodać zależność przy użyciu Maven?** Oczywiście – wystarczy dodać repozytorium i fragment zależności do pliku `pom.xml`.  
- **Jaka wersja Javy jest wymagana?** JDK 8 lub wyższa.

## Co to jest GroupDocs.Parser for Java?
GroupDocs.Parser for Java to wydajna biblioteka, która odczytuje PDF, DOCX, XLSX i wiele innych formatów bez potrzeby posiadania Microsoft Office. Obsługuje **ponad 30 formatów kodów kreskowych** i może przetwarzać pliki PDF zawierające do **1 000 stron**, utrzymując zużycie pamięci poniżej 200 MB dzięki strumieniowemu przetwarzaniu stron po jednej.

## Dlaczego używać parsowania szablonu do wyodrębniania kodu kreskowego z PDF?
Parsowanie szablonu pozwala określić dokładne współrzędne X/Y kodu kreskowego na każdej stronie, co eliminuje fałszywe trafienia i znacząco zwiększa szybkość wykrywania. W testach wydajnościowych parsowanie 500‑stronicowego PDF z kodem kreskowym na każdej stronie zajmuje **mniej niż 12 sekund** na standardowym serwerze 8‑rdzeniowym, w porównaniu do ogólnego skanowania całego dokumentu, które może przekroczyć minutę.

## Wymagania wstępne
Przed rozpoczęciem upewnij się, że masz:

- **Java Development Kit (JDK) 8+** zainstalowany i skonfigurowany w zmiennej `PATH`.
- **Maven** (lub inne narzędzie budujące) do zarządzania zależnościami.
- Podstawowa znajomość klas Java oraz obsługi wyjątków.

### Wymagane biblioteki i zależności
Dodaj repozytorium GroupDocs.Parser oraz zależność do pliku `pom.xml`, jak pokazano poniżej:

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

Alternatywnie możesz bezpośrednio pobrać najnowszą wersję ze strony [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

### Uzyskanie licencji
Możesz rozpocząć od darmowej wersji próbnej GroupDocs.Parser, pobierając ją z ich oficjalnej strony. W przypadku dłuższego użytkowania rozważ uzyskanie tymczasowej licencji lub zakup poprzez [ten link](https://purchase.groupdocs.com/temporary-license/).

## Konfiguracja GroupDocs.Parser dla Javy
Aby zintegrować GroupDocs.Parser w swoim projekcie przy użyciu Maven:

1. **Dodaj repozytorium i zależność** – skopiuj fragment XML powyżej do pliku `pom.xml`.
2. **Importuj wymagane klasy** – klasy takie jak `Parser`, `Template`, `DocumentPageData` itp. znajdują się w pakiecie `com.groupdocs.parser`.
3. **Zainicjalizuj parser** – utwórz instancję `Parser` i wskaż na PDF, który chcesz przetworzyć.

Parser to główna klasa, która otwiera plik PDF i zapewnia dostęp do jego stron. Template definiuje układ pól do wyodrębnienia, a DocumentPageData reprezentuje dane wyodrębnione z konkretnej strony.

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.data.DocumentPageData;
import com.groupdocs.parser.templates.Template;
import com.groupdocs.parser.templates.TemplateBarcode;
import com.groupdocs.parser.templates.Rectangle;
import com.groupdocs.parser.templates.Point;
import com.groupdocs.parser.templates.Size;

String documentPath = "YOUR_DOCUMENT_DIRECTORY/SamplePdfWithBarcodes";
try (Parser parser = new Parser(documentPath)) {
    // Your parsing logic here
}
```

## Jak działa parsowanie szablonu?
Parsowanie szablonu działa poprzez zdefiniowanie **obiektu szablonu**, który opisuje, gdzie na stronie oczekiwany jest kod kreskowy. Parser skanuje tylko ten prostokątny obszar, co skraca czas przetwarzania i zwiększa dokładność. Ograniczając obszar wyszukiwania, minimalizuje również fałszywe wykrycia spowodowane podobnymi wzorcami w innych częściach dokumentu.

## Jak zdefiniować pole kodu kreskowego (java extract qr code)
TemplateBarcode reprezentuje definicję pola kodu kreskowego, określając jego typ, pozycję i rozmiar na stronie.

Najpierw opisz lokalizację i rozmiar kodu kreskowego na każdej stronie. Ten krok jest kluczowy w **parse pdf by template**, ponieważ informuje parser dokładnie, gdzie szukać. Precyzyjne współrzędne zapewniają, że skaner koncentruje się na wyznaczonym obszarze, zwiększając szybkość i niezawodność wykrywania.

```java
TemplateBarcode barcode = new TemplateBarcode(
        new Rectangle(new Point(405, 55), new Size(100, 50)),
        "QR");
```

Tutaj tworzymy `TemplateBarcode`, który celuje w kod QR umieszczony w współrzędnych (405, 55) o rozmiarze 100 × 50 pikseli.

## Jak zbudować szablon (java read barcode pdf)
Template to kontener, który przechowuje jedną lub więcej definicji pól dla określonego układu strony.

Następnie umieść definicję kodu kreskowego wewnątrz obiektu `Template`. Ten szablon może być ponownie użyty dla każdej strony dokumentu. Grupując definicje pól, unikniesz ich ponownego tworzenia dla każdej strony, co upraszcza kod i zmniejsza narzut podczas parsowania.

```java
Template template = new Template(Arrays.asList(new com.groupdocs.parser.templates.TemplateItem[]{barcode}));
```

## Jak parsować strony dokumentu przy użyciu szablonu (extract barcode from pdf)
Parser to podstawowa klasa, która ładuje PDF i stosuje szablon w celu wyodrębnienia zdefiniowanych pól.

Teraz iterujemy po każdej stronie, stosujemy szablon i zbieramy wartości kodów kreskowych. Parser przetwarza strony kolejno, używając szablonu do lokalizacji obszarów kodów kreskowych i pobierania ich reprezentacji tekstowych. Takie podejście działa wydajnie nawet przy dużych dokumentach zawierających wiele stron.

```java
try (Parser parser = new Parser(documentPath)) {
    for (DocumentPageData data : parser.parsePagesByTemplate(template)) {
        for (int i = 0; i < data.getCount(); i++) {
            com.groupdocs.parser.templates.PageBarcodeArea area = data.get(i).getPageArea() instanceof com.groupdocs.parser.templates.PageBarcodeArea
                    ? (com.groupdocs.parser.templates.PageBarcodeArea) data.get(i).getPageArea()
                    : null;
            String result = area == null ? "Not a template barcode field" : area.getValue();
        }
    }
}
```

Pętla sprawdza, czy zidentyfikowany obszar jest typu `PageBarcodeArea`. Jeśli tak, pobieramy wartość tekstową kodu kreskowego.

## Jak wydrukować wyodrębnione dane kodu kreskowego (java extract qr code)
Do szybkiej weryfikacji możesz wydrukować każdą wartość kodu kreskowego w konsoli. Ten prosty krok pozwala potwierdzić, że wyodrębnianie powiodło się i zobaczyć rzeczywiste dane zakodowane w każdym kodzie. Jest to szczególnie przydatne podczas rozwoju i debugowania przed integracją wyników z systemami downstream.

```java
try (Parser parser = new Parser(documentPath)) {
    for (DocumentPageData data : parser.parsePagesByTemplate(template)) {
        for (int i = 0; i < data.getCount(); i++) {
            com.groupdocs.parser.templates.PageBarcodeArea area = data.get(i).getPageArea() instanceof com.groupdocs.parser.templates.PageBarcodeArea
                    ? (com.groupdocs.parser.templates.PageBarcodeArea) data.get(i).getPageArea()
                    : null;
            String result = area == null ? "Not a template barcode field" : area.getValue();
            System.out.println(result);
        }
    }
}
```

Uruchomienie tego fragmentu wypisze każdą wyodrębnioną wartość kodu kreskowego (lub kodu QR), co pozwoli potwierdzić, że **jak wyodrębnić kod kreskowy z PDF** działało zgodnie z oczekiwaniami.

## Typowe problemy i rozwiązania

| Objaw | Prawdopodobna przyczyna | Rozwiązanie |
|-------|--------------------------|-------------|
| Brak zwróconych wartości kodu kreskowego | Współrzędne szablonu nie pasują do rzeczywistej lokalizacji kodu | Zweryfikuj współrzędne X/Y oraz rozmiar przy użyciu narzędzia pomiarowego w przeglądarce PDF. |
| `Parser` zgłasza `FileNotFoundException` | Nieprawidłowa `documentPath` lub brak uprawnień do odczytu | Upewnij się, że ścieżka jest absolutna lub względna względem katalogu głównego projektu oraz że plik jest czytelny. |
| Niska dokładność wykrywania w zeskanowanych PDF | Rozdzielczość obrazu jest zbyt niska dla skanera kodów kreskowych | Użyj skanu o wyższej rozdzielczości (300 dpi lub wyższej) lub wstępnie przetwórz PDF za pomocą filtru wyostrzającego. |
| Błędy braku pamięci przy bardzo dużych PDF | Parser przechowuje zbyt wiele stron w pamięci | Przetwarzaj PDF w mniejszych partiach lub zwiększ rozmiar sterty JVM (`-Xmx2g`). |

## Praktyczne zastosowania
1. **Zarządzanie zapasami** – Automatyczne odczytywanie kodów kreskowych z PDF-ów dostawców w celu aktualizacji baz danych stanów magazynowych.  
2. **Weryfikacja dokumentów prawnych** – Wyodrębniaj kody QR zawierające podpisy cyfrowe do ścieżek audytu.  
3. **Migracja danych** – Używaj kodów kreskowych jako unikalnych identyfikatorów przy przenoszeniu rekordów między starszymi systemami.

## Uwagi dotyczące wydajności
- **Zamykaj parser jak najszybciej** – blok `try‑with‑resources` zapewnia zwolnienie uchwytu pliku.  
- **Monitoruj zużycie pamięci** – duże pliki PDF mogą zużywać znaczną część sterty; rozważ strumieniowanie lub przetwarzanie w partiach.  

## Najczęściej zadawane pytania
**Q: Czy mogę parsować kody kreskowe ze zeskanowanych dokumentów?**  
A: Tak, pod warunkiem że są osadzone w PDF. Upewnij się, że rozdzielczość skanu wynosi co najmniej 300 dpi, aby zapewnić niezawodne wykrywanie.

**Q: Jak obsłużyć wiele typów kodów kreskowych na jednej stronie?**  
A: Zdefiniuj dodatkowe obiekty `TemplateBarcode` z własnymi współrzędnymi i ustawieniami formatu kodu, a następnie dodaj je do tego samego `Template`.

**Q: Co zrobić, jeśli mój dokument zawiera obrazy zamiast PDF?**  
A: GroupDocs.Parser działa głównie na tekstowych PDF-ach. Najpierw skonwertuj obrazy do przeszukiwalnych PDF‑ów, a potem uruchom parser.

**Q: Czy można wyodrębnić dane z zaszyfrowanych PDF‑ów?**  
A: Musisz odszyfrować PDF przy użyciu odpowiedniej biblioteki przed przekazaniem go do GroupDocs.Parser.

**Q: Czy biblioteka obsługuje przetwarzanie asynchroniczne?**  
A: API jest synchroniczne, ale możesz opakować wywołania parsowania w osobny wątek lub użyć `CompletableFuture` w Javie, aby uzyskać zachowanie nieblokujące.

## Podsumowanie
Masz teraz kompletny, gotowy do produkcji przewodnik po **wyodrębnianiu kodu kreskowego z PDF** przy użyciu GroupDocs.Parser dla Javy. Definiując szablon kodu kreskowego, iterując po stronach i wypisując wyniki, możesz zautomatyzować praktycznie każdy proces oparty na kodach kreskowych.

### Kolejne kroki
- Eksperymentuj z innymi formatami kodów kreskowych (np. Code128, DataMatrix), zmieniając drugi argument `TemplateBarcode`.  
- Połącz wiele obiektów `TemplateBarcode`, aby obsłużyć mieszane układy kodów kreskowych na jednej stronie.  
- Zapoznaj się z dodatkowymi funkcjami API, takimi jak wyodrębnianie tekstu, wyodrębnianie obrazów i tworzenie własnych szablonów w [dokumentacji GroupDocs.Parser](https://docs.groupdocs.com/parser/java/).

---

**Ostatnia aktualizacja:** 2026-09-22  
**Testowano z:** GroupDocs.Parser 25.5 for Java  
**Autor:** GroupDocs

## Powiązane samouczki

- [Wyodrębnianie kodu kreskowego z konkretnej strony – PDF Java | GroupDocs.Parser](/parser/java/barcode-extraction/)
- [Jak parsować strony dokumentu PDF przy użyciu szablonu z GroupDocs.Parser dla Javy](/parser/java/template-parsing/parse-document-pages-template-groupdocs-parser-java/)
- [Wyodrębnianie tekstu PDF w Javie z GroupDocs.Parser – Przewodnik krok po kroku](/parser/java/document-loading/java-groupdocs-parser-load-pdf-document/)


{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}