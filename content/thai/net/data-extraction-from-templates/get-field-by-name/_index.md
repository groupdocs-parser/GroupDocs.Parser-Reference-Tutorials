---
title: รับฟิลด์ตามชื่อ
linktitle: รับฟิลด์ตามชื่อ
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกเขตข้อมูลเฉพาะจากเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET คำแนะนำทีละขั้นตอนพร้อมตัวอย่างโค้ด
type: docs
weight: 10
url: /th/net/data-extraction-from-templates/get-field-by-name/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ประโยชน์จาก GroupDocs.Parser สำหรับ .NET เพื่อแยกฟิลด์ข้อมูลเฉพาะ เช่น ราคาและอีเมลจากเอกสาร ไลบรารีอันทรงพลังนี้ทำให้งานการแยกวิเคราะห์เอกสารง่ายขึ้น ทำให้เหมาะอย่างยิ่งสำหรับความต้องการในการดึงข้อมูลที่หลากหลาย
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอน ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
- ติดตั้ง Visual Studio บนระบบของคุณแล้ว
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C#
-  ดาวน์โหลดและติดตั้ง GroupDocs.Parser สำหรับ .NET จาก[ลิงค์นี้](https://releases.groupdocs.com/parser/net/).

## นำเข้าเนมสเปซ
เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณ:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## ขั้นตอนที่ 1: กำหนดฟิลด์เทมเพลต
ขั้นแรก เราจะกำหนดฟิลด์เทมเพลตสำหรับการดึงข้อมูล ในตัวอย่างนี้ เราจะสร้างฟิลด์เพื่อบันทึกราคาและอีเมล
```csharp
// กำหนดฟิลด์ "ราคา"
TemplateField priceField = new TemplateField(
    new TemplateRegexPosition("\\$\\d+(.\\d+)?"),
    "Price");
// กำหนดฟิลด์ "อีเมล"
TemplateField emailField = new TemplateField(
    new TemplateRegexPosition("[a-z]+\\@[a-z]+\\.[a-z]+"),
    "Email");
// สร้างเทมเพลต
Template template = new Template(new TemplateItem[] { priceField, emailField });
```
## ขั้นตอนที่ 2: แยกวิเคราะห์เอกสารโดยใช้เทมเพลต
ต่อไป เราจะแยกวิเคราะห์เอกสารโดยใช้เทมเพลตที่กำหนดไว้
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // แยกวิเคราะห์เอกสารตามเทมเพลต
    DocumentData data = parser.ParseByTemplate(template);
    // พิมพ์ราคา
    Console.WriteLine("Prices:");
    foreach (FieldData field in data.GetFieldsByName("Price"))
    {
        PageTextArea area = field.PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
    // พิมพ์อีเมล
    Console.WriteLine("Emails:");
    foreach (FieldData field in data.GetFieldsByName("Email"))
    {
        PageTextArea area = field.PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกเขตข้อมูลเฉพาะจากเอกสาร ด้วยการกำหนดเทมเพลตและใช้ความสามารถในการแยกวิเคราะห์ของไลบรารี นักพัฒนาสามารถดึงข้อมูลที่มีโครงสร้าง เช่น ราคาและอีเมลจากรูปแบบเอกสารต่างๆ ได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### ฉันสามารถแยกวิเคราะห์เอกสารประเภทต่างๆ ด้วย GroupDocs.Parser for .NET ได้หรือไม่
ใช่ GroupDocs.Parser รองรับการแยกวิเคราะห์รูปแบบเอกสารต่างๆ เช่น PDF, DOCX, PPTX และอื่นๆ
### GroupDocs.Parser เหมาะสำหรับการประมวลผลเอกสารขนาดใหญ่หรือไม่
GroupDocs.Parser ได้รับการปรับให้มีประสิทธิภาพสูงสุดและสามารถจัดการเอกสารจำนวนมากได้อย่างมีประสิทธิภาพ
### ฉันจะรวม GroupDocs.Parser เข้ากับแอปพลิเคชัน .NET ของฉันได้อย่างไร
คุณสามารถรวม GroupDocs.Parser ได้อย่างง่ายดายโดยการอ้างอิงไลบรารีในโครงการ Visual Studio ของคุณและนำเข้าเนมสเปซที่จำเป็น
### GroupDocs.Parser ให้การสนับสนุนในการแยกรูปภาพหรือข้อมูลเมตาหรือไม่
ใช่ GroupDocs.Parser มี API เพื่อแยกรูปภาพ ข้อความ และข้อมูลเมตาออกจากเอกสาร
### มีฟอรัมชุมชนสำหรับผู้ใช้ GroupDocs.Parser หรือไม่?
 ใช่ คุณสามารถขอความช่วยเหลือและมีส่วนร่วมกับผู้ใช้รายอื่นได้ในฟอรัม GroupDocs.Parser[ที่นี่](https://forum.groupdocs.com/c/parser/17).