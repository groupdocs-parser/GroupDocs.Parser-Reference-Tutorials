---
title: แยกหน้าโดยใช้เทมเพลต
linktitle: แยกหน้าโดยใช้เทมเพลต
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกวิเคราะห์หน้าเอกสารโดยใช้เทมเพลตใน .NET ด้วย GroupDocs.Parser แยกเนื้อหาเฉพาะอย่างมีประสิทธิภาพสำหรับแอปพลิเคชันของคุณ
weight: 16
url: /th/net/document-template-processing/parse-pages-using-templates/
type: docs
---
# แยกหน้าโดยใช้เทมเพลต

## การแนะนำ
ในบทช่วยสอนนี้ เราจะเจาะลึกเกี่ยวกับการใช้ GroupDocs.Parser สำหรับ .NET เพื่อดึงข้อมูลจากเอกสารอย่างมีประสิทธิภาพ GroupDocs.Parser เป็นไลบรารีที่มีประสิทธิภาพซึ่งช่วยให้สามารถแยกวิเคราะห์รูปแบบเอกสารต่างๆ เช่น PDF, DOCX, PPTX และอื่นๆ อีกมากมาย เราจะมุ่งเน้นไปที่การแยกวิเคราะห์หน้าโดยใช้เทมเพลต ซึ่งช่วยให้แยกเนื้อหาเฉพาะ เช่น บาร์โค้ด ได้อย่างแม่นยำ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าต่อไปนี้:
-  GroupDocs.Parser สำหรับ .NET Library: คุณสามารถดาวน์โหลดได้[ที่นี่](https://releases.groupdocs.com/parser/net/).
- สภาพแวดล้อมการพัฒนา: Visual Studio หรือ IDE ที่เข้ากันได้กับ .NET
- เอกสารตัวอย่าง: มีเอกสารที่มีเนื้อหาที่คุณต้องการแยกวิเคราะห์

## นำเข้าเนมสเปซ
เริ่มต้นด้วยการรวมเนมสเปซที่จำเป็นในโครงการ C# ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## ขั้นตอนที่ 1: กำหนดฟิลด์บาร์โค้ด
 หากต้องการแยกบาร์โค้ด ให้กำหนด a`TemplateBarcode` วัตถุ. ระบุสถานที่ (`Rectangle`) และประเภทของบาร์โค้ด
```csharp
TemplateBarcode barcode = new TemplateBarcode(
    new Rectangle(new Point(405, 55), new Size(100, 50)),
    "QR");
```
## ขั้นตอนที่ 2: สร้างเทมเพลต
 รวมบาร์โค้ด (หรือฟิลด์อื่นๆ) ลงใน`Template` วัตถุ.
```csharp
Template template = new Template(new TemplateItem[] { barcode });
```
## ขั้นตอนที่ 3: สร้างอินสแตนซ์ Parser
 สร้างอินสแตนซ์ของ`Parser` และระบุเส้นทางเอกสารที่คุณต้องการแยกวิเคราะห์
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // วนซ้ำหน้าเอกสารโดยใช้เทมเพลต
    foreach (DocumentPageData data in parser.ParsePagesByTemplate(template))
    {
        // พิมพ์ดัชนีหน้า
        Console.WriteLine("Page: " + data.PageIndex);
        // พิมพ์ข้อมูลที่แยกออกมา
        for (int i = 0; i < data.Count; i++)
        {
            Console.Write(data[i].Name + ": ");
            PageBarcodeArea area = data[i].PageArea as PageBarcodeArea;
            Console.WriteLine(area == null ? "Not a template barcode field" : area.Value);
        }
    }
}
```

## บทสรุป
เมื่อใช้ GroupDocs.Parser สำหรับ .NET คุณสามารถแยกวิเคราะห์เอกสารและแยกเนื้อหาเฉพาะ เช่น บาร์โค้ด โดยใช้เทมเพลตได้อย่างราบรื่น บทช่วยสอนนี้ครอบคลุมขั้นตอนพื้นฐานเพื่อให้คุณเริ่มต้นการแยกวิเคราะห์เอกสารในแอปพลิเคชัน .NET ของคุณ

## คำถามที่พบบ่อย
### GroupDocs.Parser สามารถจัดการรูปแบบเอกสารที่แตกต่างกันได้หรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบต่างๆ รวมถึง PDF, DOCX, XLSX และอื่นๆ
### GroupDocs.Parser เหมาะสำหรับการดึงข้อมูลเฉพาะ เช่น บาร์โค้ด หรือไม่
อย่างแน่นอน! GroupDocs.Parser นำเสนอความสามารถในการแยกข้อมูลที่แม่นยำสำหรับการแยกเนื้อหาเป้าหมาย
### ฉันจะหาเอกสารโดยละเอียดสำหรับ GroupDocs.Parser ได้ที่ไหน
 เยี่ยมชม[เอกสารประกอบ](https://tutorials.groupdocs.com/parser/net/) เพื่อรับคำแนะนำอย่างครอบคลุม
### ฉันจะได้รับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Parser ได้อย่างไร
 ได้รับ[ใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/) เพื่อวัตถุประสงค์ในการประเมินหรือการพัฒนา
### GroupDocs ให้การสนับสนุนในการแก้ไขปัญหาหรือไม่
 ใช่ คุณสามารถขอความช่วยเหลือได้ที่[ฟอรัม GroupDocs](https://forum.groupdocs.com/c/parser/17) สำหรับข้อสงสัยหรือปัญหาใด ๆ