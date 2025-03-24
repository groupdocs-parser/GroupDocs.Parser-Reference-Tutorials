---
title: แยกตารางออกจากเอกสาร
linktitle: แยกตารางออกจากเอกสาร
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกตารางออกจากเอกสารโดยใช้ Groupdocs.Parser สำหรับ .NET ปฏิบัติตามคำแนะนำโดยละเอียดเกี่ยวกับการผสานรวมฟังก์ชันการทำงานนี้
weight: 10
url: /th/net/table-extraction/extract-tables-from-document/
---

# แยกตารางออกจากเอกสาร

## การแนะนำ
Groupdocs.Parser สำหรับ .NET เป็นไลบรารีแบบครอบคลุมที่อำนวยความสะดวกในการแยกวิเคราะห์เอกสาร ทำให้คุณสามารถดึงข้อมูลอันมีค่า เช่น ตาราง ข้อความ เมตาดาต้า และอื่นๆ จากเอกสารได้ ในบทช่วยสอนนี้ เรามุ่งเน้นที่การแยกตารางออกจากเอกสารโดยใช้ Groupdocs.Parser API โดยเฉพาะ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
- ติดตั้ง Visual Studio บนระบบของคุณแล้ว
- ติดตั้ง .NET Framework หรือ .NET Core แล้ว
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C#

## นำเข้าเนมสเปซ
ขั้นแรก คุณต้องนำเข้าเนมสเปซที่จำเป็นเพื่อเข้าถึงคลาสและวิธีการของ Groupdocs.Parser
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
 เริ่มต้นอินสแตนซ์ใหม่ของ`Parser` คลาสโดยระบุเส้นทางไปยังเอกสารตัวอย่างของคุณ
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // รหัสของคุณอยู่ที่นี่
}
```
## ขั้นตอนที่ 2: ตรวจสอบการสนับสนุนการแยกตาราง
 ตรวจสอบว่าเอกสารรองรับการแยกตารางโดยใช้`Features` ทรัพย์สินของ`Parser` ระดับ.
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document doesn't support table extraction.");
    return;
}
```
## ขั้นตอนที่ 3: กำหนดเค้าโครงตาราง
กำหนดเค้าโครงของตารางที่คุณต้องการแยกใช้`TemplateTableLayout`- ระบุความกว้างของคอลัมน์และความสูงของแถวตามโครงสร้างของเอกสารของคุณ
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },
    new double[] { 325, 340, 365, 395 });
```
## ขั้นตอนที่ 4: ตั้งค่าตัวเลือกการแยกตาราง
 สร้าง`PageTableAreaOptions` ด้วยโครงร่างที่กำหนดไว้เพื่อระบุวิธีแยกตาราง
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## ขั้นตอนที่ 5: แยกตาราง
 ใช้`GetTables` วิธีการของ`Parser` คลาสเพื่อแยกตารางออกจากเอกสารตามตัวเลือกที่ระบุ
```csharp
IEnumerable<PageTableArea> tables = parser.GetTables(options);
```
## ขั้นตอนที่ 6: วนซ้ำและเข้าถึงข้อมูลตาราง
วนซ้ำตารางที่แยกออกมา รวมถึงแถวและคอลัมน์ตามลำดับเพื่อเข้าถึงข้อมูลเซลล์
```csharp
foreach (PageTableArea table in tables)
{
    for (int row = 0; row < table.RowCount; row++)
    {
        for (int column = 0; column < table.ColumnCount; column++)
        {
            PageTableAreaCell cell = table[row, column];
            if (cell != null)
            {
                Console.Write(cell.Text);
                Console.Write(" | ");
            }
        }
        Console.WriteLine();
    }
    Console.WriteLine();
}
```
## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงวิธีใช้ Groupdocs.Parser สำหรับ .NET เพื่อแยกตารางออกจากเอกสารอย่างมีประสิทธิภาพ ด้วยการใช้ประโยชน์จากความสามารถของไลบรารีนี้ คุณสามารถรวมการแยกตารางเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น

## คำถามที่พบบ่อย
### Groupdocs.Parser สามารถจัดการรูปแบบเอกสารที่แตกต่างกันได้หรือไม่
ใช่ Groupdocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง DOCX, PDF, XLSX และอื่นๆ
### มีรุ่นทดลองใช้สำหรับ Groupdocs.Parser สำหรับ .NET หรือไม่
 ใช่ คุณสามารถดาวน์โหลดรุ่นทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนสำหรับข้อความค้นหาที่เกี่ยวข้องกับ Groupdocs.Parser ได้อย่างไร
 ท่านสามารถเยี่ยมชมได้ที่[ฟอรัม Groupdocs.Parser](https://forum.groupdocs.com/c/parser/17) สำหรับความช่วยเหลือ.
### ฉันจะซื้อใบอนุญาตสำหรับ Groupdocs.Parser ได้ที่ไหน
 คุณสามารถซื้อใบอนุญาตได้จาก[ที่นี่](https://purchase.groupdocs.com/buy).
### ฉันจะขอรับใบอนุญาตชั่วคราวเพื่อวัตถุประสงค์ในการประเมินได้อย่างไร
 คุณสามารถขอรับใบอนุญาตชั่วคราวได้[ที่นี่](https://purchase.groupdocs.com/temporary-license/).