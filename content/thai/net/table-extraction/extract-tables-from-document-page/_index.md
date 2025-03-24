---
title: แยกตารางออกจากหน้าเอกสาร
linktitle: แยกตารางออกจากหน้าเอกสาร
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกตารางออกจากเอกสารโดยทางโปรแกรมโดยใช้ GroupDocs.Parser สำหรับ .NET บทช่วยสอนที่ครอบคลุมนี้ให้คำแนะนำทีละขั้นตอน
weight: 11
url: /th/net/table-extraction/extract-tables-from-document-page/
---

# แยกตารางออกจากหน้าเอกสาร

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีแยกตารางออกจากหน้าเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET GroupDocs.Parser เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถทำงานกับรูปแบบเอกสารที่หลากหลาย เช่น PDF, DOCX, XLSX และอื่นๆ ด้วยการใช้ประโยชน์จากคุณลักษณะนี้ เราสามารถดึงข้อมูลที่มีโครงสร้าง เช่น ตาราง ออกจากเอกสารเหล่านี้ได้อย่างมีประสิทธิภาพ ทำให้เราสามารถจัดการและวิเคราะห์ข้อมูลโดยทางโปรแกรมได้
## ข้อกำหนดเบื้องต้น
ก่อนเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
- ติดตั้ง Visual Studio บนเครื่องของคุณแล้ว
- ความเข้าใจพื้นฐานเกี่ยวกับการพัฒนา C# และ .NET
-  GroupDocs.Parser สำหรับไลบรารี .NET คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
- เข้าถึงเอกสารตัวอย่าง (PDF, DOCX ฯลฯ) ที่มีตารางสำหรับการแยกข้อมูล

## นำเข้าเนมสเปซ
ขั้นแรก ให้เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ C# ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using GroupDocs.Parser.Templates;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
 ยกตัวอย่าง`Parser` คลาสโดยระบุพาธไปยังเอกสารตัวอย่างของคุณ:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //รหัสของคุณยังคงอยู่ที่นี่...
}
```
## ขั้นตอนที่ 2: ตรวจสอบการสนับสนุนการแยกตารางเอกสาร
ก่อนดำเนินการต่อ ให้ตรวจสอบว่าเอกสารรองรับการแยกตารางหรือไม่:
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document does not support table extraction.");
    return;
}
```
## ขั้นตอนที่ 3: กำหนดเค้าโครงตาราง
กำหนดเค้าโครงของตารางที่จะแยกออกจากเอกสาร ระบุความกว้างของคอลัมน์และความสูงของแถวตามโครงสร้างของเอกสารของคุณ:
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },  // ความกว้างของคอลัมน์
    new double[] { 325, 340, 365, 395 });         // ความสูงของแถว
```
## ขั้นตอนที่ 4: กำหนดค่าตัวเลือกการแยกตาราง
สร้างตัวเลือกสำหรับการแยกตารางโดยใช้เค้าโครงที่ระบุ:
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## ขั้นตอนที่ 5: ดึงข้อมูลเอกสาร
ดึงข้อมูลเกี่ยวกับเอกสาร รวมทั้งจำนวนหน้า:
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## ขั้นตอนที่ 6: วนซ้ำหน้าเอกสาร
วนซ้ำแต่ละหน้าของเอกสารเพื่อแยกตาราง:
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // แยกตารางออกจากหน้าปัจจุบัน
    IEnumerable<PageTableArea> tables = parser.GetTables(pageIndex, options);
    // วนซ้ำตารางที่แยกออกมา
    foreach (PageTableArea table in tables)
    {
        // วนซ้ำแถวของตาราง
        for (int row = 0; row < table.RowCount; row++)
        {
            // วนซ้ำคอลัมน์ของตาราง
            for (int column = 0; column < table.ColumnCount; column++)
            {
                // รับเซลล์ตาราง
                PageTableAreaCell cell = table[row, column];
                if (cell != null)
                {
                    // พิมพ์ข้อความของเซลล์ตาราง
                    Console.Write(cell.Text);
                    Console.Write(" | ");
                }
            }
            Console.WriteLine();
        }
        Console.WriteLine();
    }
}
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงกระบวนการแยกตารางออกจากหน้าเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET ด้วยการทำตามขั้นตอนที่ให้ไว้ คุณจะสามารถรวมฟังก์ชันการแยกตารางเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น ช่วยให้สามารถจัดการและจัดการข้อมูลที่มีโครงสร้างภายในเอกสารได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### GroupDocs.Parser สามารถแยกตารางจากเอกสารทุกประเภทได้หรือไม่
GroupDocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย เช่น PDF, DOCX, XLSX และอื่นๆ ช่วยให้สามารถแยกตารางจากประเภทไฟล์ที่เข้ากันได้
### GroupDocs.Parser สำหรับ .NET เหมาะสำหรับการประมวลผลเอกสารขนาดใหญ่หรือไม่
ใช่ GroupDocs.Parser ได้รับการออกแบบมาเพื่อจัดการเอกสารขนาดใหญ่อย่างมีประสิทธิภาพ ทำให้เหมาะสำหรับการประมวลผลชุดข้อมูลขนาดใหญ่
### GroupDocs.Parser รักษาการจัดรูปแบบในระหว่างการแยกตารางหรือไม่
ใช่ GroupDocs.Parser จะเก็บรายละเอียดการจัดรูปแบบ เช่น เส้นขอบเซลล์ สไตล์ข้อความ และการจัดแนวระหว่างการแยกตาราง
### ฉันสามารถแยกตารางเฉพาะตามเกณฑ์เนื้อหาได้หรือไม่
GroupDocs.Parser นำเสนอตัวเลือกที่ยืดหยุ่นในการกำหนดเป้าหมายตารางเฉพาะตามเทมเพลตเค้าโครงหรือเงื่อนไขเนื้อหาสำหรับการแยก
### GroupDocs.Parser เข้ากันได้กับ .NET Core หรือไม่
ใช่ GroupDocs.Parser เข้ากันได้กับทั้งสภาพแวดล้อม .NET Framework และ .NET Core