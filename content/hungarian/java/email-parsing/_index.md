---
date: 2026-06-17
description: Ismerje meg, hogyan használhatja a Java e-mail elemző könyvtárat, a GroupDocs.Parser-t,
  hogy e-mail szöveget, mellékleteket és metaadatokat nyerjen ki PST, OST és szerver
  forrásokból.
keywords:
- java email parsing library
- extract email text java
- GroupDocs.Parser email extraction
schemas:
- author: GroupDocs
  dateModified: '2026-06-17'
  description: Learn how to use the Java email parsing library GroupDocs.Parser to
    extract email text Java, attachments, and metadata from PST, OST, and server sources.
  headline: 'Java Email Parsing Library: GroupDocs.Parser Extraction Tutorials'
  type: TechArticle
- description: Learn how to use the Java email parsing library GroupDocs.Parser to
    extract email text Java, attachments, and metadata from PST, OST, and server sources.
  name: 'Java Email Parsing Library: GroupDocs.Parser Extraction Tutorials'
  steps:
  - name: Initialise the Parser
    text: The `Parser` class is GroupDocs.Parser's entry point for opening any supported
      email source.
  - name: Extract Text from a Specific Message
    text: A `Message` object represents a single email with its body, headers, and
      attachments. Use the `extractText()` method on a `Message` object retrieved
      from the parser. This method returns the email body as a plain‑text `String`.
      > **Why this matters:** By extracting plain text you can feed the content
  - name: Retrieve Attachments Collection
    text: The `Message` class exposes an `getAttachments()` method that returns a
      list of `Attachment` objects.
  - name: Stream Each Attachment to a File
    text: Call the `save()` method on each attachment, passing an `OutputStream` of
      your choice. The library handles MIME decoding automatically. > **Pro tip:**
      Filter attachments by MIME type (`att.getContentType()`) if you only need PDFs
      or images, reducing I/O overhead.
  - name: Configure the ExchangeClient
    text: Provide the server URL, credentials, and optionally a mailbox folder name.
      The client will handle authentication and pagination internally.
  - name: Iterate Over Messages
    text: Use the `enumerateMessages()` method to obtain an `Iterable<Message>` and
      process each message as it arrives. > **Why this matters:** Streaming enables
      real‑time processing of incoming mail for compliance monitoring, auto‑reply
      bots, or CRM integration without massive storage footprints.
  type: HowTo
- questions:
  - answer: Yes. Provide the password when initializing the `Parser` object, and the
      library will decrypt the file on the fly.
    question: Can I parse password‑protected PST files?
  - answer: Absolutely. Use the `ExchangeClient` class to connect via EWS or IMAP
      and iterate through messages without downloading the entire mailbox.
    question: Does GroupDocs.Parser support streaming from an Exchange server?
  - answer: Stream attachment content directly to a file or output stream using the
      `save()` method instead of loading it fully into memory.
    question: How do I handle large attachments without exhausting memory?
  - answer: Yes. Query the mailbox with the appropriate filter (`IsRead = false`)
      before iterating over messages.
    question: Is there a way to extract only unread emails?
  - answer: The library treats embedded images as separate attachment objects; you
      can retrieve them and embed them back into HTML if needed.
    question: What if an email contains embedded images in the body?
  type: FAQPage
title: 'Java e-mail elemző könyvtár: GroupDocs.Parser kinyerési útmutatók'
type: docs
url: /hu/java/email-parsing/
weight: 14
---

# Java e‑mail elemző könyvtár – GroupDocs.Parser kinyerési útmutatók

Ha egy robusztus **java email parsing library** integrálására keresel a Java alkalmazásaidba, jó helyen jársz. Ebben az útmutatóban bemutatjuk, miért emelkedik ki a GroupDocs.Parser, hogyan állítható be, és lépésről‑lépésre, kód‑nélküli útmutatót adunk az e‑mail szöveg, mellékletek és metaadatok kinyeréséhez PST/OST fájlokból, EML/MSG archívumokból és élő Exchange szerverekről. Emellett valós példákat, teljesítmény tippeket és linkeket találsz kész példákhoz, amelyeket azonnal adaptálhatsz.

## Gyors válaszok
- **Mi a legjobb Java könyvtár az e‑mail elemzéshez?** GroupDocs.Parser egy teljes körű java email parsing library, amely támogatja a PST, OST, EML, MSG és Exchange szerver forrásokat.  
- **Kinyerhetek egyszerű szöveget az e‑mailből?** Igen—használd a könyvtár `extractText()` metódusait, hogy tiszta e‑mail szöveget kapj Java stílusban.  
- **Szükségem van licencre a termeléshez?** Ideiglenes licenc elérhető teszteléshez; kereskedelmi licenc szükséges a termelési környezethez.  
- **Mely e‑mail formátumok támogatottak?** PST, OST, EML, MSG és közvetlen Exchange szerver kapcsolatok.  
- **Kompatibilis a könyvtár a Java 11+ verzióval?** Teljesen— a GroupDocs.Parser Java 8 és újabb verziókon fut, beleértve a Java 11, 17 és 21-et.

## Mi az a Java e‑mail elemző könyvtár?
A **java email parsing library** egy API-k gyűjteménye, amely nyers e‑mail fájlokat vagy szerver adatfolyamokat olvas be, és strukturált objektumokká alakítja, mint például üzenetek, mellékletek és fejlécek. Elrejti a formátum‑specifikus sajátosságokat, így az üzleti logikára koncentrálhatsz a részletes elemzés helyett.

## Miért használjuk a GroupDocs.Parser‑t e‑mail kinyeréshez?
A GroupDocs.Parser egységes, nagy teljesítményű megoldást nyújt számos e‑mail formátum kezelésére. Egyetlen API felületet, gyors feldolgozást, gazdag metaadatokat és platformközi kompatibilitást biztosít.

### Mérhető előnyök
A GroupDocs.Parser **50+ bemeneti és kimeneti formátumot** támogat (beleértve a PST, OST, EML, MSG, MBOX és több saját Exchange formátumot), és **akár 200 MB mellékletet** képes kinyerni üzenetenként anélkül, hogy az egész fájlt betöltené a memóriába. Streaming architektúrája a csúcs memóriahasználatot **150 MB** alá csökkenti még több gigabájtos levéltárak feldolgozása esetén is.

## Előkövetelmények
- Java Development Kit (JDK) 8 vagy újabb telepítve.  
- Maven vagy Gradle a függőségkezeléshez.  
- Érvényes GroupDocs.Parser for Java licenc (ideiglenes licenc teszteléshez).  

### Maven függőség
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-parser</artifactId>
    <version>23.12</version>
</dependency>
```

> **Pro tipp:** Adj hozzá a hivatalos dokumentációból származó repository kódrészletet, ha feloldási hibákat tapasztalsz.

## Elérhető útmutatók

### [Hatékony képek kinyerése e‑mailből a GroupDocs.Parser for Java használatával](./extract-images-emails-groupdocs-parser-java/)
Ismerd meg, hogyan lehet hatékonyan kinyerni képeket e‑mail fájlokból a GroupDocs.Parser for Java segítségével. Ez az útmutató a beállítást, megvalósítást és gyakorlati alkalmazásokat tárgyalja.

### [Hogyan nyerjünk ki e‑mail-eket Exchange szerverről a GroupDocs.Parser Java e‑mail elemzéshez](./extract-emails-groupdocs-parser-java-exchange-server/)
Lépésről‑lépésre útmutató az Exchange-hez való csatlakozáshoz, üzenetek streamingjéhez és a tartalom kinyeréséhez anélkül, hogy az egész postafiókot letöltenéd.

### [Hogyan nyerjünk ki szöveget e‑mail-ekből a GroupDocs.Parser Java használatával: Lépésről‑lépésre útmutató](./extract-text-emails-groupdocs-parser-java/)
A részletes útmutató a PST/EML fájlok betöltéséről, üzenetek lekérdezéséről és a tiszta egyszerű szöveges törzsek kinyeréséről.

## Hogyan nyerjünk ki e‑mail szöveget a GroupDocs.Parser Java-ban?

A `Parser` osztály a belépési pont bármely támogatott e‑mail forrás megnyitásához. Töltsd be a PST vagy EML fájlt a `Parser` osztállyal, és hívd meg a `extractText()`‑t – ez a kétlépéses minta a egyszerű szöveg kinyeréséhez. A könyvtár automatikusan kezeli a multipart MIME‑t, a HTML‑ról‑szövegre konverziót és a karakterkészlet felismerést, tiszta Unicode karakterláncokat adva, készen állva indexelésre vagy elemzésre.

### 1. lépés: A Parser inicializálása
A `Parser` osztály a GroupDocs.Parser belépési pontja bármely támogatott e‑mail forrás megnyitásához.  

```java
Parser parser = new Parser("path/to/mailbox.pst");
```

### 2. lépés: Szöveg kinyerése egy adott üzenetből
Egy `Message` objektum egyetlen e‑mailt képvisel a törzsével, fejléceivel és mellékleteivel. Használd a `extractText()` metódust egy `Message` objektumon, amelyet a parserből nyersz ki. Ez a metódus a e‑mail törzset egyszerű szöveg `String`‑ként adja vissza.

```java
Message message = parser.getMessage(0); // zero‑based index
String plainText = message.extractText();
System.out.println(plainText);
```

> **Miért fontos:** Az egyszerű szöveg kinyerésével a tartalmat kereső indexekbe, érzelemelemző motorokba vagy automatizált jegyrendszerekbe táplálhatod anélkül, hogy HTML címkékkel vagy beágyazott képekkel kellene foglalkoznod.

## Hogyan nyerjünk ki mellékleteket PST vagy OST fájlokból?

A GroupDocs.Parser minden mellékletet külön `Attachment` objektumként kezel, amelyet közvetlenül a lemezre streamelhetsz. Ez a megközelítés elkerüli nagy fájlok memóriába töltését, és akár **2 GB** méretű mellékletekhez is működik. Az `Attachment` osztály egy e‑mailhez csatolt fájlt kapszuláz, streaming képességekkel, amelyek alacsony memóriahasználatot biztosítanak.

### 1. lépés: Mellékletek gyűjteményének lekérése
A `Message` osztály egy `getAttachments()` metódust biztosít, amely `Attachment` objektumok listáját adja vissza.

```java
List<Attachment> attachments = message.getAttachments();
```

### 2. lépés: Minden melléklet streamelése fájlba
Hívd meg a `save()` metódust minden mellékleten, átadva egy általad választott `OutputStream`‑et. A könyvtár automatikusan kezeli a MIME dekódolást.

```java
for (Attachment att : attachments) {
    try (FileOutputStream fos = new FileOutputStream("output/" + att.getFileName())) {
        att.save(fos);
    }
}
```

> **Pro tipp:** Szűrd a mellékleteket MIME típus szerint (`att.getContentType()`), ha csak PDF-ekre vagy képekre van szükséged, ez csökkenti az I/O terhelést.

## Hogyan csatlakozzunk Exchange szerverhez és streameljük az e‑mail-eket?

Az `ExchangeClient` osztály a GroupDocs.Parser magas szintű csatlakozója a Microsoft Exchange Web Services (EWS) és IMAP számára. Üzeneteket egyesével streamel, így soha nem kell letölteni az egész postafiókot. Ez a streaming képesség valós idejű feldolgozást, megfelelőségi monitorozást és automatizált munkafolyamatokat tesz lehetővé nagy tárolási igények nélkül.

### 1. lépés: Az ExchangeClient konfigurálása
Add meg a szerver URL‑t, hitelesítő adatokat, és opcionálisan egy postafiók mappa nevét. A kliens belsőleg kezeli a hitelesítést és a lapozást.

```java
ExchangeClient client = new ExchangeClient(
    "https://mail.example.com/EWS/Exchange.asmx",
    "user@example.com",
    "password"
);
client.setFolder("Inbox");
```

### 2. lépés: Üzenetek iterálása
Használd az `enumerateMessages()` metódust egy `Iterable<Message>` lekéréséhez, és dolgozd fel minden üzenetet, ahogy megérkezik.

```java
for (Message msg : client.enumerateMessages()) {
    System.out.println("Subject: " + msg.getSubject());
    System.out.println("Body: " + msg.extractText());
}
```

> **Miért fontos:** A streaming lehetővé teszi a bejövő levelek valós idejű feldolgozását megfelelőségi monitorozáshoz, automatikus válasz botokhoz vagy CRM integrációhoz anélkül, hogy hatalmas tárolási lábnyomra lenne szükség.

## Gyakori problémák és megoldások

| Probléma | Tipikus tünet | Javasolt megoldás |
|-------|----------------|-----------------|
| **Jelszóval védett PST** | `ParserException: Access denied` | Add meg a jelszót a `Parser` konstruktorban: `new Parser("file.pst", "password")`. |
| **Memóriahiány nagy postafiókoknál** | JVM összeomlik `java.lang.OutOfMemoryError`‑ral | Engedélyezd a streaming módot: `parser.setLoadOptions(LoadOptions.STREAMING)`. |
| **Hiányzó melléklet tartalom** | A mellékletek 0 bájtosak | Győződj meg róla, hogy a `attachment.save(outputStream)`‑t hívod, a `attachment.getData()` helyett, amely lehet, hogy lazy‑loaded. |
| **Helytelen dátumformátumok** | A dátumok UTC‑ben jelennek meg a helyi idő helyett | Használd a `msg.getMetadata().getSentDate().toInstant().atZone(ZoneId.systemDefault())`‑t. |
| **Exchange korlátozás** | API visszaadja a `429 Too Many Requests` hibát | Implementálj exponenciális back‑off‑ot, és tartsd be a szerver által biztosított `Retry-After` fejlécet. |

## Gyakran feltett kérdések

**K: Kinyerhetek jelszóval védett PST fájlokat?**  
V: Igen. Add meg a jelszót a `Parser` objektum inicializálásakor, és a könyvtár a helyben dekódolja a fájlt.

**K: Támogatja a GroupDocs.Parser a streaminget Exchange szerverről?**  
V: Teljesen. Használd az `ExchangeClient` osztályt EWS vagy IMAP kapcsolathoz, és iterálj az üzeneteken anélkül, hogy az egész postafiókot letöltenéd.

**K: Hogyan kezeljem a nagy mellékleteket anélkül, hogy kimeríteném a memóriát?**  
V: Streameld a melléklet tartalmát közvetlenül egy fájlba vagy output streambe a `save()` metódus segítségével, ahelyett, hogy teljesen betöltenéd a memóriába.

**K: Van mód csak a olvasatlan e‑mail-ek kinyerésére?**  
V: Igen. Szűrd a postafiókot a megfelelő szűrővel (`IsRead = false`) az üzenetek iterálása előtt.

**K: Mi van, ha egy e‑mail beágyazott képeket tartalmaz a törzsben?**  
V: A könyvtár a beágyazott képeket külön melléklet objektumként kezeli; lekérheted őket, és szükség esetén visszaágyazhatod a HTML-be.

## További források

- [GroupDocs.Parser Java dokumentáció](https://docs.groupdocs.com/parser/java/)
- [GroupDocs.Parser Java API referencia](https://reference.groupdocs.com/parser/java/)
- [GroupDocs.Parser Java letöltése](https://releases.groupdocs.com/parser/java/)
- [GroupDocs.Parser fórum](https://forum.groupdocs.com/c/parser)
- [Ingyenes támogatás](https://forum.groupdocs.com/)
- [Ideiglenes licenc](https://purchase.groupdocs.com/temporary-license/)

## Összegzés

A GroupDocs.Parser használatával a kaotikus e‑mail archívumokat strukturált, kereshető adatokra alakíthatod néhány Java sor kóddal. Akár régi postafiókok migrálásáról, megfelelőségi irányítópultok építéséről vagy jegy létrehozás automatizálásáról van szó, ez a **java email parsing library** a teljesítményt, formátum lefedettséget és fejlesztőbarát API‑t biztosítja, amire szükséged van. Fedezd fel a linkelt útmutatókat konkrét kódmintákért, és kezdj el értéket kinyerni minden üzenetből még ma.

---

**Legutóbb frissítve:** 2026-06-17  
**Tesztelve:** GroupDocs.Parser for Java 23.12 (legújabb a írás időpontjában)  
**Szerző:** GroupDocs

## Kapcsolódó útmutatók

- [Hogyan nyerjünk ki szöveget e‑mail-ekből a GroupDocs.Parser Java használatával: Lépésről‑lépésre útmutató](/parser/java/email-parsing/extract-text-emails-groupdocs-parser-java/)
- [Hogyan nyerjünk ki e‑mail metaadatokat a GroupDocs.Parser Java‑val – Átfogó útmutató](/parser/java/metadata-extraction/extract-metadata-emails-groupdocs-parser-java/)
- [E‑mail mellékletek metaadatainak kinyerése és nyomtatása a GroupDocs.Parser for Java használatával](/parser/java/metadata-extraction/extract-print-email-attachments-metadata-groupdocs-parser-java/)