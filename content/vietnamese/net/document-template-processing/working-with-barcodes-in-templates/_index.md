---
title: Làm việc với mã vạch trong mẫu
linktitle: Làm việc với mã vạch trong mẫu
second_title: API GroupDocs.Parser .NET
description: Tìm hiểu cách sử dụng GroupDocs.Parser cho .NET để trích xuất dữ liệu có cấu trúc từ tài liệu bằng các mẫu. Đơn giản hóa việc trích xuất dữ liệu với các trường mã vạch.
weight: 10
url: /vi/net/document-template-processing/working-with-barcodes-in-templates/
---
## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ khám phá cách trích xuất dữ liệu từ tài liệu một cách hiệu quả bằng cách sử dụng các mẫu với GroupDocs.Parser cho .NET. GroupDocs.Parser đơn giản hóa quá trình trích xuất dữ liệu bằng cách cho phép bạn xác định mẫu cho các loại dữ liệu cụ thể, chẳng hạn như mã vạch, sau đó phân tích cú pháp tài liệu theo các mẫu này.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn đã thiết lập sau:
-  GroupDocs.Parser cho .NET: Bạn có thể tải xuống thư viện từ[đây](https://releases.groupdocs.com/parser/net/).
- Tài liệu mẫu: Chuẩn bị tệp mẫu (ví dụ: PDF, DOCX) chứa dữ liệu bạn muốn trích xuất.

## Nhập không gian tên
Trước tiên, hãy bao gồm các không gian tên cần thiết trong mã C# của bạn:
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
using System;
```
## Bước 1: Xác định trường mã vạch
Xác định trường mã vạch trong mẫu. Ví dụ này thiết lập trường mã QR:
```csharp
TemplateBarcode barcode = new TemplateBarcode(
    new Rectangle(new Point(590, 80), new Size(150, 150)),
    "QR");
```
 Đây,`Rectangle` xác định vị trí và kích thước của trường mã vạch trên tài liệu.
## Bước 2: Tạo mẫu
Tạo một mẫu và thêm trường mã vạch vào đó:
```csharp
Template template = new Template(new TemplateItem[] { barcode });
```
## Bước 3: Phân tích tài liệu bằng mẫu
 Khởi tạo`Parser` class bằng đường dẫn tệp tài liệu của bạn và phân tích tài liệu bằng mẫu đã xác định:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    // In dữ liệu được trích xuất
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageBarcodeArea area = data[i].PageArea as PageBarcodeArea;
        Console.WriteLine(area == null ? "Not a template barcode field" : area.Value);
    }
}
```
Đoạn mã này mở tài liệu, áp dụng mẫu và trích xuất dữ liệu dựa trên trường mã vạch được xác định. Sau đó nó in dữ liệu được trích xuất.

## Phần kết luận
Sử dụng GroupDocs.Parser cho .NET với các mẫu giúp đơn giản hóa việc trích xuất dữ liệu có cấu trúc từ tài liệu, đặc biệt khi xử lý các loại dữ liệu cụ thể như mã vạch. Bằng cách làm theo hướng dẫn này, bạn có thể tích hợp hiệu quả khả năng phân tích tài liệu vào các ứng dụng .NET của mình.

## Câu hỏi thường gặp
### Câu hỏi: Tôi có thể trích xuất nhiều trường mã vạch từ một tài liệu không?
Trả lời: Có, bạn có thể xác định nhiều trường mã vạch trong một mẫu và trích xuất dữ liệu tương ứng từ tài liệu.
### Câu hỏi: Định dạng tài liệu nào được hỗ trợ để phân tích cú pháp?
Đáp: GroupDocs.Parser hỗ trợ nhiều định dạng tài liệu, bao gồm PDF, DOCX, XLSX, PPTX, v.v.
### Hỏi: Có phiên bản dùng thử không?
 Đáp: Có, bạn có thể dùng thử miễn phí GroupDocs.Parser từ[đây](https://releases.groupdocs.com/).
### Hỏi: Làm thế nào tôi có thể nhận được hỗ trợ kỹ thuật?
 Đáp: Để được hỗ trợ kỹ thuật, hãy truy cập[diễn đàn GroupDocs](https://forum.groupdocs.com/c/parser/17).
### Hỏi: Tôi có thể mua giấy phép ở đâu?
 Đáp: Bạn có thể mua giấy phép cho GroupDocs.Parser từ[đây](https://purchase.groupdocs.com/buy).