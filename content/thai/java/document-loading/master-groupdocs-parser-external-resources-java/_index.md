---
date: '2025-12-29'
description: เรียนรู้วิธีดึงรูปภาพจากเอกสารและวิธีกรองทรัพยากรโดยใช้ GroupDocs.Parser
  สำหรับ Java คู่มือนี้ครอบคลุมการกำหนดค่า ตัวจัดการแบบกำหนดเอง และตัวอย่างเชิงปฏิบัติ
keywords:
- GroupDocs.Parser for Java
- external resource loading in Java
- custom handlers in GroupDocs
title: สกัดภาพจากเอกสารด้วย GroupDocs.Parser Java – คู่มือ
type: docs
url: /th/java/document-loading/master-groupdocs-parser-external-resources-java/
weight: 1
---

# ดึงรูปภาพจากเอกสารและกรองทรัพยากรด้วย GroupDocs.Parser Java

การดึงรูปภาพจากเอกสารเป็นความต้องการทั่วไปเมื่อสร้าง pipeline การประมวลผลเอกสาร ในบทเรียนนี้คุณจะได้ค้นพบ **วิธีดึงรูปภาพจากเอกสาร** ด้วย GroupDocs.Parser สำหรับ Java และคุณยังจะได้เรียนรู้ **วิธีกรองทรัพยากร** เพื่อให้โหลดเฉพาะไฟล์ที่คุณต้องการ เราจะอธิบายขั้นตอนการตั้งค่าห้องสมุด การสร้าง `ExternalResourceHandler` แบบกำหนดเอง และการใช้ตรรกะการกรองเพื่อให้แอปพลิเคชันของคุณทำงานได้เร็วและปลอดภัย

## คำตอบสั้น
- **GroupDocs.Parser ทำอะไร?** มันทำการแยกรูปแบบเอกสารหลากหลายและให้คุณเข้าถึงข้อความ รูปภาพ และทรัพยากรฝังอื่น ๆ  
- **ฉันสามารถข้ามรูปภาพที่ไม่ต้องการได้หรือไม่?** ได้ — โดยการทำ `ExternalResourceHandler` แบบกำหนดเอง คุณสามารถตัดสินใจได้ว่าจะโหลดทรัพยากรใด  
- **ต้องใช้เวอร์ชัน Maven ใด?** ใช้ GroupDocs.Parser Java 25.5 หรือใหม่กว่า  
- **ต้องมีลิขสิทธิ์หรือไม่?** ทดลองใช้ฟรีได้สำหรับการประเมิน; ต้องมีลิขสิทธิ์ถาวรสำหรับการใช้งานจริง  
- **วิธีนี้ปลอดภัยต่อการทำงานหลายเธรดหรือไม่?** วัตถุ Parser ไม่ได้แชร์ระหว่างเธรด; สร้างอินสแตนซ์ `Parser` ใหม่ต่อแต่ละเธรด

## “ดึงรูปภาพจากเอกสาร” คืออะไร?
เมื่อเอกสารมีรูปภาพ กราฟิก หรือสื่ออื่นฝังอยู่ “ดึงรูปภาพจากเอกสาร” หมายถึงการดึงไฟล์ไบนารีเหล่านั้นออกมาโดยอัตโนมัติเพื่อให้คุณสามารถเก็บ แสดง หรือประมวลผลต่อได้นอกไฟล์ต้นฉบับ

## ทำไมต้องกรองทรัพยากรขณะดึงรูปภาพ?
การกรองทรัพยากรช่วยให้คุณ:
- ลดการใช้หน่วยความจำโดยละเว้นไฟล์ขนาดใหญ่หรือไม่เกี่ยวข้อง  
- ปรับปรุงความปลอดภัยโดยป้องกันการโหลดเนื้อหาที่อาจเป็นอันตราย  
- เร่งความเร็วการประมวลผล โดยเฉพาะกับเอกสารขนาดใหญ่ที่มีออบเจ็กต์ฝังจำนวนมาก

## ข้อกำหนดเบื้องต้น

- **Java Development Kit (JDK)** – เวอร์ชัน 8 หรือสูงกว่า  
- **Maven** – สำหรับจัดการ dependencies  
- ความคุ้นเคยพื้นฐานกับ Java I/O และการจัดการข้อยกเว้น

## การตั้งค่า GroupDocs.Parser สำหรับ Java

เพิ่ม repository ของ GroupDocs และ dependency ของ parser ลงใน `pom.xml` ของคุณ:

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

หรือดาวน์โหลดเวอร์ชันล่าสุดจาก [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/)

### การจัดหาลิขสิทธิ์
- **Free Trial** – ทดลองใช้ฟีเจอร์หลักโดยไม่เสียค่าใช้จ่าย  
- **Temporary License** – ปลดล็อกฟังก์ชันเต็มระหว่างการประเมิน  
- **Purchased License** – จำเป็นสำหรับการใช้งานเชิงพาณิชย์

## วิธีกรองทรัพยากรขณะดึงรูปภาพ

### ขั้นตอน 1: สร้าง handler แบบกำหนดเอง
กำหนดคลาสที่สืบทอดจาก `ExternalResourceHandler` ภายในเมธอด `onLoading` คุณจะตัดสินใจว่าจะเก็บทรัพยากรใด

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

### ขั้นตอน 2: ตั้งค่า `ParserSettings` พร้อม handler
ส่งอินสแตนซ์ `Handler` ของคุณไปยัง `ParserSettings` และใช้เมื่อเปิดเอกสาร

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

### ขั้นตอน 3: ปรับแต่งตรรกะการกรอง
หากต้องการกฎที่ซับซ้อนมากขึ้น — เช่น การกรองตามขนาดรูปภาพ รูปแบบ หรือรูปแบบ URI — ให้ขยายเมธอด `onLoading` ตามต้องการ:

```java
@Override
public void onLoading(ExternalResourceLoadingArgs args) {
    if (!args.getUri().endsWith("installation.png")) {
        args.setSkipped(true);
    }
}
```

## การประยุกต์ใช้งานจริง

1. **Document Management Systems** – ดึงเฉพาะรูปภาพที่จำเป็นจากสัญญาที่สแกนเพื่อสร้าง thumbnail  
2. **Data Extraction Services** – ข้ามกราฟิกตกแต่งและโฟกัสที่แผนภูมิที่มีข้อมูลสำคัญ  
3. **Web Scraping Tools** – กรอง pixel ติดตามขณะดึงสื่อที่มีความหมายจากเอกสารแบบ HTML

## พิจารณาด้านประสิทธิภาพ
- **กรองตั้งแต่ต้น**: ใช้ handler ของคุณก่อนวนลูปทรัพยากรเพื่อหลีกเลี่ยงการโหลดข้อมูลที่ไม่ต้องการเข้าสู่หน่วยความจำ  
- **ปล่อยทรัพยากรทันท่วงที**: ใช้ try‑with‑resources (`try (Parser parser = …)`) เพื่อคืนทรัพยากรเนทีฟ  
- **การประมวลผลแบบอะซิง**: สำหรับชุดข้อมูลขนาดใหญ่ ให้ประมวลผลเอกสารด้วย parallel streams โดยให้แต่ละอินสแตนซ์ `Parser` ทำงานในเธรดเดียวเท่านั้น

## ปัญหาที่พบบ่อยและวิธีแก้
| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|--------|--------|
| ไม่พบรูปภาพ | Handler ข้ามทรัพยากทั้งหมดโดยไม่ได้ตั้งใจ | ตรวจสอบเงื่อนไข `if` และให้แน่ใจว่า `args.setSkipped(true)` ถูกเรียกเฉพาะ URI ที่ไม่ต้องการ |
| `IOException` กับไฟล์ขนาดใหญ่ | หน่วยความจำ heap ไม่พอ | เพิ่ม heap ของ JVM (`-Xmx2g`) หรือประมวลผลหน้าเป็นส่วนย่อย |
| ลิขสิทธิ์ไม่ถูกต้อง | ใช้ DLL trial กับโค้ด production | ตั้งค่าไฟล์ลิขสิทธิ์ที่ถูกต้องด้วย `License.setLicense("path/to/license")` |

## คำถามที่พบบ่อย

**Q: จุดประสงค์หลักของการใช้ `ExternalResourceHandler` แบบกำหนดเองคืออะไร?**  
A: ช่วยให้คุณควบคุมว่าทรัพยากรภายนอกใดจะถูกโหลด เพิ่มความปลอดภัยและประสิทธิภาพโดยกรองไฟล์ที่ไม่จำเป็นออก

**Q: สามารถใช้ GroupDocs.Parser สำหรับ Java ได้โดยไม่มีลิขสิทธิ์หรือไม่?**  
A: ใช่ มีรุ่นทดลองฟรีให้ใช้ แต่บางฟีเจอร์ขั้นสูงอาจจำกัดจนกว่าจะได้ลิขสิทธิ์ชั่วคราวหรือถาวร

**Q: จะจัดการข้อยกเว้นระหว่างการแยกข้อมูลด้วย GroupDocs.Parser อย่างไร?**  
A: ห่อการเรียกเมธอดการแยกด้วยบล็อก try‑catch สำหรับ `IOException` และข้อยกเว้นเฉพาะอื่น ๆ เพื่อจัดการข้อผิดพลาดอย่างราบรื่น

**Q: ข้อผิดพลาดทั่วไปเมื่อกรองทรัพยากรคืออะไร?**  
A: การตรวจสอบ URI ผิดพลาดอาจทำให้ข้ามไฟล์ที่ต้องการ ใช้ logging หรือ breakpoint เพื่อตรวจสอบเงื่อนไขของคุณ

**Q: สามารถแยกเอกสารที่ไม่ใช่ HTML ด้วย GroupDocs.Parser for Java ได้หรือไม่?**  
A: แน่นอน — GroupDocs.Parser รองรับ PDF, Word, Excel, PowerPoint และรูปแบบอื่น ๆ อีกมากมาย

## ขั้นตอนต่อไป
สำรวจไลบรารีให้ลึกขึ้นโดยดูที่ [API Reference](https://reference.groupdocs.com/parser/java) หรือทดลองตั้งค่าเพิ่มเติม เช่น `ParserSettings.setDetectTables(true)` เพื่อดึงตาราง

---

**อัปเดตล่าสุด:** 2025-12-29  
**ทดสอบกับ:** GroupDocs.Parser 25.5 for Java  
**ผู้เขียน:** GroupDocs  

**แหล่งข้อมูล**  
- **Documentation:** [GroupDocs.Parser Documentation](https://docs.groupdocs.com/parser/java/)  
- **API Reference:** [API Details](https://reference.groupdocs.com/parser/java)  
- **Downloads:** [Latest Versions](https://releases.groupdocs.com/parser/java/)