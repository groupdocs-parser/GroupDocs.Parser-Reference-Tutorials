---
title: Trích xuất bảng từ tài liệu
linktitle: Trích xuất bảng từ tài liệu
second_title: API GroupDocs.Parser .NET
description: Tìm hiểu cách trích xuất bảng từ tài liệu bằng Groupdocs.Parser cho .NET. Hãy làm theo hướng dẫn chi tiết về cách tích hợp chức năng này.
type: docs
weight: 10
url: /vi/net/table-extraction/extract-tables-from-document/
---
## Giới thiệu
Groupdocs.Parser cho .NET là một thư viện toàn diện hỗ trợ phân tích cú pháp tài liệu, cho phép bạn trích xuất thông tin có giá trị như bảng, văn bản, siêu dữ liệu và nhiều thông tin khác từ tài liệu. Trong hướng dẫn này, chúng tôi đặc biệt tập trung vào việc trích xuất các bảng từ tài liệu bằng API Groupdocs.Parser.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn có những điều sau:
- Visual Studio được cài đặt trên hệ thống của bạn.
- Đã cài đặt .NET Framework hoặc .NET Core.
- Kiến thức cơ bản về lập trình C#.

## Nhập không gian tên
Trước tiên, bạn cần nhập các không gian tên cần thiết để truy cập các lớp và phương thức Groupdocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using GroupDocs.Parser.Templates;
```
## Bước 1: Tạo một phiên bản của lớp trình phân tích cú pháp
 Khởi tạo một phiên bản mới của`Parser` class bằng cách cung cấp đường dẫn đến tài liệu mẫu của bạn.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Mã của bạn ở đây
}
```
## Bước 2: Kiểm tra hỗ trợ trích xuất bảng
 Xác minh xem tài liệu có hỗ trợ trích xuất bảng bằng cách sử dụng`Features` tài sản của`Parser` lớp học.
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document doesn't support table extraction.");
    return;
}
```
## Bước 3: Xác định bố cục bảng
Xác định bố cục của các bảng bạn muốn trích xuất bằng cách sử dụng`TemplateTableLayout`. Chỉ định chiều rộng cột và chiều cao hàng dựa trên cấu trúc tài liệu của bạn.
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },
    new double[] { 325, 340, 365, 395 });
```
## Bước 4: Đặt tùy chọn trích xuất bảng
 Tạo nên`PageTableAreaOptions` với bố cục đã xác định để chỉ định cách trích xuất bảng.
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Bước 5: Trích xuất bảng
 Sử dụng`GetTables` phương pháp của`Parser` class để trích xuất các bảng từ tài liệu dựa trên các tùy chọn đã chỉ định.
```csharp
IEnumerable<PageTableArea> tables = parser.GetTables(options);
```
## Bước 6: Lặp lại và truy cập dữ liệu bảng
Lặp lại qua các bảng được trích xuất cũng như các hàng và cột tương ứng của chúng để truy cập dữ liệu ô.
```csharp
foreach (PageTableArea table in tables)
{
    for (int row = 0; row < table.RowCount; row++)
    {
        for (int column = 0; column < table.ColumnCount; column++)
        {
            PageTableAreaCell cell = table[row, column];
            if (cell != null)
            {
                Console.Write(cell.Text);
                Console.Write(" | ");
            }
        }
        Console.WriteLine();
    }
    Console.WriteLine();
}
```
## Phần kết luận
Trong hướng dẫn này, chúng tôi đã đề cập đến cách sử dụng Groupdocs.Parser cho .NET để trích xuất bảng từ tài liệu một cách hiệu quả. Tận dụng các khả năng của thư viện này, bạn có thể tích hợp trích xuất bảng vào các ứng dụng .NET của mình một cách liền mạch.

## Câu hỏi thường gặp
### Groupdocs.Parser có thể xử lý các định dạng tài liệu khác nhau không?
Có, Groupdocs.Parser hỗ trợ nhiều định dạng tài liệu bao gồm DOCX, PDF, XLSX, v.v.
### Có phiên bản dùng thử nào cho Groupdocs.Parser cho .NET không?
 Có, bạn có thể tải xuống bản dùng thử miễn phí từ[đây](https://releases.groupdocs.com/).
### Làm cách nào tôi có thể nhận được hỗ trợ cho các truy vấn liên quan đến Groupdocs.Parser?
 Bạn có thể ghé thăm[Diễn đàn Groupdocs.Parser](https://forum.groupdocs.com/c/parser/17) để được hỗ trợ.
### Tôi có thể mua giấy phép cho Groupdocs.Parser ở đâu?
 Bạn có thể mua giấy phép từ[đây](https://purchase.groupdocs.com/buy).
### Làm cách nào để có được giấy phép tạm thời cho mục đích đánh giá?
 Bạn có thể có được giấy phép tạm thời[đây](https://purchase.groupdocs.com/temporary-license/).