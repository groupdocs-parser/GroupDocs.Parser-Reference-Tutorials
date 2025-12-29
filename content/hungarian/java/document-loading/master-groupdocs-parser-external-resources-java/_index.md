---
date: '2025-12-29'
description: Tanulja meg, hogyan lehet képeket kinyerni a dokumentumokból, és hogyan
  szűrheti a forrásokat a GroupDocs.Parser for Java használatával. Ez az útmutató
  a konfigurációt, az egyéni kezelőket és gyakorlati példákat fed le.
keywords:
- GroupDocs.Parser for Java
- external resource loading in Java
- custom handlers in GroupDocs
title: Képek kinyerése dokumentumokból a GroupDocs.Parser Java segítségével – Útmutató
type: docs
url: /hu/java/document-loading/master-groupdocs-parser-external-resources-java/
weight: 1
---

# Képek kinyerése dokumentumokból és erőforrások szűrése a GroupDocs.Parser Java-val

A képek kinyerése dokumentumokból gyakori követelmény dokumentumfeldolgozó csővezetékek építésekor. Ebben az útmutatóban megtudja, **hogyan kell képeket kinyerni dokumentumokból** a GroupDocs.Parser for Java használatával, és **hogyan lehet szűrni az erőforrásokat**, hogy csak a szükséges fájlok legyenek betöltve. Lépésről lépésre bemutatjuk a könyvtár beállítását, egy egyedi `ExternalResourceHandler` létrehozását, és a szűrési logika alkalmazását, hogy alkalmazása gyors és biztonságos legyen.

## Gyors válaszok
- **Mi a GroupDocs.Parser feladata?** Dokumentumformátumok széles skáláját elemzi, és hozzáférést biztosít a szöveghez, képekhez és egyéb beágyazott erőforrásokhoz.  
- **Kihagyhatom a nem kívánt képeket?** Igen – egy egyedi `ExternalResourceHandler` megvalósításával eldöntheti, mely erőforrásokat tölti be.  
- **Mely Maven verzió szükséges?** Használja a GroupDocs.Parser Java 25.5 vagy újabb verziót.  
- **Szükségem van licencre?** Egy ingyenes próba a kiértékeléshez elegendő; a termeléshez állandó licenc szükséges.  
- **Ez a megközelítés szálbiztos?** Az elemző objektumok nincsenek megosztva szálak között; minden szálnak hozzon létre egy új `Parser` példányt.

## Mi az a „képek kinyerése dokumentumokból”?
Amikor egy dokumentum beágyazott képeket, diagramokat vagy egyéb médiát tartalmaz, a „képek kinyerése dokumentumokból” azt jelenti, hogy programozottan lekéri ezeket a bináris fájlokat, hogy tárolja, megjelenítse vagy tovább feldolgozza őket az eredeti fájlon kívül.

## Miért szűrje az erőforrásokat képek kinyerése közben?
Az erőforrások szűrése segít:
- Csökkenteni a memóriahasználatot nagy vagy irreleváns fájlok figyelmen kívül hagyásával.  
- A biztonság javítása azzal, hogy megakadályozza a potenciálisan veszélyes tartalom betöltését.  
- Felgyorsítani a feldolgozást, különösen nagy dokumentumok esetén, amelyek sok beágyazott objektumot tartalmaznak.

## Előfeltételek

- **Java Development Kit (JDK)** – 8 vagy újabb verzió.  
- **Maven** – a függőségek kezeléséhez.  
- Alapvető ismeretek a Java I/O-val és a kivételkezeléssel.

## A GroupDocs.Parser beállítása Java-hoz

Adja hozzá a GroupDocs tárolót és a parser függőséget a `pom.xml` fájlhoz:

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

Alternatívaként töltse le a legújabb verziót a [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/) oldalról.

### Licenc beszerzése
- **Ingyenes próba** – a fő funkciók költség nélkül való felfedezése.  
- **Ideiglenes licenc** – a teljes funkcionalitás feloldása kiértékelés közben.  
- **Megvásárolt licenc** – kereskedelmi bevetéshez szükséges.

## Hogyan szűrje az erőforrásokat képek kinyerése közben

### 1. lépés: Egyedi kezelő létrehozása
Definiáljon egy osztályt, amely kiterjeszti az `ExternalResourceHandler`-t. Az `onLoading` metódusban dönthet arról, mely erőforrásokat tartja meg.

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

### 2. lépés: `ParserSettings` konfigurálása a kezelővel
Adja át a `Handler` példányát a `ParserSettings`-nek, és használja a dokumentum megnyitásakor.

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

### 3. lépés: A szűrési logika finomhangolása
Ha összetettebb szabályokra van szüksége – például képméret, formátum vagy URI-minta alapján történő szűrésre – bővítse az `onLoading` metódust ennek megfelelően:

```java
@Override
public void onLoading(ExternalResourceLoadingArgs args) {
    if (!args.getUri().endsWith("installation.png")) {
        args.setSkipped(true);
    }
}
```

## Gyakorlati alkalmazások

1. **Dokumentumkezelő rendszerek** – csak a szükséges képeket húzza ki a beolvasott szerződésekből, hogy bélyegképeket generáljon.  
2. **Adatkinyerő szolgáltatások** – hagyja ki a díszítő grafikákat, és a hasznos adatokat tartalmazó diagramokra koncentráljon.  
3. **Webkaparó eszközök** – szűrje ki a nyomkövető pixeleket, miközben értelmes médiát szerez be HTML‑alapú dokumentumokból.

## Teljesítményfontosságú szempontok
- **Korai szűrés**: Alkalmazza az egyedi kezelőt az erőforrások iterálása előtt, hogy elkerülje a nem kívánt adatok memóriába töltését.  
- **Gyors felszabadítás**: Használjon try‑with‑resources (`try (Parser parser = …)`) szintaxist a natív erőforrások felszabadításához.  
- **Aszinkron feldolgozás**: Nagy kötegek esetén dolgozza fel a dokumentumokat párhuzamos streamekben, miközben minden `Parser` példányt egyetlen szálra korlátozza.

## Gyakori problémák és megoldások
| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| Nincsenek visszaadott képek | A kezelő véletlenül minden erőforrást kihagy | Ellenőrizze az `if` feltételt, és győződjön meg róla, hogy a `args.setSkipped(true)` csak a nem kívánt URI-k esetén kerül meghívásra. |
| `IOException` nagy fájlok esetén | Nem elegendő heap memória | Növelje a JVM heap méretét (`-Xmx2g`), vagy dolgozza fel az oldalakat kisebb darabokban. |
| A licenc nem ismerhető fel | Próba DLL használata termelési kóddal | Adja meg a helyes licencfájl útvonalát a `License.setLicense("path/to/license")` hívással. |

## Gyakran ismételt kérdések

**Q: Mi a fő célja egy egyedi `ExternalResourceHandler` használatának?**  
A: Lehetővé teszi, hogy szabályozza, mely külső erőforrások kerülnek betöltésre, ezáltal növelve a biztonságot és a teljesítményt a felesleges fájlok szűrésével.

**Q: Használhatom a GroupDocs.Parser for Java-t licenc nélkül?**  
A: Igen, elérhető egy ingyenes próba, de egyes fejlett funkciók korlátozottak lehetnek, amíg nem szerez ideiglenes vagy megvásárolt licencet.

**Q: Hogyan kezeljem a kivételeket a GroupDocs.Parser használata közben?**  
A: A parsing hívásokat `try‑catch` blokkokba kell helyezni `IOException` és egyéb specifikus kivételek esetén, hogy hibákat elegánsan kezeljen.

**Q: Mik a gyakori buktatók az erőforrások szűrésekor?**  
A: Hibás URI-ellenőrzések elhagyhatják a szükséges fájlokat; használjon naplózást vagy breakpoint-okat a feltételek ellenőrzéséhez.

**Q: Lehet nem‑HTML dokumentumokat is feldolgozni a GroupDocs.Parser for Java-val?**  
A: Természetesen – a GroupDocs.Parser támogatja a PDF-eket, Word, Excel, PowerPoint és számos más formátumot.

## Következő lépések
Mélyedjen el a könyvtárban a [API Reference](https://reference.groupdocs.com/parser/java) felfedezésével, vagy kísérletezzen további beállításokkal, például a `ParserSettings.setDetectTables(true)`-val a táblázatok kinyeréséhez.

---

**Last Updated:** 2025-12-29  
**Tested With:** GroupDocs.Parser 25.5 for Java  
**Author:** GroupDocs  

**Erőforrások**  
- **Dokumentáció:** [GroupDocs.Parser Documentation](https://docs.groupdocs.com/parser/java/)  
- **API referencia:** [API Details](https://reference.groupdocs.com/parser/java)  
- **Letöltések:** [Latest Versions](https://releases.groupdocs.com/parser/java/)