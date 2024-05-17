---
title: แยกข้อความที่จัดรูปแบบออกจากเอกสาร
linktitle: แยกข้อความที่จัดรูปแบบออกจากเอกสาร
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกข้อความที่จัดรูปแบบออกจากเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET การแยกข้อความที่ง่ายและมีประสิทธิภาพสำหรับแอปพลิเคชันของคุณ
type: docs
weight: 10
url: /th/net/formatted-text-extraction/extract-formatted-text-from-document/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกข้อความที่จัดรูปแบบแล้วจากเอกสารประเภทต่างๆ GroupDocs.Parser เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถทำงานกับเอกสารในลักษณะที่เรียบง่ายและมีประสิทธิภาพ เมื่อสิ้นสุดคู่มือนี้ คุณจะสามารถรวมความสามารถในการแยกข้อความเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
- Visual Studio: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Visual Studio ในระบบของคุณ
-  GroupDocs.Parser สำหรับ .NET: ดาวน์โหลดและติดตั้งไลบรารี GroupDocs.Parser จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
- ตัวอย่างเอกสาร: เตรียมเอกสารตัวอย่าง (เช่น PDF, DOCX) สำหรับการแยกข้อความ
## นำเข้าเนมสเปซ
ขั้นแรก ใส่เนมสเปซที่จำเป็นในโค้ด C# ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของ Parser Class
 เริ่มต้นด้วยการเริ่มต้น a`Parser` วัตถุที่มีเส้นทางไปยังเอกสารตัวอย่างของคุณ
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // รหัสการแยกข้อความอยู่ที่นี่
}
```
 แทนที่`"YourSampleFile.pdf"` พร้อมเส้นทางไปยังไฟล์เอกสารของคุณ

## ขั้นตอนที่ 2: แยกข้อความที่จัดรูปแบบ
 ภายใน`using` บล็อกให้ใช้`GetFormattedText` วิธีการแยกข้อความที่จัดรูปแบบออกจากเอกสาร ระบุรูปแบบผลลัพธ์ที่ต้องการ (เช่น HTML) โดยใช้`FormattedTextOptions`.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // แยกข้อความที่จัดรูปแบบลงในเครื่องอ่าน
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // ตรวจสอบว่ารองรับการแตกไฟล์หรือไม่
        if (reader == null)
        {
            Console.WriteLine("Formatted text extraction isn't supported.");
        }
        else
        {
            // อ่านและแสดงข้อความที่แยกออกมา
            Console.WriteLine(reader.ReadToEnd());
        }
    }
}
```

## บทสรุป
ยินดีด้วย! คุณได้เรียนรู้วิธีแยกข้อความที่จัดรูปแบบออกจากเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET ไลบรารีอเนกประสงค์นี้เปิดโอกาสให้ประมวลผลและวิเคราะห์ข้อความภายในแอปพลิเคชันของคุณ

## คำถามที่พบบ่อย
### ถาม: GroupDocs.Parser สามารถแยกข้อความจากเอกสารที่มีการป้องกันด้วยรหัสผ่านได้หรือไม่
ตอบ: ใช่ GroupDocs.Parser รองรับการแยกข้อความจากเอกสารที่มีการป้องกันด้วยรหัสผ่าน
### ถาม: GroupDocs.Parser รองรับรูปแบบเอกสารใดบ้าง
ตอบ: GroupDocs.Parser รองรับรูปแบบที่หลากหลาย รวมถึง PDF, DOCX, XLSX, PPTX และอื่นๆ
### ถาม: ฉันจะรับสิทธิ์ใช้งานชั่วคราวสำหรับ GroupDocs.Parser ได้อย่างไร
 ตอบ: คุณสามารถขอรับใบอนุญาตชั่วคราวได้จาก[ที่นี่](https://purchase.groupdocs.com/temporary-license/).
### ถาม: GroupDocs.Parser รองรับการแยกรูปภาพจากเอกสารหรือไม่
ตอบ: ใช่ GroupDocs.Parser รองรับการแยกรูปภาพควบคู่ไปกับการแยกข้อความ
### ถาม: ฉันจะรับการสนับสนุนเพิ่มเติมหรือถามคำถามเกี่ยวกับ GroupDocs.Parser ได้ที่ไหน
 ตอบ: เยี่ยมชม[ฟอรัม GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17)สำหรับการสนับสนุนและการอภิปราย