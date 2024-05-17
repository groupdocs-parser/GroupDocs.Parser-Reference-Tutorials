---
title: การทำงานกับพารามิเตอร์ตารางในเทมเพลต
linktitle: การทำงานกับพารามิเตอร์ตารางในเทมเพลต
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกข้อมูลจากตารางในเอกสารโดยใช้ GroupDocs.Parser for .NET คำแนะนำทีละขั้นตอนสำหรับการใช้งานพารามิเตอร์ตาราง
type: docs
weight: 15
url: /th/net/document-template-processing/working-with-table-parameters-in-templates/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อทำงานกับพารามิเตอร์ตารางในเทมเพลต คู่มือนี้จะแบ่งกระบวนการออกเป็นคำแนะนำทีละขั้นตอนเพื่อช่วยให้คุณแยกวิเคราะห์และดึงข้อมูลจากตารางภายในเอกสารได้อย่างมีประสิทธิภาพ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
-  GroupDocs.Parser สำหรับ .NET Library: คุณสามารถดาวน์โหลดไลบรารีได้จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
- สภาพแวดล้อมการพัฒนา: ตรวจสอบให้แน่ใจว่าคุณมีสภาพแวดล้อมการพัฒนาที่เหมาะสมสำหรับการพัฒนา .NET
- เอกสารตัวอย่าง: เตรียมเอกสารตัวอย่าง (เช่น PDF, DOCX) ที่มีตารางที่คุณต้องการแยกข้อมูล

## นำเข้าเนมสเปซ
ขั้นแรก คุณจะต้องนำเข้าเนมสเปซที่จำเป็นสำหรับการทำงานกับ GroupDocs.Parser ในแอปพลิเคชัน .NET ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## ขั้นตอนที่ 1: สร้างเทมเพลตตาราง
หากต้องการทำงานกับพารามิเตอร์ตาราง ให้เริ่มต้นด้วยการกำหนดเทมเพลตตารางด้วยพารามิเตอร์เฉพาะ:
```csharp
//กำหนดพารามิเตอร์ตาราง (ตำแหน่งและขนาด)
TemplateTableParameters tableParams = new TemplateTableParameters(new Rectangle(new Point(35, 320), new Size(530, 55)), null);
// สร้างวัตถุ TemplateTable พร้อมพารามิเตอร์และชื่อ
TemplateTable table = new TemplateTable(tableParams, "Details", null);
```
## ขั้นตอนที่ 2: สร้างเทมเพลต
ตอนนี้ ประกอบเทมเพลตของคุณด้วยตารางที่กำหนด:
```csharp
// สร้างวัตถุเทมเพลตและรวมตารางไว้ด้วย
Template template = new Template(new TemplateItem[] { table });
```
## ขั้นตอนที่ 3: แยกวิเคราะห์เอกสารโดยใช้เทมเพลต
ใช้คลาส Parser เพื่อแยกวิเคราะห์เอกสารของคุณตามเทมเพลตที่สร้างขึ้น:
```csharp
// ระบุเส้นทางไปยังเอกสารตัวอย่างของคุณ
string filePath = "Your Sample File Path";
// สร้างอินสแตนซ์ของคลาส Parser ด้วยเส้นทางเอกสาร
using (Parser parser = new Parser(filePath))
{
    // แยกวิเคราะห์เอกสารโดยใช้เทมเพลต
    DocumentData data = parser.ParseByTemplate(template);
    // ทำซ้ำผ่านข้อมูลที่แยกออกมา
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        
        // ตรวจสอบว่าฟิลด์ที่แยกออกมาเป็นตารางหรือไม่
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
                // พิมพ์ค่าเซลล์ (พร้อมการแยกแท็บ)
                Console.Write(cellValue == null ? "" : cellValue.Text + "\t");
            }
            
            // ย้ายไปยังบรรทัดถัดไปสำหรับแถวถัดไป
            Console.WriteLine();
        }
    }
}
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงวิธีการทำงานอย่างมีประสิทธิภาพกับพารามิเตอร์ตารางในเทมเพลตโดยใช้ GroupDocs.Parser สำหรับ .NET เมื่อทำตามขั้นตอนเหล่านี้ คุณจะดึงข้อมูลที่มีโครงสร้างจากตารางภายในเอกสารของคุณได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### GroupDocs.Parser สำหรับ .NET รองรับไฟล์รูปแบบใดบ้าง
GroupDocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, DOCX, XLSX, PPTX และอื่นๆ อีกมากมาย
### ฉันสามารถดึงข้อมูลจากภูมิภาคเฉพาะภายในเอกสารได้หรือไม่
ได้ คุณสามารถกำหนดเทมเพลตแบบกำหนดเองเพื่อดึงข้อมูลจากพื้นที่หรือพารามิเตอร์เฉพาะภายในเอกสารได้
### GroupDocs.Parser เหมาะสำหรับการจัดการเอกสารขนาดใหญ่หรือไม่
ใช่ GroupDocs.Parser ได้รับการปรับให้เหมาะสมสำหรับการจัดการเอกสารขนาดต่างๆ รวมถึงไฟล์ขนาดใหญ่
### ฉันจะจัดการกับข้อยกเว้นระหว่างการแยกวิเคราะห์เอกสารได้อย่างไร
คุณสามารถใช้เทคนิคการจัดการข้อผิดพลาดภายในแอปพลิเคชัน .NET ของคุณเพื่อจัดการข้อยกเว้นที่อาจเกิดขึ้นระหว่างการแยกวิเคราะห์
### GroupDocs.Parser ให้การสนับสนุนหรือความช่วยเหลือในการบูรณาการหรือไม่
 ใช่ คุณสามารถขอรับการสนับสนุนและความช่วยเหลือได้จากฟอรัม GroupDocs[ที่นี่](https://forum.groupdocs.com/c/parser/17).