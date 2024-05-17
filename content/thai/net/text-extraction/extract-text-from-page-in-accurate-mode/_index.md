---
title: แยกข้อความออกจากเพจในโหมดแม่นยำ
linktitle: แยกข้อความออกจากเพจในโหมดแม่นยำ
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกข้อความจากเอกสารอย่างถูกต้องโดยใช้ GroupDocs.Parser สำหรับ .NET ในบทช่วยสอนที่ครอบคลุมนี้
type: docs
weight: 16
url: /th/net/text-extraction/extract-text-from-page-in-accurate-mode/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกข้อความจากเอกสารในโหมดที่แม่นยำ GroupDocs.Parser เป็น API อันทรงพลังที่ช่วยให้นักพัฒนาสามารถทำงานกับรูปแบบเอกสารที่หลากหลายในแอปพลิเคชัน .NET ของตน ทำให้สามารถแยกข้อความได้อย่างแม่นยำและง่ายดาย ในตอนท้ายของคู่มือนี้ คุณจะพร้อมที่จะใช้ประโยชน์จากความสามารถของ GroupDocs.Parser เพื่อแยกข้อความจากเอกสารได้อย่างมีประสิทธิภาพ
## ข้อกำหนดเบื้องต้น
ก่อนดำเนินการต่อ ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
- การตั้งค่าสภาพแวดล้อม: มีสภาพแวดล้อมการทำงานที่ติดตั้ง .NET
-  การติดตั้ง GroupDocs.Parser: ดาวน์โหลดและติดตั้ง GroupDocs.Parser สำหรับ .NET จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
- ความเข้าใจพื้นฐานของ C#: ความคุ้นเคยกับภาษาการเขียนโปรแกรม C# จะเป็นประโยชน์
## นำเข้าเนมสเปซ
ก่อนที่จะเริ่มใช้งาน ตรวจสอบให้แน่ใจว่าได้นำเข้าเนมสเปซที่จำเป็นแล้ว:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
 ขั้นแรก สร้างอินสแตนซ์ของ`Parser` คลาสโดยระบุเส้นทางไปยังไฟล์ตัวอย่างของคุณ
```csharp
using (Parser parser = new Parser("YourSampleFile"))
{
    // การติดตั้งโค้ดอยู่ที่นี่
}
```
## ขั้นตอนที่ 2: ตรวจสอบการสนับสนุนการแยกข้อความ
 จากนั้นตรวจสอบว่าเอกสารรองรับการแยกข้อความโดยใช้หรือไม่`Features.Text` คุณสมบัติ.
```csharp
if (!parser.Features.Text)
{
    Console.WriteLine("Document doesn't support text extraction.");
    return;
}
```
## ขั้นตอนที่ 3: รับข้อมูลเอกสาร
 รับข้อมูลเกี่ยวกับเอกสารโดยใช้`GetDocumentInfo()` วิธี.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document doesn't have pages.");
    return;
}
```
## ขั้นตอนที่ 4: วนซ้ำหน้าต่างๆ และแยกข้อความ
 วนซ้ำแต่ละหน้าของเอกสารและแยกข้อความโดยใช้`GetText()` วิธี.
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    using (TextReader reader = parser.GetText(p))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงกระบวนการแยกข้อความจากเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET เมื่อทำตามขั้นตอนเหล่านี้ คุณจะสามารถรวมฟังก์ชันการแยกข้อความเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น ช่วยให้คุณสามารถทำงานกับเอกสารรูปแบบต่างๆ ได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### GroupDocs.Parser เหมาะสำหรับการแยกข้อความจากรูปแบบเอกสารที่ซับซ้อนหรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย รวมถึงรูปแบบที่ซับซ้อน เช่น PDF, DOCX และอื่นๆ อีกมากมาย
### ฉันสามารถแยกข้อความบางส่วนจากเอกสารโดยใช้ API นี้ได้หรือไม่
แน่นอน คุณสามารถแยกข้อความจากหน้าใดหน้าหนึ่ง หรือแม้แต่กำหนดพื้นที่แยกแบบกำหนดเองภายในเอกสารได้
### GroupDocs.Parser รักษาการจัดรูปแบบในระหว่างการแยกข้อความหรือไม่
GroupDocs.Parser มุ่งเน้นไปที่การแยกข้อความที่แม่นยำในขณะที่ยังคงรักษาการจัดรูปแบบเอกสารตามความเหมาะสม
### มีเวอร์ชันทดลองใช้งานสำหรับทดสอบ GroupDocs.Parser หรือไม่
 ใช่ คุณสามารถรับเวอร์ชันทดลองใช้ฟรีได้[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนหรือความช่วยเหลือเพิ่มเติมเกี่ยวกับ GroupDocs.Parser ได้ที่ไหน
 ท่านสามารถเยี่ยมชมได้ที่[ฟอรัม GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) สำหรับข้อสงสัยการสนับสนุนใด ๆ