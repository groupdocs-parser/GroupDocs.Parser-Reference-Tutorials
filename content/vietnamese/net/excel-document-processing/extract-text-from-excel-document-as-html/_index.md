---
title: Trích xuất văn bản từ tài liệu Excel dưới dạng HTML
linktitle: Trích xuất văn bản từ tài liệu Excel dưới dạng HTML
second_title: API GroupDocs.Parser .NET
description: Tìm hiểu cách trích xuất văn bản từ tài liệu Excel và chuyển đổi nó thành HTML bằng GroupDocs.Parser cho .NET.
weight: 13
url: /vi/net/excel-document-processing/extract-text-from-excel-document-as-html/
type: docs
---
# Trích xuất văn bản từ tài liệu Excel dưới dạng HTML

## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ khám phá cách sử dụng GroupDocs.Parser cho .NET để trích xuất văn bản từ tài liệu Excel và chuyển đổi nó sang định dạng HTML. GroupDocs.Parser là một thư viện mạnh mẽ cho phép các nhà phát triển làm việc với nhiều định dạng tài liệu khác nhau, trích xuất văn bản và siêu dữ liệu một cách hiệu quả.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn đã thiết lập sau:
- Visual Studio được cài đặt trên hệ thống của bạn.
- Hiểu biết cơ bản về lập trình C#.
-  Thư viện GroupDocs.Parser cho .NET. Bạn có thể tải nó xuống từ[đây](https://releases.groupdocs.com/parser/net/).
## Nhập không gian tên
Bắt đầu bằng cách đưa các không gian tên cần thiết vào dự án C# của bạn để truy cập các chức năng GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Bước 1: Tạo một phiên bản của lớp trình phân tích cú pháp
 Đầu tiên, khởi tạo`Parser` lớp bằng cách cung cấp đường dẫn đến tài liệu Excel của bạn.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // Mã tiếp theo sẽ ở đây
}
```
 Thay thế`"YourSampleFile.xlsx"` với đường dẫn đến tệp Excel của bạn.
## Bước 2: Trích xuất văn bản dưới dạng HTML
 Trong`using` khối của`Parser` Ví dụ, sử dụng`GetFormattedText` phương pháp trích xuất văn bản được định dạng ở chế độ HTML.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Mã tiếp theo sẽ ở đây
    }
}
```
## Bước 3: Đọc và in văn bản HTML được trích xuất
 Tiếp theo, đọc văn bản HTML được trích xuất từ`TextReader` và in nó ra bàn điều khiển.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
Sau khi được thực thi, mã này sẽ trích xuất văn bản từ tài liệu Excel và hiển thị dưới dạng định dạng HTML trong bảng điều khiển.
## Phần kết luận
Trong hướng dẫn này, chúng ta đã học cách sử dụng GroupDocs.Parser cho .NET để trích xuất văn bản từ tài liệu Excel và chuyển đổi nó sang định dạng HTML. Thư viện này cung cấp một cách đơn giản để làm việc với nhiều định dạng tài liệu khác nhau, cho phép các nhà phát triển xử lý hiệu quả các tác vụ trích xuất văn bản trong ứng dụng của họ.

## Câu hỏi thường gặp
### GroupDocs.Parser có thể xử lý các định dạng tài liệu khác ngoài Excel không?
Có, GroupDocs.Parser hỗ trợ nhiều định dạng tệp bao gồm PDF, Word, PowerPoint, v.v.
### GroupDocs.Parser có tương thích với .NET Core không?
Có, GroupDocs.Parser tương thích với cả .NET Framework và .NET Core.
### GroupDocs.Parser có giữ nguyên định dạng trong quá trình trích xuất văn bản không?
Có, GroupDocs.Parser có thể giữ nguyên định dạng như phông chữ, kiểu và bố cục trong quá trình trích xuất văn bản.
### Tôi có thể trích xuất siêu dữ liệu từ tài liệu bằng GroupDocs.Parser không?
Có, GroupDocs.Parser cho phép trích xuất siêu dữ liệu như tác giả, ngày tạo, v.v. từ các loại tài liệu được hỗ trợ.
### Có bản dùng thử miễn phí cho GroupDocs.Parser không?
 Có, bạn có thể tải xuống bản dùng thử miễn phí từ[đây](https://releases.groupdocs.com/).