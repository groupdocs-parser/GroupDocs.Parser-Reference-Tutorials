---
date: '2026-01-27'
description: เรียนรู้วิธีดึงไฟล์แนบจากไฟล์ msg และพิมพ์ข้อมูลเมตาของไฟล์เหล่านั้นโดยใช้
  GroupDocs.Parser สำหรับ Java คู่มือขั้นตอนต่อขั้นตอนนี้แสดงวิธีดึงไฟล์แนบ, แยกวิเคราะห์ไฟล์ msg
  ด้วย Java, และจัดการข้อมูลเมตาอย่างมีประสิทธิภาพ
keywords:
- GroupDocs.Parser for Java
- email attachment extraction
- metadata printing
title: ดึงไฟล์แนบจากไฟล์ msg ด้วย GroupDocs.Parser สำหรับ Java
type: docs
url: /th/java/metadata-extraction/extract-print-email-attachments-metadata-groupdocs-parser-java/
weight: 1
---

# ดึงไฟล์แนบจาก msg ด้วย GroupDocs.Parser สำหรับ Java

การจัดการไฟล์แนบของอีเมลโดยโปรแกรมเป็นความต้องการทั่วไปสำหรับนักพัฒนา Java ที่ทำงานกับการเก็บถาวรอัตโนมัติ, การสแกนความปลอดภัย, หรือสายงานการสกัดข้อมูล ในบทเรียนนี้คุณจะได้เรียนรู้ **วิธีดึงไฟล์แนบจาก msg** ไฟล์, พิมพ์เมตาดาต้า, และเข้าใจว่าทำไมวิธีนี้จึงมีคุณค่าสำหรับโครงการในโลกจริง

## คำตอบด่วน
- **ควรใช้ไลบรารีอะไร?** GroupDocs.Parser for Java.  
- **ฉันสามารถดึงไฟล์แนบจากไฟล์ .msg ได้หรือไม่?** ได้, API ให้การเข้าถึงโดยตรงกับแต่ละไฟล์แนบ.  
- **ต้องการไลเซนส์หรือไม่?** รุ่นทดลองใช้ได้สำหรับการประเมิน; ต้องมีไลเซนส์เต็มสำหรับการใช้งานจริง.  
- **รองรับเวอร์ชัน Java ใด?** Java 8 หรือสูงกว่า.  
- **สามารถประมวลผลแบบกลุ่มได้หรือไม่?** แน่นอน – ผสานโค้ดตัวอย่างกับลูปหรือ parallel streams.  

## “ดึงไฟล์แนบจาก msg” คืออะไร?
เมื่อคุณได้รับไฟล์ Outlook `.msg` เนื้อหาอีเมลและไฟล์แนบจะถูกเก็บไว้ด้วยกัน “ดึงไฟล์แนบจาก msg” หมายถึงการแยกไฟล์แนะแต่ละไฟล์โดยโปรแกรมเพื่อให้คุณสามารถเก็บ, วิเคราะห์, หรือแปลงได้อย่างอิสระ

## ทำไมต้องใช้ GroupDocs.Parser สำหรับ Java?
- **รองรับรูปแบบที่แข็งแกร่ง** – จัดการกับ `.msg`, `.eml`, และรูปแบบอีเมลอื่น ๆ มากมาย.  
- **เข้าถึงเมตาดาต้า** – ดึงเส้นทางไฟล์, ขนาด, และแอตทริบิวต์ที่กำหนดเองโดยไม่ต้องพาร์สด้วยตนเอง.  
- **API ที่ง่าย** – ต้องการโค้ดน้อยที่สุดในการเปิดข้อความ, วนลูปไฟล์แนบ, และอ่านเนื้อหา.  
- **เน้นประสิทธิภาพ** – ใช้การสตรีมและ try‑with‑resources เพื่อลดการใช้หน่วยความจำ.  

## ข้อกำหนดเบื้องต้น
- **Java Development Kit (JDK):** เวอร์ชัน 8 หรือใหม่กว่า.  
- **IDE:** IntelliJ IDEA, Eclipse, หรือเครื่องมือแก้ไขที่รองรับ Java ใด ๆ.  
- **ไลบรารี GroupDocs.Parser:** เพิ่มผ่าน Maven หรือการใส่ JAR ด้วยตนเอง (ดูด้านล่าง).  

## การตั้งค่า GroupDocs.Parser สำหรับ Java

### การตั้งค่า Maven
เพิ่มการกำหนดค่าต่อไปนี้ในไฟล์ `pom.xml` ของคุณเพื่อรวม GroupDocs.Parser ผ่าน Maven:

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

### ดาวน์โหลดโดยตรง
หรือคุณสามารถดาวน์โหลดเวอร์ชันล่าสุดจาก [หน้า releases ของ GroupDocs.Parser for Java](https://releases.groupdocs.com/parser/java/). เพิ่มไฟล์ JAR ไปยัง classpath ของโปรเจกต์ของคุณด้วยตนเอง.

#### การรับไลเซนส์
GroupDocs มีตัวเลือกไลเซนส์หลายแบบ:
- **Free Trial:** การประเมินคุณสมบัติที่จำกัด.  
- **Temporary License:** การเข้าถึงเต็มรูปแบบในช่วงระยะเวลาประเมินสั้น.  
- **Commercial License:** จำเป็นสำหรับการใช้งานในสภาพแวดล้อมการผลิต.  

ใส่ไฟล์ไลเซนส์ที่ได้รับตามที่อธิบายในเอกสารอย่างเป็นทางการเพื่อเปิดใช้งานคุณสมบัติทั้งหมด.

### การเริ่มต้นพื้นฐาน
นี่คือตัวอย่างขั้นต่ำที่พิสูจน์ว่ามีการอ้างอิงไลบรารีอย่างถูกต้อง:

```java
import com.groupdocs.parser.Parser;

public class SetupExample {
    public static void main(String[] args) {
        // Initialize the Parser object with an email file path.
        try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY/sample.msg")) {
            System.out.println("GroupDocs.Parser is set up successfully!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

เมื่อ parser พร้อมแล้ว, เรามาเข้าสู่ภารกิจหลัก: **วิธีดึงไฟล์แนบจาก msg** และพิมพ์เมตาดาต้าของมัน.

## วิธีดึงไฟล์แนบจาก msg ด้วย GroupDocs.Parser?

### ขั้นตอนที่ 1: เริ่มต้นอ็อบเจ็กต์ Parser
สร้างอินสแตนซ์ `Parser` ที่ชี้ไปยังไฟล์ `.msg` ที่คุณต้องการประมวลผล:

```java
try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY/sample.msg")) {
    // Proceed with attachment extraction.
}
```

### ขั้นตอนที่ 2: ดึงไฟล์แนบ
ใช้ container API เพื่อดึงไฟล์แนบทั้งหมดที่ฝังอยู่ในอีเมล:

```java
Iterable<ContainerItem> attachments = parser.getContainer();
if (attachments == null) {
    System.out.println("No attachments found.");
    return;
}

for (ContainerItem item : attachments) {
    // Continue to parse each attachment.
}
```

### ขั้นตอนที่ 3: พาร์สไฟล์แนบแต่ละไฟล์ (java parse email attachments)
สำหรับแต่ละ `ContainerItem` ให้เปิดอินสแตนซ์ parser แยกเฉพาะ. สิ่งนี้ทำให้คุณสามารถอ่านเนื้อหาของไฟล์แนบได้หากเป็นรูปแบบข้อความ:

```java
try (Parser attachmentParser = item.openParser()) {
    try (TextReader reader = attachmentParser.getText()) {
        String attachmentText = reader == null ? "No text" : reader.readToEnd();
        // Handle or process the extracted text as needed.
    }
} catch (UnsupportedDocumentFormatException ex) {
    System.out.println("Unsupported document format.");
}
```

### ขั้นตอนที่ 4: พิมพ์เมตาดาต้าไฟล์แนบ
เมื่อคุณมีอ็อบเจ็กต์ไฟล์แนบแต่ละอันแล้ว, คุณสามารถแสดงเมตาดาต้าของมัน—เส้นทางไฟล์, ขนาด, และแอตทริบิวต์ที่กำหนดเองใด ๆ:

```java
for (ContainerItem item : attachments) {
    System.out.println("File Path: " + item.getFilePath());

    // Proceed to retrieve metadata.
}
```

```java
for (MetadataItem metadata : item.getMetadata()) {
    System.out.println(String.format("%s: %s", metadata.getName(), metadata.getValue()));
}
```

## ปัญหาที่พบบ่อยและวิธีแก้
- **รูปแบบที่ไม่รองรับ:** อัปเกรดเป็นเวอร์ชันล่าสุดของ GroupDocs.Parser หากคุณเจอ `UnsupportedDocumentFormatException`.  
- **ไฟล์แนบเป็น null:** ตรวจสอบว่าไฟล์ `.msg` ต้นทางมีไฟล์แนบจริงหรือไม่; บางข้อความอาจมีแค่เนื้อหาเท่านั้น.  
- **การใช้หน่วยความจำ:** เมื่อประมวลผลกล่องเมลขนาดใหญ่, จัดการไฟล์แนบเป็นชุดและปิด parser อย่างรวดเร็ว (รูปแบบ try‑with‑resources ช่วยได้แล้ว).  

## การประยุกต์ใช้งานจริง
การดึงและพิมพ์เมตาดาต้าไฟล์แนบมีประโยชน์สำหรับ:
1. **Data Archiving:** เก็บไฟล์แนบพร้อมเมตาดาต้าสำหรับการตรวจสอบตามข้อกำหนด.  
2. **Email Filtering:** ส่งต่อข้อความโดยอัตโนมัติตามประเภทหรือขนาดของไฟล์แนบ.  
3. **Security Scanning:** ส่งเมตาดาต้าเข้าสู่สายงานตรวจจับมัลแวร์ก่อนการตรวจสอบเนื้อหาอย่างละเอียด.  

## เคล็ดลับด้านประสิทธิภาพ
- **การจัดการทรัพยากร:** ใช้ try‑with‑resources เสมอเพื่อปล่อย native handles.  
- **การประมวลผลเป็นชุด:** ประมวลผลจำนวนอีเมลที่จำกัดต่อเธรดเพื่อให้การใช้หน่วยความจำคาดเดาได้.  
- **การทำงานแบบขนาน:** ใช้ `ExecutorService` ของ Java เพื่อพาร์สไฟล์ `.msg` หลายไฟล์พร้อมกัน.  

## คำถามที่พบบ่อย

**Q: ฉันจะจัดการไฟล์ .msg จำนวนมากอย่างมีประสิทธิภาพได้อย่างไร?**  
A: ผสานโค้ดตัวอย่างกับ thread pool (เช่น `Executors.newFixedThreadPool`) และประมวลผลแต่ละไฟล์ในงานของมันเอง. จำไว้ว่าให้ parser มีอายุสั้นเพื่อหลีกเลี่ยงการรั่วไหลของหน่วยความจำ.

**Q: ฉันสามารถดึงไฟล์แนบจากอีเมลที่เข้ารหัสหรือป้องกันด้วยรหัสผ่านได้หรือไม่?**  
A: GroupDocs.Parser รองรับไฟล์ `.msg` ที่เข้ารหัสเมื่อคุณให้รหัสผ่านที่ถูกต้องผ่านการ overload ของคอนสตรัคเตอร์ `Parser`.

**Q: มีฟิลด์เมตาดาต้าอะไรบ้างที่พร้อมใช้งานสำหรับไฟล์แนบแต่ละไฟล์?**  
A: ฟิลด์ทั่วไปได้แก่ `FilePath`, `Size`, `CreationTime`, และคุณสมบัติที่กำหนดเองที่ Outlook เก็บไว้ (เช่น `ContentId`).

**Q: มีวิธีกรองไฟล์แนบตามประเภทไฟล์ก่อนพาร์สหรือไม่?**  
A: มี, ตรวจสอบ `item.getFilePath()` หรือ `metadata.getName()` เพื่อดูส่วนขยายไฟล์และข้ามประเภทที่ไม่ต้องการ.

**Q: ไลบรารีทำงานบนแพลตฟอร์มที่ไม่ใช่ Windows ได้หรือไม่?**  
A: GroupDocs.Parser เป็นแบบข้ามแพลตฟอร์ม; มันทำงานบน OS ใดก็ได้ที่รองรับ Java 8+.

## สรุป
ตอนนี้คุณมีเวิร์กโฟลว์ที่ครบถ้วนและพร้อมสำหรับการผลิตเพื่อ **ดึงไฟล์แนบจาก msg** และพิมพ์เมตาดาต้าโดยใช้ GroupDocs.Parser สำหรับ Java. พื้นฐานนี้ทำให้คุณสร้างโซลูชันที่หลากหลาย—สายงานการเก็บถาวร, ตัวสแกนความปลอดภัย, หรือโปรเซสเซอร์อีเมลแบบกำหนดเอง—โดยรักษาโค้ดให้สะอาดและมีประสิทธิภาพ.

สำรวจความสามารถเพิ่มเติม เช่น การสกัดข้อความเต็ม, การพาร์สข้อมูลโครงสร้าง, หรือการแปลงไฟล์แนบเป็นรูปแบบอื่น. [เอกสาร GroupDocs](https://docs.groupdocs.com/parser/java/) มีตัวอย่างและอ้างอิง API ที่ลึกกว่าเพื่อช่วยคุณต่อยอดบทเรียนนี้ต่อไป.

---

**อัปเดตล่าสุด:** 2026-01-27  
**ทดสอบด้วย:** GroupDocs.Parser 25.5  
**ผู้เขียน:** GroupDocs