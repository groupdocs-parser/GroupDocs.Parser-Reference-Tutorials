---
title: Làm việc với các trường tại các vị trí được liên kết trong mẫu
linktitle: Làm việc với các trường tại các vị trí được liên kết trong mẫu
second_title: API GroupDocs.Parser .NET
description: Tìm hiểu cách trích xuất dữ liệu hiệu quả từ tài liệu bằng GroupDocs.Parser cho .NET. Hướng dẫn từng bước với các ví dụ về mã.
type: docs
weight: 12
url: /vi/net/document-template-processing/working-with-fields-at-linked-positions-in-templates/
---
## Giới thiệu
GroupDocs.Parser cho .NET là một thư viện mạnh mẽ được thiết kế để hỗ trợ các tác vụ phân tích cú pháp tài liệu và trích xuất dữ liệu. Nó hỗ trợ nhiều định dạng tệp, bao gồm PDF, DOCX, XLSX, v.v. Một trong những tính năng chính của nó là trích xuất dữ liệu dựa trên mẫu, cho phép bạn xác định các trường trong tài liệu và trích xuất dữ liệu cụ thể dựa trên các mẫu được xác định trước này.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn có những điều sau:
- Hiểu biết cơ bản về lập trình C#
- Visual Studio được cài đặt trên hệ thống của bạn
-  GroupDocs.Parser cho thư viện .NET (tải xuống từ[đây](https://releases.groupdocs.com/parser/net/))
- Các tệp tài liệu mẫu để làm việc

## Nhập không gian tên
Bắt đầu bằng cách thêm các không gian tên cần thiết vào dự án C# của bạn:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Bước 1: Xác định trường mẫu
Đầu tiên, xác định các trường mẫu bằng cách sử dụng biểu thức chính quy và vị trí được liên kết:
```csharp
// Xác định trường bằng biểu thức chính quy
TemplateField field = new TemplateField(
    new TemplateRegexPosition("Tax"),
    "Tax");
// Xác định trường được liên kết với cài đặt vị trí cụ thể
TemplateField linkedField = new TemplateField(
    new TemplateLinkedPosition(
        "Tax",
        new Size(100, 20),
        new TemplateLinkedPositionEdges(false, false, true, false)),
    "TaxValue");
```
## Bước 2: Tạo mẫu
Tiếp theo, tạo một mẫu chứa các trường được xác định:
```csharp
// Tạo mẫu với các trường được xác định
Template template = new Template(new TemplateItem[] { field, linkedField });
```
## Bước 3: Phân tích tài liệu bằng mẫu
 Bây giờ, khởi tạo`Parser` lớp và phân tích tài liệu bằng mẫu:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Phân tích tài liệu theo mẫu
    DocumentData data = parser.ParseByTemplate(template);
    // Lặp lại dữ liệu được trích xuất và in kết quả
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

## Phần kết luận
GroupDocs.Parser cho .NET đơn giản hóa quá trình trích xuất dữ liệu có cấu trúc từ tài liệu bằng cách sử dụng các mẫu. Bằng cách xác định các trường và áp dụng các mẫu, bạn có thể trích xuất thông tin liên quan một cách hiệu quả, nâng cao khả năng tự động hóa và năng suất trong các tác vụ xử lý tài liệu.

## Câu hỏi thường gặp
### GroupDocs.Parser có thể trích xuất dữ liệu từ các tệp PDF được mã hóa không?
Có, GroupDocs.Parser hỗ trợ phân tích cú pháp các tệp PDF được mã hóa bằng cách cung cấp mật khẩu trong quá trình phân tích cú pháp.
### Những định dạng tệp nào được hỗ trợ để trích xuất dựa trên mẫu?
GroupDocs.Parser hỗ trợ nhiều định dạng tệp bao gồm PDF, DOCX, XLSX, PPTX, TXT, v.v.
### Có phiên bản dùng thử cho GroupDocs.Parser không?
 Có, bạn có thể tải xuống phiên bản dùng thử miễn phí từ[đây](https://releases.groupdocs.com/).
### Tôi có thể sử dụng GroupDocs.Parser để xử lý hàng loạt tài liệu không?
Có, GroupDocs.Parser cho phép xử lý hàng loạt để phân tích đồng thời nhiều tài liệu.
### Tôi có thể nhận hỗ trợ kỹ thuật cho GroupDocs.Parser ở đâu?
 Bạn có thể tìm kiếm hỗ trợ kỹ thuật và tham gia với cộng đồng tại[diễn đàn GroupDocs](https://forum.groupdocs.com/c/parser/17).