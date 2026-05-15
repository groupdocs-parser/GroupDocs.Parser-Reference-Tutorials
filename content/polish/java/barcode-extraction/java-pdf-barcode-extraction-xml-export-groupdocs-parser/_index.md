---
date: '2026-02-19'
description: Dowiedz się, jak odczytywać kody QR w plikach PDF w Javie przy użyciu
  GroupDocs.Parser i eksportować dane kodów kreskowych do formatu XML.
keywords:
- Java PDF barcode extraction
- GroupDocs.Parser for Java
- XML export from PDF
title: Jak odczytywać kody QR w plikach PDF w Javie przy użyciu GroupDocs.Parser
type: docs
url: /pl/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

.

# Jak odczytywać kody QR w plikach PDF Java przy użyciu GroupDocs.Parser

W nowoczesnych przepływach pracy biznesowej **jak odczytywać QR** kody z dokumentów PDF może decydować o różnicy między ręcznym wąskim gardłem wprowadzania danych a w pełni zautomatyzowanym potokiem. Niezależnie od tego, czy obsługujesz listy przewozowe, paragony detaliczne, czy katalogi produktów, szybkie i niezawodne wyodrębnianie informacji z kodów QR jest niezbędne. Ten samouczek przeprowadzi Cię przez użycie **GroupDocs.Parser for Java**, aby odczytywać kody QR (i inne kody kreskowe) z PDF‑ów oraz eksportować wyniki do czystego pliku XML, który mogą przetwarzać systemy downstream.

## Szybkie odpowiedzi
- **Co robi GroupDocs.Parser for Java?** Odczytuje pliki PDF i wyodrębnia dane strukturalne, takie jak kody kreskowe.  
- **Jak wyodrębnić kody QR?** Konfigurując `BarcodeOptions` z typem QR i wywołując `parser.getBarcodes()`.  
- **Czy mogę odczytywać kody QR w Javie?** Tak — ustaw typ kodu kreskowego na `"QR"` w opcjach.  
- **Czy potrzebna jest licencja?** Wersja próbna działa do testów; licencja komercyjna jest wymagana w produkcji.  
- **Jakiej wersji Javy potrzebuję?** Zalecana jest Java 8 lub nowsza.

## Co oznacza „jak odczytywać QR” w kontekście przetwarzania PDF‑ów?
Odczytywanie kodów QR z PDF‑ów oznacza skanowanie każdej strony w poszukiwaniu grafik zakodowanych jako QR, dekodowanie osadzonych danych i zwracanie ich w formacie przyjaznym dla programu. GroupDocs.Parser abstrahuje niskopoziomową analizę obrazu, dzięki czemu możesz skupić się na logice biznesowej, a nie na manipulacji pikselami.

## Dlaczego warto używać GroupDocs.Parser do ekstrakcji QR?
- **Wysoka dokładność:** Wbudowane algorytmy przetwarzania obrazu radzą sobie z niską rozdzielczością skanów.  
- **Opcje wydajności:** Wybierz `QualityMode.Low` dla szybkości lub `QualityMode.High` dla maksymalnej precyzji.  
- **Obsługa wielu formatów:** Działa z PDF‑ami, obrazami i nawet dokumentami Office, więc możesz ponownie wykorzystać ten sam kod bazowy dla różnych typów plików.

## Wymagania wstępne
- **GroupDocs.Parser for Java** (wersja 25.5 lub nowsza).  
- Maven lub ręczne pobranie JAR‑a.  
- Środowisko programistyczne Java 8+ (IntelliJ IDEA, Eclipse lub dowolny edytor).  

## Konfiguracja GroupDocs.Parser for Java
### Użycie Maven
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

### Bezpośrednie pobranie
Alternatywnie pobierz najnowszy JAR z [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

#### Kroki uzyskania licencji
- **Bezpłatna wersja próbna:** 30‑dniowy trial z pełnym zestawem funkcji.  
- **Licencja tymczasowa:** Poproś o tymczasowy klucz do przedłużonej ewaluacji.  
- **Zakup:** Uzyskaj licencję komercyjną do wdrożeń produkcyjnych.

### Podstawowa inicjalizacja i konfiguracja
Utwórz instancję `Parser`, która wskazuje na PDF, który chcesz analizować:

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

## Jak odczytywać kody QR w PDF‑ach Java przy użyciu GroupDocs.Parser
### Krok 1: Zweryfikuj obsługę kodów kreskowych
Zanim przystąpisz do ekstrakcji, potwierdź, że format dokumentu obsługuje skanowanie kodów kreskowych:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*Wyjaśnienie:* To zabezpieczenie zapobiega błędom w czasie wykonywania przy nieobsługiwanych typach plików.

### Krok 2: Skonfiguruj opcje kodu kreskowego (Read QR codes Java)
Ustaw jakość skanowania i określ, że interesują Cię wyłącznie kody QR:

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*Wyjaśnienie:* `QualityMode.Low` przyspiesza przetwarzanie; przełącz na `High`, jeśli potrzebna jest większa dokładność. Argument `"QR"` informuje silnik, aby szukał wyłącznie kodów typu QR.

### Krok 3: Wyodrębnij dane QR
Pobierz informacje o kodach kreskowych ze wszystkich stron PDF:

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*Wyjaśnienie:* `parser.getBarcodes` zwraca iterowalną kolekcję obiektów `PageBarcodeArea`, z których każdy zawiera zdekodowaną wartość QR oraz jej położenie na stronie.

## Eksport wyodrębnionych danych do XML
### Krok 4: Inicjalizacja eksportera XML
Utwórz eksporter, który przekształci kolekcję kodów kreskowych w dobrze ustrukturyzowany plik XML:

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*Wyjaśnienie:* `XmlExporter` zajmuje się serializacją obiektów kodów kreskowych do standardowego XML, gotowego do integracji z systemami ERP lub inwentaryzacji.

### Krok 5: Zapisz plik XML
Zapisz wyodrębnione informacje QR na dysku:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*Wyjaśnienie:* Powstały `data.xml` zawiera jeden element `<Barcode>` dla każdego kodu QR, z atrybutami numeru strony, współrzędnych i zdekodowanej wartości.

## Praktyczne zastosowania
1. **Zarządzanie zapasami:** Automatyczne wypełnianie baz danych magazynowych poprzez odczyt tagów QR w przychodzących PDF‑ach przewozowych.  
2. **Widoczność łańcucha dostaw:** Śledzenie paczek w czasie rzeczywistym przez wyodrębnianie identyfikatorów QR osadzonych w dokumentach logistycznych.  
3. **Paragony detaliczne:** Pobieranie informacji promocyjnych lub gwarancyjnych z kodów QR wydrukowanych na cyfrowych paragonach.

## Rozważania dotyczące wydajności
- **Zarządzanie pamięcią:** W przypadku bardzo dużych PDF‑ów przetwarzaj strony w trybie strumieniowym zamiast ładować cały plik do pamięci.  
- **Wybór QualityMode:** Używaj `Low` przy masowej obróbce; przełącz na `High`, gdy masz do czynienia z niską rozdzielczością skanów.  
- **Aktualizacje biblioteki:** Utrzymuj GroupDocs.Parser w najnowszej wersji, aby korzystać z najnowszych usprawnień wydajności i poprawek błędów.

## Typowe problemy i rozwiązywanie ich
| Objaw | Prawdopodobna przyczyna | Rozwiązanie |
|---------|--------------|-----|
| Brak zwróconych kodów kreskowych | Nieprawidłowo określony typ kodu kreskowego | Zmień `"QR"` na odpowiedni typ (np. `"CODE_128"`). |
| Błąd pamięci przy dużych PDF‑ach | Cały dokument ładowany jednocześnie | Przetwarzaj strony pojedynczo lub zwiększ rozmiar sterty JVM (`-Xmx2g`). |
| Pusty plik XML | `exportBarcodes` wywołane przed ekstrakcją | Upewnij się, że `parser.getBarcodes(options)` zwraca dane przed eksportem. |

## Najczęściej zadawane pytania
**P: Czy mogę wyodrębniać kody kreskowe z plików graficznych przy użyciu GroupDocs.Parser?**  
O: Tak, biblioteka obsługuje wyodrębnianie kodów kreskowych z popularnych formatów obrazów (PNG, JPEG, TIFF).

**P: Jakie formaty kodów kreskowych są rozpoznawane?**  
O: QR, Code 39, Code 128, DataMatrix, PDF417 i wiele innych. Pełną listę znajdziesz w dokumentacji API.

**P: Jak obsłużyć PDF‑y zabezpieczone hasłem?**  
O: Przekaż hasło do konstruktora `Parser`: `new Parser(filePath, "password")`.

**P: Czy wersja próbna wystarczy do testów produkcyjnych?**  
O: Wersja próbna zapewnia pełną funkcjonalność, ale dodaje znak wodny do wyodrębnionych danych. Do produkcji potrzebna jest licencja komercyjna.

**P: Co zrobić, gdy mój PDF zawiera zarówno kody QR, jak i liniowe?**  
O: Utwórz wiele instancji `BarcodeOptions` lub przekaż tablicę typów, aby zeskanować wszystkie potrzebne formaty w jednym przebiegu.

---

**Ostatnia aktualizacja:** 2026-02-19  
**Testowano z:** GroupDocs.Parser 25.5  
**Autor:** GroupDocs  

## Zasoby
- [GroupDocs.Parser Java Documentation](https://docs.groupdocs.com/parser/java/)
- [API Reference](https://reference.groupdocs.com/parser/java)
- [Download GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [GitHub Repository](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/parser)
- [Temporary License Application](https://purchase.groupdocs.com/temporary-license/)