---
title: ค้นหาข้อความตามหน้า
linktitle: ค้นหาข้อความตามหน้า
second_title: GroupDocs.Parser .NET API
description: เรียนรู้การค้นหาข้อความตามหน้าโดยใช้ GroupDocs.Parser สำหรับ .NET แยกเนื้อหาเฉพาะอย่างมีประสิทธิภาพจากเอกสารในแอปพลิเคชัน .NET ของคุณ
weight: 22
url: /th/net/text-extraction/search-text-by-pages/
---

# ค้นหาข้อความตามหน้า

## การแนะนำ
ในโลกของการพัฒนา .NET การแยกวิเคราะห์และแยกข้อความจากเอกสารอย่างมีประสิทธิภาพถือเป็นงานที่สำคัญ GroupDocs.Parser for .NET นำเสนอความสามารถอันทรงพลังในการทำงานกับเอกสารรูปแบบต่างๆ ช่วยให้นักพัฒนาสามารถค้นหาและแยกเนื้อหาเฉพาะได้อย่างราบรื่น บทช่วยสอนนี้จะแนะนำคุณตลอดกระบวนการใช้ประโยชน์จาก GroupDocs.Parser เพื่อค้นหาข้อความตามหน้าในแอปพลิเคชัน .NET ของคุณ
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอนนี้ ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
- ความเข้าใจพื้นฐานเกี่ยวกับกรอบงาน C# และ .NET
- ติดตั้ง Visual Studio บนระบบของคุณแล้ว
-  ติดตั้ง GroupDocs.Parser สำหรับไลบรารี .NET แล้ว (ดาวน์โหลดจาก[ที่นี่](https://releases.groupdocs.com/parser/net/-)
- ไฟล์ตัวอย่างสำหรับทดสอบฟังก์ชันการค้นหา
## นำเข้าเนมสเปซ
ประการแรก รวมเนมสเปซที่จำเป็นในโครงการของคุณเพื่อเข้าถึงฟังก์ชัน GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
 เริ่มต้นด้วยการยกตัวอย่าง`Parser` คลาสพร้อมพาธไปยังไฟล์ตัวอย่างของคุณ:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // รหัสของคุณอยู่ที่นี่
}
```
## ขั้นตอนที่ 2: ค้นหาข้อความด้วยหมายเลขหน้า
 ใช้`Search` วิธีค้นหาคำสำคัญเฉพาะภายในเอกสารพร้อมกับหมายเลขหน้า:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword", new SearchOptions(false, false, false, true));
```
## ขั้นตอนที่ 3: ตรวจสอบการสนับสนุนการค้นหา
ตรวจสอบว่าการดำเนินการค้นหาได้รับการสนับสนุนสำหรับประเภทเอกสารหรือไม่:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported for this document type.");
    return;
}
```
## ขั้นตอนที่ 4: วนซ้ำผลการค้นหา
วนซ้ำผลการค้นหาเพื่อดึงข้อมูลตำแหน่งที่จัดทำดัชนี หมายเลขหน้า และข้อความที่พบ:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position} (page {result.PageIndex}): {result.Text}");
}
```
## บทสรุป
ในบทช่วยสอนนี้ เราได้สำรวจวิธีการใช้การค้นหาข้อความตามหน้าต่างๆ โดยใช้ GroupDocs.Parser สำหรับ .NET ด้วยการทำตามขั้นตอนเหล่านี้ คุณสามารถรวมฟังก์ชันการแยกวิเคราะห์เอกสารและการค้นหาเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### GroupDocs.Parser เข้ากันได้กับรูปแบบเอกสารต่าง ๆ หรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง DOCX, PDF, XLSX, PPTX และอื่นๆ
### ฉันสามารถแยกรูปภาพและข้อมูลเมตาจากเอกสารโดยใช้ GroupDocs.Parser ได้หรือไม่
GroupDocs.Parser ช่วยให้สามารถแยกรูปภาพ ข้อมูลเมตา และข้อความจากเอกสารได้อย่างแน่นอน
### ฉันจะหาเอกสารโดยละเอียดสำหรับ GroupDocs.Parser ได้ที่ไหน
 คุณสามารถเข้าถึงเอกสารประกอบ[ที่นี่](https://tutorials.groupdocs.com/parser/net/).
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Parser ได้อย่างไร
 คุณสามารถขอใบอนุญาตชั่วคราวได้[ที่นี่](https://purchase.groupdocs.com/temporary-license/).
### ฉันจะรับการสนับสนุนหรือความช่วยเหลือเกี่ยวกับ GroupDocs.Parser ได้ที่ไหน
 สำหรับการสนับสนุนและการสนทนา โปรดไปที่ฟอรัม GroupDocs.Parser[ที่นี่](https://forum.groupdocs.com/c/parser/17).