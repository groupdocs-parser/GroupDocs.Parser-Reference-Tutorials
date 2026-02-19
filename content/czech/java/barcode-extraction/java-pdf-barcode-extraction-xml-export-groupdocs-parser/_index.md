---
date: '2026-02-19'
description: Naučte se, jak číst QR kódy v PDF souborech v Javě pomocí GroupDocs.Parser
  a exportovat data čárových kódů do XML.
keywords:
- Java PDF barcode extraction
- GroupDocs.Parser for Java
- XML export from PDF
title: Jak číst QR kódy v PDF souborech v Javě pomocí GroupDocs.Parser
type: docs
url: /cs/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Jak číst QR kódy v PDF souborech Java pomocí GroupDocs.Parser

V moderních obchodních pracovních postupech může **jak číst QR** kódy z PDF dokumentů rozhodnout o rozdílu mezi úzkým hrdlem ručního zadávání dat a plně automatizovaným tokem. Ať už zpracováváte přepravní manifesty, maloobchodní účtenky nebo produktové katalogy, rychlé a spolehlivé získávání informací z QR kódu je nezbytné. Tento tutoriál vás provede používáním **GroupDocs.Parser pro Java** k načtení QR kódů (a dalších čárových kódů) z PDF a exportem výsledků do čistého XML souboru, který mohou spotřebovat následné systémy.

## Rychlé odpovědi
- **Co GroupDocs.Parser pro Java dělá?** Čte PDF soubory a extrahuje strukturovaná data, jako jsou čárové kódy.  
- **Jak extrahovat QR kódy?** Konfigurací `BarcodeOptions` s typem QR a voláním `parser.getBarcodes()`.  
- **Mohu číst QR kódy v Javě?** Ano — nastavte typ čárového kódu na `"QR"` v možnostech.  
- **Potřebuji licenci?** Zkušební verze funguje pro testování; pro produkci je vyžadována komerční licence.  
- **Jaká verze Javy je požadována?** Doporučuje se Java 8 nebo vyšší.

## Co znamená „jak číst QR“ v kontextu zpracování PDF?
Čtení QR kódů z PDF znamená skenování každé stránky pro grafiku zakódovanou QR, dekódování vložených dat a vrácení ve formátu přátelském pro program. GroupDocs.Parser abstrahuje nízkoúrovňovou analýzu obrazu, takže se můžete soustředit na obchodní logiku místo manipulace s pixely.

## Proč použít GroupDocs.Parser pro extrakci QR?
- **Vysoká přesnost:** Vestavěné algoritmy zpracování obrazu zvládají skeny s nízkým rozlišením.  
- **Možnosti výkonu:** Vyberte `QualityMode.Low` pro rychlost nebo `QualityMode.High` pro maximální přesnost.  
- **Podpora napříč formáty:** Funguje s PDF, obrázky i s Office dokumenty, takže můžete znovu použít stejný kód pro různé typy souborů.

## Předpoklady
- **GroupDocs.Parser pro Java** (verze 25.5 nebo novější).  
- Maven nebo ruční stažení JAR souboru.  
- Vývojové prostředí Java 8+ (IntelliJ IDEA, Eclipse nebo jakýkoli editor).  

## Nastavení GroupDocs.Parser pro Java
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

### Přímé stažení
Alternativně stáhněte nejnovější JAR ze [GroupDocs.Parser pro Java – vydání](https://releases.groupdocs.com/parser/java/).

#### Kroky pro získání licence
- **Bezplatná zkušební verze:** 30‑denní zkušební verze s plnou sadou funkcí.  
- **Dočasná licence:** Požádejte o dočasný klíč pro rozšířené hodnocení.  
- **Nákup:** Získejte komerční licenci pro produkční nasazení.

### Základní inicializace a nastavení
Vytvořte instanci `Parser`, která ukazuje na PDF, které chcete analyzovat:

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

## Jak číst QR kódy v PDF souborech Java pomocí GroupDocs.Parser
### Krok 1: Ověření podpory čárových kódů
Před pokusem o extrakci potvrďte, že formát dokumentu podporuje skenování čárových kódů:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*Vysvětlení:* Tento guard zabraňuje chybám za běhu u nepodporovaných typů souborů.

### Krok 2: Konfigurace možností čárových kódů (Read QR codes Java)
Nastavte kvalitu skenování a specifikujte, že vás zajímají QR kódy:

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*Vysvětlení:* `QualityMode.Low` urychluje zpracování; přepněte na `High`, pokud potřebujete vyšší přesnost. Argument `"QR"` říká enginu, aby hledal pouze čárové kódy typu QR.

### Krok 3: Extrakce QR dat
Získejte informace o čárových kódech ze všech stránek PDF:

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*Vysvětlení:* `parser.getBarcodes` vrací iterovatelnou kolekci objektů `PageBarcodeArea`, z nichž každý obsahuje dekódovanou hodnotu QR a její umístění na stránce.

## Export extrahovaných dat do XML
### Krok 4: Inicializace XML exportéru
Vytvořte exportér, který převádí kolekci čárových kódů do dobře strukturovaného XML souboru:

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*Vysvětlení:* `XmlExporter` zajišťuje serializaci objektů čárových kódů do standardního XML, připraveného pro integraci s ERP nebo inventárními systémy.

### Krok 5: Zápis XML souboru
Uložte extrahované QR informace na disk:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*Vysvětlení:* Výsledný `data.xml` obsahuje jeden element `<Barcode>` pro každý QR kód, s atributy pro číslo stránky, souřadnice a dekódovanou hodnotu.

## Praktické aplikace
1. **Řízení zásob:** Automaticky naplňujte databáze zásob čtením QR tagů na PDF příchozích zásilek.  
2. **Viditelnost v dodavatelském řetězci:** Sledujte balíky v reálném čase extrakcí QR identifikátorů vložených do logistických dokumentů.  
3. **Maloobchodní účtenky:** Získejte propagační nebo zárukové informace z QR kódů tištěných na digitálních účtenkách.

## Úvahy o výkonu
- **Správa paměti:** U velmi velkých PDF zpracovávejte stránky ve streamovacím režimu místo načítání celého souboru do paměti.  
- **Výběr QualityMode:** Použijte `Low` pro hromadné zpracování; přepněte na `High`, když pracujete s nízkým rozlišením skenů.  
- **Aktualizace knihovny:** Udržujte GroupDocs.Parser aktuální, abyste těžili z nejnovějších vylepšení výkonu a oprav chyb.

## Časté problémy a řešení
| Příznak | Předpokládaná příčina | Řešení |
|---------|-----------------------|--------|
| Žádné čárové kódy nebyly vráceny | Zadán nesprávný typ čárového kódu | Změňte `"QR"` na odpovídající typ (např. `"CODE_128"`). |
| Chyba nedostatku paměti u velkých PDF | Celý dokument byl načten najednou | Zpracovávejte stránky jednotlivě nebo zvětšete velikost haldy JVM (`-Xmx2g`). |
| Prázdný XML soubor | `exportBarcodes` byl zavolán před extrakcí | Ujistěte se, že `parser.getBarcodes(options)` vrací data před exportem. |

## Často kladené otázky
**Q: Mohu extrahovat čárové kódy z obrazových souborů pomocí GroupDocs.Parser?**  
A: Ano, knihovna podporuje extrakci čárových kódů z běžných formátů obrázků (PNG, JPEG, TIFF).

**Q: Jaké formáty čárových kódů jsou rozpoznány?**  
A: QR, Code 39, Code 128, DataMatrix, PDF417 a mnoho dalších. Viz API dokumentace pro úplný seznam.

**Q: Jak mám zacházet s PDF chráněnými heslem?**  
A: Předávejte heslo konstruktoru `Parser`: `new Parser(filePath, "password")`.

**Q: Je zkušební verze dostatečná pro testování v produkci?**  
A: Zkušební verze poskytuje plnou funkčnost, ale přidává vodoznak k extrahovaným datům. Pro produkci pořiďte komerční licenci.

**Q: Co když moje PDF obsahuje jak QR, tak lineární čárové kódy?**  
A: Vytvořte více instancí `BarcodeOptions` nebo předávejte pole typů, aby se v jednom průchodu skenovaly všechny požadované formáty.

---

**Poslední aktualizace:** 2026-02-19  
**Testováno s:** GroupDocs.Parser 25.5  
**Autor:** GroupDocs  

## Zdroje
- [Dokumentace GroupDocs.Parser pro Java](https://docs.groupdocs.com/parser/java/)
- [Reference API](https://reference.groupdocs.com/parser/java)
- [Stáhnout GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [Repozitář na GitHubu](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Bezplatné fórum podpory](https://forum.groupdocs.com/c/parser)
- [Žádost o dočasnou licenci](https://purchase.groupdocs.com/temporary-license/)