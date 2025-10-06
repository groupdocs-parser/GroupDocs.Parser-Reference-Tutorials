---
title: แยกข้อมูลจากแบบฟอร์ม PDF
linktitle: แยกข้อมูลจากแบบฟอร์ม PDF
second_title: GroupDocs.Parser .NET API
description: เรียนรู้วิธีดึงข้อมูลจากแบบฟอร์ม PDF โดยใช้ GroupDocs.Parser สำหรับ .NET คำแนะนำทีละขั้นตอนพร้อมตัวอย่างโค้ดและคำถามที่พบบ่อย
weight: 11
url: /th/net/pdf-processing/extract-data-from-pdf-forms/
type: docs
---
# แยกข้อมูลจากแบบฟอร์ม PDF

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Parser สำหรับ .NET เพื่อแยกข้อมูลจากแบบฟอร์ม PDF GroupDocs.Parser เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถทำงานกับเอกสารรูปแบบต่างๆ ได้อย่างมีประสิทธิภาพ รวมถึง PDF, DOCX, XLSX และอื่นๆ อีกมากมาย เราจะอธิบายขั้นตอนที่จำเป็นเพื่อแยกฟิลด์เฉพาะจากแบบฟอร์ม PDF และจัดการข้อมูลที่แยกออกมา
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C#
- ติดตั้ง Visual Studio บนระบบของคุณแล้ว
- ติดตั้ง GroupDocs.Parser สำหรับไลบรารี .NET แล้ว คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/parser/net/).

## นำเข้าเนมสเปซ
ในการเริ่มต้น คุณจะต้องนำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ C# ของคุณ:
```csharp
using System;
using System.Linq;
using GroupDocs.Parser.Data;
```
## ขั้นตอนที่ 1: เริ่มต้น Parser
 ขั้นแรก สร้างอินสแตนซ์ของ`Parser` คลาสโดยการระบุเส้นทางไปยังไฟล์ PDF ตัวอย่างของคุณ:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //รหัสสำหรับการดึงข้อมูลจะอยู่ที่นี่
}
```
## ขั้นตอนที่ 2: แยกข้อมูลจากเอกสาร PDF
 ต่อไปภายใน.`using` บล็อก, เรียกใช้`ParseForm` วิธีการดึงข้อมูลจากเอกสาร PDF:
```csharp
DocumentData data = parser.ParseForm();
if (data == null)
{
    Console.WriteLine("Form extraction isn't supported.");
    return;
}
```
## ขั้นตอนที่ 3: เข้าถึงข้อมูลฟิลด์เฉพาะ
 ตอนนี้ให้กำหนดวิธีการ`GetFieldText` เพื่อดึงข้อความจากฟิลด์เฉพาะภายในข้อมูลที่แยกออกมา:
```csharp
private static string GetFieldText(DocumentData data, string fieldName)
{
    FieldData fieldData = data.GetFieldsByName(fieldName).FirstOrDefault();
    return fieldData != null && fieldData.PageArea is PageTextArea
        ? (fieldData.PageArea as PageTextArea).Text
        : null;
}
```
## ขั้นตอนที่ 4: สร้างวัตถุบันทึกเบื้องต้น
 หลังจากกำหนด`GetFieldText` วิธีการใช้เพื่อเติมข้อมูล`PreliminaryRecord` วัตถุที่มีข้อมูลที่แยกออกมา:
```csharp
PreliminaryRecord rec = new PreliminaryRecord();
rec.Name = GetFieldText(data, "Name");
rec.Model = GetFieldText(data, "Model");
rec.Time = GetFieldText(data, "Time");
rec.Description = GetFieldText(data, "Description");
```
## ขั้นตอนที่ 5: ใช้ข้อมูลที่แยกออกมา
สุดท้าย คุณสามารถใช้ข้อมูลที่แยกออกมาได้ตามต้องการ ไม่ว่าจะบันทึกลงในฐานข้อมูล ส่งเป็นเว็บตอบกลับ หรือแสดงข้อมูล:
```csharp
Console.WriteLine("Preliminary record");
Console.WriteLine("Name: {0}", rec.Name);
Console.WriteLine("Model: {0}", rec.Model);
Console.WriteLine("Time: {0}", rec.Time);
Console.WriteLine("Description: {0}", rec.Description);
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงพื้นฐานของการแยกข้อมูลจากแบบฟอร์ม PDF โดยใช้ GroupDocs.Parser สำหรับ .NET เมื่อทำตามขั้นตอนเหล่านี้ คุณจะสามารถดึงข้อมูลเฉพาะจากเอกสาร PDF ภายในแอปพลิเคชัน C# ของคุณได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### GroupDocs.Parser เข้ากันได้กับรูปแบบเอกสารอื่นนอกเหนือจาก PDF หรือไม่
ใช่ GroupDocs.Parser รองรับรูปแบบต่างๆ รวมถึง DOCX, XLSX, PPTX และอื่นๆ
### ฉันสามารถแยกรูปภาพและข้อมูลเมตาโดยใช้ GroupDocs.Parser ได้หรือไม่
ใช่ GroupDocs.Parser อนุญาตให้แยกรูปภาพ ข้อมูลเมตา และข้อความจากเอกสาร
### ฉันจะหาการสนับสนุนหรือเอกสารเพิ่มเติมสำหรับ GroupDocs.Parser ได้ที่ไหน
 ท่านสามารถเยี่ยมชมได้ที่[เอกสาร GroupDocs.Parser](https://tutorials.groupdocs.com/parser/net/) สำหรับข้อมูลโดยละเอียดและตัวอย่าง
### GroupDocs.Parser มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถเข้าถึง[ทดลองใช้ GroupDocs.Parser ฟรี](https://releases.groupdocs.com/) เพื่อสำรวจคุณลักษณะต่างๆ
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Parser ได้อย่างไร
 คุณสามารถได้รับ[ใบอนุญาตชั่วคราวสำหรับ GroupDocs.Parser](https://purchase.groupdocs.com/temporary-license/) เพื่อประเมินความสามารถในโครงการของคุณ