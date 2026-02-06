---
date: '2026-02-06'
description: Dowiedz się, jak podglądać pliki Excel i konwertować xlsx na png przy
  użyciu GroupDocs.Parser dla Javy. Ten samouczek obejmuje konfigurację, implementację
  i praktyczne zastosowania.
keywords:
- GroupDocs.Parser
- Java
- Document Processing
title: Jak podglądać pliki Excel za pomocą GroupDocs.Parser w Javie
type: docs
url: /pl/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# Jak podglądać pliki Excel przy użyciu GroupDocs.Parser w Javie

Jeśli szukasz **jak podglądać Excel** arkusze kalkulacyjne programowo, trafiłeś we właściwe miejsce. W tym przewodniku przeprowadzimy Cię przez proces tworzenia podglądów obrazów (PNG) z zeszytów `.xlsx` przy użyciu GroupDocs.Parser dla Javy — idealne do szybkiego generowania miniatur, udostępniania zrzutów ekranu lub budowania funkcji podglądu dokumentów w Twojej aplikacji.

## Szybkie odpowiedzi
- **Co oznacza „preview Excel”?** Generowanie plików graficznych (np. PNG), które przedstawiają każdą stronę arkusza.  
- **Jaki format jest zalecany?** PNG zapewnia jakość bezstratną i dobrze sprawdza się w miniaturach internetowych.  
- **Czy potrzebna jest licencja?** Darmowa wersja próbna wystarcza do rozwoju; licencja komercyjna jest wymagana w produkcji.  
- **Czy mogę zmienić rozdzielczość obrazu?** Tak — dostosuj DPI w `PreviewOptions`.  
- **Czy można podglądać inne formaty?** GroupDocs.Parser obsługuje także PDF, Word i wiele typów obrazów.

## Co to jest „jak podglądać Excel” z GroupDocs.Parser?
GroupDocs.Parser odczytuje zeszyty Excel, renderuje każdy arkusz jako wizualną stronę i umożliwia strumieniowanie tych stron do plików graficznych. Dzięki temu nie potrzebujesz interfejsu Office ani konwerterów firm trzecich.

## Dlaczego warto używać GroupDocs.Parser do podglądów Excel?
- **Brak wymogu instalacji Office** – działa w dowolnym środowisku Java po stronie serwera.  
- **Obsługa dużych plików** – strumieniuje strony pojedynczo, utrzymując niskie zużycie pamięci.  
- **Wysokiej jakości wynik** – kontrola nad DPI, formatem i opcjami renderowania.  
- **Elastyczność wieloformatowa** – to samo API działa dla PDF‑ów, dokumentów Word i innych.

## Wymagania wstępne
- **Java Development Kit** (8 +).  
- **IDE**, np. IntelliJ IDEA lub Eclipse.  
- **GroupDocs.Parser for Java SDK** – pobierz z [tutaj](https://releases.groupdocs.com/parser/java/).  
- **Przykładowy plik Excel** (`.xlsx`), który chcesz podglądać.  
- **Maven lub Gradle** (opcjonalnie) do zarządzania zależnościami.

## Importowanie pakietów
Te importy dają dostęp do parsera, opcji podglądu oraz narzędzi obsługi strumieni.

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

### Krok 1: Inicjalizacja instancji Parsera
Utwórz obiekt `Parser` wskazujący na Twój zeszyt Excel. Blok *try‑with‑resources* zapewnia automatyczne zamknięcie parsera.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **Porada:** Użyj ścieżki bezwzględnej lub skonfiguruj folder zasobów, aby uniknąć `FileNotFoundException`.

### Krok 2: Przygotowanie opcji podglądu
Zdefiniuj, w jaki sposób każda strona ma być zapisywana. Implementacja `ICreatePageStream` zwraca nowy `FileOutputStream` dla każdej strony arkusza.

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

> Ten krok to miejsce, w którym **konwertujesz xlsx na png** — strumień zapisuje dane PNG na dysku.

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

### Krok 4: Określenie formatu wyjściowego i DPI
Wybierz PNG jako format obrazu i ustaw DPI, które równoważy jakość i rozmiar pliku.

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> Dostosuj DPI, jeśli potrzebujesz mniejszych miniatur (np. 96) lub wydruków wysokiej rozdzielczości (np. 300).

### Krok 5: Generowanie podglądów
Po skonfigurowaniu wszystkiego, wywołaj `generatePreview`. SDK przeiteruje każdy arkusz i wywoła podany strumień.

```java
parser.generatePreview(previewOptions);
```

### Krok 6: Definicja pomocniczej metody `getOutputPath()`
Ta metoda tworzy nazwę pliku na podstawie numeru strony (arkusza). Możesz dowolnie dostosować strukturę folderów.

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **Częsty błąd:** Zapomnienie o utworzeniu katalogu `output` wcześniej spowoduje `IOException`. Utwórz go programowo lub upewnij się, że istnieje.

## Pełny działający przykład (uproszczony)

Poniżej znajduje się kompaktowa wersja, która łączy wszystkie elementy. Demonstratuje przepływ pracy **tworzenia podglądu strony Excel** od początku do końca.

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

Uruchom ten fragment, a w folderze `output` znajdziesz serię plików `preview_page_1.png`, `preview_page_2.png`, … — każdy reprezentuje arkusz z oryginalnego zeszytu Excel.

## Typowe problemy i rozwiązania
| Problem | Przyczyna | Rozwiązanie |
|-------|-------|-----|
| **Brak wygenerowanych obrazów** | `getOutputPath` zwraca nieprawidłowy katalog | Upewnij się, że docelowy folder istnieje lub utwórz go za pomocą `new File("output").mkdirs();` |
| **Błąd Out‑of‑memory przy dużych plikach** | Ładowanie całego zeszytu jednocześnie | Użyj podejścia strumieniowego (jak pokazano) i przetwarzaj strony pojedynczo |
| **Nieprawidłowe DPI** | `setDpi` nie wywołane lub ustawione na domyślne (96) | Wywołaj `previewOptions.setDpi(yourDesiredValue);` przed `generatePreview` |
| **Nieobsługiwany format** | Próba podglądu uszkodzonego pliku `.xlsx` | Zweryfikuj plik w Excelu lub użyj `Parser.isSupported` przed przetwarzaniem |

## Najczęściej zadawane pytania

**Q: Czy mogę generować podglądy dla PDF‑ów i obrazów przy użyciu GroupDocs.Parser?**  
A: Tak, to samo API działa dla PDF‑ów, dokumentów Word i wielu formatów obrazów.

**Q: Jak zmienić format wyjściowego obrazu?**  
A: Wywołaj `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (lub `Gif`, `Bmp` itd.).

**Q: Czy wydajność jest problemem przy bardzo dużych zeszytach?**  
A: SDK strumieniuje strony, co utrzymuje niskie zużycie pamięci. W przypadku ogromnych plików rozważ przetwarzanie w równoległych partiach.

**Q: Jak obsłużyć błędy podczas generowania podglądu?**  
A: Otocz kod blokami try‑catch (jak pokazano) i loguj szczegóły wyjątku. Upewnij się, że strumienie są zamykane w bloku `finally`, jeśli nie używasz try‑with‑resources.

**Q: Czy biblioteka wymaga zainstalowanego Microsoft Office?**  
A: Nie. GroupDocs.Parser jest czystym rozwiązaniem Java i działa na każdej platformie obsługującej Java 8+.

## Zakończenie
Masz teraz kompletną, gotową do produkcji metodę **jak podglądać Excel** zeszyty i **konwertować xlsx na png** przy użyciu GroupDocs.Parser. Dostosuj DPI, folder wyjściowy lub format obrazu do potrzeb projektu i włącz ten fragment do większych przepływów pracy zarządzania dokumentami.

Gotowy na kolejny krok? Zapoznaj się z oficjalną [dokumentacją](https://docs.groupdocs.com/parser/java/) dotyczącą zaawansowanych opcji renderowania, plików chronionych hasłem i technik przetwarzania wsadowego.

---

**Ostatnia aktualizacja:** 2026-02-06  
**Testowano z:** GroupDocs.Parser 23.11 (najnowsza w momencie pisania)  
**Autor:** GroupDocs