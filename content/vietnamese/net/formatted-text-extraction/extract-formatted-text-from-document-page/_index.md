---
title: Trích xuất văn bản được định dạng từ trang tài liệu
linktitle: Trích xuất văn bản được định dạng từ trang tài liệu
second_title: API GroupDocs.Parser .NET
description: Trích xuất văn bản được định dạng từ các trang tài liệu bằng GroupDocs.Parser cho .NET. Giải pháp trích xuất văn bản hiệu quả và đáng tin cậy.
weight: 11
url: /vi/net/formatted-text-extraction/extract-formatted-text-from-document-page/
---
## Giới thiệu
Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn quy trình trích xuất văn bản được định dạng từ các trang tài liệu bằng GroupDocs.Parser cho .NET. Thư viện này cho phép bạn phân tích cú pháp và trích xuất văn bản một cách hiệu quả từ nhiều định dạng tài liệu khác nhau như PDF, Word, Excel, v.v.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn có những điều sau:
- Visual Studio được cài đặt trên hệ thống của bạn.
- Kiến thức cơ bản về lập trình C#.
-  GroupDocs.Parser cho thư viện .NET. Bạn có thể tải nó xuống[đây](https://releases.groupdocs.com/parser/net/).

## Nhập không gian tên
Trước tiên, hãy bắt đầu bằng cách nhập các vùng tên cần thiết vào dự án C# của bạn.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Bước 1: Tạo một phiên bản của lớp trình phân tích cú pháp
 Bắt đầu bằng cách tạo một thể hiện của`Parser` class bằng cách cung cấp đường dẫn đến tệp mẫu của bạn.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Mã sẽ ở đây
}
```
## Bước 2: Kiểm tra xem Trích xuất văn bản có định dạng có được hỗ trợ không
Trước khi tiến hành trích xuất văn bản, hãy xác minh xem tài liệu có hỗ trợ trích xuất văn bản được định dạng hay không.
```csharp
if (!parser.Features.FormattedText)
{
    Console.WriteLine("Document does not support formatted text extraction.");
    return;
}
```
## Bước 3: Nhận thông tin tài liệu
Truy xuất thông tin về tài liệu, chẳng hạn như số trang.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Bước 4: Lặp lại các trang tài liệu và trích xuất văn bản có định dạng
Lặp lại qua từng trang của tài liệu và trích xuất văn bản được định dạng bằng các tùy chọn đã chỉ định (ví dụ: định dạng Markdown).
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    
    using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Markdown)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Phần kết luận
Bây giờ bạn đã biết cách trích xuất văn bản có định dạng từ các trang tài liệu bằng GroupDocs.Parser cho .NET. Thư viện này cung cấp giải pháp mạnh mẽ và dễ sử dụng để trích xuất văn bản từ nhiều định dạng tệp khác nhau.

## Câu hỏi thường gặp
### GroupDocs.Parser có thể xử lý các định dạng tệp khác nhau không?
Có, GroupDocs.Parser hỗ trợ nhiều định dạng tài liệu, bao gồm PDF, DOCX, XLSX, PPTX, v.v.
### GroupDocs.Parser có tương thích với .NET Core không?
Có, GroupDocs.Parser hỗ trợ .NET Core và .NET Framework.
### GroupDocs.Parser có giữ nguyên định dạng văn bản trong quá trình trích xuất không?
Có, GroupDocs.Parser có thể giữ lại định dạng như kiểu và phông chữ khi trích xuất văn bản.
### Tôi có thể trích xuất hình ảnh và siêu dữ liệu bằng GroupDocs.Parser không?
Có, GroupDocs.Parser cho phép trích xuất hình ảnh, siêu dữ liệu và văn bản từ tài liệu.
### Làm cách nào tôi có thể nhận được hỗ trợ cho GroupDocs.Parser?
 Bạn có thể nhận được sự hỗ trợ từ[Diễn đàn GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).