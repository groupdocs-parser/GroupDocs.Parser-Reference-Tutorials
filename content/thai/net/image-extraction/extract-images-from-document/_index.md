---
title: แยกรูปภาพออกจากเอกสาร
linktitle: แยกรูปภาพออกจากเอกสาร
second_title: GroupDocs.Parser .NET API
description: แยกรูปภาพออกจากเอกสารได้อย่างง่ายดายโดยใช้ GroupDocs.Parser สำหรับ .NET ความสามารถในการประมวลผลเอกสารของคุณและปรับปรุงงานการแยกภาพได้อย่างมีประสิทธิภาพ
weight: 11
url: /th/net/image-extraction/extract-images-from-document/
---

# แยกรูปภาพออกจากเอกสาร

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีการแยกรูปภาพจากเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET GroupDocs.Parser เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถแยกข้อความ เมตาดาต้า รูปภาพ และอื่นๆ จากรูปแบบเอกสารต่างๆ ได้
## ข้อกำหนดเบื้องต้น
ก่อนที่คุณจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าข้อกำหนดเบื้องต้นต่อไปนี้:
- Visual Studio: ติดตั้ง Visual Studio บนเครื่องของคุณ
-  GroupDocs.Parser สำหรับ .NET: ดาวน์โหลดและติดตั้ง GroupDocs.Parser จาก[หน้าดาวน์โหลด](https://releases.groupdocs.com/parser/net/).
- เอกสารตัวอย่าง: เตรียมเอกสารตัวอย่าง (PDF, DOCX ฯลฯ) ที่คุณต้องการแยกรูปภาพ

## นำเข้าเนมสเปซ
เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ C# ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของคลาส Parser
 ขั้นแรก สร้างอินสแตนซ์ของ`Parser` คลาสโดยระบุเส้นทางไปยังเอกสารตัวอย่างของคุณ
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // รหัสของคุณอยู่ที่นี่
}
```
 แทนที่`"YourSampleFile.pdf"` พร้อมเส้นทางไปยังไฟล์เอกสารของคุณ
## ขั้นตอนที่ 2: แยกรูปภาพออกจากเอกสาร
 จากนั้น แยกรูปภาพออกจากเอกสารโดยใช้`GetImages()` วิธี.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
 ที่`GetImages()` วิธีการส่งคืนคอลเลกชันของ`PageImageArea` วัตถุที่แสดงภาพที่พบในเอกสาร
## ขั้นตอนที่ 3: ตรวจสอบการสนับสนุนการแยกรูปภาพ
ก่อนที่จะวนซ้ำรูปภาพ ให้ตรวจสอบว่าเอกสารรองรับการแยกรูปภาพหรือไม่
```csharp
if (images == null)
{
    Console.WriteLine("Images extraction isn't supported");
    return;
}
```
ขั้นตอนนี้ช่วยให้แน่ใจว่าเอกสารมีรูปภาพที่สามารถแยกออกมาได้
## ขั้นตอนที่ 4: ทำซ้ำรูปภาพที่แยกออกมา
ตอนนี้ ให้วนซ้ำรูปภาพที่แยกออกมาเพื่อเข้าถึงข้อมูลโดยละเอียดเกี่ยวกับรูปภาพแต่ละรูป เช่น ดัชนีหน้า พิกัดสี่เหลี่ยม และประเภทรูปภาพ
```csharp
foreach (PageImageArea image in images)
{
    Console.WriteLine($"Page: {image.Page.Index}, Rectangle: {image.Rectangle}, Type: {image.FileType}");
}
```
ลูปนี้จะพิมพ์ข้อมูลเกี่ยวกับภาพที่แยกออกมาแต่ละภาพ รวมถึงตำแหน่งและประเภทของภาพ

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกรูปภาพจากเอกสารโดยทางโปรแกรม ด้วยการทำตามขั้นตอนเหล่านี้ คุณสามารถรวมฟังก์ชันการแยกรูปภาพเอกสารเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น

## คำถามที่พบบ่อย
### GroupDocs.Parser สามารถแยกรูปภาพจากเอกสารทุกรูปแบบได้หรือไม่
GroupDocs.Parser รองรับการแยกรูปภาพจากรูปแบบต่างๆ รวมถึง PDF, DOCX, XLSX และอื่นๆ
### GroupDocs.Parser มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถเข้าถึง GroupDocs.Parser รุ่นทดลองใช้ฟรีได้จาก[เว็บไซต์](https://releases.groupdocs.com/).
### ฉันจะหาเอกสารสำหรับ GroupDocs.Parser ได้ที่ไหน
 สามารถดูเอกสารประกอบโดยละเอียดสำหรับ GroupDocs.Parser ได้[ที่นี่](https://tutorials.groupdocs.com/parser/net/).
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Parser ได้อย่างไร
 คุณสามารถขอรับใบอนุญาตชั่วคราวได้จาก[หน้าใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/).
### ฉันจะรับการสนับสนุนสำหรับ GroupDocs.Parser ได้ที่ไหน
 สำหรับการสนับสนุนทางเทคนิคและความช่วยเหลือ โปรดไปที่[ฟอรัม GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).