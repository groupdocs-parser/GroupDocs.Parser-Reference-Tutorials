---
title: แยกรูปภาพออกจากหน้าเอกสาร
linktitle: แยกรูปภาพออกจากหน้าเอกสาร
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกรูปภาพจากเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET เพิ่มความสามารถในการประมวลผลเอกสารของคุณ
weight: 12
url: /th/net/image-extraction/extract-images-from-document-page/
---

# แยกรูปภาพออกจากหน้าเอกสาร

## การแนะนำ
ในบทช่วยสอนนี้ เราจะได้เรียนรู้วิธีแยกรูปภาพจากหน้าเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET GroupDocs.Parser เป็นไลบรารีที่มีประสิทธิภาพซึ่งช่วยให้คุณสามารถดึงข้อความ ข้อมูลเมตา รูปภาพ และอื่นๆ จากรูปแบบเอกสารต่างๆ เช่น PDF, Microsoft Word, Excel, PowerPoint และอื่นๆ เราจะอธิบายขั้นตอนที่จำเป็นเพื่อแยกรูปภาพออกจากหน้าเอกสารโดยใช้ไลบรารีนี้
## ข้อกำหนดเบื้องต้น
ก่อนที่คุณจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
- ติดตั้ง Visual Studio บนเครื่องของคุณแล้ว
- ความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรม C# และ .NET
- ติดตั้ง GroupDocs.Parser สำหรับไลบรารี .NET แล้ว คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).

## นำเข้าเนมสเปซ
เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ C# ของคุณเพื่อใช้ฟังก์ชันของ GroupDocs.Parser
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของคลาส Parser
 เริ่มต้นด้วยการสร้างอินสแตนซ์ของ`Parser` และระบุเส้นทางไปยังเอกสารตัวอย่างของคุณ
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // รหัสของคุณที่นี่
}
```
## ขั้นตอนที่ 2: ตรวจสอบเอกสารสำหรับการรองรับการแยกรูปภาพ
 จากนั้นตรวจสอบว่าเอกสารรองรับการแยกรูปภาพโดยใช้หรือไม่`Features.Images` คุณสมบัติ.
```csharp
if (!parser.Features.Images)
{
    Console.WriteLine("Document doesn't support image extraction.");
    return;
}
```
## ขั้นตอนที่ 3: รับข้อมูลเอกสาร
 ดึงข้อมูลเกี่ยวกับเอกสารโดยใช้`GetDocumentInfo()` วิธี.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## ขั้นตอนที่ 4: วนซ้ำหน้าเอกสาร
ตรวจสอบว่าเอกสารมีหน้าหรือไม่ จากนั้นวนซ้ำแต่ละหน้าเพื่อแยกรูปภาพ
```csharp
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // รหัสของคุณเพื่อแยกภาพออกจากหน้า
}
```
## ขั้นตอนที่ 5: แยกรูปภาพจากแต่ละหน้า
 ภายในลูปการวนซ้ำเพจ ให้ใช้`GetImages(pageIndex)` วิธีการดึงภาพจากแต่ละหน้า
```csharp
foreach (PageImageArea image in parser.GetImages(pageIndex))
{
    Console.WriteLine($"Rectangle: {image.Rectangle}, FileType: {image.FileType}");
    // โค้ดเพิ่มเติมสำหรับบันทึกหรือประมวลผลรูปภาพ
}
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้สำรวจวิธีแยกรูปภาพจากหน้าเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET เราได้ครอบคลุมขั้นตอนที่สำคัญต่างๆ เช่น การสร้างอินสแตนซ์ parser การตรวจสอบการสนับสนุนการแยกรูปภาพ การดึงข้อมูลเอกสาร การวนซ้ำหน้าต่างๆ และการแยกรูปภาพจากแต่ละหน้า ตอนนี้คุณสามารถรวมฟังก์ชันการแยกรูปภาพเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### GroupDocs.Parser สามารถแยกรูปภาพจากเอกสาร PDF ได้หรือไม่
ใช่ GroupDocs.Parser รองรับการแยกรูปภาพจากเอกสารรูปแบบต่างๆ รวมถึง PDF
### GroupDocs.Parser เหมาะสำหรับการประมวลผลเอกสารเป็นชุดหรือไม่
อย่างแน่นอน! คุณสามารถใช้ GroupDocs.Parser เพื่อประมวลผลเอกสารหลายชุดเป็นชุดและแยกเนื้อหาที่ต้องการได้อย่างมีประสิทธิภาพ
### ฉันจะค้นหาแหล่งข้อมูลเพิ่มเติมและการสนับสนุนสำหรับ GroupDocs.Parser ได้ที่ไหน
 ท่านสามารถเยี่ยมชมได้ที่[ฟอรัม GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) สำหรับการสนับสนุนและการอภิปรายของชุมชน
### ฉันสามารถลองใช้ GroupDocs.Parser ก่อนซื้อได้หรือไม่
 ใช่ คุณจะได้รับ[รุ่นทดลองใช้ฟรี](https://releases.groupdocs.com/) เพื่อประเมินความสามารถของห้องสมุด
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Parser ได้อย่างไร
 คุณสามารถได้รับ[ใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/) เพื่อวัตถุประสงค์ในการทดสอบและพัฒนา