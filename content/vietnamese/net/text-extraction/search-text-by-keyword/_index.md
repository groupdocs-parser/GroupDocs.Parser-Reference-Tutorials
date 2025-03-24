---
title: Tìm kiếm văn bản theo từ khóa
linktitle: Tìm kiếm văn bản theo từ khóa
second_title: API GroupDocs.Parser .NET
description: Tìm hiểu cách tìm kiếm văn bản theo từ khóa trong tài liệu bằng GroupDocs.Parser cho .NET. Trích xuất hiệu quả nội dung có liên quan một cách dễ dàng.
weight: 21
url: /vi/net/text-extraction/search-text-by-keyword/
---

# Tìm kiếm văn bản theo từ khóa

## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ đi sâu vào cách sử dụng GroupDocs.Parser cho .NET để tìm kiếm văn bản theo từ khóa trong tài liệu. GroupDocs.Parser là một thư viện mạnh mẽ cho phép các nhà phát triển trích xuất văn bản, siêu dữ liệu và thông tin khác từ nhiều định dạng tệp khác nhau, chẳng hạn như PDF, tài liệu Microsoft Office, v.v. Việc tìm kiếm các từ khóa cụ thể trong các tài liệu này có thể cần thiết cho các ứng dụng xử lý khối lượng lớn dữ liệu văn bản.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn đã thiết lập sau:
1. Môi trường phát triển: Visual Studio hoặc bất kỳ .NET IDE ưa thích nào.
2.  GroupDocs.Parser cho .NET: Tải xuống thư viện từ[đây](https://releases.groupdocs.com/parser/net/).
3. Truy cập vào Tệp mẫu: Chuẩn bị tệp mẫu (ví dụ: PDF, DOCX) để kiểm tra chức năng tìm kiếm từ khóa.

## Nhập không gian tên
Trước tiên, bạn cần bao gồm các không gian tên cần thiết trong dự án của mình.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Bước 1: Khởi tạo lớp trình phân tích cú pháp
 Bắt đầu bằng cách tạo một thể hiện của`Parser` class và cung cấp đường dẫn đến tệp mẫu của bạn.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Tìm kiếm từ khóa
    IEnumerable<SearchResult> searchResults = parser.Search("test");
    // Lặp lại kết quả tìm kiếm
    foreach (SearchResult result in searchResults)
    {
        //In chỉ mục và văn bản tìm thấy
        Console.WriteLine($"At {result.Position}: {result.Text}");
    }
}
```
## Bước 2: Tìm kiếm từ khóa
 Trong`using` chặn, gọi`Search` phương pháp trên`parser` đối tượng, chuyển từ khóa mong muốn làm đối số.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("test");
```
 Thay thế`"test"` với từ khóa bạn muốn tìm kiếm trong tài liệu.
## Bước 3: Lặp lại kết quả tìm kiếm
 Tiếp theo, lặp lại các kết quả tìm kiếm thu được từ`Search` phương pháp sử dụng một`foreach` vòng.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
 Cho mỗi`SearchResult` sự vật`result` , bạn có thể truy cập nó`Position` (chỉ số) và`Text` (văn bản tìm thấy).

## Phần kết luận
 Trong hướng dẫn này, chúng tôi đã khám phá cách sử dụng GroupDocs.Parser cho .NET để tìm kiếm văn bản theo từ khóa trong tài liệu một cách dễ dàng. Tận dụng các`Search` phương pháp của`Parser` lớp cho phép truy xuất hiệu quả các đoạn văn bản có liên quan dựa trên các cụm từ tìm kiếm cụ thể.

## Câu hỏi thường gặp
### GroupDocs.Parser có tương thích với nhiều định dạng tài liệu khác nhau không?
Có, GroupDocs.Parser hỗ trợ nhiều định dạng tệp, bao gồm PDF, DOCX, XLSX, PPTX, v.v.
### Tôi có thể thực hiện các thao tác trích xuất văn bản nâng cao bằng GroupDocs.Parser không?
Tuyệt đối! Ngoài tìm kiếm văn bản, GroupDocs.Parser còn cho phép trích xuất siêu dữ liệu, trích xuất văn bản có cấu trúc, v.v.
### Tôi có thể tìm tài liệu chi tiết về GroupDocs.Parser ở đâu?
Khám phá tài liệu đầy đủ[đây](https://tutorials.groupdocs.com/parser/net/).
### Làm cách nào tôi có thể nhận được hỗ trợ hoặc trợ giúp với các truy vấn liên quan đến GroupDocs.Parser?
 Truy cập diễn đàn GroupDocs để được hỗ trợ và thảo luận[đây](https://forum.groupdocs.com/c/parser/17).
### Có phiên bản dùng thử nào để đánh giá GroupDocs.Parser trước khi mua không?
 Có, bạn có thể truy cập bản dùng thử miễn phí[đây](https://releases.groupdocs.com/).