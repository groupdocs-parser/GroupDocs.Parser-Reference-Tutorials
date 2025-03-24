---
title: แยกข้อความจากแผ่นงาน Excel ในโหมด Raw
linktitle: แยกข้อความจากแผ่นงาน Excel ในโหมด Raw
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกข้อความจากชีต Excel โดยใช้ GroupDocs.Parser สำหรับ .NET ในบทช่วยสอนที่ครอบคลุมนี้ ดาวน์โหลดและเริ่มแยกวิเคราะห์
weight: 15
url: /th/net/excel-document-processing/extract-text-from-excel-sheet-in-raw-mode/
---

# แยกข้อความจากแผ่นงาน Excel ในโหมด Raw

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีแยกข้อความจากชีต Excel โดยใช้ GroupDocs.Parser สำหรับ .NET ในโหมด Raw GroupDocs.Parser เป็น API อันทรงพลังที่ช่วยให้นักพัฒนาสามารถทำงานกับรูปแบบเอกสารที่หลากหลาย รวมถึงไฟล์ Excel เพื่อแยกและวิเคราะห์ข้อความ เราจะอธิบายข้อกำหนดเบื้องต้น นำเข้าเนมสเปซ และแจกแจงแต่ละขั้นตอนเพื่อสาธิตกระบวนการแยกข้อความจากชีต Excel
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าข้อกำหนดเบื้องต้นต่อไปนี้:
- Visual Studio: ติดตั้ง Visual Studio IDE บนเครื่องของคุณ
-  GroupDocs.Parser สำหรับ .NET: ดาวน์โหลดและติดตั้ง GroupDocs.Parser จาก[หน้าดาวน์โหลด](https://releases.groupdocs.com/parser/net/).
- ไฟล์ Excel ตัวอย่าง: เตรียมไฟล์ Excel ตัวอย่างที่คุณจะใช้สำหรับการแยกข้อความ

## นำเข้าเนมสเปซ
เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณเพื่อเข้าถึงฟังก์ชันการทำงานของ GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
 ขั้นแรก สร้างอินสแตนซ์ของ`Parser` คลาสโดยระบุเส้นทางไปยังไฟล์ Excel ตัวอย่างของคุณ:
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // รหัสของคุณสำหรับการแยกข้อความจะอยู่ที่นี่
}
```
## ขั้นตอนที่ 2: รับข้อมูลเอกสาร
 ดึงข้อมูลเอกสารโดยใช้`GetDocumentInfo()` วิธี:
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## ขั้นตอนที่ 3: ทำซ้ำบนชีต
วนซ้ำแต่ละแผ่นงานในไฟล์ Excel:
```csharp
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine(string.Format("Page {0}/{1}", p + 1, documentInfo.RawPageCount));
    
    //รหัสของคุณสำหรับการแยกข้อความจากแต่ละแผ่นจะอยู่ที่นี่
}
```
## ขั้นตอนที่ 4: แยกข้อความจากแต่ละแผ่น
 แยกข้อความจากแต่ละแผ่นโดยใช้`TextReader`-
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงวิธีการแยกข้อความจากชีต Excel โดยใช้ GroupDocs.Parser สำหรับ .NET ด้วยการทำตามขั้นตอนที่อธิบายไว้ข้างต้น คุณสามารถดึงข้อมูลข้อความจากไฟล์ Excel ได้อย่างมีประสิทธิภาพสำหรับการประมวลผลหรือการวิเคราะห์เพิ่มเติมในแอปพลิเคชัน .NET ของคุณ

## คำถามที่พบบ่อย
### GroupDocs.Parser สามารถแยกข้อความจากรูปแบบเอกสารอื่นได้หรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง Word, PDF, PowerPoint และอื่นๆ
### GroupDocs.Parser เหมาะสำหรับการประมวลผลไฟล์ Excel ขนาดใหญ่หรือไม่
ใช่ GroupDocs.Parser ได้รับการออกแบบมาเพื่อจัดการเอกสารขนาดใหญ่อย่างมีประสิทธิภาพ
### ฉันจะหาเอกสารเพิ่มเติมเกี่ยวกับ GroupDocs.Parser ได้ที่ไหน
 คุณสามารถอ้างถึง[เอกสารประกอบ](https://tutorials.groupdocs.com/parser/net/) สำหรับข้อมูลโดยละเอียดและตัวอย่าง
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Parser ได้อย่างไร
 เยี่ยม[ลิงค์นี้](https://purchase.groupdocs.com/temporary-license/) เพื่อขอใบอนุญาตชั่วคราว
### GroupDocs.Parser ให้การสนับสนุนลูกค้าหรือไม่
ได้ คุณสามารถขอความช่วยเหลือหรือถามคำถามได้ที่[ฟอรัม GroupDocs](https://forum.groupdocs.com/c/parser/17).