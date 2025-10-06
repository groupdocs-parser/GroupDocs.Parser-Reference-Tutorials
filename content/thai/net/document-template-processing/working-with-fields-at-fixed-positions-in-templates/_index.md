---
title: การทำงานกับฟิลด์ในตำแหน่งคงที่ในเทมเพลต
linktitle: การทำงานกับฟิลด์ในตำแหน่งคงที่ในเทมเพลต
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีดึงข้อมูลจากเอกสารโดยใช้ GroupDocs.Parser สำหรับ .NET บทช่วยสอนที่ครอบคลุมพร้อมตัวอย่างโค้ด
weight: 11
url: /th/net/document-template-processing/working-with-fields-at-fixed-positions-in-templates/
type: docs
---
# การทำงานกับฟิลด์ในตำแหน่งคงที่ในเทมเพลต

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีการทำงานกับฟิลด์ในตำแหน่งคงที่ภายในเทมเพลตโดยใช้ GroupDocs.Parser สำหรับ .NET GroupDocs.Parser เป็นไลบรารีการแยกวิเคราะห์เอกสารที่มีประสิทธิภาพซึ่งช่วยให้นักพัฒนาสามารถดึงข้อมูลจากรูปแบบเอกสารต่างๆ เช่น PDF, Word, Excel และอื่นๆ โดยเฉพาะอย่างยิ่ง เราจะมุ่งเน้นไปที่การกำหนดและการใช้ฟิลด์เทมเพลตเพื่อดึงข้อมูลเป้าหมายตามตำแหน่งคงที่
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
- ความเข้าใจพื้นฐานเกี่ยวกับการพัฒนา C# และ .NET
- ติดตั้ง Visual Studio บนระบบของคุณแล้ว
- ติดตั้ง GroupDocs.Parser สำหรับไลบรารี .NET แล้ว คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).
- ตัวอย่างไฟล์เอกสารสำหรับการทดสอบ

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
## ขั้นตอนที่ 1: กำหนดฟิลด์เทมเพลต
ขั้นแรก ให้กำหนดฟิลด์ที่มีตำแหน่งคงที่ภายในเทมเพลต ฟิลด์นี้แสดงถึงพื้นที่ที่จะดึงข้อมูลออกมา
```csharp
TemplateField field = new TemplateField(
    new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))),
    "FromCompany");
```
ที่นี่:
- `Rectangle` ระบุตำแหน่งและขนาดของสนาม
- `Point(35, 135)` แสดงถึงพิกัดมุมซ้ายบน
- `Size(100, 10)` กำหนดความกว้างและความสูงของฟิลด์
- `"FromCompany"` เป็นชื่อที่กำหนดให้กับฟิลด์นี้
## ขั้นตอนที่ 2: สร้างเทมเพลต
สร้างเทมเพลตโดยใช้ฟิลด์ที่กำหนด
```csharp
Template template = new Template(new TemplateItem[] { field });
```
 ที่`Template` วัตถุเก็บฟิลด์ที่กำหนดไว้
## ขั้นตอนที่ 3: แยกวิเคราะห์เอกสารโดยใช้เทมเพลต
 ยกตัวอย่าง`Parser` ด้วยเส้นทางเอกสารเป้าหมาย จากนั้นแยกวิเคราะห์เอกสารโดยใช้เทมเพลตที่สร้างขึ้น
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    // ทำซ้ำผ่านข้อมูลที่แยกออกมา
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
ที่นี่:
- `Parser` เริ่มต้นได้ด้วยเส้นทางไฟล์เอกสารตัวอย่าง
- `ParseByTemplate` วิธีการใช้ในการดึงข้อมูลตามเทมเพลตที่ให้มา
-  ข้อมูลที่แยกออกมามีการเข้าถึงโดยใช้`DocumentData`โดยที่แต่ละรายการสอดคล้องกับฟิลด์ที่กำหนด

## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงกระบวนการทำงานกับฟิลด์ที่มีตำแหน่งคงที่ในเทมเพลตโดยใช้ GroupDocs.Parser สำหรับ .NET ด้วยการกำหนดเทมเพลตที่มีตำแหน่งฟิลด์เฉพาะ นักพัฒนาสามารถดึงข้อมูลเป้าหมายจากรูปแบบเอกสารต่างๆ ได้อย่างแม่นยำ

## คำถามที่พบบ่อย
### GroupDocs.Parser เข้ากันได้กับรูปแบบเอกสารทั้งหมดหรือไม่
 GroupDocs.Parser รองรับรูปแบบไฟล์ที่หลากหลาย รวมถึง PDF, Microsoft Word, Excel, PowerPoint และอื่นๆ อ้างถึง[เอกสารประกอบ](https://tutorials.groupdocs.com/parser/net/) สำหรับรายการโดยละเอียด
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Parser ได้อย่างไร
 คุณสามารถรับใบอนุญาตชั่วคราวเพื่อการทดสอบได้จาก[ที่นี่](https://purchase.groupdocs.com/temporary-license/).
### ฉันจะรับการสนับสนุนสำหรับ GroupDocs.Parser ได้ที่ไหน
 สำหรับความช่วยเหลือทางเทคนิคและการสนทนา โปรดไปที่[ฟอรัม GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).
### ฉันสามารถลองใช้ GroupDocs.Parser ก่อนซื้อได้หรือไม่
 ใช่ คุณสามารถสำรวจห้องสมุดพร้อมให้ทดลองใช้ฟรีได้[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะซื้อใบอนุญาตสำหรับ GroupDocs.Parser ได้อย่างไร
 หากต้องการซื้อใบอนุญาต โปรดไปที่[หน้าซื้อ](https://purchase.groupdocs.com/buy).