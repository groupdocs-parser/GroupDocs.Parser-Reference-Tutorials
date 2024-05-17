---
title: ค้นหาข้อความในเอกสาร Excel ด้วยนิพจน์ปกติ
linktitle: ค้นหาข้อความในเอกสาร Excel ด้วยนิพจน์ปกติ
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีค้นหาข้อความในเอกสาร Excel โดยใช้นิพจน์ทั่วไปด้วย GroupDocs.Parser for .NET ทำการค้นหาข้อความขั้นสูงอย่างมีประสิทธิภาพ
type: docs
weight: 17
url: /th/net/excel-document-processing/search-text-in-excel-document-by-regular-expression/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อค้นหารูปแบบข้อความเฉพาะภายในเอกสาร Excel โดยใช้นิพจน์ทั่วไป GroupDocs.Parser เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถดึงข้อความและข้อมูลเมตาจากรูปแบบเอกสารต่างๆ รวมถึงสเปรดชีต เช่น Excel ด้วยการใช้ประโยชน์จากนิพจน์ทั่วไป เราจึงสามารถดำเนินการค้นหาข้อความขั้นสูงได้อย่างมีประสิทธิภาพ
## ข้อกำหนดเบื้องต้น
ก่อนเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าต่อไปนี้:
1. Visual Studio: ติดตั้ง Visual Studio หรือ IDE อื่นที่เข้ากันได้สำหรับการพัฒนา .NET
2.  GroupDocs.Parser สำหรับ .NET: ดาวน์โหลดและติดตั้งไลบรารีจาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
3. ไฟล์ Excel ตัวอย่าง: เตรียมไฟล์ Excel ตัวอย่างที่มีข้อความที่คุณต้องการค้นหา

## นำเข้าเนมสเปซ
ขั้นแรก ให้รวมเนมสเปซที่จำเป็นเพื่อใช้ GroupDocs.Parser ในโปรเจ็กต์ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
 เริ่มต้นด้วยการสร้างอินสแตนซ์ของ`Parser` คลาสโดยส่งเส้นทางไปยังเอกสาร Excel ของคุณเป็นพารามิเตอร์
```csharp
// สร้างอินสแตนซ์ของคลาส Parser
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // รหัสดำเนินต่อไปที่นี่...
}
```
## ขั้นตอนที่ 2: ทำการค้นหานิพจน์ทั่วไป
 ภายใน`using` บล็อก ให้ดำเนินการค้นหาข้อความโดยใช้รูปแบบนิพจน์ทั่วไป
```csharp
//ค้นหาด้วยนิพจน์ทั่วไปพร้อมการจับคู่ตัวพิมพ์
IEnumerable<SearchResult> searchResults = parser.Search("\\sthe\\s", new SearchOptions(true, false, true));
```
- คำอธิบายรูปแบบ Regex:
  - `\\sthe\\s`: รูปแบบ regex นี้ค้นหาคำว่า "the" (คำนึงถึงตัวพิมพ์เล็กและตัวพิมพ์ใหญ่) ที่ล้อมรอบด้วยช่องว่าง
## ขั้นตอนที่ 3: ทำซ้ำผลการค้นหา
จากนั้น วนซ้ำผลการค้นหาเพื่อเข้าถึงรายการที่ตรงกันแต่ละรายการ
```csharp
// ทำซ้ำกับผลการค้นหา
foreach (SearchResult result in searchResults)
{
    // พิมพ์ตำแหน่งและข้อความที่พบ
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
- เอาท์พุท:
  - การวนซ้ำนี้จะพิมพ์รูปแบบข้อความที่ระบุแต่ละครั้งพร้อมกับตำแหน่งภายในเอกสาร

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อทำการค้นหานิพจน์ทั่วไปภายในเอกสาร Excel ด้วยการทำตามขั้นตอนเหล่านี้ คุณสามารถรวมความสามารถในการค้นหาข้อความขั้นสูงเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### GroupDocs.Parser สามารถดึงข้อมูลจากรูปแบบเอกสารอื่นนอกเหนือจาก Excel ได้หรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Word, PDF, PowerPoint และอื่นๆ
### GroupDocs.Parser มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถดาวน์โหลดรุ่นทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนหรือถามคำถามเกี่ยวกับ GroupDocs.Parser ได้ที่ไหน
 เยี่ยมชม[ฟอรัม GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17)สำหรับการสนับสนุนและการอภิปราย
### ฉันจะซื้อใบอนุญาตสำหรับ GroupDocs.Parser ได้อย่างไร
 คุณสามารถซื้อใบอนุญาตได้จาก[ที่นี่](https://purchase.groupdocs.com/buy).
### ฉันสามารถขอรับใบอนุญาตชั่วคราวเพื่อการทดสอบได้หรือไม่
 ใช่ คุณสามารถรับใบอนุญาตชั่วคราวได้[ที่นี่](https://purchase.groupdocs.com/temporary-license/).