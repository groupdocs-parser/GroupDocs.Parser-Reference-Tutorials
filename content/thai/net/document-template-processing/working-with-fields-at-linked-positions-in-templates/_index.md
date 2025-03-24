---
title: การทำงานกับฟิลด์ที่ตำแหน่งที่เชื่อมโยงในเทมเพลต
linktitle: การทำงานกับฟิลด์ที่ตำแหน่งที่เชื่อมโยงในเทมเพลต
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีแยกข้อมูลจากเอกสารอย่างมีประสิทธิภาพโดยใช้ GroupDocs.Parser for .NET บทช่วยสอนทีละขั้นตอนพร้อมตัวอย่างโค้ด
weight: 12
url: /th/net/document-template-processing/working-with-fields-at-linked-positions-in-templates/
---

# การทำงานกับฟิลด์ที่ตำแหน่งที่เชื่อมโยงในเทมเพลต

## การแนะนำ
GroupDocs.Parser สำหรับ .NET เป็นไลบรารีที่มีประสิทธิภาพซึ่งออกแบบมาเพื่ออำนวยความสะดวกในการแยกวิเคราะห์เอกสารและการแยกข้อมูล รองรับรูปแบบไฟล์ที่หลากหลาย รวมถึง PDF, DOCX, XLSX และอื่นๆ หนึ่งในคุณสมบัติหลักของมันคือการแยกข้อมูลตามเทมเพลต ซึ่งช่วยให้คุณกำหนดฟิลด์ภายในเอกสารและแยกข้อมูลเฉพาะตามเทมเพลตที่กำหนดไว้ล่วงหน้าเหล่านี้
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
- ความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรม C#
- ติดตั้ง Visual Studio บนระบบของคุณแล้ว
-  GroupDocs.Parser สำหรับไลบรารี .NET (ดาวน์โหลดจาก[ที่นี่](https://releases.groupdocs.com/parser/net/-)
- ตัวอย่างไฟล์เอกสารที่จะใช้งาน

## การนำเข้าเนมสเปซ
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
ขั้นแรก ให้กำหนดฟิลด์เทมเพลตโดยใช้นิพจน์ทั่วไปและตำแหน่งที่เชื่อมโยง:
```csharp
// กำหนดฟิลด์ด้วยนิพจน์ทั่วไป
TemplateField field = new TemplateField(
    new TemplateRegexPosition("Tax"),
    "Tax");
// กำหนดฟิลด์ที่เชื่อมโยงด้วยการตั้งค่าตำแหน่งเฉพาะ
TemplateField linkedField = new TemplateField(
    new TemplateLinkedPosition(
        "Tax",
        new Size(100, 20),
        new TemplateLinkedPositionEdges(false, false, true, false)),
    "TaxValue");
```
## ขั้นตอนที่ 2: สร้างเทมเพลต
ถัดไป สร้างเทมเพลตที่มีฟิลด์ที่กำหนดไว้:
```csharp
// สร้างเทมเพลตด้วยฟิลด์ที่กำหนด
Template template = new Template(new TemplateItem[] { field, linkedField });
```
## ขั้นตอนที่ 3: แยกวิเคราะห์เอกสารด้วยเทมเพลต
 ตอนนี้เริ่มต้น`Parser` คลาสและแยกวิเคราะห์เอกสารโดยใช้เทมเพลต:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // แยกวิเคราะห์เอกสารตามเทมเพลต
    DocumentData data = parser.ParseByTemplate(template);
    // ทำซ้ำผ่านข้อมูลที่แยกออกมาและผลลัพธ์การพิมพ์
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

## บทสรุป
GroupDocs.Parser สำหรับ .NET ช่วยลดความยุ่งยากในการแยกข้อมูลที่มีโครงสร้างจากเอกสารโดยใช้เทมเพลต ด้วยการกำหนดฟิลด์และการใช้เทมเพลต คุณสามารถดึงข้อมูลที่เกี่ยวข้องได้อย่างมีประสิทธิภาพ เพิ่มประสิทธิภาพการทำงานอัตโนมัติและประสิทธิผลในงานการประมวลผลเอกสาร

## คำถามที่พบบ่อย
### GroupDocs.Parser สามารถแยกข้อมูลจากไฟล์ PDF ที่เข้ารหัสได้หรือไม่
ใช่ GroupDocs.Parser รองรับการแยกวิเคราะห์ไฟล์ PDF ที่เข้ารหัสโดยระบุรหัสผ่านระหว่างการแยกวิเคราะห์
### ไฟล์รูปแบบใดบ้างที่รองรับการแตกไฟล์ตามเทมเพลต
GroupDocs.Parser รองรับรูปแบบไฟล์ที่หลากหลาย รวมถึง PDF, DOCX, XLSX, PPTX, TXT และอื่นๆ
### มีรุ่นทดลองใช้งานสำหรับ GroupDocs.Parser หรือไม่
 ใช่ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันสามารถใช้ GroupDocs.Parser เพื่อประมวลผลเอกสารเป็นชุดได้หรือไม่
ใช่ GroupDocs.Parser ช่วยให้การประมวลผลเป็นชุดสามารถแยกวิเคราะห์เอกสารหลายชุดพร้อมกันได้
### ฉันจะรับการสนับสนุนด้านเทคนิคสำหรับ GroupDocs.Parser ได้ที่ไหน
 คุณสามารถขอรับการสนับสนุนทางเทคนิคและมีส่วนร่วมกับชุมชนได้ที่[ฟอรัม GroupDocs](https://forum.groupdocs.com/c/parser/17).