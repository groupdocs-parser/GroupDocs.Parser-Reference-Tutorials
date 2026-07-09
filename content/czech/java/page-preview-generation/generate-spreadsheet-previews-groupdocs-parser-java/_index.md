---
date: '2026-02-06'
description: Naučte se, jak zobrazit náhled souborů Excel a převést xlsx na png pomocí
  GroupDocs.Parser pro Javu. Tento tutoriál pokrývá nastavení, implementaci a praktické
  aplikace.
keywords:
- GroupDocs.Parser
- Java
- Document Processing
title: Jak zobrazit náhled Excel souborů pomocí GroupDocs.Parser v Javě
type: docs
url: /cs/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# Jak zobrazit náhled souborů Excel pomocí GroupDocs.Parser v Javě

Pokud hledáte **jak zobrazit náhled Excel** tabulek programově, jste na správném místě. V tomto průvodci si ukážeme, jak vytvořit náhledy obrázků (PNG) z `.xlsx` sešitů pomocí GroupDocs.Parser pro Java — ideální pro rychlé miniatury, sdílení snímků nebo vytvoření funkce náhledu dokumentů ve vaší aplikaci.

## Rychlé odpovědi
- **Co znamená „preview Excel“?** Generování souborů obrázků (např. PNG), které představují každou stránku listu.  
- **Jaký formát je doporučen?** PNG poskytuje bezztrátovou kvalitu a dobře se hodí pro webové miniatury.  
- **Potřebuji licenci?** Bezplatná zkušební verze funguje pro vývoj; pro produkci je vyžadována komerční licence.  
- **Mohu změnit rozlišení obrázku?** Ano — upravte DPI v `PreviewOptions`.  
- **Je možné zobrazit náhled i jiných formátů?** GroupDocs.Parser také podporuje PDF, Word a mnoho typů obrázků.

## Co je „jak zobrazit náhled Excel“ s GroupDocs.Parser?
GroupDocs.Parser čte sešity Excel, vykresluje každý list jako vizuální stránku a umožňuje vám streamovat tyto stránky do souborů obrázků. Tím se eliminuje potřeba Office interop nebo konvertorů třetích stran.

## Proč použít GroupDocs.Parser pro náhledy Excelu?
- **Není vyžadována instalace Office** – běží na jakémkoli serverovém prostředí Java.  
- **Podporuje velké soubory** – streamuje stránky po jedné, udržuje nízkou spotřebu paměti.  
- **Výstup ve vysoké kvalitě** – kontrola nad DPI, formátem a možnostmi vykreslování.  
- **Flexibilita napříč formáty** – stejné API funguje pro PDF, Word dokumenty a další.

## Požadavky
- **Java Development Kit** (8 +).  
- **IDE** jako IntelliJ IDEA nebo Eclipse.  
- **GroupDocs.Parser for Java SDK** – stáhněte z [zde](https://releases.groupdocs.com/parser/java/).  
- **Ukázkový soubor Excel** (`.xlsx`), který chcete zobrazit.  
- **Maven nebo Gradle** (volitelné) pro správu závislostí.

## Import balíčků
Tyto importy vám poskytují přístup k parseru, možnostem náhledu a utilitám pro práci se streamy.

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

## Průvodce krok za krokem pro generování náhledů stránek tabulky

### Krok 1: Inicializace instance Parseru
Vytvořte objekt `Parser`, který ukazuje na váš sešit Excel. Blok *try‑with‑resources* zajistí automatické uzavření parseru.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **Tip:** Použijte absolutní cestu nebo nakonfigurujte složku zdrojů, abyste se vyhnuli `FileNotFoundException`.

### Krok 2: Připravte možnosti náhledu
Definujte, jak bude každá stránka uložena. Implementace `ICreatePageStream` vrací nový `FileOutputStream` pro každou stránku listu.

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

> Tento krok je místem, kde **převádíte xlsx na png** — stream zapisuje PNG data na disk.

### Krok 3: Připojte delegáta pro zachycení informací o vykreslení
Pokud potřebujete podrobnosti o každém vykresleném listu (např. rozměry, název listu), zaregistrujte zpětné volání.

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### Krok 4: Zadejte výstupní formát a DPI
Vyberte PNG jako formát obrázku a nastavte DPI, které vyvažuje kvalitu a velikost souboru.

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> Upravit DPI, pokud potřebujete menší miniatury (např. 96) nebo vysoce rozlišené tisky (např. 300).

### Krok 5: Vygenerujte náhledy
Po nastavení všeho zavolejte `generatePreview`. SDK projde každý list a zavolá poskytnutý stream.

```java
parser.generatePreview(previewOptions);
```

### Krok 6: Definujte pomocnou metodu `getOutputPath()`
Tato metoda vytvoří název souboru na základě čísla stránky (listu). Klidně přizpůsobte strukturu složek.

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **Častá chyba:** Zapomenutí vytvořit předem adresář `output` způsobí `IOException`. Vytvořte jej programově nebo se ujistěte, že existuje.

## Kompletní funkční příklad (zjednodušený)

Níže je kompaktní verze, která spojuje všechny části dohromady. Ukazuje workflow **create excel page preview** od začátku do konce.

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

Spusťte tento úryvek a v adresáři `output` najdete sérii souborů `preview_page_1.png`, `preview_page_2.png`, … — každý představuje list z původního sešitu Excel.

## Časté problémy a řešení
| Problém | Příčina | Řešení |
|-------|-------|-----|
| **Žádné obrázky nebyly vygenerovány** | `getOutputPath` vrací neplatný adresář | Ujistěte se, že cílová složka existuje, nebo ji vytvořte pomocí `new File("output").mkdirs();` |
| **Chyba nedostatku paměti u velkých souborů** | Načítání celého sešitu najednou | Použijte streamingový přístup (jak je ukázáno) a zpracovávejte stránky po jedné |
| **Nesprávné DPI** | `setDpi` nebylo zavoláno nebo je nastaveno na výchozí (96) | Zavolejte `previewOptions.setDpi(vámiPožadovanáHodnota);` před `generatePreview` |
| **Nepodporovaný formát** | Pokus o náhled poškozeného `.xlsx` | Ověřte soubor v Excelu nebo použijte `Parser.isSupported` před zpracováním |

## Často kladené otázky

**Q: Mohu generovat náhledy pro PDF a obrázky pomocí GroupDocs.Parser?**  
A: Ano, stejné API funguje pro PDF, Word dokumenty a mnoho formátů obrázků.

**Q: Jak změním výstupní formát obrázku?**  
A: Zavolejte `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (nebo `Gif`, `Bmp` atd.).

**Q: Je výkon problém u velmi velkých sešitů?**  
A: SDK streamuje stránky, což udržuje nízkou spotřebu paměti. U obrovských souborů zvažte zpracování ve paralelních dávkách.

**Q: Jak mohu ošetřit chyby během generování náhledu?**  
A: Zabalte kód do bloků try‑catch (jak je ukázáno) a zaznamenejte podrobnosti výjimky. Ujistěte se, že streamy jsou uzavřeny v bloku `finally`, pokud nepoužíváte try‑with‑resources.

**Q: Vyžaduje knihovna instalaci Microsoft Office?**  
A: Ne. GroupDocs.Parser je čistě Java řešení a funguje na jakékoli platformě, která podporuje Java 8+.

## Závěr
Nyní máte kompletní, připravenou metodu pro **jak zobrazit náhled Excel** sešitů a **převést xlsx na png** pomocí GroupDocs.Parser. Přizpůsobte DPI, výstupní složku nebo formát obrázku podle potřeb vašeho projektu a integrujte tento úryvek do větších pracovních postupů správy dokumentů.

Jste připraveni na další krok? Prozkoumejte oficiální [dokumentaci](https://docs.groupdocs.com/parser/java/) pro pokročilé možnosti vykreslování, soubory chráněné heslem a techniky dávkového zpracování.

---

**Poslední aktualizace:** 2026-02-06  
**Testováno s:** GroupDocs.Parser 23.11 (nejnovější v době psaní)  
**Autor:** GroupDocs