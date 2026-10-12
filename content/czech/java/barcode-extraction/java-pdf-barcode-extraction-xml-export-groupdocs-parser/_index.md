---
date: '2026-10-12'
description: Naučte se, jak extrahovat QR z PDF v Javě pomocí GroupDocs.Parser a exportovat
  data barcode do XML pro následné zpracování.
keywords:
- extract QR from PDF
- how to read QR
- read QR codes Java
- parse QR codes Java
- PDF QR code extraction
lastmod: '2026-10-12'
og_description: Naučte se, jak extrahovat QR z PDF v Javě pomocí GroupDocs.Parser
  a exportovat data barcode do XML pro následné zpracování.
og_image_alt: Guide showing Java code that extracts QR codes from PDF files with GroupDocs.Parser
  and saves results as XML
og_title: Jak extrahovat QR z PDF v Javě pomocí GroupDocs.Parser
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
title: Jak extrahovat QR z PDF v Javě pomocí GroupDocs.Parser
type: docs
url: /cs/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Jak extrahovat QR z PDF v Javě s GroupDocs.Parser

V moderních obchodních pracovních postupech může **extrahování QR z PDF** souborů proměnit úzké hrdlo ručního zadávání dat v plně automatizovanou pipeline. Ať už zpracováváte přepravní manifesty, maloobchodní účtenky nebo produktové katalogy, rychlé a spolehlivé získávání informací z QR je nezbytné pro systémy níže v řetězci. Tento tutoriál vás provede používáním **GroupDocs.Parser for Java** k načtení QR kódů (a dalších čárových kódů) z PDF a exportem výsledků do čistého XML souboru, který může konzumovat váš ERP, inventární nebo analytický platforma.

## Rychlé odpovědi
- **Co dělá GroupDocs.Parser for Java?** Čte PDF soubory a extrahuje strukturovaná data, jako jsou čárové kódy, tabulky a text.  
- **Jak extrahovat QR kódy?** Nakonfigurujte `BarcodeOptions` s typem QR a zavolejte `parser.getBarcodes()`.  
- **Mohu číst QR kódy v Javě?** Ano—nastavte typ čárového kódu na `"QR"` v možnostech.  
- **Potřebuji licenci?** Zkušební verze funguje pro testování; pro produkci je vyžadována komerční licence.  
- **Jaká verze Javy je požadována?** Doporučuje se Java 8 nebo vyšší.

## Co znamená „extrahovat QR z PDF“ v kontextu zpracování PDF?
Extrahování QR z PDF znamená skenování každé stránky pro grafiku kódovanou QR, dekódování vložených dat a jejich vrácení ve formátu přátelském pro programy. GroupDocs.Parser abstrahuje nízkoúrovňovou analýzu obrazu, takže se můžete soustředit na obchodní logiku místo manipulace s pixely.

## Proč použít GroupDocs.Parser pro extrakci QR?
GroupDocs.Parser podporuje **více než 30 vstupních formátů** a může zpracovávat PDF až do **500 MB** bez načítání celého souboru do paměti, poskytující vysoce přesné výsledky i při nízkém rozlišení skenů. Můžete zvolit `QualityMode.Low` pro rychlost nebo `QualityMode.High` pro maximální přesnost a stejná API funguje pro PDF, obrázky i Office dokumenty, čímž eliminuje potřebu více knihoven.

## Předpoklady
- **GroupDocs.Parser for Java** (verze 25.5 nebo novější).  
- Maven nebo ruční stažení JAR.  
- Vývojové prostředí Java 8+ (IntelliJ IDEA, Eclipse nebo jakýkoli editor).  

## Nastavení GroupDocs.Parser pro Javu
### Použití Maven
Přidejte repozitář GroupDocs a závislost do vašeho `pom.xml`:

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

### Přímé stažení
Alternativně stáhněte nejnovější JAR z [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

#### Kroky získání licence
- **Free trial:** 30‑denní zkušební verze s plnou sadou funkcí.  
- **Temporary license:** Požádejte o dočasný klíč pro rozšířené hodnocení.  
- **Purchase:** Získejte komerční licenci pro produkční nasazení.

### Základní inicializace a nastavení
Vytvořte instanci `Parser`, která ukazuje na PDF, které chcete analyzovat:

`Parser` je hlavní třída v GroupDocs.Parser, která představuje dokument a poskytuje metody pro extrahování obsahu, jako je text, tabulky a čárové kódy.  

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

## Jak číst QR kódy v PDF v Javě pomocí GroupDocs.Parser
Čtení QR kódů v PDF v Javě pomocí GroupDocs.Parser zahrnuje vytvoření instance parseru, konfiguraci možností čárových kódů pro cílení na typy QR, vyvolání metody pro extrakci čárových kódů a následné zpracování vrácených objektů čárových kódů. Proces je jednoduchý, funguje na jakékoli stránce PDF a vrací dekódované hodnoty spolu s pozičními metadaty pro další zpracování.

### Krok 1: ověření podpory čárových kódů
Před pokusem o extrakci potvrďte, že formát dokumentu podporuje skenování čárových kódů:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*Vysvětlení:* Tento guard (ochrana) zabraňuje chybám za běhu u nepodporovaných typů souborů.

### Krok 2: konfigurace možností čárových kódů (čtení QR kódů v Javě)
`BarcodeOptions` je konfigurační objekt, který vám umožňuje specifikovat, které symbologie čárových kódů detekovat, nastavit režim kvality skenování a jemně doladit parametry jako prahy detekce, což zajišťuje optimální výkon pro cílové QR kódy.

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*Vysvětlení:* `QualityMode.Low` urychluje zpracování; přepněte na `High`, pokud potřebujete vyšší přesnost. Argument `"QR"` říká enginu, aby hledal pouze čárové kódy typu QR.

### Krok 3: extrahování QR dat
`parser.getBarcodes(options)` skenuje dokument pomocí poskytnutých `BarcodeOptions` a vrací kolekci objektů `PageBarcodeArea`, z nichž každý obsahuje dekódovanou QR hodnotu, číslo stránky a přesné souřadnice čárového kódu na stránce, což umožňuje přesné následné zpracování.

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*Vysvětlení:* `parser.getBarcodes` vrací iterovatelnou kolekci objektů `PageBarcodeArea`, z nichž každý obsahuje dekódovanou QR hodnotu a její umístění na stránce.

## Export extrahovaných dat do XML
### Krok 4: inicializace XML exportéru
`XmlExporter` je pomocná třída, která převádí kolekci objektů čárových kódů do dobře strukturovaného XML dokumentu, automaticky generuje elementy pro každý čárový kód s atributy pro index stránky, pozici a dekódovanou hodnotu, které lze následně uložit nebo streamovat do jiných systémů.

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*Vysvětlení:* `XmlExporter` zajišťuje serializaci objektů čárových kódů do standardního XML, připraveného pro integraci s ERP nebo inventárními systémy.

### Krok 5: zápis XML souboru
Uložte extrahované QR informace na disk:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*Vysvětlení:* Výsledný `data.xml` obsahuje jeden element `<Barcode>` na QR kód, s atributy pro číslo stránky, souřadnice a dekódovanou hodnotu.

## Praktické aplikace
1. **Inventory management:** Automaticky naplňovat databáze zásob čtením QR značek na příchozích PDF přepravních dokumentech.  
2. **Supply‑chain visibility:** Sledovat balíky v reálném čase extrahováním QR identifikátorů vložených do logistických dokumentů.  
3. **Retail receipts:** Získávat propagační nebo zárukové informace z QR kódů tištěných na digitálních účtenkách.

## Úvahy o výkonu
- **Memory management:** Pro velmi velké PDF soubory zpracovávejte stránky ve streamovacím režimu místo načítání celého souboru do paměti.  
- **QualityMode selection:** Použijte `Low` pro hromadné zpracování; přepněte na `High`, když pracujete s nízkým rozlišením skenů.  
- **Library updates:** Udržujte GroupDocs.Parser aktuální, aby jste těžili z nejnovějších vylepšení výkonu a oprav chyb.

## Časté problémy a řešení
| Příznak | Pravděpodobná příčina | Řešení |
|---------|-----------------------|--------|
| Žádné čárové kódy nebyly vráceny | Zadán nesprávný typ čárového kódu | Změňte `"QR"` na odpovídající typ (např. `"CODE_128"`). |
| Chyba nedostatku paměti u velkých PDF | Celý dokument načten najednou | Zpracovávejte stránky jednotlivě nebo zvyšte velikost haldy JVM (`-Xmx2g`). |
| Prázdný XML soubor | `exportBarcodes` zavoláno před extrakcí | Ujistěte se, že `parser.getBarcodes(options)` vrací data před exportem. |

## Často kladené otázky
**Q: Mohu extrahovat čárové kódy ze souborů obrázků pomocí GroupDocs.Parser?**  
A: Ano, knihovna podporuje extrakci čárových kódů z běžných formátů obrázků (PNG, JPEG, TIFF).

**Q: Jaké formáty čárových kódů jsou rozpoznány?**  
A: QR, Code 39, Code 128, DataMatrix, PDF417 a mnoho dalších. Viz dokumentace API pro úplný seznam.

**Q: Jak mám zacházet s PDF chráněnými heslem?**  
A: Předávejte heslo konstruktoru `Parser`: `new Parser(filePath, "password")`.

**Q: Je zkušební verze dostatečná pro testování v produkci?**  
A: Zkušební verze poskytuje plnou funkčnost, ale přidává vodoznak k extrahovaným datům. Pro produkci si pořiďte komerční licenci.

**Q: Co když moje PDF obsahuje jak QR, tak lineární čárové kódy?**  
A: Vytvořte více instancí `BarcodeOptions` nebo předávejte pole typů, aby se skenovaly všechny potřebné formáty najednou.

**Poslední aktualizace:** 2026-10-12  
**Testováno s:** GroupDocs.Parser 25.5  
**Autor:** GroupDocs  

## Zdroje
- [GroupDocs.Parser Java dokumentace](https://docs.groupdocs.com/parser/java/)
- [API reference](https://reference.groupdocs.com/parser/java)
- [Download GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [GitHub repozitář](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Bezplatné fórum podpory](https://forum.groupdocs.com/c/parser)
- [Žádost o dočasnou licenci](https://purchase.groupdocs.com/temporary-license/)

## Související tutoriály
- [Extrahovat čárový kód PDF GroupDocs Parser Java](/parser/java/barcode-extraction/extract-barcode-pdf-groupdocs-parser-java/)
- [Jak načíst PDF z URL pomocí GroupDocs.Parser pro Javu](/parser/java/document-loading/)
- [Extrahovat data formulářů PDF pomocí GroupDocs.Parser v Javě](/parser/java/form-extraction/groupdocs-parser-java-pdf-form-extraction/)