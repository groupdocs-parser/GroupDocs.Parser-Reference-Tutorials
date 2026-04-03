---
date: '2026-02-06'
description: เรียนรู้วิธีแสดงตัวอย่างไฟล์ Excel และแปลงไฟล์ xlsx เป็น png ด้วย GroupDocs.Parser
  สำหรับ Java การสอนนี้ครอบคลุมการตั้งค่า การดำเนินการ และการประยุกต์ใช้ในเชิงปฏิบัติ
keywords:
- GroupDocs.Parser
- Java
- Document Processing
title: วิธีแสดงตัวอย่างไฟล์ Excel ด้วย GroupDocs.Parser ใน Java
type: docs
url: /th/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# วิธีการแสดงตัวอย่างไฟล์ Excel ด้วย GroupDocs.Parser ใน Java

หากคุณกำลังมองหา **วิธีการแสดงตัวอย่าง Excel** แบบโปรแกรม คุณมาถูกที่แล้ว ในคู่มือนี้เราจะอธิบายการสร้างตัวอย่างภาพ (PNG) จากเวิร์กบุ๊ก `.xlsx` ด้วย GroupDocs.Parser สำหรับ Java—เหมาะสำหรับการสร้างภาพย่ออย่างรวดเร็ว, แชร์ภาพหน้าจอ, หรือสร้างฟีเจอร์แสดงตัวอย่างเอกสารในแอปพลิเคชันของคุณ

## คำตอบสั้น ๆ
- **“preview Excel” หมายถึงอะไร?** การสร้างไฟล์ภาพ (เช่น PNG) ที่แทนแต่ละหน้า worksheet.  
- **รูปแบบใดที่แนะนำ?** PNG ให้คุณภาพ loss‑less และทำงานได้ดีสำหรับภาพย่อบนเว็บ.  
- **ต้องมีลิขสิทธิ์หรือไม่?** ทดลองใช้ฟรีได้สำหรับการพัฒนา; ต้องมีลิขสิทธิ์เชิงพาณิชย์สำหรับการใช้งานจริง.  
- **สามารถเปลี่ยนความละเอียดของภาพได้หรือไม่?** ได้ — ปรับ DPI ใน `PreviewOptions`.  
- **สามารถแสดงตัวอย่างรูปแบบอื่นได้หรือไม่?** GroupDocs.Parser ยังรองรับ PDF, Word และหลายรูปแบบภาพอื่น ๆ.

## “วิธีการแสดงตัวอย่าง Excel” กับ GroupDocs.Parser คืออะไร?
GroupDocs.Parser อ่านเวิร์กบุ๊ก Excel, เรนเดอร์แต่ละชีตเป็นหน้าแบบภาพ, และให้คุณสตรีมหน้าดังกล่าวไปยังไฟล์ภาพ ซึ่งช่วยขจัดความจำเป็นในการใช้ Office interop หรือเครื่องแปลงของบุคคลที่สาม

## ทำไมต้องใช้ GroupDocs.Parser สำหรับการแสดงตัวอย่าง Excel?
- **ไม่ต้องติดตั้ง Office** – ทำงานได้บนสภาพแวดล้อม Java ฝั่งเซิร์ฟเวอร์ใดก็ได้.  
- **รองรับไฟล์ขนาดใหญ่** – สตรีมหน้าแบบหนึ่งต่อหนึ่ง, ทำให้การใช้หน่วยความจำน้อย.  
- **ผลลัพธ์คุณภาพสูง** – ควบคุม DPI, รูปแบบ, และตัวเลือกการเรนเดอร์.  
- **ความยืดหยุ่นข้ามรูปแบบ** – API เดียวกันทำงานกับ PDF, Word และอื่น ๆ อีกมากมาย.

## ข้อกำหนดเบื้องต้น
- **Java Development Kit** (8 +).  
- **IDE** เช่น IntelliJ IDEA หรือ Eclipse.  
- **GroupDocs.Parser for Java SDK** – ดาวน์โหลดจาก [here](https://releases.groupdocs.com/parser/java/).  
- **ไฟล์ Excel ตัวอย่าง** (`.xlsx`) ที่คุณต้องการแสดงตัวอย่าง.  
- **Maven หรือ Gradle** (ไม่บังคับ) สำหรับการจัดการ dependencies.

## นำเข้าแพ็กเกจ
การนำเข้าดังต่อไปนี้ทำให้คุณเข้าถึง parser, ตัวเลือกการแสดงตัวอย่าง, และยูทิลิตี้การจัดการสตรีม

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

## คู่มือขั้นตอนต่อขั้นตอนเพื่อสร้างตัวอย่างหน้า Spreadsheet

### ขั้นตอนที่ 1: เริ่มต้นอินสแตนซ์ Parser
สร้างอ็อบเจ็กต์ `Parser` ที่ชี้ไปยังเวิร์กบุ๊ก Excel ของคุณ บล็อก *try‑with‑resources* จะทำให้ parser ปิดโดยอัตโนมัติ

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **เคล็ดลับ:** ใช้เส้นทางแบบ absolute หรือกำหนดโฟลเดอร์ทรัพยากรเพื่อหลีกเลี่ยง `FileNotFoundException`.

### ขั้นตอนที่ 2: เตรียมตัวเลือกการแสดงตัวอย่างของคุณ
กำหนดวิธีการบันทึกแต่ละหน้า `ICreatePageStream` implementation จะคืนค่า `FileOutputStream` ใหม่สำหรับแต่ละ worksheet page

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

> ขั้นตอนนี้คือจุดที่คุณ **convert xlsx to png** — สตรีมจะเขียนข้อมูล PNG ลงดิสก์

### ขั้นตอนที่ 3: แนบ Delegate เพื่อจับข้อมูลการเรนเดอร์
หากต้องการรายละเอียดของแต่ละชีตที่เรนเดอร์ (เช่น ขนาด, ชื่อชีต) ให้ลงทะเบียน callback

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### ขั้นตอนที่ 4: ระบุรูปแบบเอาต์พุตและ DPI
เลือก PNG เป็นรูปแบบภาพและตั้งค่า DPI ที่สมดุลระหว่างคุณภาพและขนาดไฟล์

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> ปรับ DPI หากต้องการภาพย่อขนาดเล็กกว่า (เช่น 96) หรือการพิมพ์ความละเอียดสูง (เช่น 300)

### ขั้นตอนที่ 5: สร้างตัวอย่าง
เมื่อกำหนดค่าทั้งหมดแล้ว ให้เรียก `generatePreview` SDK จะวนลูปแต่ละ worksheet และเรียกสตรีมที่คุณให้ไว้

```java
parser.generatePreview(previewOptions);
```

### ขั้นตอนที่ 6: กำหนดเมธอดช่วย `getOutputPath()`
เมธอดนี้สร้างชื่อไฟล์ตามหมายเลขหน้า (ชีต) คุณสามารถปรับโครงสร้างโฟลเดอร์ได้ตามต้องการ

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **ข้อผิดพลาดทั่วไป:** ลืมสร้างโฟลเดอร์ `output` ล่วงหน้าจะทำให้เกิด `IOException`. สร้างโฟลเดอร์โดยโปรแกรมหรือให้แน่ใจว่ามีอยู่แล้ว

## ตัวอย่างทำงานเต็ม (แบบย่อ)

ด้านล่างเป็นเวอร์ชันกะทัดรัดที่เชื่อมส่วนต่าง ๆ เข้าด้วยกัน แสดง workflow **create excel page preview** ตั้งแต่เริ่มต้นจนจบ

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

รันสคริปต์นี้แล้วคุณจะพบไฟล์ `preview_page_1.png`, `preview_page_2.png`, … อยู่ในโฟลเดอร์ `output` — แต่ละไฟล์แทนชีตจากเวิร์กบุ๊ก Excel ดั้งเดิม

## ปัญหาที่พบบ่อย & วิธีแก้
| Issue | Cause | Fix |
|-------|-------|-----|
| **ไม่มีภาพถูกสร้าง** | `getOutputPath` คืนค่าไดเรกทอรีที่ไม่ถูกต้อง | ตรวจสอบให้แน่ใจว่าโฟลเดอร์เป้าหมายมีอยู่หรือสร้างด้วย `new File("output").mkdirs();` |
| **Out‑of‑memory error on huge files** | โหลดเวิร์กบุ๊กทั้งหมดในครั้งเดียว | ใช้วิธีสตรีมตามที่แสดงและประมวลผลหน้าแบบทีละหน้า |
| **Incorrect DPI** | ไม่ได้เรียก `setDpi` หรือตั้งค่าเป็นค่าเริ่มต้น (96) | เรียก `previewOptions.setDpi(yourDesiredValue);` ก่อน `generatePreview` |
| **Unsupported format** | พยายามแสดงตัวอย่างไฟล์ `.xlsx` ที่เสียหาย | ตรวจสอบไฟล์ด้วย Excel หรือใช้ `Parser.isSupported` ก่อนประมวลผล |

## คำถามที่พบบ่อย

**Q: ฉันสามารถสร้างตัวอย่างสำหรับ PDF และรูปภาพโดยใช้ GroupDocs.Parser ได้หรือไม่?**  
A: ได้, API เดียวกันทำงานกับ PDF, เอกสาร Word, และรูปแบบภาพหลายประเภท

**Q: จะเปลี่ยนรูปแบบภาพเอาต์พุตได้อย่างไร?**  
A: เรียก `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (หรือ `Gif`, `Bmp`, ฯลฯ)

**Q: ประสิทธิภาพเป็นปัญหากับเวิร์กบุ๊กขนาดใหญ่มากหรือไม่?**  
A: SDK สตรีมหน้า ทำให้การใช้หน่วยความจำน้อย. สำหรับไฟล์ขนาดมหาศาล ควรพิจารณาประมวลผลเป็นชุดแบบขนาน

**Q: จะจัดการข้อผิดพลาดระหว่างการสร้างตัวอย่างอย่างไร?**  
A: ห่อโค้ดด้วยบล็อก try‑catch (ตามตัวอย่าง) และบันทึกรายละเอียดข้อยกเว้น. หากไม่ใช้ try‑with‑resources ให้ปิดสตรีมในบล็อก `finally`

**Q: ไลบรารีต้องการให้ติดตั้ง Microsoft Office ไหม?**  
A: ไม่จำเป็น. GroupDocs.Parser เป็นโซลูชัน Java แท้ ๆ ทำงานบนแพลตฟอร์มใดก็ได้ที่รองรับ Java 8+

## สรุป
ตอนนี้คุณมีวิธีที่ครบถ้วนและพร้อมใช้งานในระดับ production สำหรับ **วิธีการแสดงตัวอย่าง Excel** เวิร์กบุ๊กและ **convert xlsx to png** ด้วย GroupDocs.Parser ปรับ DPI, โฟลเดอร์เอาต์พุต, หรือรูปแบบภาพให้ตรงกับความต้องการของโครงการของคุณ และนำสคริปต์นี้ไปผสานใน workflow การจัดการเอกสารที่ใหญ่ขึ้น

พร้อมก้าวต่อไปหรือยัง? สำรวจ [documentation](https://docs.groupdocs.com/parser/java/) อย่างเป็นทางการสำหรับตัวเลือกการเรนเดอร์ขั้นสูง, ไฟล์ที่ป้องกันด้วยรหัสผ่าน, และเทคนิคการประมวลผลเป็นชุด

---

**Last Updated:** 2026-02-06  
**Tested With:** GroupDocs.Parser 23.11 (latest at time of writing)  
**Author:** GroupDocs