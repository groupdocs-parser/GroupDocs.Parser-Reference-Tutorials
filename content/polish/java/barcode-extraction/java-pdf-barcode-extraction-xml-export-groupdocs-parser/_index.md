---
date: '2026-10-12'
description: Dowiedz się, jak wyodrębnić kod QR z PDF w Javie przy użyciu GroupDocs.Parser
  i wyeksportować dane kodu kreskowego do XML w celu dalszego przetwarzania.
keywords:
- extract QR from PDF
- how to read QR
- read QR codes Java
- parse QR codes Java
- PDF QR code extraction
lastmod: '2026-10-12'
og_description: Dowiedz się, jak wyodrębnić kod QR z PDF w Javie przy użyciu GroupDocs.Parser
  i wyeksportować dane kodu kreskowego do XML w celu dalszego przetwarzania.
og_image_alt: Guide showing Java code that extracts QR codes from PDF files with GroupDocs.Parser
  and saves results as XML
og_title: Jak wyodrębnić kod QR z PDF w Javie przy użyciu GroupDocs.Parser
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
title: Jak wyodrębnić kod QR z PDF w Javie przy użyciu GroupDocs.Parser
type: docs
url: /pl/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Jak wyodrębnić QR z PDF w Javie przy użyciu GroupDocs.Parser

W nowoczesnych przepływach pracy biznesowej **wyodrębnianie QR z PDF** może przekształcić ręczną wąską szyjkę wprowadzania danych w w pełni zautomatyzowany proces. Niezależnie od tego, czy obsługujesz listy przewozowe, paragony detaliczne czy katalogi produktów, szybkie i niezawodne pobieranie informacji QR jest niezbędne dla systemów downstream. Ten samouczek prowadzi Cię przez użycie **GroupDocs.Parser for Java** do odczytu kodów QR (i innych kodów kreskowych) z PDF‑ów oraz eksportu wyników do czystego pliku XML, który może być konsumowany przez Twój system ERP, magazynowy lub analityczny.

## Szybkie odpowiedzi
- **Co robi GroupDocs.Parser for Java?** Odczytuje pliki PDF i wyodrębnia dane strukturalne, takie jak kody kreskowe, tabele i tekst.  
- **Jak wyodrębnić kody QR?** Skonfiguruj `BarcodeOptions` z typem QR i wywołaj `parser.getBarcodes()`.  
- **Czy mogę odczytywać kody QR w Javie?** Tak — ustaw typ kodu kreskowego na `"QR"` w opcjach.  
- **Czy potrzebna jest licencja?** Wersja próbna działa do testów; licencja komercyjna jest wymagana w produkcji.  
- **Jaka wersja Javy jest wymagana?** Zalecana jest Java 8 lub nowsza.

## Co oznacza „wyodrębnić QR z PDF” w kontekście przetwarzania PDF?
Wyodrębnianie QR z PDF oznacza skanowanie każdej strony w poszukiwaniu grafik zakodowanych QR, dekodowanie osadzonych danych i zwracanie ich w formacie przyjaznym dla programu. GroupDocs.Parser abstrahuje niskopoziomową analizę obrazu, dzięki czemu możesz skupić się na logice biznesowej, a nie na manipulacji pikselami.

## Dlaczego używać GroupDocs.Parser do wyodrębniania QR?
GroupDocs.Parser obsługuje **ponad 30 formatów wejściowych** i może przetwarzać PDF‑y do **500 MB** bez ładowania całego pliku do pamięci, dostarczając wyniki o wysokiej dokładności nawet przy skanach o niskiej rozdzielczości. Możesz wybrać `QualityMode.Low` dla szybkości lub `QualityMode.High` dla maksymalnej precyzji, a to samo API działa dla PDF‑ów, obrazów i dokumentów Office, eliminując potrzebę wielu bibliotek.

## Wymagania wstępne
- **GroupDocs.Parser for Java** (wersja 25.5 lub nowsza).  
- Maven lub ręczne pobranie JAR.  
- Środowisko programistyczne Java 8+ (IntelliJ IDEA, Eclipse lub dowolny edytor).  

## Konfigurowanie GroupDocs.Parser dla Javy
### Korzystanie z Maven
Dodaj repozytorium GroupDocs i zależność do swojego `pom.xml`:

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

### Bezpośrednie pobranie
Alternatywnie pobierz najnowszy JAR z [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

#### Kroki uzyskania licencji
- **Bezpłatna wersja próbna:** 30‑dniowa wersja próbna z pełnym zestawem funkcji.  
- **Licencja tymczasowa:** Poproś o tymczasowy klucz do rozszerzonej oceny.  
- **Zakup:** Uzyskaj licencję komercyjną do wdrożeń produkcyjnych.

### Podstawowa inicjalizacja i konfiguracja
Utwórz instancję `Parser`, która wskazuje na PDF, który chcesz analizować:

`Parser` jest podstawową klasą w GroupDocs.Parser, reprezentującą dokument i udostępniającą metody do wyodrębniania treści, takich jak tekst, tabele i kody kreskowe.  

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

## Jak odczytywać kody QR w PDF‑ach Javy przy użyciu GroupDocs.Parser
Odczytywanie kodów QR w PDF‑ach Javy przy użyciu GroupDocs.Parser polega na stworzeniu instancji parsera, skonfigurowaniu opcji kodów kreskowych pod kątem typów QR, wywołaniu metody wyodrębniania kodów oraz obsłudze zwróconych obiektów kodów. Proces jest prosty, działa na dowolnej stronie PDF i zwraca odszyfrowane wartości wraz z metadanymi położenia do dalszego przetwarzania.

### Krok 1: sprawdź obsługę kodów kreskowych
Przed próbą wyodrębnienia potwierdź, że format dokumentu obsługuje skanowanie kodów kreskowych:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*Wyjaśnienie:* Ten warunek zapobiega błędom w czasie wykonywania przy nieobsługiwanych typach plików.

### Krok 2: skonfiguruj opcje kodów kreskowych (odczyt QR w Javie)
`BarcodeOptions` jest obiektem konfiguracyjnym, który pozwala określić, które symbologie kodów kreskowych wykrywać, ustawić tryb jakości skanowania oraz dostroić parametry, takie jak progi wykrywania, zapewniając optymalną wydajność dla docelowych kodów QR.  

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*Wyjaśnienie:* `QualityMode.Low` przyspiesza przetwarzanie; przełącz na `High`, jeśli potrzebna jest większa dokładność. Argument `"QR"` informuje silnik, aby szukał wyłącznie kodów typu QR.

### Krok 3: wyodrębnij dane QR
`parser.getBarcodes(options)` skanuje dokument przy użyciu podanych `BarcodeOptions` i zwraca kolekcję obiektów `PageBarcodeArea`, z których każdy zawiera odszyfrowaną wartość QR, numer strony oraz dokładne współrzędne kodu na stronie, umożliwiając precyzyjną obsługę downstream.  

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*Wyjaśnienie:* `parser.getBarcodes` zwraca iterowalną kolekcję obiektów `PageBarcodeArea`, z których każdy zawiera odszyfrowaną wartość QR i jej położenie na stronie.

## Eksportowanie wyodrębnionych danych do XML
### Krok 4: zainicjuj eksportera XML
`XmlExporter` jest klasą pomocniczą, która przekształca kolekcję obiektów kodów kreskowych w dobrze ustrukturyzowany dokument XML, automatycznie generując elementy dla każdego kodu z atrybutami indeksu strony, pozycji i odszyfrowanej wartości, które można następnie zapisać lub przesłać do innych systemów.  

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*Wyjaśnienie:* `XmlExporter` obsługuje serializację obiektów kodów kreskowych do standardowego XML, gotowego do integracji z systemami ERP lub magazynowymi.

### Krok 5: zapisz plik XML
Zapisz wyodrębnione informacje QR na dysku:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*Wyjaśnienie:* Powstały `data.xml` zawiera jeden element `<Barcode>` na każdy kod QR, z atrybutami numeru strony, współrzędnych i odszyfrowanej wartości.

## Praktyczne zastosowania
1. **Zarządzanie zapasami:** Automatyczne wypełnianie baz danych zapasów poprzez odczyt tagów QR w przychodzących PDF‑ach przesyłek.  
2. **Widoczność łańcucha dostaw:** Śledzenie paczek w czasie rzeczywistym poprzez wyodrębnianie identyfikatorów QR osadzonych w dokumentach logistycznych.  
3. **Paragony detaliczne:** Pobieranie informacji promocyjnych lub gwarancyjnych z kodów QR wydrukowanych na cyfrowych paragonach.

## Wskazówki dotyczące wydajności
- **Zarządzanie pamięcią:** Dla bardzo dużych PDF‑ów przetwarzaj strony w trybie strumieniowym zamiast ładować cały plik do pamięci.  
- **Wybór QualityMode:** Użyj `Low` do przetwarzania wsadowego; przełącz na `High`, gdy masz do czynienia ze skanami niskiej rozdzielczości.  
- **Aktualizacje biblioteki:** Utrzymuj GroupDocs.Parser w najnowszej wersji, aby korzystać z najnowszych usprawnień wydajności i poprawek błędów.

## Typowe problemy i rozwiązywanie
| Objaw | Prawdopodobna przyczyna | Rozwiązanie |
|---------|--------------|-----|
| Brak zwróconych kodów kreskowych | Podano niewłaściwy typ kodu kreskowego | Zmień `"QR"` na odpowiedni typ (np. `"CODE_128"`). |
| Błąd braku pamięci przy dużych PDF-ach | Cały dokument ładowany jednocześnie | Przetwarzaj strony pojedynczo lub zwiększ rozmiar sterty JVM (`-Xmx2g`). |
| Pusty plik XML | `exportBarcodes` wywołano przed wyodrębnieniem | Upewnij się, że `parser.getBarcodes(options)` zwraca dane przed eksportem. |

## Najczęściej zadawane pytania
**Q: Czy mogę odczytywać kody kreskowe z plików graficznych przy użyciu GroupDocs.Parser?**  
A: Tak, biblioteka obsługuje wyodrębnianie kodów kreskowych z popularnych formatów obrazów (PNG, JPEG, TIFF).

**Q: Jakie formaty kodów kreskowych są rozpoznawane?**  
A: QR, Code 39, Code 128, DataMatrix, PDF417 i wiele innych. Pełną listę znajdziesz w dokumentacji API.

**Q: Jak obsłużyć PDF‑y zabezpieczone hasłem?**  
A: Przekaż hasło do konstruktora `Parser`: `new Parser(filePath, "password")`.

**Q: Czy wersja próbna wystarczy do testów produkcyjnych?**  
A: Wersja próbna zapewnia pełną funkcjonalność, ale dodaje znak wodny do wyodrębnionych danych. Do produkcji należy nabyć licencję komercyjną.

**Q: Co zrobić, jeśli mój PDF zawiera zarówno QR, jak i kody liniowe?**  
A: Utwórz wiele instancji `BarcodeOptions` lub przekaż tablicę typów, aby zeskanować wszystkie potrzebne formaty w jednym przebiegu.

---

**Ostatnia aktualizacja:** 2026-10-12  
**Testowano z:** GroupDocs.Parser 25.5  
**Autor:** GroupDocs  

## Zasoby
- [dokumentacja GroupDocs.Parser Java](https://docs.groupdocs.com/parser/java/)
- [referencja API](https://reference.groupdocs.com/parser/java)
- [Pobierz GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [repozytorium GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [bezpłatne forum wsparcia](https://forum.groupdocs.com/c/parser)
- [wniosek o licencję tymczasową](https://purchase.groupdocs.com/temporary-license/)

## Powiązane samouczki

- [Wyodrębnij kod kreskowy PDF GroupDocs Parser Java](/parser/java/barcode-extraction/extract-barcode-pdf-groupdocs-parser-java/)
- [Jak załadować PDF z URL przy użyciu GroupDocs.Parser dla Javy](/parser/java/document-loading/)
- [Wyodrębnij dane formularzy PDF przy użyciu GroupDocs.Parser w Javie](/parser/java/form-extraction/groupdocs-parser-java-pdf-form-extraction/)