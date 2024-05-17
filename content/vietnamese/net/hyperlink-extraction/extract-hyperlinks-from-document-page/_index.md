---
title: Trích xuất siêu liên kết từ trang tài liệu
linktitle: Trích xuất siêu liên kết từ trang tài liệu
second_title: API GroupDocs.Parser .NET
description: Tìm hiểu cách trích xuất siêu liên kết từ tài liệu bằng GroupDocs.Parser cho .NET. Hướng dẫn từng bước để trích xuất siêu liên kết trong C#.
type: docs
weight: 11
url: /vi/net/hyperlink-extraction/extract-hyperlinks-from-document-page/
---
## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ khám phá cách sử dụng GroupDocs.Parser cho .NET để trích xuất siêu liên kết từ tài liệu theo từng bước. GroupDocs.Parser là một thư viện mạnh mẽ cho phép các nhà phát triển phân tích cú pháp các định dạng tài liệu khác nhau và trích xuất văn bản, siêu dữ liệu và các thành phần khác.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn có những điều sau:
- Visual Studio: Cài đặt Visual Studio trên máy phát triển của bạn.
-  Thư viện GroupDocs.Parser: Tải xuống và tham khảo thư viện GroupDocs.Parser. Bạn có thể lấy nó từ[đây](https://releases.groupdocs.com/parser/net/).
- Tài liệu mẫu: Chuẩn bị một tài liệu mẫu (ví dụ: DOCX, PDF) có chứa các siêu liên kết để kiểm tra.

## Nhập không gian tên
Đầu tiên, bao gồm các không gian tên cần thiết để sử dụng các chức năng của GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Bước 1: Tạo phiên bản trình phân tích cú pháp
 Khởi tạo`Parser` class bằng đường dẫn đến tài liệu mẫu của bạn.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Mã ở đây ...
}
```
## Bước 2: Kiểm tra hỗ trợ trích xuất siêu liên kết
Đảm bảo rằng tài liệu hỗ trợ trích xuất siêu liên kết trước khi tiếp tục.
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
## Bước 3: Truy xuất thông tin tài liệu
Nhận thông tin cơ bản về tài liệu và kiểm tra xem nó có chứa các trang hay không.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Bước 4: Lặp lại các trang tài liệu
Lặp lại qua từng trang của tài liệu.
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Trích xuất siêu liên kết từ trang hiện tại
    IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks(pageIndex);
    // Lặp lại các siêu liên kết được trích xuất
    foreach (PageHyperlinkArea hyperlink in hyperlinks)
    {
        Console.WriteLine($"Hyperlink Text: {hyperlink.Text}");
        Console.WriteLine($"Hyperlink URL: {hyperlink.Url}");
        Console.WriteLine(); // Dòng trống để dễ đọc
    }
}
```

## Phần kết luận
Trong hướng dẫn này, chúng tôi đã trình bày những kiến thức cơ bản về cách sử dụng GroupDocs.Parser cho .NET để trích xuất siêu liên kết từ tài liệu. Bạn đã học cách khởi tạo trình phân tích cú pháp, kiểm tra hỗ trợ siêu liên kết, truy xuất thông tin tài liệu và lặp qua các trang tài liệu để trích xuất siêu liên kết một cách hiệu quả.

## Câu hỏi thường gặp
### Tôi có thể trích xuất siêu liên kết từ các định dạng tài liệu khác nhau không?
Có, GroupDocs.Parser hỗ trợ nhiều định dạng khác nhau như DOCX, PDF, PPTX, v.v. để trích xuất siêu liên kết.
### GroupDocs.Parser có dễ tích hợp vào các ứng dụng .NET hiện có không?
Hoàn toàn có thể, GroupDocs.Parser được thiết kế đơn giản và có thể dễ dàng tích hợp vào các dự án .NET của bạn.
### Tôi có thể trích xuất siêu dữ liệu khác cùng với các siêu liên kết bằng GroupDocs.Parser không?
Có, ngoài siêu liên kết, bạn có thể trích xuất văn bản, hình ảnh và siêu dữ liệu từ tài liệu bằng thư viện này.
### GroupDocs.Parser có xử lý các tài liệu được mã hóa hoặc bảo vệ bằng mật khẩu không?
GroupDocs.Parser có thể phân tích cú pháp các tài liệu được bảo vệ bằng mật khẩu nếu mật khẩu được cung cấp.
### Có phiên bản dùng thử để kiểm tra trước khi mua không?
 Có, bạn có thể tải xuống phiên bản dùng thử miễn phí[đây](https://releases.groupdocs.com/).