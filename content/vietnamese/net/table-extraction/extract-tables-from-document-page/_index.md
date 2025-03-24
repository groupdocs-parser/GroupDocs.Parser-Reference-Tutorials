---
title: Trích xuất bảng từ trang tài liệu
linktitle: Trích xuất bảng từ trang tài liệu
second_title: API GroupDocs.Parser .NET
description: Tìm hiểu cách trích xuất bảng từ tài liệu theo chương trình bằng GroupDocs.Parser cho .NET. Hướng dẫn toàn diện này cung cấp hướng dẫn từng bước.
weight: 11
url: /vi/net/table-extraction/extract-tables-from-document-page/
---
## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ khám phá cách trích xuất bảng từ một trang tài liệu bằng GroupDocs.Parser cho .NET. GroupDocs.Parser là một thư viện mạnh mẽ cho phép các nhà phát triển làm việc với nhiều định dạng tài liệu khác nhau như PDF, DOCX, XLSX, v.v. Bằng cách tận dụng các tính năng của nó, chúng tôi có thể trích xuất dữ liệu có cấu trúc như bảng từ các tài liệu này một cách hiệu quả, cho phép chúng tôi thao tác và phân tích thông tin theo chương trình.
## Điều kiện tiên quyết
Trước khi bắt đầu, hãy đảm bảo bạn có những điều sau:
- Visual Studio được cài đặt trên máy của bạn.
- Hiểu biết cơ bản về phát triển C# và .NET.
-  GroupDocs.Parser cho thư viện .NET. Bạn có thể tải nó xuống từ[đây](https://releases.groupdocs.com/parser/net/).
- Truy cập vào tài liệu mẫu (PDF, DOCX, v.v.) có chứa các bảng để trích xuất.

## Nhập không gian tên
Trước tiên, hãy bắt đầu bằng cách nhập các không gian tên cần thiết vào dự án C# của bạn:
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
 Khởi tạo`Parser` lớp bằng cách cung cấp đường dẫn đến tài liệu mẫu của bạn:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //Mã của bạn tiếp tục ở đây...
}
```
## Bước 2: Kiểm tra hỗ trợ trích xuất bảng tài liệu
Trước khi tiếp tục, hãy xác minh xem tài liệu có hỗ trợ trích xuất bảng hay không:
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document does not support table extraction.");
    return;
}
```
## Bước 3: Xác định bố cục bảng
Xác định cách bố trí các bảng được trích xuất từ tài liệu. Chỉ định chiều rộng cột và chiều cao hàng theo cấu trúc tài liệu của bạn:
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },  // Độ rộng cột
    new double[] { 325, 340, 365, 395 });         // Chiều cao hàng
```
## Bước 4: Định cấu hình tùy chọn trích xuất bảng
Tạo các tùy chọn để trích xuất bảng bằng cách sử dụng bố cục đã chỉ định:
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Bước 5: Truy xuất thông tin tài liệu
Lấy thông tin về tài liệu, bao gồm số trang:
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Bước 6: Lặp lại các trang tài liệu
Lặp lại qua từng trang của tài liệu để trích xuất bảng:
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Trích xuất bảng từ trang hiện tại
    IEnumerable<PageTableArea> tables = parser.GetTables(pageIndex, options);
    // Lặp lại các bảng được trích xuất
    foreach (PageTableArea table in tables)
    {
        // Lặp lại các hàng của bảng
        for (int row = 0; row < table.RowCount; row++)
        {
            // Lặp lại các cột của bảng
            for (int column = 0; column < table.ColumnCount; column++)
            {
                // Lấy ô của bảng
                PageTableAreaCell cell = table[row, column];
                if (cell != null)
                {
                    // In văn bản của ô bảng
                    Console.Write(cell.Text);
                    Console.Write(" | ");
                }
            }
            Console.WriteLine();
        }
        Console.WriteLine();
    }
}
```

## Phần kết luận
Trong hướng dẫn này, chúng tôi đã đề cập đến quá trình trích xuất bảng từ các trang tài liệu bằng GroupDocs.Parser cho .NET. Bằng cách làm theo các bước được cung cấp, bạn có thể tích hợp liền mạch chức năng trích xuất bảng vào các ứng dụng .NET của mình, cho phép xử lý và thao tác hiệu quả dữ liệu có cấu trúc trong tài liệu.

## Câu hỏi thường gặp
### GroupDocs.Parser có thể trích xuất bảng từ tất cả các loại tài liệu không?
GroupDocs.Parser hỗ trợ nhiều định dạng tài liệu khác nhau như PDF, DOCX, XLSX, v.v., cho phép trích xuất bảng từ các loại tệp tương thích.
### GroupDocs.Parser cho .NET có phù hợp để xử lý tài liệu quy mô lớn không?
Có, GroupDocs.Parser được thiết kế để xử lý các tài liệu lớn một cách hiệu quả, giúp nó phù hợp để xử lý các tập dữ liệu mở rộng.
### GroupDocs.Parser có giữ nguyên định dạng trong quá trình trích xuất bảng không?
Có, GroupDocs.Parser giữ lại các chi tiết định dạng như viền ô, kiểu văn bản và căn chỉnh trong quá trình trích xuất bảng.
### Tôi có thể trích xuất các bảng cụ thể dựa trên tiêu chí nội dung không?
GroupDocs.Parser cung cấp các tùy chọn linh hoạt để nhắm mục tiêu các bảng cụ thể dựa trên mẫu bố cục hoặc điều kiện nội dung để trích xuất.
### GroupDocs.Parser có tương thích với .NET Core không?
Có, GroupDocs.Parser tương thích với cả môi trường .NET Framework và .NET Core.