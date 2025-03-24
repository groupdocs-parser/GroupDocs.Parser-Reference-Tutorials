---
title: แยกข้อความจากหน้าในรูปแบบ PDF ในโหมด Raw
linktitle: แยกข้อความจากหน้าในรูปแบบ PDF ในโหมด Raw
second_title: GroupDocs.Parser .NET API
description: แยกข้อความจาก PDF โดยใช้ GroupDocs.Parser ใน C# เรียนรู้การแยกข้อความ PDF ที่มีประสิทธิภาพด้วยไลบรารี .NET อันทรงพลังนี้
weight: 16
url: /th/net/pdf-processing/extract-text-from-page-in-pdf-in-raw-mode/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกข้อความจากหน้าในเอกสาร PDF โดยใช้โหมด Raw GroupDocs.Parser เป็นเครื่องมืออันทรงพลังที่ช่วยให้นักพัฒนาสามารถทำงานกับเอกสารรูปแบบต่างๆ โดยทางโปรแกรม
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเริ่มบทช่วยสอนนี้ ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
- ติดตั้ง Visual Studio บนเครื่องของคุณแล้ว
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C#
- GroupDocs.Parser สำหรับไลบรารี .NET ซึ่งคุณสามารถทำได้[ดาวน์โหลดได้ที่นี่](https://releases.groupdocs.com/parser/net/).
- ไฟล์ PDF ตัวอย่างเพื่อการทดสอบ

## นำเข้าเนมสเปซ
ขั้นแรก ตรวจสอบให้แน่ใจว่าได้นำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ C# ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
 ในการเริ่มต้น ให้ยกตัวอย่าง`Parser`คลาสโดยระบุเส้นทางไปยังไฟล์ PDF ตัวอย่างของคุณ
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // รหัสของคุณอยู่ที่นี่
}
```
## ขั้นตอนที่ 2: รับข้อมูลเอกสารและวนซ้ำหน้าต่างๆ
จากนั้น ดึงข้อมูลเอกสารและวนซ้ำแต่ละหน้าเพื่อแยกข้อความ
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // รหัสของคุณสำหรับการแยกข้อความอยู่ที่นี่
}
```
## ขั้นตอนที่ 3: แยกข้อความจากแต่ละหน้า
 ภายในลูปให้ใช้`GetText` วิธีการแยกข้อความจากแต่ละหน้าแล้วพิมพ์
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## บทสรุป
 ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีแยกข้อความจากหน้า PDF ในโหมด Raw โดยใช้ GroupDocs.Parser สำหรับ .NET กระบวนการนี้เกี่ยวข้องกับการสร้าง`Parser` เช่น การได้รับข้อมูลเอกสาร การวนซ้ำแต่ละหน้า และการแยกข้อความโดยใช้`GetText` วิธี.

## คำถามที่พบบ่อย
### GroupDocs.Parser สำหรับ .NET คืออะไร
GroupDocs.Parser สำหรับ .NET เป็น API การแยกวิเคราะห์เอกสารที่ช่วยให้นักพัฒนาสามารถดึงข้อความ ข้อมูลเมตา และข้อมูลอื่น ๆ จากรูปแบบไฟล์ต่างๆ โดยทางโปรแกรม
### ฉันจะดาวน์โหลด GroupDocs.Parser สำหรับ .NET ได้อย่างไร
 คุณสามารถดาวน์โหลดห้องสมุดได้จาก[เว็บไซต์กรุ๊ปดอคส์](https://releases.groupdocs.com/parser/net/).
### มีการทดลองใช้ฟรีหรือไม่?
 ใช่ คุณสามารถเข้าถึง GroupDocs.Parser สำหรับ .NET รุ่นทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนสำหรับ GroupDocs.Parser สำหรับ .NET ได้ที่ไหน
 สำหรับความช่วยเหลือด้านเทคนิคและการสนับสนุนชุมชน โปรดไปที่[ฟอรัม GroupDocs](https://forum.groupdocs.com/c/parser/17).
### ฉันจะซื้อใบอนุญาตสำหรับ GroupDocs.Parser สำหรับ .NET ได้อย่างไร
 คุณสามารถซื้อใบอนุญาตได้จาก[หน้าซื้อ](https://purchase.groupdocs.com/buy) หรือได้รับใบอนุญาตชั่วคราว[ที่นี่](https://purchase.groupdocs.com/temporary-license/).