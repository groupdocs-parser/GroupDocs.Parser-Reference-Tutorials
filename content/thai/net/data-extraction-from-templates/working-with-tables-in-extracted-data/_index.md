---
title: การทำงานกับตารางในข้อมูลที่แยกออกมา
linktitle: การทำงานกับตารางในข้อมูลที่แยกออกมา
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกข้อมูลตารางออกจากเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET แยกวิเคราะห์เนื้อหาที่มีโครงสร้างอย่างมีประสิทธิภาพด้วยเทมเพลตที่กำหนดไว้ล่วงหน้า
weight: 12
url: /th/net/data-extraction-from-templates/working-with-tables-in-extracted-data/
type: docs
---
# การทำงานกับตารางในข้อมูลที่แยกออกมา

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกข้อมูลจากตารางในเอกสาร GroupDocs.Parser เป็นเครื่องมืออันทรงพลังที่ช่วยให้นักพัฒนาสามารถแยกวิเคราะห์และแยกข้อความ ข้อมูลเมตา และเนื้อหาที่มีโครงสร้างจากไฟล์รูปแบบต่างๆ เช่น PDF, DOCX, XLSX และอื่นๆ โดยเฉพาะอย่างยิ่ง เราจะมุ่งเน้นไปที่การแยกข้อมูลตารางอย่างมีประสิทธิภาพโดยใช้เทมเพลตที่กำหนดไว้ล่วงหน้า
## ข้อกำหนดเบื้องต้น
ก่อนที่คุณจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
- ติดตั้ง Visual Studio บนเครื่องของคุณแล้ว
- ความเข้าใจพื้นฐานเกี่ยวกับกรอบงาน C# และ .NET
- ติดตั้งไลบรารี GroupDocs.Parser ผ่านตัวจัดการแพ็คเกจ NuGet

## นำเข้าเนมสเปซ
เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นสำหรับการทำงานกับ GroupDocs.Parser และฟังก์ชันที่เกี่ยวข้อง
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## ขั้นตอนที่ 1: สร้างเทมเพลตตาราง
หากต้องการแยกข้อมูลจากตาราง ขั้นแรก ให้กำหนดเทมเพลตที่แสดงถึงโครงสร้างของตารางที่คุณต้องการแยก ระบุตำแหน่งและขนาดของตารางภายในเอกสาร
```csharp
// กำหนดพารามิเตอร์ตาราง (ตำแหน่งและขนาด)
TemplateTableParameters parameters = new TemplateTableParameters(new Rectangle(new Point(35, 320), new Size(530, 55)), null);
// สร้างเทมเพลตตารางพร้อมพารามิเตอร์
TemplateTable table = new TemplateTable(parameters, "Details", null);
```
## ขั้นตอนที่ 2: กำหนดเทมเพลต
สร้างเทมเพลตที่มีเทมเพลตตารางที่คุณกำหนดไว้ เทมเพลตนี้จะแนะนำ parser เกี่ยวกับสิ่งที่ต้องค้นหาเมื่อแยกข้อมูลตาราง
```csharp
// สร้างเทมเพลตพร้อมตาราง
Template template = new Template(new TemplateItem[] { table });
```
## ขั้นตอนที่ 3: แยกวิเคราะห์เอกสารและแยกข้อมูลตาราง
ใช้คลาส Parser จาก GroupDocs.Parser เพื่อแยกวิเคราะห์เอกสารเฉพาะโดยใช้เทมเพลตที่คุณกำหนด
```csharp
// ระบุเส้นทางไปยังไฟล์ตัวอย่างของคุณ
string filePath = "YourSampleFile.pdf";
// สร้างอินสแตนซ์ของคลาส Parser
using (Parser parser = new Parser(filePath))
{
    // แยกวิเคราะห์เอกสารตามเทมเพลต
    DocumentData data = parser.ParseByTemplate(template);
    // วนซ้ำข้อมูลที่แยกออกมาทั้งหมด
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        // ตรวจสอบว่าฟิลด์ที่แยกออกมาเป็นตารางหรือไม่
        PageTableArea area = data[i].PageArea as PageTableArea;
        if (area == null)
        {
            continue;
        }
        // วนซ้ำแถวของตาราง
        for (int row = 0; row < area.RowCount; row++)
        {
            // วนซ้ำคอลัมน์ของตาราง
            for (int column = 0; column < area.ColumnCount; column++)
            {
                // รับค่าเซลล์
                PageTextArea cellValue = area[row, column].PageArea as PageTextArea;
                // พิมพ์ค่าของเซลล์ (หรือสตริงว่างถ้าเป็นโมฆะ)
                Console.Write(cellValue == null ? "" : cellValue.Text);
                // พิมพ์ช่องว่างแท็บระหว่างคอลัมน์
                if (column > 0)
                {
                    Console.Write("\t");
                }
            }
            // ย้ายไปยังบรรทัดถัดไปหลังจากพิมพ์แต่ละแถว
            Console.WriteLine();
        }
    }
}
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้สำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกข้อมูลตารางจากเอกสาร ด้วยการกำหนดเทมเพลตและใช้วิธีการแยกวิเคราะห์ นักพัฒนาสามารถดึงข้อมูลที่มีโครงสร้าง เช่น ตาราง จากรูปแบบไฟล์ต่างๆ ได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### GroupDocs.Parser เข้ากันได้กับรูปแบบเอกสารทั้งหมดหรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบไฟล์ที่หลากหลาย รวมถึง PDF, DOCX, XLSX, PPTX และอื่นๆ
### ฉันสามารถดึงข้อมูลจากภูมิภาคเฉพาะภายในเอกสารได้หรือไม่
แน่นอน คุณสามารถกำหนดเทมเพลตที่กำหนดเป้าหมายพื้นที่เฉพาะ (เช่น ตาราง) ภายในเอกสารเพื่อแยกออกมาได้
### GroupDocs.Parser เหมาะสำหรับเอกสารขนาดใหญ่หรือไม่
ใช่ GroupDocs.Parser ได้รับการปรับให้จัดการเอกสารขนาดใหญ่ได้อย่างมีประสิทธิภาพ ช่วยให้นักพัฒนาสามารถดึงข้อมูลได้อย่างราบรื่น
### GroupDocs.Parser รองรับการแยกข้อความควบคู่ไปกับข้อมูลที่มีโครงสร้างหรือไม่
ใช่ นอกเหนือจากการแยกข้อมูลที่มีโครงสร้าง (เช่น ตาราง) แล้ว GroupDocs.Parser ยังสามารถแยกข้อความธรรมดาและข้อมูลเมตาจากเอกสารได้อีกด้วย
### ฉันจะรับการสนับสนุนหรือความช่วยเหลือเกี่ยวกับการบูรณาการ GroupDocs.Parser ได้อย่างไร
 สำหรับการสนับสนุนและการสนทนา โปรดไปที่ฟอรัมชุมชน GroupDocs[ที่นี่](https://forum.groupdocs.com/c/parser/17).