---
date: '2025-12-29'
description: เรียนรู้วิธีดึงรูปภาพจากอีเมลและไฟล์ .msg ด้วย GroupDocs.Parser สำหรับ
  Java รวมขั้นตอนการตั้งค่า โค้ด และเคล็ดลับจากโลกจริง
keywords:
- extract images from emails
- GroupDocs.Parser for Java
- image extraction email
title: ดึงรูปภาพจากอีเมลด้วย GroupDocs.Parser สำหรับ Java
type: docs
url: /th/java/email-parsing/extract-images-emails-groupdocs-parser-java/
weight: 1
---

# ดึงรูปภาพจากอีเมลด้วย GroupDocs.Parser สำหรับ Java

การดึงรูปภาพจากข้อความอีเมลเป็นความต้องการทั่วไปสำหรับนักพัฒนาที่ต้องการอัตโนมัติการจัดการข้อมูล, ปรับปรุงกระบวนการสนับสนุนลูกค้า, หรือสร้างคลังข้อมูลที่มีเนื้อหามาก. ในบทแนะนำนี้คุณจะได้เรียนรู้วิธี **ดึงรูปภาพจากอีเมล** ไฟล์—โดยเฉพาะไฟล์ `.msg`—โดยใช้ไลบรารี GroupDocs.Parser ที่ทรงพลังสำหรับ Java.

## คำตอบอย่างรวดเร็ว
- **GroupDocs.Parser ทำอะไร?** มันทำการแยกรูปแบบเอกสารหลายประเภท, รวมถึง Outlook `.msg` และ `.eml`, และให้การเข้าถึงทรัพยากรที่ฝังอยู่เช่นรูปภาพได้อย่างง่ายดาย.  
- **รูปแบบภาพใดที่ใช้สำหรับการดึงออก?** PNG, เนื่องจากรักษาคุณภาพและได้รับการสนับสนุนอย่างกว้างขวาง.  
- **ฉันต้องการไลเซนส์หรือไม่?** การทดลองใช้ฟรีทำงานสำหรับการทดสอบ; จำเป็นต้องมีไลเซนส์เต็มสำหรับการใช้งานจริง.  
- **ฉันสามารถประมวลผลหลายอีเมลพร้อมกันได้หรือไม่?** ได้—การประมวลผลเป็นชุดสามารถทำได้โดยวนลูปไฟล์.  
- **ต้องการเวอร์ชัน Java ใด?** Java 8 หรือใหม่กว่า.

## “ดึงรูปภาพจากอีเมล” คืออะไร?
เมื่ออีเมลมีรูปภาพฝังอยู่—เช่นภาพหน้าจอ, ภาพสินค้า, หรือโลโก้—สินทรัพย์ภาพเหล่านั้นจะถูกเก็บไว้ในไฟล์ข้อความ. **ดึงรูปภาพจากอีเมล** หมายถึงการดึงวัตถุไบนารีเหล่านั้นออกจากคอนเทนเนอร์ `.msg` หรือ `.eml` อย่างโปรแกรมมิ่งเพื่อให้สามารถบันทึก, วิเคราะห์, หรือแสดงในที่อื่นได้.

## ทำไมต้องใช้ GroupDocs.Parser สำหรับงานนี้?
- **การสนับสนุนรูปแบบที่กว้าง** – จัดการทั้งไฟล์ `.msg` และ `.eml` โดยไม่ต้องใช้ปลั๊กอินเพิ่มเติม.  
- **API ที่เรียบง่าย** – วิธีเดียว (`getImages()`) จะคืนค่าพื้นที่รูปภาพทั้งหมด.  
- **ประสิทธิภาพที่ปรับแต่ง** – ออกแบบมาสำหรับไฟล์ขนาดใหญ่และสถานการณ์ปริมาณสูง.  
- **ข้ามแพลตฟอร์ม** – ทำงานบนระบบปฏิบัติการใดก็ได้ที่รัน Java.

## ข้อกำหนดเบื้องต้น
- **GroupDocs.Parser for Java** ≥ 25.5 (แนะนำให้ใช้รุ่นล่าสุด).  
- Java Development Kit (JDK) 8 หรือใหม่กว่า.  
- IDE เช่น IntelliJ IDEA หรือ Eclipse.  
- ความคุ้นเคยพื้นฐานกับไวยากรณ์ Java และการสร้างด้วย Maven/Gradle.

## การตั้งค่า GroupDocs.Parser สำหรับ Java

### การพึ่งพา Maven (แนะนำ)
Add the repository and dependency to your `pom.xml`:

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

### ดาวน์โหลดโดยตรง (หากคุณต้องการตั้งค่าด้วยตนเอง)
คุณยังสามารถดาวน์โหลดไลบรารีจากหน้าปล่อยอย่างเป็นทางการ: [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

### การรับไลเซนส์
- **ทดลองใช้ฟรี** – ประเมิน API โดยไม่มีค่าใช้จ่าย.  
- **ไลเซนส์ชั่วคราว** – ขยายระยะเวลาการทดลองใช้หากต้องการ.  
- **ไลเซนส์เต็ม** – ซื้อเพื่อการใช้งานผลิตภัณฑ์โดยไม่มีข้อจำกัด.

### การเริ่มต้นและตั้งค่าเบื้องต้น
Below is a minimal Java program that opens an email file and prepares it for image extraction:

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.data.PageImageArea;

public class EmailImageExtractor {
    public static void main(String[] args) {
        String inputFilePath = "path/to/your/sample.msg";
        
        try (Parser parser = new Parser(inputFilePath)) {
            Iterable<PageImageArea> images = parser.getImages();
            // Further processing will follow...
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## คู่มือการดำเนินการ

### วิธีดึงรูปภาพจากอีเมลโดยใช้ GroupDocs.Parser?

#### ขั้นตอน 1: กำหนดค่าตัวเลือกการดึงรูปภาพ  
Set the desired output format (PNG) before you start saving files:

```java
import com.groupdocs.parser.options.ImageOptions;
import com.groupdocs.parser.options.ImageFormat;

ImageOptions options = new ImageOptions(ImageFormat.Png);
```

#### ขั้นตอน 2: วนลูปผ่านรูปภาพและบันทึก  
The following loop saves each discovered image to a target folder, naming them sequentially:

```java
int imageNumber = 0;

for (PageImageArea image : parser.getImages()) {
    String outputFilePath = "YOUR_OUTPUT_DIRECTORY/" + imageNumber + ".png";
    
    // Save each image using the configured options
    image.save(outputFilePath, options);
    imageNumber++;
}
```

#### ขั้นตอน 3: ตรวจสอบผลลัพธ์  
After the program finishes, check `YOUR_OUTPUT_DIRECTORY`. You should see a series of PNG files (`0.png`, `1.png`, …) representing every image that was embedded in the original email.

หลังจากโปรแกรมทำงานเสร็จ, ตรวจสอบ `YOUR_OUTPUT_DIRECTORY`. คุณควรเห็นชุดไฟล์ PNG (`0.png`, `1.png`, …) ที่แสดงรูปภาพทุกภาพที่ฝังอยู่ในอีเมลต้นฉบับ.

### วิธีดึงรูปภาพจากไฟล์ msg?
โค้ดเดียวกันทำงานกับไฟล์ `.msg` เนื่องจาก GroupDocs.Parser ตรวจจับรูปแบบโดยอัตโนมัติ. เพียงชี้ `inputFilePath` ไปยังไฟล์ `.msg` แล้วรันลูปการดึงเดียวกัน.

### วิธีแยกไฟล์ msg ด้วย Java?
หากคุณต้องการอ่านส่วนอื่นของข้อความ (หัวเรื่อง, เนื้อหา, ไฟล์แนบ) ร่วมกับรูปภาพ, คุณสามารถใช้เมธอด `Parser` เพิ่มเติมเช่น `getDocumentInfo()`, `getAttachments()`, และ `getText()`. การดึงรูปภาพที่แสดงที่นี่เป็นส่วนสำคัญของกระบวนการทำงาน **parse msg files java** ที่กว้างขึ้น.

## เคล็ดลับการแก้ไขปัญหา
- **ข้อผิดพลาดเส้นทางไฟล์:** ตรวจสอบให้แน่ใจว่าไฟล์ `.msg` อินพุตและไดเรกทอรีเอาต์พุตมีอยู่และเข้าถึงได้.  
- **เวอร์ชันไม่ตรงกัน:** ตรวจสอบให้แน่ใจว่าเวอร์ชันของการพึ่งพา Maven ตรงกับไลบรารีที่คุณดาวน์โหลด.  
- **ปัญหาการอนุญาต:** รัน IDE หรือบรรทัดคำสั่งของคุณด้วยสิทธิ์การอ่าน/เขียนที่เพียงพอ, โดยเฉพาะบน Windows ที่การอนุญาตโฟลเดอร์อาจจำกัด.

## การประยุกต์ใช้งานจริง
1. **การอัตโนมัติการสนับสนุนลูกค้า** – ดึงภาพหน้าจอจากอีเมลสนับสนุนที่เข้ามาเพื่อการวิเคราะห์อย่างรวดเร็ว.  
2. **การวิเคราะห์การตลาด** – เก็บรวบรวมสินทรัพย์ภาพจากอีเมลแคมเปญเพื่อวัดความสอดคล้องของแบรนด์.  
3. **ระบบจัดการเอกสาร** – เพิ่มข้อมูลเมตาดาต้าโดยแนบรูปภาพที่ดึงออกไปยังบันทึกที่เกี่ยวข้อง.

## พิจารณาด้านประสิทธิภาพ
- **การจัดการหน่วยความจำ:** ประมวลผลกล่องเมลขนาดใหญ่เป็นชุดเพื่อหลีกเลี่ยงการใช้ heap มากเกินไป.  
- **การประมวลผลแบบอะซิงโครนัส:** ใช้ `CompletableFuture` ของ Java หรือ thread pool เพื่อทำการดึงแบบขนานเมื่อจัดการไฟล์จำนวนมาก.  
- **อัปเดตอยู่เสมอ:** อัปเกรดเป็นรุ่นล่าสุดของ GroupDocs.Parser อย่างสม่ำเสมอเพื่อรับประโยชน์จากการปรับปรุงประสิทธิภาพและการแก้ไขบั๊ก.

## สรุป
ตอนนี้คุณมีวิธีการที่ครบถ้วนและพร้อมใช้งานในสภาพแวดล้อมการผลิตเพื่อ **ดึงรูปภาพจากอีเมล** ไฟล์โดยใช้ GroupDocs.Parser สำหรับ Java. ด้วยการกำหนดค่า `ImageOptions`, วนลูปผ่านอ็อบเจ็กต์ `PageImageArea`, และบันทึกรูปภาพแต่ละภาพเป็น PNG, คุณสามารถอัตโนมัติกระบวนการทำงานหลากหลาย—from การจัดการตั๋วสนับสนุนถึงการจัดการสินทรัพย์การตลาด. อย่าลังเลที่จะขยายตัวอย่างนี้โดยเพิ่มการดึงข้อความ, การจัดการไฟล์แนบ, หรือการประมวลผลเป็นชุดเพื่อให้ตรงกับความต้องการของโครงการของคุณ.

## คำถามที่พบบ่อย

**ถาม: ฉันจะจัดการกับอีเมลที่มีไฟล์แนบเข้ารหัสอย่างไร?**  
ตอบ: GroupDocs.Parser ไม่ทำการถอดรหัสเนื้อหาที่เข้ารหัส; คุณต้องถอดรหัสไฟล์แนบล่วงหน้าหรือได้รับข้อมูลประจำตัวที่จำเป็น.

**ถาม: GroupDocs.Parser สามารถดึงรูปภาพจากรูปแบบอีเมลทั้งหมดได้หรือไม่?**  
ตอบ: รองรับรูปแบบที่พบบ่อยที่สุด, รวมถึง `.msg` และ `.eml`. ดูเอกสารอย่างเป็นทางการสำหรับรายการความเข้ากันได้ทั้งหมด.

**ถาม: ความต้องการระบบสำหรับการรัน GroupDocs.Parser คืออะไร?**  
ตอบ: ต้องการ Java 8 หรือใหม่กว่า, พร้อมหน่วยความจำเพียงพอเพื่อเก็บไฟล์อีเมลในหน่วยความจำ (โดยทั่วไป 256 MB สำหรับข้อความโดยเฉลี่ย).

**ถาม: ฉันจะปรับปรุงความเร็วการดึงข้อมูลสำหรับอีเมลหลายพันฉบับได้อย่างไร?**  
ตอบ: ใช้การประมวลผลเป็นชุด, จำกัดจำนวนเธรดพร้อมกันให้ตรงกับจำนวนคอร์ของ CPU, และใช้ `Parser` อินสแตนซ์เดียวซ้ำเมื่อเป็นไปได้.

**ถาม: ฉันจะหาโค้ดตัวอย่างเพิ่มเติมได้จากที่ไหน?**  
ตอบ: เยี่ยมชม [GroupDocs GitHub repository](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java) เพื่อดูตัวอย่างเพิ่มเติมและการมีส่วนร่วมของชุมชน.

**อัปเดตล่าสุด:** 2025-12-29  
**ทดสอบกับ:** GroupDocs.Parser 25.5 for Java  
**ผู้เขียน:** GroupDocs  

## แหล่งข้อมูล

- **เอกสาร:** [GroupDocs Parser Java Docs](https://docs.groupdocs.com/parser/java/)  
- **อ้างอิง API:** [GroupDocs API Documentation](https://reference.groupdocs.com/parser/java)  
- **ดาวน์โหลด:** [Get the Latest Version](https://releases.groupdocs.com/parser/java/)  
- **GitHub:** [Explore on GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)  
- **สนับสนุนฟรี:** [Join GroupDocs Forum](https://forum.groupdocs.com/c/parser)  
- **ไลเซนส์ชั่วคราว:** [Request a Temporary License](https://purchase.groupdocs.com/temporary-license/)