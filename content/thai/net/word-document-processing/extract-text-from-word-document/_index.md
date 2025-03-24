---
title: แยกข้อความจากเอกสาร Word
linktitle: แยกข้อความจากเอกสาร Word
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกข้อความจากเอกสาร Word โดยใช้ GroupDocs.Parser สำหรับ .NET คำแนะนำทีละขั้นตอนพร้อมตัวอย่างโค้ด
weight: 15
url: /th/net/word-document-processing/extract-text-from-word-document/
---

# แยกข้อความจากเอกสาร Word

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีแยกข้อความจากเอกสาร Word โดยใช้ GroupDocs.Parser สำหรับ .NET GroupDocs.Parser เป็นไลบรารี .NET อันทรงประสิทธิภาพที่ช่วยให้นักพัฒนาสามารถทำงานกับเอกสารรูปแบบต่างๆ ได้ รวมถึงเอกสาร Word, PDF และอื่นๆ อีกมากมาย ในตอนท้ายของคู่มือนี้ คุณจะสามารถแยกข้อความจากไฟล์ Word ได้อย่างมีประสิทธิภาพโดยใช้โค้ด C# แบบง่ายๆ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
- Visual Studio (หรือสภาพแวดล้อมการพัฒนา C# ที่ต้องการ)
- ติดตั้ง GroupDocs.Parser สำหรับไลบรารี .NET แล้ว (ดาวน์โหลด[ที่นี่](https://releases.groupdocs.com/parser/net/-)
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C#

## นำเข้าเนมสเปซ
ขั้นแรก คุณต้องนำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ C# ของคุณเพื่อเข้าถึงฟังก์ชัน GroupDocs.Parser
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
 เริ่มต้นด้วยการสร้างอินสแตนซ์ของ`Parser` คลาสเพื่อระบุเส้นทางไปยังเอกสาร Word ของคุณ
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // รหัสของคุณสำหรับการแยกข้อความจะอยู่ที่นี่
}
```
 แทนที่`"YourSampleFile.docx"` พร้อมเส้นทางไปยังเอกสาร Word จริงของคุณ
## ขั้นตอนที่ 2: แยกข้อความลงใน TextReader
 ภายใน`using` บล็อกของ`Parser` เช่น ใช้`GetText()` วิธีการแยกเนื้อหาข้อความออกเป็น`TextReader`.
```csharp
using (TextReader reader = parser.GetText())
{
    // รหัสประมวลผลข้อความของคุณจะไปที่นี่
}
```
## ขั้นตอนที่ 3: อ่านและแสดงข้อความที่แยกออกมา
 ตอนนี้ภายใน`TextReader` บล็อก คุณสามารถอ่านและพิมพ์ข้อความที่แยกจากเอกสาร Word ได้
```csharp
using (TextReader reader = parser.GetText())
{
    // อ่านข้อความที่แยกออกมาแล้วพิมพ์
    Console.WriteLine(reader.ReadToEnd());
}
```

## บทสรุป
ยินดีด้วย! คุณได้เรียนรู้วิธีแยกข้อความจากเอกสาร Word โดยใช้ GroupDocs.Parser for .NET ไลบรารีที่เรียบง่ายแต่ทรงพลังนี้ช่วยให้คุณสามารถรวมความสามารถในการแยกข้อความเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### GroupDocs.Parser เข้ากันได้กับ .NET ทุกเวอร์ชันหรือไม่
ใช่ GroupDocs.Parser สำหรับ .NET เข้ากันได้กับ .NET Framework 4.6.1 และเวอร์ชันที่ใหม่กว่า
### ฉันสามารถแยกข้อความจากเอกสาร Word ที่เข้ารหัสหรือป้องกันด้วยรหัสผ่านได้หรือไม่
GroupDocs.Parser รองรับการแยกข้อความจากเอกสาร Word ที่มีการป้องกันด้วยรหัสผ่าน
### GroupDocs.Parser รองรับรูปแบบเอกสารอื่นนอกเหนือจากเอกสาร Word หรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Excel, PowerPoint และอื่นๆ
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Parser ได้อย่างไร
 คุณสามารถขอใบอนุญาตชั่วคราวสำหรับ GroupDocs.Parser[ที่นี่](https://purchase.groupdocs.com/temporary-license/).
### ฉันจะรับการสนับสนุนเพิ่มเติมหรือถามคำถามเกี่ยวกับ GroupDocs.Parser ได้ที่ไหน
 คุณสามารถเยี่ยมชมฟอรัม GroupDocs.Parser[ที่นี่](https://forum.groupdocs.com/c/parser/17)สำหรับการสนับสนุนและการอภิปราย