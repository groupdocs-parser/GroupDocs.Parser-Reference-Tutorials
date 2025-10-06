---
title: แยกข้อความตามรายการสารบัญ (TOC)
linktitle: แยกข้อความตามรายการสารบัญ (TOC)
second_title: GroupDocs.Parser .NET API
description: แยกข้อความตามสารบัญ (TOC) โดยใช้ GroupDocs.Parser สำหรับ .NET เรียนรู้เทคนิคการแยกวิเคราะห์เอกสารที่มีประสิทธิภาพสำหรับการดึงข้อมูลที่มีโครงสร้าง
weight: 15
url: /th/net/text-extraction/extract-text-by-toc-item/
type: docs
---
# แยกข้อความตามรายการสารบัญ (TOC)

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีการใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกข้อความตามรายการสารบัญ (TOC) จากเอกสาร GroupDocs.Parser เป็นเครื่องมืออันทรงพลังที่ช่วยให้การแยกวิเคราะห์และการแยกเอกสารมีประสิทธิภาพ
## ข้อกำหนดเบื้องต้น
ก่อนดำเนินการบทช่วยสอนนี้ ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1. Visual Studio: ติดตั้ง Visual Studio IDE บนระบบของคุณ
2.  GroupDocs.Parser for .NET: ดาวน์โหลดและติดตั้ง GroupDocs.Parser for .NET จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
3. เอกสารตัวอย่างที่มี TOC: เตรียมเอกสาร (เช่น PDF, DOCX) ที่มีสารบัญ

## การนำเข้าเนมสเปซ
ขั้นแรก รวมเนมสเปซที่จำเป็นในโครงการ C# ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
 ยกตัวอย่าง`Parser` คลาสพร้อมพาธไปยังเอกสารตัวอย่างของคุณ:
```csharp
using (Parser parser = new Parser("YourSampleFileWithToc"))
{
    // ทำตามขั้นตอนต่อไปได้ที่นี่...
}
```
## ขั้นตอนที่ 2: แยกสารบัญ (TOC)
รับรายการสารบัญ (TOC) จากเอกสาร:
```csharp
IEnumerable<TocItem> tocItems = parser.GetToc();
if (tocItems == null)
{
    Console.WriteLine("Table of contents extraction isn't supported");
    return;
}
```
## ขั้นตอนที่ 3: วนซ้ำรายการ TOC และแยกข้อความ
วนซ้ำแต่ละรายการ TOC และแยกข้อความที่เกี่ยวข้อง:
```csharp
foreach (TocItem tocItem in tocItems)
{
    using (TextReader reader = tocItem.ExtractText())
    {
        Console.WriteLine("----");
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## บทสรุป
บทช่วยสอนนี้ได้สาธิตวิธีการแยกข้อความจากเอกสารตามรายการสารบัญ (TOC) โดยใช้ GroupDocs.Parser สำหรับ .NET เมื่อทำตามขั้นตอนที่ระบุไว้ คุณจะสามารถแยกวิเคราะห์และแยกเนื้อหาเฉพาะจากเอกสารของคุณโดยทางโปรแกรมได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### GroupDocs.Parser รองรับไฟล์รูปแบบใดบ้าง
GroupDocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Microsoft Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX) และอื่นๆ
### ฉันสามารถดึงข้อมูลที่มีโครงสร้าง เช่น ตารางหรือรูปภาพโดยใช้ GroupDocs.Parser ได้หรือไม่
ใช่ GroupDocs.Parser มี API เพื่อดึงข้อมูลที่มีโครงสร้าง เช่น ตาราง รูปภาพ และข้อมูลเมตาจากเอกสารประเภทต่างๆ
### GroupDocs.Parser เหมาะสำหรับเอกสารขนาดใหญ่หรือไม่
GroupDocs.Parser ได้รับการปรับให้เหมาะสมสำหรับการจัดการเอกสารขนาดใหญ่อย่างมีประสิทธิภาพ ช่วยให้สามารถแยกเนื้อหาจากไฟล์ขนาดใหญ่ได้อย่างราบรื่น
### ฉันจะรับการสนับสนุนทางเทคนิคสำหรับ GroupDocs.Parser ได้อย่างไร
 คุณสามารถขอรับการสนับสนุนทางเทคนิคและโต้ตอบกับชุมชนได้ที่[ฟอรัม GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).
### GroupDocs เสนอให้ทดลองใช้งานประเมินผลฟรีหรือไม่
ใช่ คุณสามารถดาวน์โหลด GroupDocs.Parser เวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).