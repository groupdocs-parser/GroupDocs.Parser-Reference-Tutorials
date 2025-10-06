---
title: แยกสารบัญออกจากเอกสาร Word
linktitle: แยกสารบัญออกจากเอกสาร Word
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกสารบัญ (TOC) จากเอกสาร Word โดยทางโปรแกรมโดยใช้ GroupDocs.Parser สำหรับ .NET
weight: 13
url: /th/net/word-document-processing/extract-table-of-contents-from-word-document/
type: docs
---
# แยกสารบัญออกจากเอกสาร Word

## การแนะนำ
ในบทช่วยสอนนี้ คุณจะได้เรียนรู้วิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกสารบัญ (TOC) ออกจากเอกสาร Word ทีละขั้นตอน GroupDocs.Parser เป็นไลบรารีที่มีประสิทธิภาพซึ่งช่วยให้คุณทำงานกับรูปแบบเอกสารต่างๆ โดยทางโปรแกรม
## ข้อกำหนดเบื้องต้น
ก่อนที่คุณจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1. Visual Studio: ติดตั้ง Visual Studio IDE บนระบบของคุณ
2.  GroupDocs.Parser for .NET: ดาวน์โหลดและติดตั้ง GroupDocs.Parser for .NET จาก[หน้าดาวน์โหลด](https://releases.groupdocs.com/parser/net/).
3. ความรู้พื้นฐานของ C#: ความคุ้นเคยกับภาษาการเขียนโปรแกรม C#

## นำเข้าเนมสเปซ
ขั้นแรก นำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ C# ของคุณเพื่อใช้ GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
เริ่มต้นคลาส Parser โดยระบุเส้นทางไปยังเอกสาร Word ตัวอย่างของคุณ:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // รหัสของคุณอยู่ที่นี่
}
```
## ขั้นตอนที่ 2: ดึงสารบัญ (TOC)
 ใช้`GetToc()` วิธีการของ`Parser` วัตถุเพื่อแยกสารบัญ:
```csharp
IEnumerable<TocItem> tocItems = parser.GetToc();
```
## ขั้นตอนที่ 3: ทำซ้ำรายการ TOC
วนซ้ำรายการ TOC ที่ได้รับในขั้นตอนก่อนหน้าเพื่อเข้าถึงแต่ละบทหรือส่วน:
```csharp
foreach (TocItem tocItem in tocItems)
{
    // รหัสของคุณอยู่ที่นี่
}
```
## ขั้นตอนที่ 4: แยกข้อความออกจากรายการ TOC
 แยกและพิมพ์เนื้อหาข้อความของแต่ละรายการ TOC (บท) โดยใช้`TextReader`-
```csharp
using (TextReader reader = tocItem.ExtractText())
{
    Console.WriteLine("----");
    Console.WriteLine(reader.ReadToEnd());
}
```

## บทสรุป
ด้วยการทำตามขั้นตอนเหล่านี้ คุณสามารถแยกสารบัญจากเอกสาร Word ได้อย่างง่ายดายโดยใช้ GroupDocs.Parser สำหรับ .NET ไลบรารีนี้มอบวิธีที่ตรงไปตรงมาในการทำงานกับโครงสร้างเอกสารโดยทางโปรแกรม ช่วยให้คุณสามารถดำเนินงานการประมวลผลเอกสารต่างๆ โดยอัตโนมัติได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### GroupDocs.Parser สามารถแยก TOC จากเอกสารรูปแบบอื่น เช่น PDF หรือ EPUB ได้หรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, EPUB, Word, Excel, PowerPoint และอื่นๆ
### GroupDocs.Parser เหมาะสำหรับการประมวลผลเอกสารขนาดใหญ่หรือไม่
ใช่ GroupDocs.Parser ได้รับการปรับให้เหมาะสมเพื่อการจัดการเอกสารขนาดใหญ่อย่างมีประสิทธิภาพ ด้วยฟีเจอร์ต่างๆ เช่น การแยกข้อความ การแยกข้อมูลเมตา และการแยกข้อมูลที่มีโครงสร้าง
### ฉันจะหาเอกสารและบทช่วยสอนเพิ่มเติมสำหรับ GroupDocs.Parser ได้ที่ไหน
 เยี่ยมชม[เอกสาร GroupDocs.Parser](https://tutorials.groupdocs.com/parser/net/) สำหรับการอ้างอิง API โดยละเอียดและบทช่วยสอน
### ฉันจะรับการสนับสนุนสำหรับ GroupDocs.Parser ได้อย่างไร
 เข้าร่วม[ฟอรัม GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) เพื่อถามคำถามและโต้ตอบกับชุมชน
### มีรุ่นทดลองใช้งานสำหรับ GroupDocs.Parser หรือไม่
 ใช่ คุณสามารถดาวน์โหลด[ทดลองฟรี](https://releases.groupdocs.com/) ของ GroupDocs.Parser เพื่อสำรวจคุณลักษณะต่างๆ