---
date: '2026-07-16'
description: Dowiedz się, jak tworzyć miniatury arkuszy kalkulacyjnych w Java przy
  użyciu GroupDocs.Parser, podglądać Excel bez Office i renderować arkusze Excel jako
  obrazy. Ten przewodnik obejmuje setup, implementation oraz praktyczne use cases.
keywords:
- create spreadsheet thumbnail java
- preview excel without office
- render excel sheets as images
lastmod: '2026-07-16'
og_description: Tworzenie miniatury arkusza kalkulacyjnego w Java przy użyciu GroupDocs.Parser
  — podgląd Excel bez Office i renderowanie arkuszy Excel jako obrazy. Postępuj zgodnie
  z tym step‑by‑step przewodnikiem, aby efektywnie generować podglądy PNG.
og_image_alt: 'Developer guide: Create spreadsheet thumbnail Java using GroupDocs.Parser'
og_title: Tworzenie miniatury arkusza kalkulacyjnego w Java przy użyciu GroupDocs.Parser
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
title: Tworzenie miniatury arkusza kalkulacyjnego w Java przy użyciu GroupDocs.Parser
type: docs
url: /pl/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# Utwórz miniaturkę arkusza kalkulacyjnego w Javie przy użyciu GroupDocs.Parser

Jeśli szukasz programów **create spreadsheet thumbnail Java**, trafiłeś we właściwe miejsce. W tym przewodniku przeprowadzimy Cię przez generowanie wysokiej jakości podglądów PNG z zeszytów `.xlsx` przy użyciu GroupDocs.Parser dla Javy — idealne do szybkich miniatur, udostępniania zrzutów ekranu lub budowania funkcji podglądu dokumentów w Twojej aplikacji. Rozwiązanie działa bez instalacji Microsoft Office i skalowuje się do dużych zeszytów, jednocześnie utrzymując niskie zużycie pamięci.

## Szybkie odpowiedzi
- **Co oznacza „preview Excel”?** Generowanie plików graficznych (np. PNG), które przedstawiają każdą stronę arkusza.  
- **Jaki format jest zalecany?** PNG zapewnia jakość bezstratną i dobrze sprawdza się jako miniatury w sieci.  
- **Czy potrzebuję licencji?** Darmowa wersja próbna działa w środowisku deweloperskim; licencja komercyjna jest wymagana w produkcji.  
- **Czy mogę zmienić rozdzielczość obrazu?** Tak — dostosuj DPI w `PreviewOptions`.  
- **Czy można podglądać inne formaty?** GroupDocs.Parser obsługuje również PDF, Word oraz wiele typów obrazów.

## Co to jest „how to preview Excel” z GroupDocs.Parser?

Załaduj swój zeszyt Excel i renderuj każdy arkusz jako obraz PNG, nie potrzebując Microsoft Office. GroupDocs.Parser strumieniuje strony po jednej, tworząc bezstratne miniatury, które można zapisać na dysku lub zwrócić przez HTTP, co czyni go idealnym do usług podglądu w sieci.

GroupDocs.Parser odczytuje zeszyty Excel, renderuje każdy arkusz jako wizualną stronę i pozwala strumieniować te strony do plików graficznych. Eliminuje to potrzebę używania interfejsu Office lub konwerterów firm trzecich.

## Dlaczego używać GroupDocs.Parser do podglądu Excel?

Powinieneś używać GroupDocs.Parser, ponieważ działa na dowolnym serwerze Java, nie wymaga instalacji Office, obsługuje duże zeszyty przy niskim zużyciu pamięci i tworzy bezstratne obrazy PNG z konfigurowalnym DPI. SDK obsługuje **ponad 100 formatów wejściowych i wyjściowych**, może przetworzyć 200‑stronicowy zeszyt w mniej niż 3 sekundy i utrzymuje zużycie pamięci poniżej 50 MB na arkusz.

- **Brak wymogu instalacji Office** – działa w dowolnym środowisku Java po stronie serwera.  
- **Obsługa dużych plików** – strumieniuje strony po jednej, utrzymując niskie zużycie pamięci.  
- **Wysokiej jakości wyjście** – kontrola nad DPI, formatem i opcjami renderowania.  
- **Elastyczność wieloformatowa** – to samo API działa dla PDF‑ów, dokumentów Word i innych.

## Wymagania wstępne
- **Java Development Kit** (8 +).  
- **IDE** takie jak IntelliJ IDEA lub Eclipse.  
- **GroupDocs.Parser for Java SDK** – pobierz z [tutaj](https://releases.groupdocs.com/parser/java/).  
- **Documentation** – zobacz oficjalną [dokumentację](https://docs.groupdocs.com/parser/java/).  
- **Przykładowy plik Excel** (`.xlsx`), który chcesz podglądnąć.  
- **Maven lub Gradle** (opcjonalnie) do zarządzania zależnościami.

## Importowanie pakietów
Te importy zapewniają dostęp do parsera, opcji podglądu i narzędzi obsługi strumieni.

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

## Przewodnik krok po kroku generowania podglądów stron arkusza kalkulacyjnego

### Krok 1: Zainicjalizuj instancję parsera
`Parser` jest podstawową klasą GroupDocs.Parser, która zapewnia dostęp do odczytu plików arkuszy kalkulacyjnych i umożliwia renderowanie stron.  
Utwórz obiekt `Parser` wskazujący na Twój zeszyt Excel. Blok *try‑with‑resources* zapewnia automatyczne zamknięcie parsera.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **Wskazówka:** Użyj ścieżki bezwzględnej lub skonfiguruj folder zasobów, aby uniknąć `FileNotFoundException`.

### Krok 2: Przygotuj opcje podglądu
`PreviewOptions` konfiguruje parametry renderowania, takie jak format wyjściowy i DPI.  
`ICreatePageStream` jest interfejsem zwrotnym, który dostarcza strumień wyjściowy dla każdej wygenerowanej strony. Zdefiniuj, w jaki sposób każda strona będzie zapisywana. Implementacja `ICreatePageStream` zwraca nowy `FileOutputStream` dla każdej strony arkusza.

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

> Ten krok to miejsce, w którym **convert xlsx to png** — strumień zapisuje dane PNG na dysku.

### Krok 3: Dołącz delegata do przechwytywania informacji o renderowaniu
Jeśli potrzebujesz szczegółów o każdym renderowanym arkuszu (np. wymiary, nazwa arkusza), zarejestruj wywołanie zwrotne.

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### Krok 4: Określ format wyjściowy i DPI
Wybierz PNG jako format obrazu i ustaw DPI, które równoważy jakość i rozmiar pliku.

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> Dostosuj DPI, jeśli potrzebujesz mniejszych miniatur (np. 96) lub wydruków wysokiej rozdzielczości (np. 300).

### Krok 5: Wygeneruj podglądy
Po skonfigurowaniu wszystkiego, wywołaj `generatePreview`. SDK przeiteruje każdy arkusz i wywoła dostarczony strumień.

```java
parser.generatePreview(previewOptions);
```

### Krok 6: Zdefiniuj pomocniczą metodę `getOutputPath()`
`getOutputPath()` tworzy nazwę pliku na podstawie numeru strony (arkusza) i zwraca pełną ścieżkę do obrazu wyjściowego. Śmiało dostosuj strukturę folderów.

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **Częsty błąd:** Zapomnienie o wcześniejszym utworzeniu katalogu `output` spowoduje `IOException`. Utwórz go programowo lub upewnij się, że istnieje.

## Pełny działający przykład (uproszczony)

Poniżej znajduje się kompaktowa wersja, która łączy wszystkie elementy. Demonstratuje ona przepływ pracy **create spreadsheet thumbnail Java** od początku do końca.

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

Uruchom ten fragment, a znajdziesz serię plików `preview_page_1.png`, `preview_page_2.png`, … w folderze `output` — każdy reprezentuje arkusz z oryginalnego zeszytu Excel.

## Typowe problemy i rozwiązania

| Problem | Przyczyna | Rozwiązanie |
|-------|-------|-----|
| **Brak wygenerowanych obrazów** | `getOutputPath` zwraca nieprawidłowy katalog | Upewnij się, że docelowy folder istnieje lub utwórz go za pomocą `new File("output").mkdirs();` |
| **Błąd pamięci (Out‑of‑memory) przy dużych plikach** | Ładowanie całego zeszytu jednocześnie | Użyj podejścia strumieniowego (jak pokazano) i przetwarzaj strony po jednej. |
| **Nieprawidłowe DPI** | `setDpi` nie wywołano lub ustawiono domyślne (96) | Wywołaj `previewOptions.setDpi(wartość);` przed `generatePreview`. |
| **Nieobsługiwany format** | Próba podglądu uszkodzonego `.xlsx` | Zweryfikuj plik w Excelu lub użyj `Parser.isSupported` przed przetwarzaniem. |

## Najczęściej zadawane pytania

**Q: Czy mogę generować podglądy dla PDF‑ów i obrazów używając GroupDocs.Parser?**  
A: Tak, to samo API działa dla PDF‑ów, dokumentów Word i wielu formatów obrazów.

**Q: Jak zmienić format wyjściowego obrazu?**  
A: Wywołaj `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (lub `Gif`, `Bmp` itd.).

**Q: Czy wydajność jest problemem przy bardzo dużych zeszytach?**  
A: SDK strumieniuje strony, co utrzymuje niskie zużycie pamięci. W przypadku bardzo dużych plików rozważ przetwarzanie w równoległych partiach.

**Q: Jak obsłużyć błędy podczas generowania podglądu?**  
A: Umieść kod w blokach try‑catch (jak pokazano) i loguj szczegóły wyjątku. Upewnij się, że strumienie są zamykane w bloku `finally`, jeśli nie używasz try‑with‑resources.

**Q: Czy biblioteka wymaga zainstalowanego Microsoft Office?**  
A: Nie. GroupDocs.Parser jest czystym rozwiązaniem Java i działa na każdej platformie obsługującej Java 8+.

**Ostatnia aktualizacja:** 2026-07-16  
**Testowano z:** GroupDocs.Parser 23.11 (latest at time of writing)  
**Autor:** GroupDocs

## Powiązane samouczki

- [Jak generować podgląd – Samouczki generowania podglądu stron dokumentu dla GroupDocs.Parser Java](/parser/java/page-preview-generation/)
- [Parsowanie Excel w Javie z GroupDocs.Parser: Kompletny przewodnik](/parser/java/getting-started/mastering-document-parsing-java-groupdocs-parser/)
- [Jak wyodrębnić surowy tekst z arkuszy Excel przy użyciu GroupDocs.Parser dla Javy: Przewodnik krok po kroku](/parser/java/text-extraction/extract-raw-text-excel-groupdocs-parser-java/)