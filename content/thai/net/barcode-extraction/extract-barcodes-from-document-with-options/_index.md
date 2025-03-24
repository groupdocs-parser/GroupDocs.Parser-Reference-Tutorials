---
title: แยกบาร์โค้ดออกจากเอกสารพร้อมตัวเลือก
linktitle: แยกบาร์โค้ดออกจากเอกสารพร้อมตัวเลือก
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกบาร์โค้ดออกจากเอกสารโดยใช้ GroupDocs.Parser for .NET บทช่วยสอนที่ครอบคลุมพร้อมตัวอย่างโค้ดและคำถามที่พบบ่อย
weight: 14
url: /th/net/barcode-extraction/extract-barcodes-from-document-with-options/
---

# แยกบาร์โค้ดออกจากเอกสารพร้อมตัวเลือก

## การแนะนำ
ในบทช่วยสอนนี้ เราจะอธิบายขั้นตอนการแยกบาร์โค้ดออกจากเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET GroupDocs.Parser เป็นไลบรารีที่มีประสิทธิภาพซึ่งช่วยให้คุณสามารถแยกข้อความ ข้อมูลเมตา และบาร์โค้ดจากรูปแบบเอกสารต่างๆ เช่น PDF, Microsoft Word, Excel และอื่นๆ
## ข้อกำหนดเบื้องต้น
ก่อนที่คุณจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1. สภาพแวดล้อมการพัฒนา: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Visual Studio บนเครื่องของคุณ
2.  GroupDocs.Parser Library: ดาวน์โหลดและติดตั้งไลบรารี GroupDocs.Parser สำหรับ .NET จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
3. เอกสารตัวอย่าง: เตรียมเอกสารตัวอย่าง (เช่น PDF, DOCX) ที่มีบาร์โค้ดสำหรับการแยก

## นำเข้าเนมสเปซ
ขั้นแรก คุณต้องนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณเพื่อใช้ฟังก์ชัน GroupDocs.Parser
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using System;
using System.Collections.Generic;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
 ในการเริ่มต้น ให้สร้างอินสแตนซ์ของ`Parser` คลาสโดยส่งพาธไปยังเอกสารตัวอย่างของคุณ
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // รหัสที่จะเพิ่มในขั้นตอนถัดไป
}
```
## ขั้นตอนที่ 2: ตรวจสอบการสนับสนุนการแยกบาร์โค้ด
 ถัดไป ตรวจสอบว่าเอกสารรองรับการแยกบาร์โค้ดโดยใช้หรือไม่`Features` ทรัพย์สินของ`Parser` ตัวอย่าง.
```csharp
if (!parser.Features.Barcodes)
{
    Console.WriteLine("Document doesn't support barcode extraction.");
    return;
}
```
## ขั้นตอนที่ 3: กำหนดตัวเลือกการแยกบาร์โค้ด
 ตอนนี้ ให้ระบุตัวเลือกสำหรับการแยกบาร์โค้ดโดยใช้`BarcodeOptions`- คุณสามารถตั้งค่าพารามิเตอร์ เช่น โหมดคุณภาพและประเภทบาร์โค้ดได้
```csharp
BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```
## ขั้นตอนที่ 4: แยกบาร์โค้ดออกจากเอกสาร
 ใช้`GetBarcodes` วิธีการของ`Parser` คลาสเพื่อแยกบาร์โค้ดตามตัวเลือกที่กำหนดไว้
```csharp
IEnumerable<PageBarcodeArea> barcodes = parser.GetBarcodes(options);
```
## ขั้นตอนที่ 5: ทำซ้ำและแสดงบาร์โค้ดที่แยกออกมา
สุดท้าย วนซ้ำบาร์โค้ดที่แยกออกมา และแสดงดัชนีหน้าและค่าต่างๆ
```csharp
foreach (PageBarcodeArea barcode in barcodes)
{
    Console.WriteLine("Page: " + barcode.Page.Index.ToString());
    Console.WriteLine("Value: " + barcode.Value);
}
```

## บทสรุป
 ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีแยกบาร์โค้ดออกจากเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET กระบวนการนี้เกี่ยวข้องกับการสร้าง`Parser` เช่น การกำหนดตัวเลือกการแยก และวนซ้ำผ่านบาร์โค้ดที่แยกออกมา GroupDocs.Parser ทำให้งานแยกบาร์โค้ดจากเอกสารรูปแบบต่างๆ ง่ายขึ้น ช่วยให้สามารถประมวลผลเอกสารภายในแอปพลิเคชัน .NET ของคุณได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### GroupDocs.Parser สามารถแยกบาร์โค้ดออกจากเอกสาร PDF ได้หรือไม่
ใช่ GroupDocs.Parser รองรับการแยกบาร์โค้ดจากเอกสาร PDF พร้อมกับรูปแบบอื่นๆ เช่น DOCX, XLSX เป็นต้น
### GroupDocs.Parser รองรับบาร์โค้ดประเภทใดบ้าง
GroupDocs.Parser รองรับบาร์โค้ดหลายประเภท รวมถึงรหัส QR, รหัส 39, รหัส 128 และอื่นๆ
### GroupDocs.Parser ต้องมีใบอนุญาตสำหรับการใช้งานเชิงพาณิชย์หรือไม่
 ใช่ จำเป็นต้องมีใบอนุญาตที่ถูกต้องสำหรับการใช้งานเชิงพาณิชย์ คุณสามารถขอรับใบอนุญาตได้จาก[ที่นี่](https://purchase.groupdocs.com/buy).
### GroupDocs.Parser เหมาะสำหรับการประมวลผลเอกสารเป็นชุดหรือไม่
ใช่ GroupDocs.Parser สามารถจัดการการประมวลผลเอกสารเป็นชุดสำหรับการดึงข้อความ การดึงข้อมูลเมตา และการดึงบาร์โค้ดได้อย่างมีประสิทธิภาพ
### ฉันจะรับการสนับสนุนด้านเทคนิคสำหรับ GroupDocs.Parser ได้ที่ไหน
 คุณสามารถรับการสนับสนุนทางเทคนิคหรือถามคำถามได้ที่[ฟอรัม GroupDocs](https://forum.groupdocs.com/c/parser/17).