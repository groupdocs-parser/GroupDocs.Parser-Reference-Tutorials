---
title: แยกและเน้นข้อความ
linktitle: แยกและเน้นข้อความ
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกและเน้นข้อความจากเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET ขั้นตอนง่ายๆ สำหรับการแยกข้อความอย่างมีประสิทธิภาพในโครงการ .NET ของคุณ
weight: 11
url: /th/net/text-extraction/extract-and-highlight-text/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกและเน้นข้อความจากเอกสาร GroupDocs.Parser เป็นไลบรารีที่มีประสิทธิภาพซึ่งช่วยให้คุณสามารถแยกวิเคราะห์รูปแบบเอกสารต่างๆ และดำเนินการแยกข้อความขั้นสูงได้
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
- Visual Studio: ติดตั้ง Visual Studio สำหรับการพัฒนา .NET
-  GroupDocs.Parser for .NET: ดาวน์โหลดและติดตั้ง GroupDocs.Parser for .NET จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
- ไฟล์ตัวอย่าง: เตรียมเอกสารตัวอย่างให้พร้อมสำหรับการแยกข้อความ

## การนำเข้าเนมสเปซ
ขั้นแรก ให้เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ Parser
 ยกตัวอย่าง`Parser` คลาสพร้อมพาธไฟล์ตัวอย่างของคุณ:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // เพิ่มตรรกะการแยกและการเน้นที่นี่
}
```
## ขั้นตอนที่ 2: แยกและเน้นข้อความ
 ตอนนี้ภายใน`using`บล็อก คุณสามารถแยกและเน้นข้อความได้:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // แยกไฮไลท์ที่ตำแหน่ง 2 สูงสุด 3 คำ
    HighlightItem highlight = parser.GetHighlight(2, true, new HighlightOptions(3));
    // ตรวจสอบว่ารองรับการแยกไฮไลต์หรือไม่
    if (highlight == null)
    {
        Console.WriteLine("Highlight extraction isn't supported");
        return;
    }
    // พิมพ์ไฮไลท์ที่แยกออกมา
    Console.WriteLine($"At {highlight.Position}: {highlight.Text}");
}
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงพื้นฐานของการใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกและเน้นข้อความจากเอกสาร คุณสามารถสำรวจความสามารถของไลบรารีนี้เพิ่มเติมเพื่อดำเนินการแยกข้อความขั้นสูงเพิ่มเติมได้

### คำถามที่พบบ่อย
### GroupDocs.Parser for .NET เข้ากันได้กับรูปแบบเอกสารต่าง ๆ หรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบไฟล์ที่หลากหลาย รวมถึง DOCX, PDF, TXT และอื่นๆ
### ฉันสามารถแยกส่วนหรือองค์ประกอบเฉพาะจากเอกสารโดยใช้ GroupDocs.Parser ได้หรือไม่
GroupDocs.Parser ช่วยให้สามารถแยกข้อความ รูปภาพ ตาราง และข้อมูลเมตาได้อย่างแม่นยำ
### GroupDocs.Parser เหมาะสำหรับเอกสารขนาดใหญ่หรือไม่
ใช่ GroupDocs.Parser ได้รับการปรับให้เหมาะสมเพื่อการจัดการเอกสารขนาดใหญ่อย่างมีประสิทธิภาพ
### ฉันจะรับการสนับสนุนสำหรับคำถามที่เกี่ยวข้องกับ GroupDocs.Parser ได้ที่ไหน
 เยี่ยมชม[ฟอรัม GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) สำหรับการสนับสนุนและการอภิปรายของชุมชน
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Parser ได้อย่างไร
 คุณจะได้รับ[ใบอนุญาตชั่วคราวที่นี่](https://purchase.groupdocs.com/temporary-license/)เพื่อวัตถุประสงค์ในการทดสอบ