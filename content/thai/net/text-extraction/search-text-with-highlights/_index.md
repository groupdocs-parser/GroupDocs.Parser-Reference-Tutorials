---
title: ค้นหาข้อความด้วยไฮไลท์
linktitle: ค้นหาข้อความด้วยไฮไลท์
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีค้นหาและเน้นข้อความในเอกสารโดยใช้ GroupDocs.Parser for .NET ดึงข้อมูลเชิงลึกอันมีค่าออกมาอย่างมีประสิทธิภาพ
weight: 24
url: /th/net/text-extraction/search-text-with-highlights/
type: docs
---
# ค้นหาข้อความด้วยไฮไลท์

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อค้นหาข้อความภายในเอกสารและเน้นผลลัพธ์การค้นหา GroupDocs.Parser เป็นไลบรารีที่มีประสิทธิภาพซึ่งช่วยให้คุณสามารถทำงานกับรูปแบบเอกสารต่างๆ และแยกข้อความ ข้อมูลเมตา และอื่นๆ ได้
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
1.  GroupDocs.Parser สำหรับ .NET: ดาวน์โหลดและติดตั้งไลบรารีจาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
2. IDE: ใช้ Visual Studio หรือ IDE ที่ต้องการสำหรับการพัฒนา .NET
3. ไฟล์ตัวอย่าง: เตรียมเอกสารตัวอย่าง (เช่น PDF, DOCX) สำหรับการค้นหาข้อความ

## นำเข้าเนมสเปซ
ขั้นแรก ให้เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ .NET ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ Parser
 เริ่มต้นด้วยการยกตัวอย่าง`Parser` คลาสพร้อมพาธไปยังไฟล์ตัวอย่างของคุณ:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // รหัสของคุณที่นี่
}
```
## ขั้นตอนที่ 2: กำหนดตัวเลือกไฮไลต์
 ระบุ`HighlightOptions` เพื่อกำหนดค่าวิธีการเน้นผลการค้นหา ตัวอย่างเช่น การตั้งค่าหน้าต่างบริบทเป็น 15 ตัวอักษร:
```csharp
HighlightOptions highlightOptions = new HighlightOptions(15);
```
## ขั้นตอนที่ 3: ค้นหาข้อความ
ตอนนี้ ให้ทำการค้นหาข้อความภายในเอกสาร ระบุคำสำคัญที่คุณต้องการค้นหา (เช่น "lorem"):
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("lorem", new SearchOptions(true, false, false, highlightOptions));
```
## ขั้นตอนที่ 4: ประมวลผลผลการค้นหา
วนซ้ำผลการค้นหาและแสดงข้อความที่พบพร้อมกับไฮไลต์:
```csharp
if (searchResults != null)
{
    foreach (SearchResult result in searchResults)
    {
        Console.WriteLine($"{result.LeftHighlightItem.Text}{result.Text}{result.RightHighlightItem.Text}");
    }
}
else
{
    Console.WriteLine("Search isn't supported");
}
```

## บทสรุป
ในบทช่วยสอนนี้ คุณได้เรียนรู้วิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อค้นหาข้อความภายในเอกสารและเน้นผลลัพธ์การค้นหา ฟังก์ชันนี้มีประโยชน์อย่างมากสำหรับการแยกและวิเคราะห์ข้อความในแอปพลิเคชัน .NET ของคุณ

## คำถามที่พบบ่อย
### GroupDocs.Parser เหมาะสำหรับการประมวลผลเอกสารรูปแบบต่างๆ หรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, DOCX, XLSX, PPTX และอื่นๆ
### ฉันสามารถใช้ GroupDocs.Parser เพื่อดึงข้อมูลเมตาจากเอกสารได้หรือไม่
อย่างแน่นอน! GroupDocs.Parser ช่วยให้คุณสามารถแยกข้อมูลเมตา ข้อความ และข้อมูลที่มีโครงสร้างออกจากเอกสารได้
### ฉันจะรับการสนับสนุนหรือถามคำถามเกี่ยวกับ GroupDocs.Parser ได้ที่ไหน
 ท่านสามารถเยี่ยมชมได้ที่[ฟอรัม GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) สำหรับคำถามที่เกี่ยวข้องกับการสนับสนุน
### GroupDocs.Parser มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถเข้าถึง[ทดลองฟรี](https://releases.groupdocs.com/) ของ GroupDocs.Parser เพื่อประเมินคุณสมบัติต่างๆ
### ฉันจะซื้อใบอนุญาตสำหรับ GroupDocs.Parser ได้อย่างไร
 คุณสามารถซื้อใบอนุญาตได้จาก[ที่นี่](https://purchase.groupdocs.com/buy) และยังได้รับใบอนุญาตชั่วคราวอีกด้วย[ที่นี่](https://purchase.groupdocs.com/temporary-license/).