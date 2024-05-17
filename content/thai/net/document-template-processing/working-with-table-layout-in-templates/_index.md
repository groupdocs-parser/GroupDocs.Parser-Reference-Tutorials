---
title: การทำงานกับเค้าโครงตารางในเทมเพลต
linktitle: การทำงานกับเค้าโครงตารางในเทมเพลต
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีทำงานกับเค้าโครงตารางในเทมเพลตโดยใช้ GroupDocs.Parser for .NET แยกข้อมูลที่มีโครงสร้างออกจากเอกสารได้อย่างมีประสิทธิภาพ
type: docs
weight: 14
url: /th/net/document-template-processing/working-with-table-layout-in-templates/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีการทำงานกับเค้าโครงตารางในเทมเพลตโดยใช้ GroupDocs.Parser สำหรับ .NET GroupDocs.Parser เป็น API การแยกวิเคราะห์เอกสารที่มีประสิทธิภาพซึ่งช่วยให้นักพัฒนาสามารถดึงข้อความและข้อมูลเมตาจากรูปแบบเอกสารต่างๆ รวมถึง PDF, Microsoft Office และอื่นๆ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
- ความรู้พื้นฐานเกี่ยวกับการพัฒนา C# และ .NET
- ติดตั้ง Visual Studio บนเครื่องของคุณแล้ว
-  ติดตั้ง GroupDocs.Parser สำหรับ .NET แล้ว คุณสามารถดาวน์โหลดได้[ที่นี่](https://releases.groupdocs.com/parser/net/).

## นำเข้าเนมสเปซ
ขั้นแรก ตรวจสอบให้แน่ใจว่าได้นำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## ขั้นตอนที่ 1: สร้างเทมเพลตตารางพร้อมเค้าโครง
ในการทำงานกับเค้าโครงตารางในเทมเพลต คุณต้องกำหนดโครงสร้างของตารางโดยใช้`TemplateTableLayout`- โครงร่างนี้ระบุความกว้างของคอลัมน์และความสูงของแถว
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 30, 100, 320, 400, 480, 550 },   // ความกว้างของคอลัมน์
    new double[] { 320, 345, 375 }                  // ความสูงของแถว
);
// สร้างตารางเทมเพลต
TemplateTable table = new TemplateTable(layout, "Details", null);
```
## ขั้นตอนที่ 2: สร้างเทมเพลต
ตอนนี้ สร้างเทมเพลตโดยใช้ตารางที่กำหนด
```csharp
Template template = new Template(new TemplateItem[] { table });
```
## ขั้นตอนที่ 3: แยกวิเคราะห์เอกสารโดยใช้เทมเพลต
 ถัดไป ยกตัวอย่าง`Parser` คลาสและแยกวิเคราะห์เอกสารโดยใช้เทมเพลตที่สร้างขึ้น
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // แยกวิเคราะห์เอกสารตามเทมเพลต
    DocumentData data = parser.ParseByTemplate(template);
    // ทำซ้ำกับข้อมูลที่แยกออกมา
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        // ตรวจสอบว่าฟิลด์นั้นเป็นตารางหรือไม่
        PageTableArea area = data[i].PageArea as PageTableArea;
        if (area == null)
        {
            continue;
        }
        // วนซ้ำตามแถวของตาราง
        for (int row = 0; row < area.RowCount; row++)
        {
            // วนซ้ำผ่านคอลัมน์ของตาราง
            for (int column = 0; column < area.ColumnCount; column++)
            {
                // รับค่าเซลล์
                PageTextArea cellValue = area[row, column].PageArea as PageTextArea;
                // พิมพ์ค่าของเซลล์
                Console.Write(cellValue == null ? "" : cellValue.Text);
                // พิมพ์ช่องว่างระหว่างคอลัมน์
                Console.Write("\t");
            }
            // ย้ายไปยังบรรทัดถัดไปหลังจากแต่ละแถว
            Console.WriteLine();
        }
    }
}
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อทำงานกับเค้าโครงตารางในเทมเพลตเอกสาร ด้วยการทำตามขั้นตอนที่ระบุไว้ คุณจะสามารถแยกวิเคราะห์และแยกข้อมูลที่มีโครงสร้างออกจากเอกสารได้อย่างมีประสิทธิภาพ อำนวยความสะดวกให้กับงานการประมวลผลข้อมูลต่างๆ ในแอปพลิเคชันของคุณ

## คำถามที่พบบ่อย
### ฉันสามารถแยกตารางจากเอกสาร PDF โดยใช้ GroupDocs.Parser สำหรับ .NET ได้หรือไม่
ใช่ GroupDocs.Parser รองรับการแยกวิเคราะห์ตารางจากเอกสาร PDF พร้อมกับรูปแบบยอดนิยมอื่นๆ
### GroupDocs.Parser เหมาะสำหรับการแยกเขตข้อมูลเฉพาะจากเอกสารหรือไม่
แน่นอนว่า GroupDocs.Parser นำเสนอฟีเจอร์ที่มีประสิทธิภาพสำหรับการแยกฟิลด์ข้อมูลเป้าหมายตามเทมเพลตที่กำหนดไว้ล่วงหน้า
### ฉันจะจัดการเค้าโครงตารางต่างๆ ภายในเอกสารได้อย่างไร
GroupDocs.Parser ช่วยให้สามารถกำหนดเทมเพลตแบบกำหนดเองเพื่อจัดการเค้าโครงตารางที่หลากหลายได้อย่างมีประสิทธิภาพ
### GroupDocs.Parser รองรับการประมวลผลเอกสารขนาดใหญ่หรือไม่
ใช่ GroupDocs.Parser ได้รับการปรับให้เหมาะสมสำหรับการจัดการเอกสารที่มีขนาดแตกต่างกัน ทำให้มั่นใจได้ถึงประสิทธิภาพและความน่าเชื่อถือ
### ฉันสามารถรวม GroupDocs.Parser เข้ากับไลบรารี .NET อื่นๆ ได้หรือไม่
แน่นอนว่า GroupDocs.Parser ทำงานร่วมกับไลบรารี .NET อื่นๆ ได้อย่างราบรื่น ช่วยให้เวิร์กโฟลว์การประมวลผลเอกสารครอบคลุม