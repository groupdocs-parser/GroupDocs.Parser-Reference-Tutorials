---
date: '2026-01-19'
description: Tanulja meg, hogyan lehet képeket kinyerni Word-dokumentumokból a GroupDocs.Parser
  for Java segítségével, és hatékonyan PNG formátumban menteni a Word-képeket.
keywords:
- extract images from Word documents
- GroupDocs.Parser for Java
- automate image extraction
title: Képek kinyerése a Wordből a GroupDocs.Parser for Java használatával
type: docs
url: /hu/java/image-extraction/extract-images-word-docs-groupdocs-parser-java/
weight: 1
---

 kinyerése Word fájlokból manuálisan időigényes és hibára hajlamos. Ebben az útmutatóban megtudja, hogyan **hogyan nyerhet ki képeket a Word-ből** automatikusan a GroupDocs.Parser for Java segítségével,## Gyors válaszok a könyson a szöveghez, táblázatokhoz és képekhez.  
- **Hány sor kódból áll?** Körülbelül 30 sor Java, plusz néhány konfigurációs sor.  
- **Szükségem van licencre?** Egy ingyenes pró szükséges.  
-tek beágyazott képeket?** Igen – a `getImages()` metódus minden beágyazott képet visszaad.  
- **Támogatott kimenetiráját, és minden képet `PageImageArea` objektumként jelenít meg. Ez lehetővé teszi, hogy programozottan kinyerje az összes képet a Microsoft Word megnyitása nélkül.

## Miért használjuk a GroupDocs.Parser for Java-t?
- **Sebesség:** A tiszta Java elemzés elkerüli a COM vagy Office automatizálás terheit.  
- **Megbízhatóság:** Bármely platformon (Windows, Linux, macOS) működik, és hibás fájlok esetén is megfelelően kezeli őket.  
- **Rugalmasság:** Széles körű formátumot támogat, így ugyanazt a kódot használhatja PDF, PPTX stb. esetén is.

## Előfeltételek
- **GroupDocs.Parser for Java** (25.5 vagy újabb verzió)  
- **JDK 8+**  
- IDE, például IntelliJ IDEA, Eclipse vagy NetBeans  

## A GroupDocs.Parser for Java beállítása

Adja hozzá a könyvtárat Maven projektjéhez:

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

Alternatívaként töltse le a legújabb verziót közvetlenül a [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/) oldalról.

### Licenc megsenes próba:** Kezdjen egy ingyenes próbával a funkciók felfedezéséhez.  
- **Ideiglenerezzen teljes licencet a termelési környezethez.

Az alábbiakban a teljes, azonnal futtatható Java kód található, amely **képeket nyer ki a Word dokumentumokból** és PNG fájlokként menti őket.

### 1. lépés: A Parser inicializálása

```java
// Initialize the Parser with the document path.
try (Parser parser = new Parser(documentPath)) {
    // Proceed with image extraction...
}
```

### 2. lépés: Képek kinyerése

```java
// Extract images from the document.
Iterable<PageImageArea> images = parser.getImages();
```

### 3. lépés: Képkimeneti beállítások konfigurálása

```java
// Set options to save images in PNG format.
ImageOptions options = new ImageOptions(ImageFormat.Png);
```

### 4. lépés: Minden kép mentése

```java
int imageNumber = 0;
for (PageImageArea image : images) {
    String outputPath = YOUR_OUTPUT_DIRECTORY + "/" + imageNumber + ".png";
    image.save(outputPath, options);
    imageNumber++;
}
```

### 5. lépés: Segédmetódusok definiálása az elérési utakhoz

```java
public static String getDocumentDirectory() {
    return YOUR_DOCUMENT_DIRECTORY;
}

public static String getOutputDirectory() {
    return YOUR_OUTPUT_DIRECTORY;
}
```

Cserélje le a `YOUR_DOCUMENT_DIRECTORY` és `YOUR_OUTPUT_DIRECTORY` értékeket a tényleges fájlrendszer helyekre, amelyeket használni kíván.

## Hogyan nyerhetünk ki beágyazott képeket a docx‑ből?
A `getImages()` hívás automatikusan visszaadja a **beágyazott képeket** egy DOCX fájlból, legyenek azok beágyazott, lebegő vagy alakzat részei. Nem szükséges további API hívás.

## Hogyan nyerhetünk ki képeket a docx‑ből és menthetjük PNG‑ként?
A **3. lépésben** bemutatott `ImageOptions` objektum beállítja a kimeneti formátumot. Az `ImageFormat.Png` átadásával minden kinyert kép PNG fájlként kerül mentésre, ezzel teljesítve a **Word képek mentése PNG formátumban** követelményt.

## Gyakorlati alkalmazások
1. **Tartalomkezelés:** Képek kinyerése régi Word fájlokból egy digitális eszközkönyvtár számára.  
2. **Adatmigráció:** Beágyazott grafikák áthelyezése egy új CMS‑be manuális másolás‑beillesztés nélkül.  
3. **Dokumentum archiválás:** Képek külön tárolása az archívum méretének csökkentése és a kereshetőség javítása érdekében.  
4. **Automatizált publikálás:** A kinyert PNG‑eket közvetlenül weboldalkészítő vagy e‑mail sablonokba táplálja.  

## Teljesítménybeli megfontolások
- **Memória:** Elég heap memóriát (`-Xmx2g` vagy nagyobb) kell biztosítani nagy dokumentumok feldolgozásakor.  
- **Kötegelt feldolgozás:** Futtassa a ciklust egy mappában lévő fájlokon, és egy `Parser` példányt használjon dokumentumonként a memóriahasználat alacsonyan tartásához.  
- **Fájlkezelők:** A try‑with‑resources blokk biztosítja, hogy a parser gyorsan bezáruljon, megakadályozva a szivárgásokat problémák és megoldások

| Probléma | Megoldás |
|----------|----------|
| **OutOfMemoryError** hatalmas DOCX fájlok esetén | Növelje a JVM heap méretét vagy dolgozza fel a dokumentumot kisebb kötegekőum valóban tartalmaz beágyazott képeket; egyes „képek” VML rajzok, amelyek nem jelennek meg képként. |
| **Helytelen képorientáció** | Néhány DOCX kép EXIF forgatást tárol; szükség esetén utófeldolgozza egy képkönyvtárral. |

## Gyakran feltett kérdések

**K: Milyen fájlformátumokat támogat a GroupDocs.Parser a képek kinyeréséhez?**  
V: Kezeli a DOC, DOCX, PDF, PPT, PPTX és számos egyéb formátumot, a képeket ugyanazon `getImages()` metóduson keresztül teszi elérhetővé.

**K: Kinyerhetek képeket jelszóval védett Word fájlokból?**  
V: Igen – adja meg a jelszót a `Parser` konstruktorának, és a könyvtár a kinyerés előtt visszafejti a dokumentumot.

**K: Van mód csak bizonyos képformátumok (pl. csak JPEG) kinyerésére?**  
V: A `PageImageArea` objektumok lekérése után ellenőrizze az `image.getFormat()` értékét, és a mentés előtt szűrje a kívánt formátumra.

**K: Támogatja a könyvtár az aszinkron feldolgozást?**  
V: Bár a mag API szinkron, a kinyerési logikát be lehet csomagolni egy külön szálba vagy használhatja a Java `CompletableFuture`‑t a párhuzamos feldolgozáshoz.

**K: Szükségem van kereskedelmi licencre a termeléshez?**  
V: Az ingyenes próba elegendő a kiértékeléshez, de a kereskedelmi telepítésekhez fizetett licenc szükséges.

## Következtetés teljes, termelésre kész megoldással a **képekvel és a **Word képek mentésére PNG formátumban**. Integrálja ezt a kódot meglévő folyamatokba, automatizálja a kötegelt kinyerést, és szabadítsa fel a Word fájlokban rejtett vizuális eszközöket.

---

**Utolsó frissítés:** 2026-01-19  
**Tesztelve:** GroupDocs.Parser 25.5  
**Szerző:** GroupDocs  

**Erőforrások**
- **Dokumentáció:** [GroupDocs Parser Java Documentation](https://docs.groupdocs.com/parser/java/)
- **API referencia:** [GroupDocs API Reference](https://reference.groupdocs.com/parser/java)
- **Letöltés:** [Latest Release](https://releases.groupdocs.com/parser/java/)
- **GitHub:** [Source Code on GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- **Ingyenes támogatás:** [GroupDocs Forum](https://forum.groupdocs.com/c/parser)
- **Ideiglenes licenc:** [Obtain a Temporary License](https://purchase.groupdocs.com/temporary-license/)