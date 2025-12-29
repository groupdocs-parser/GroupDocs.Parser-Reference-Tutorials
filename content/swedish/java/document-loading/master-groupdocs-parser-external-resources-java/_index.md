---
date: '2025-12-29'
description: Lär dig hur du extraherar bilder från dokument och hur du filtrerar resurser
  med GroupDocs.Parser för Java. Denna guide täcker konfiguration, anpassade hanterare
  och praktiska exempel.
keywords:
- GroupDocs.Parser for Java
- external resource loading in Java
- custom handlers in GroupDocs
title: Extrahera bilder från dokument med GroupDocs.Parser Java – En guide
type: docs
url: /sv/java/document-loading/master-groupdocs-parser-external-resources-java/
weight: 1
---

# Extrahera bilder från dokument och filtrera resurser med GroupDocs.Parser Java

Att extrahera bilder från dokument är ett vanligt krav när man bygger dokument‑behandlingspipelines. I den här handledningen kommer du att upptäcka **hur man extraherar bilder från dokument** med GroupDocs.Parser för Java, och du kommer också att lära dig **hur man filtrerar resurser** så att endast de filer du behöver laddas. Vi går igenom hur du installerar biblioteket, skapar en anpassad `ExternalResourceHandler` och tillämpar filtreringslogik för att hålla din applikation snabb och säker.

## Snabba svar
- **Vad gör GroupDocs.Parser?** Det parsar ett brett spektrum av dokumentformat och ger dig åtkomst till text, bilder och andra inbäddade resurser.  
- **Kan jag hoppa över oönskade bilder?** Ja—genom att implementera en anpassad `ExternalResourceHandler` kan du bestämma vilka resurser som ska laddas.  
- **Vilken Maven‑version krävs?** Använd GroupDocs.Parser Java 25.5 eller nyare.  
- **Behöver jag en licens?** En gratis provperiod fungerar för utvärdering; en permanent licens krävs för produktion.  
- **Är detta tillvägagångssätt trådsäkert?** Parser‑objekt delas inte mellan trådar; skapa en ny `Parser`‑instans per tråd.

## Vad betyder “extrahera bilder från dokument”?
När ett dokument innehåller inbäddade bilder, diagram eller annan media innebär “extrahera bilder från dokument” att programmässigt hämta dessa binära filer så att du kan lagra, visa eller vidarebearbeta dem utanför den ursprungliga filen.

## Varför filtrera resurser vid extrahering av bilder?
- Minska minnesförbrukningen genom att ignorera stora eller irrelevanta filer.  
- Förbättra säkerheten genom att förhindra laddning av potentiellt osäkert innehåll.  
- Snabba upp bearbetningen, särskilt med enorma dokument som innehåller många inbäddade objekt.

## Förutsättningar

- **Java Development Kit (JDK)** – version 8 eller högre.  
- **Maven** – för beroendehantering.  
- Grundläggande kunskap om Java I/O och undantagshantering.

## Installera GroupDocs.Parser för Java

Lägg till GroupDocs‑förrådet och parser‑beroendet i din `pom.xml`:

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

Alternativt, ladda ner den senaste versionen från [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

### Licensanskaffning
- **Free Trial** – utforska kärnfunktioner utan kostnad.  
- **Temporary License** – lås upp full funktionalitet under utvärdering.  
- **Purchased License** – krävs för kommersiell distribution.

## Hur man filtrerar resurser vid extrahering av bilder

### Steg 1: Skapa en anpassad hanterare
Definiera en klass som ärver `ExternalResourceHandler`. Inuti `onLoading`‑metoden bestämmer du vilka resurser som ska behållas.

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

### Steg 2: Konfigurera `ParserSettings` med hanteraren
Skicka din `Handler`‑instans till `ParserSettings` och använd den när du öppnar ett dokument.

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

### Steg 3: Finjustera filtreringslogiken
Om du behöver mer sofistikerade regler—t.ex. filtrering efter bildstorlek, format eller URI‑mönster—utöka `onLoading`‑metoden därefter:

```java
@Override
public void onLoading(ExternalResourceLoadingArgs args) {
    if (!args.getUri().endsWith("installation.png")) {
        args.setSkipped(true);
    }
}
```

## Praktiska tillämpningar

1. **Document Management Systems** – Hämta endast de nödvändiga bilderna från skannade kontrakt för att generera miniatyrbilder.  
2. **Data Extraction Services** – Hoppa över dekorativa grafik och fokusera på diagram som innehåller värdefull data.  
3. **Web Scraping Tools** – Filtrera bort spårningspixlar medan du hämtar meningsfull media från HTML‑baserade dokument.

## Prestandaöverväganden
- **Filter early**: Använd din anpassade hanterare innan du itererar över resurser för att undvika att ladda oönskad data i minnet.  
- **Dispose promptly**: Använd try‑with‑resources (`try (Parser parser = …)`) för att frigöra inhemska resurser.  
- **Async processing**: För stora batcher, bearbeta dokument i parallella strömmar samtidigt som varje `Parser`‑instans hålls till en enda tråd.

## Vanliga problem & lösningar

| Problem | Varför det händer | Lösning |
|---------|-------------------|---------|
| Inga bilder returneras | Hantera (handler) hoppar över alla resurser av misstag | Verifiera `if`‑villkoret och säkerställ att `args.setSkipped(true)` endast anropas för oönskade URI:er. |
| `IOException` på stora filer | Otillräckligt heap‑minne | Öka JVM‑heap (`-Xmx2g`) eller bearbeta sidor i mindre delar. |
| Licensen känns inte igen | Använder trial‑DLL med produktionskod | Ange rätt licensfilssökväg via `License.setLicense("path/to/license")`. |

## Vanliga frågor

**Q: Vad är huvudsyftet med att använda en anpassad `ExternalResourceHandler`?**  
A: Det låter dig kontrollera vilka externa resurser som laddas, vilket förbättrar säkerhet och prestanda genom att filtrera bort onödiga filer.

**Q: Kan jag använda GroupDocs.Parser för Java utan licens?**  
A: Ja, en gratis provperiod finns tillgänglig, men vissa avancerade funktioner kan vara begränsade tills du får en temporär eller köpt licens.

**Q: Hur hanterar jag undantag under parsning med GroupDocs.Parser?**  
A: Omge parsningsanrop med try‑catch‑block för `IOException` och andra specifika undantag för att hantera fel på ett smidigt sätt.

**Q: Vilka är vanliga fallgropar vid filtrering av resurser?**  
A: Felaktiga URI‑kontroller kan hoppa över nödvändiga filer; använd loggning eller brytpunkter för att verifiera dina villkor.

**Q: Är det möjligt att parsra icke‑HTML‑dokument med GroupDocs.Parser för Java?**  
A: Absolut—GroupDocs.Parser stödjer PDF‑filer, Word, Excel, PowerPoint och många andra format.

## Nästa steg
Fördjupa dig i biblioteket genom att utforska [API Reference](https://reference.groupdocs.com/parser/java) eller experimentera med ytterligare inställningar såsom `ParserSettings.setDetectTables(true)` för tabellutvinning.

---

**Senast uppdaterad:** 2025-12-29  
**Testad med:** GroupDocs.Parser 25.5 for Java  
**Författare:** GroupDocs  

## Resurser
- **Documentation:** [GroupDocs.Parser-dokumentation](https://docs.groupdocs.com/parser/java/)  
- **API Reference:** [API‑detaljer](https://reference.groupdocs.com/parser/java)  
- **Downloads:** [Senaste versioner](https://releases.groupdocs.com/parser/java/)