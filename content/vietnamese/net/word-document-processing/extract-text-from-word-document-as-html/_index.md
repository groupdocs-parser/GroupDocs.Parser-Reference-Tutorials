---
title: Trích xuất văn bản từ tài liệu Word dưới dạng HTML
linktitle: Trích xuất văn bản từ tài liệu Word dưới dạng HTML
second_title: API GroupDocs.Parser .NET
description: Tìm hiểu cách sử dụng GroupDocs.Parser cho .NET để trích xuất văn bản từ tài liệu Word và lưu dưới dạng HTML. Hướng dẫn từng bước với các ví dụ về mã.
weight: 16
url: /vi/net/word-document-processing/extract-text-from-word-document-as-html/
---

# Trích xuất văn bản từ tài liệu Word dưới dạng HTML

## Giới thiệu
GroupDocs.Parser for .NET là một thư viện phân tích tài liệu mạnh mẽ cho phép các nhà phát triển trích xuất văn bản và siêu dữ liệu từ nhiều định dạng tệp khác nhau một cách liền mạch. Trong hướng dẫn này, chúng tôi sẽ tập trung vào việc tận dụng GroupDocs.Parser để trích xuất văn bản từ tài liệu Word và lưu dưới dạng HTML. Quá trình này rất cần thiết cho các tác vụ như phân tích nội dung, lập chỉ mục hoặc chuyển đổi tài liệu sang định dạng thân thiện với web. Đến cuối hướng dẫn này, bạn sẽ hiểu rõ về cách sử dụng GroupDocs.Parser một cách hiệu quả trong các ứng dụng .NET của mình.
## Điều kiện tiên quyết
Trước khi đi sâu vào hướng dẫn này, hãy đảm bảo bạn có các điều kiện tiên quyết sau:
- Kiến thức cơ bản về lập trình C#.
- Visual Studio được cài đặt trên máy phát triển của bạn.
-  GroupDocs.Parser cho thư viện .NET. Bạn có thể tải nó xuống từ[đây](https://releases.groupdocs.com/parser/net/).
- Truy cập vào một tài liệu Word mẫu cho mục đích thử nghiệm.
## Nhập không gian tên
Để bắt đầu, bạn cần nhập các vùng tên cần thiết vào dự án C# của mình:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Hãy làm theo các bước chi tiết sau để trích xuất văn bản từ tài liệu Word và lưu dưới dạng HTML bằng GroupDocs.Parser cho .NET:
## Bước 1: Tạo một phiên bản của lớp trình phân tích cú pháp
 Đầu tiên, tạo một thể hiện của`Parser` lớp bằng cách cung cấp đường dẫn đến tài liệu Word mẫu của bạn:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Tiếp tục đến Bước 2...
}
```
 Thay thế`"YourSampleFile.docx"`với đường dẫn đến tài liệu Word của bạn.
## Bước 2: Trích xuất văn bản được định dạng dưới dạng HTML
 Tiếp theo, sử dụng`GetFormattedText` phương pháp cùng với`FormattedTextOptions`để trích xuất văn bản ở định dạng HTML:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Trích xuất văn bản đã định dạng vào trình đọc
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // Tiếp tục đến Bước 3...
    }
}
```
## Bước 3: Đọc và xuất HTML được trích xuất
 Cuối cùng, đọc nội dung HTML được trích xuất từ`TextReader` và in nó ra bàn điều khiển:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Trích xuất văn bản đã định dạng vào trình đọc
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // In văn bản được định dạng dưới dạng HTML
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
## Phần kết luận
Trong hướng dẫn này, chúng ta đã khám phá cách sử dụng GroupDocs.Parser cho .NET để trích xuất văn bản từ tài liệu Word và lưu dưới dạng HTML. Thư viện này cung cấp một cách đơn giản và hiệu quả để phân tích nội dung tài liệu, khiến nó trở thành một công cụ vô giá cho các tác vụ xử lý tài liệu trong các ứng dụng .NET.

## Câu hỏi thường gặp
### Làm cách nào tôi có thể nhận được giấy phép tạm thời cho GroupDocs.Parser?
 Bạn có thể yêu cầu giấy phép tạm thời từ[đây](https://purchase.groupdocs.com/temporary-license/).
### Tôi có thể tìm thêm tài liệu về GroupDocs.Parser ở đâu?
 Tài liệu chi tiết có sẵn[đây](https://tutorials.groupdocs.com/parser/net/).
### Có bản dùng thử miễn phí cho GroupDocs.Parser không?
 Có, bạn có thể truy cập phiên bản dùng thử miễn phí[đây](https://releases.groupdocs.com/).
### Làm cách nào để nhận được hỗ trợ cho GroupDocs.Parser?
 Truy cập diễn đàn hỗ trợ[đây](https://forum.groupdocs.com/c/parser/17).
### GroupDocs.Parser hỗ trợ những loại tài liệu nào?
GroupDocs.Parser hỗ trợ nhiều định dạng tài liệu khác nhau bao gồm Word, PDF, Excel, PowerPoint, v.v.