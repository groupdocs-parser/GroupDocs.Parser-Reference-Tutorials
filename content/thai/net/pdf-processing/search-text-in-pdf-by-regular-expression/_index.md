---
title: ค้นหาข้อความในรูปแบบ PDF ด้วยนิพจน์ปกติ
linktitle: ค้นหาข้อความในรูปแบบ PDF ด้วยนิพจน์ปกติ
second_title: GroupDocs.Parser .NET API
description: ค้นหาข้อความเฉพาะในเอกสาร PDF โดยใช้นิพจน์ทั่วไปด้วย GroupDocs.Parser แยก วิเคราะห์ และจัดการข้อความ PDF ได้อย่างง่ายดาย
weight: 19
url: /th/net/pdf-processing/search-text-in-pdf-by-regular-expression/
---

# ค้นหาข้อความในรูปแบบ PDF ด้วยนิพจน์ปกติ

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีการแยกข้อความจากเอกสาร PDF อย่างมีประสิทธิภาพโดยใช้ GroupDocs.Parser สำหรับ .NET GroupDocs.Parser เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถแยกวิเคราะห์และแยกข้อความ เมตาดาต้า และข้อมูลที่มีโครงสร้างจากรูปแบบเอกสารต่างๆ รวมถึง PDF ไม่ว่าคุณจะทำงานเกี่ยวกับการดึงข้อมูล การวิเคราะห์เนื้อหา หรือฟังก์ชันการค้นหาภายในแอปพลิเคชัน .NET ของคุณ GroupDocs.Parser ก็มีชุดเครื่องมือที่ครอบคลุมเพื่อจัดการงานเหล่านี้ได้อย่างราบรื่น
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอนนี้ ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าข้อกำหนดเบื้องต้นต่อไปนี้:
1. สภาพแวดล้อมการพัฒนา: ติดตั้ง Visual Studio หรือสภาพแวดล้อมการพัฒนา .NET ที่ต้องการ
2.  GroupDocs.Parser for .NET: ดาวน์โหลดและติดตั้งไลบรารี GroupDocs.Parser for .NET คุณสามารถค้นหาห้องสมุดและเอกสารประกอบของห้องสมุดได้[ที่นี่](https://releases.groupdocs.com/parser/net/).
3. ไฟล์ PDF ตัวอย่าง: เตรียมไฟล์ PDF ตัวอย่างที่คุณจะใช้ในการค้นหาข้อความ

## นำเข้าเนมสเปซ
ขั้นแรก คุณจะต้องนำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ .NET ของคุณเพื่อเข้าถึงฟังก์ชัน GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของคลาส Parser
 ในการเริ่มต้น ให้ยกตัวอย่าง`Parser` คลาสโดยการระบุเส้นทางไปยังไฟล์ PDF ตัวอย่างของคุณ:
```csharp
using (Parser parser = new Parser("Path_to_Your_PDF_File.pdf"))
{
    // รหัสของคุณสำหรับการค้นหาข้อความจะอยู่ที่นี่
}
```
 แทนที่`"Path_to_Your_PDF_File.pdf"` พร้อมเส้นทางจริงไปยังไฟล์ PDF ของคุณ
## ขั้นตอนที่ 2: ค้นหาข้อความโดยใช้นิพจน์ทั่วไป
 ข้างใน`using` บล็อกของ`Parser`อินสแตนซ์ ดำเนินการค้นหาข้อความโดยใช้นิพจน์ทั่วไป ตัวอย่างนี้สาธิตการค้นหาคำว่า "the" โดยเปิดใช้งานการจับคู่ตัวพิมพ์:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("\\sthe\\s", new SearchOptions(true, false, true));
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
- `\\sthe\\s`: นิพจน์ทั่วไปนี้จะค้นหาคำว่า "the" แบบตรงทั้งหมดโดยมีช่องว่างล้อมรอบ (ขอบเขตคำ)
- `new SearchOptions(true, false, true)`: ตัวเลือกเหล่านี้กำหนดค่าการค้นหาให้คำนึงถึงตัวพิมพ์เล็กและตัวพิมพ์ใหญ่ (`true`) ทั้งคำ (`false`) และนิพจน์ทั่วไป (`true`) การจับคู่

## บทสรุป
ในบทช่วยสอนนี้ เราได้สำรวจวิธีการใช้ GroupDocs.Parser สำหรับ .NET เพื่อค้นหาข้อความในเอกสาร PDF โดยใช้นิพจน์ทั่วไป ไลบรารีนี้ทำให้งานการแยกวิเคราะห์เอกสารที่ซับซ้อนง่ายขึ้น ทำให้ง่ายต่อการแยกและจัดการข้อมูลที่เป็นข้อความภายในแอปพลิเคชัน .NET ของคุณ

## คำถามที่พบบ่อย
### GroupDocs.Parser สามารถจัดการรูปแบบเอกสารอื่นนอกเหนือจาก PDF ได้หรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย เช่น DOCX, XLSX, PPTX และอื่นๆ
### ฉันจะค้นหาแหล่งข้อมูลเพิ่มเติมและการสนับสนุนสำหรับ GroupDocs.Parser ได้ที่ไหน
 ท่านสามารถเยี่ยมชมได้ที่[เอกสาร GroupDocs.Parser](https://tutorials.groupdocs.com/parser/net/) และขอความช่วยเหลือจาก[ฟอรัม GroupDocs](https://forum.groupdocs.com/c/parser/17).
### GroupDocs.Parser มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถเข้าถึง[รุ่นทดลองใช้ฟรี](https://releases.groupdocs.com/) ของ GroupDocs.Parser เพื่อสำรวจคุณลักษณะต่างๆ
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Parser ได้อย่างไร
 คุณสามารถได้รับ[ใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/) เพื่อการทดสอบก่อนซื้อ
### ฉันจะซื้อ GroupDocs.Parser เวอร์ชันลิขสิทธิ์ได้ที่ไหน
 คุณสามารถซื้อ GroupDocs.Parser เวอร์ชันลิขสิทธิ์ได้จาก[ที่นี่](https://purchase.groupdocs.com/buy).