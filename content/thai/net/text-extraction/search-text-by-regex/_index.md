---
title: ค้นหาข้อความตามนิพจน์ทั่วไป (Regex)
linktitle: ค้นหาข้อความตามนิพจน์ทั่วไป (Regex)
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีค้นหาข้อความโดยใช้นิพจน์ทั่วไปในเอกสารโดยใช้ GroupDocs.Parser for .NET แยกเนื้อหาเฉพาะเจาะจงได้อย่างง่ายดาย
weight: 23
url: /th/net/text-extraction/search-text-by-regex/
---

# ค้นหาข้อความตามนิพจน์ทั่วไป (Regex)

## การแนะนำ
ในบทช่วยสอนนี้ เราจะเจาะลึกเกี่ยวกับการใช้ GroupDocs.Parser สำหรับ .NET เพื่อค้นหาข้อความด้วยนิพจน์ทั่วไป (Regex) ภายในเอกสาร GroupDocs.Parser เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถแยกข้อความและข้อมูลเมตาจากไฟล์รูปแบบต่างๆ เช่น PDF, DOCX, XLSX และอื่นๆ การค้นหาข้อความโดยใช้นิพจน์ทั่วไปมีประโยชน์อย่างยิ่งในการค้นหารูปแบบหรือเนื้อหาเฉพาะภายในเอกสารอย่างมีประสิทธิภาพ
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอนนี้ ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1. Visual Studio: ติดตั้ง Visual Studio IDE สำหรับการพัฒนา .NET
2.  GroupDocs.Parser for .NET: ดาวน์โหลดและติดตั้ง GroupDocs.Parser for .NET จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
3. ไฟล์ตัวอย่าง: เตรียมเอกสารตัวอย่าง (PDF, DOCX ฯลฯ) เพื่อทดสอบฟังก์ชันการค้นหา

## นำเข้าเนมสเปซ
ขั้นแรก ให้เริ่มต้นด้วยการรวมเนมสเปซที่จำเป็นไว้ในโค้ด C# ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
 ยกตัวอย่าง`Parser` คลาสโดยระบุเส้นทางไปยังไฟล์ตัวอย่างของคุณ:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // รหัสไปที่นี่
}
```
 แทนที่`"YourSampleFile.pdf"` พร้อมเส้นทางไปยังไฟล์จริงของคุณ
## ขั้นตอนที่ 2: ค้นหาโดยใช้นิพจน์ทั่วไป
กำหนดและดำเนินการค้นหาโดยใช้รูปแบบนิพจน์ทั่วไป ตัวอย่างเช่น หากต้องการค้นหาลำดับตัวเลข (เช่น จำนวนเต็ม) ภายในเอกสาร:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("[0-9]+", new SearchOptions(true, false, true));
```
 ในตัวอย่างนี้`[0-9]+` เป็นรูปแบบนิพจน์ทั่วไปที่ตรงกับตัวเลขตั้งแต่หนึ่งหลักขึ้นไป
## ขั้นตอนที่ 3: ตรวจสอบการสนับสนุนการค้นหา
ตรวจสอบว่าการดำเนินการค้นหาได้รับการสนับสนุนสำหรับประเภทเอกสารหรือไม่:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported");
    return;
}
```
## ขั้นตอนที่ 4: วนซ้ำผลการค้นหา
วนซ้ำผลการค้นหาและประมวลผลแต่ละนัด:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
วงนี้จะพิมพ์ตำแหน่งและข้อความที่ตรงกันที่พบในเอกสาร

## บทสรุป
โดยสรุป การใช้ประโยชน์จาก GroupDocs.Parser สำหรับ .NET ช่วยให้สามารถค้นหาข้อความได้อย่างมีประสิทธิภาพโดยใช้นิพจน์ทั่วไปในรูปแบบเอกสารต่างๆ ด้วยการทำตามคำแนะนำนี้ นักพัฒนาสามารถรวมการแยกวิเคราะห์เอกสารและการแยกข้อความที่ใช้ regex เข้ากับแอปพลิเคชัน .NET ของตนได้อย่างราบรื่น

## คำถามที่พบบ่อย
### GroupDocs.Parser สามารถค้นหาภายในเอกสารที่เข้ารหัสได้หรือไม่
ไม่ GroupDocs.Parser ไม่สามารถค้นหาภายในเอกสารที่เข้ารหัสหรือป้องกันด้วยรหัสผ่านได้
### GroupDocs.Parser รองรับ OCR (Optical Character Recognition) หรือไม่
ไม่ GroupDocs.Parser ไม่ดำเนินการ OCR ขึ้นอยู่กับการแยกข้อความจากโครงสร้างภายในของเอกสาร
### ฉันสามารถค้นหารูปแบบที่ซับซ้อนโดยใช้นิพจน์ทั่วไปได้หรือไม่
ใช่ GroupDocs.Parser รองรับนิพจน์ทั่วไปเต็มรูปแบบ ช่วยให้สามารถจับคู่รูปแบบที่ซับซ้อนภายในเอกสารได้
### เอกสารรูปแบบใดบ้างที่รองรับการแยกข้อความ
GroupDocs.Parser รองรับรูปแบบที่หลากหลาย รวมถึง PDF, DOCX, XLSX, PPTX และอื่นๆ
### GroupDocs.Parser เข้ากันได้กับ .NET Core หรือไม่
ใช่ GroupDocs.Parser เข้ากันได้กับ .NET Core สำหรับการพัฒนาข้ามแพลตฟอร์ม