---
title: Tìm kiếm văn bản trong tài liệu Word theo từ khóa
linktitle: Tìm kiếm văn bản trong tài liệu Word theo từ khóa
second_title: API GroupDocs.Parser .NET
description: Tìm hiểu cách tìm kiếm văn bản trong tài liệu Word bằng GroupDocs.Parser cho .NET. Trích xuất các từ khóa cụ thể một cách hiệu quả.
type: docs
weight: 18
url: /vi/net/word-document-processing/search-text-in-word-document-by-keyword/
---
## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ khám phá cách sử dụng GroupDocs.Parser cho .NET để tìm kiếm văn bản cụ thể trong tài liệu Word bằng C#. GroupDocs.Parser là một thư viện mạnh mẽ cho phép các nhà phát triển trích xuất văn bản và siêu dữ liệu từ nhiều định dạng tài liệu khác nhau, bao gồm cả tài liệu Word.
## Điều kiện tiên quyết
Trước khi bắt đầu, hãy đảm bảo bạn có các điều kiện tiên quyết sau:
1. Môi trường phát triển: Cài đặt Visual Studio hoặc IDE tương thích khác.
2.  Thư viện GroupDocs.Parser: Tải xuống và cài đặt thư viện GroupDocs.Parser cho .NET từ[trang mạng](https://releases.groupdocs.com/parser/net/).
3. Tài liệu Word mẫu: Chuẩn bị một tài liệu Word mẫu để sử dụng cho việc tìm kiếm văn bản.

## Nhập không gian tên
Bắt đầu bằng cách nhập các vùng tên cần thiết trong dự án C# của bạn:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Bước 1: Tạo một phiên bản của lớp trình phân tích cú pháp
 Đầu tiên, tạo một thể hiện của`Parser` lớp bằng cách chuyển đường dẫn đến tài liệu Word mẫu của bạn.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Mã ở đây
}
```
## Bước 2: Tìm kiếm từ khóa
 Tiếp theo, sử dụng`Search` phương pháp của`Parser` class để tìm kiếm một từ khóa cụ thể trong tài liệu.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword");
```
 Thay thế`"keyword"` với văn bản bạn muốn tìm kiếm trong tài liệu.
## Bước 3: Lặp lại kết quả tìm kiếm
 Lặp lại các kết quả tìm kiếm bằng cách sử dụng một`foreach` vòng lặp để truy cập từng`SearchResult` sự vật.
```csharp
foreach (SearchResult result in searchResults)
{
    //Mã để xử lý từng kết quả tìm kiếm
}
```
## Bước 4: Truy cập chi tiết kết quả tìm kiếm
 Trong vòng lặp, bạn có thể truy cập vị trí và văn bản của từng kết quả tìm kiếm bằng cách sử dụng`Position` Và`Text` thuộc tính của`SearchResult` sự vật.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Đoạn mã này in chỉ mục (`Position`) và văn bản tìm thấy (`Text`) cho mỗi kết quả tìm kiếm vào bảng điều khiển.

## Phần kết luận
Trong hướng dẫn này, bạn đã học cách sử dụng GroupDocs.Parser cho .NET để tìm kiếm văn bản cụ thể trong tài liệu Word. Thư viện này cung cấp một cách thuận tiện để trích xuất và thao tác nội dung từ các định dạng tài liệu khác nhau theo chương trình.

## Câu hỏi thường gặp
### GroupDocs.Parser có thể xử lý các định dạng tài liệu khác ngoài Word không?
Có, GroupDocs.Parser hỗ trợ nhiều định dạng, bao gồm PDF, Excel, PowerPoint, v.v.
### GroupDocs.Parser có tương thích với .NET Core không?
Có, GroupDocs.Parser tương thích với cả .NET Framework và .NET Core.
### Làm cách nào để có được giấy phép tạm thời cho GroupDocs.Parser?
 Bạn có thể yêu cầu giấy phép tạm thời từ[Trang mua GroupDocs](https://purchase.groupdocs.com/temporary-license/).
### Tôi có thể tìm thêm hỗ trợ hoặc đặt câu hỏi về GroupDocs.Parser ở đâu?
 Tham quan[Diễn đàn GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) để được cộng đồng hỗ trợ và thảo luận.
### Tôi có thể dùng thử GroupDocs.Parser miễn phí trước khi mua không?
 Có, bạn có thể tải xuống phiên bản dùng thử miễn phí từ[Trang phát hành GroupDocs](https://releases.groupdocs.com/).