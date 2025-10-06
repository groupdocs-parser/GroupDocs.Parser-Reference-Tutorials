---
title: Tìm kiếm văn bản theo biểu thức chính quy (Regex)
linktitle: Tìm kiếm văn bản theo biểu thức chính quy (Regex)
second_title: API GroupDocs.Parser .NET
description: Tìm hiểu cách tìm kiếm văn bản bằng cách sử dụng cụm từ thông dụng trong tài liệu bằng GroupDocs.Parser cho .NET. Trích xuất nội dung cụ thể một cách dễ dàng.
weight: 23
url: /vi/net/text-extraction/search-text-by-regex/
type: docs
---
# Tìm kiếm văn bản theo biểu thức chính quy (Regex)

## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ đi sâu vào việc sử dụng GroupDocs.Parser cho .NET để tìm kiếm văn bản theo biểu thức chính quy (Regex) trong tài liệu. GroupDocs.Parser là một thư viện mạnh mẽ cho phép các nhà phát triển trích xuất văn bản và siêu dữ liệu từ nhiều định dạng tệp khác nhau như PDF, DOCX, XLSX, v.v. Tìm kiếm văn bản bằng cách sử dụng biểu thức chính quy đặc biệt hữu ích để tìm mẫu hoặc nội dung cụ thể trong tài liệu một cách hiệu quả.
## Điều kiện tiên quyết
Trước khi đi sâu vào hướng dẫn này, hãy đảm bảo bạn có những điều sau:
1. Visual Studio: Cài đặt Visual Studio IDE để phát triển .NET.
2.  GroupDocs.Parser cho .NET: Tải xuống và cài đặt GroupDocs.Parser cho .NET từ[đây](https://releases.groupdocs.com/parser/net/).
3. Tệp mẫu: Chuẩn bị một tài liệu mẫu (PDF, DOCX, v.v.) để kiểm tra chức năng tìm kiếm.

## Nhập không gian tên
Trước tiên, hãy bắt đầu bằng cách đưa các không gian tên cần thiết vào mã C# của bạn:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Bước 1: Tạo một phiên bản của lớp trình phân tích cú pháp
 Khởi tạo`Parser` class bằng cách cung cấp đường dẫn đến tệp mẫu của bạn:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Mã ở đây
}
```
 Thay thế`"YourSampleFile.pdf"` với đường dẫn đến tập tin thực tế của bạn.
## Bước 2: Tìm kiếm bằng biểu thức chính quy
Xác định và thực hiện tìm kiếm bằng cách sử dụng mẫu biểu thức chính quy. Ví dụ: để tìm các chuỗi số (ví dụ: số nguyên) trong tài liệu:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("[0-9]+", new SearchOptions(true, false, true));
```
 Trong ví dụ này,`[0-9]+` là mẫu biểu thức chính quy khớp với một hoặc nhiều chữ số.
## Bước 3: Kiểm tra hỗ trợ tìm kiếm
Xác minh xem hoạt động tìm kiếm có được hỗ trợ cho loại tài liệu hay không:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported");
    return;
}
```
## Bước 4: Lặp lại kết quả tìm kiếm
Lặp lại qua các kết quả tìm kiếm và xử lý từng kết quả phù hợp:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Vòng lặp này sẽ in vị trí và văn bản phù hợp được tìm thấy trong tài liệu.

## Phần kết luận
Tóm lại, việc tận dụng GroupDocs.Parser cho .NET cho phép tìm kiếm văn bản hiệu quả bằng cách sử dụng các biểu thức chính quy trên nhiều định dạng tài liệu khác nhau. Bằng cách làm theo hướng dẫn này, các nhà phát triển có thể tích hợp liền mạch tính năng phân tích cú pháp tài liệu và trích xuất văn bản dựa trên biểu thức chính quy vào các ứng dụng .NET của họ.

## Câu hỏi thường gặp
### GroupDocs.Parser có thể tìm kiếm trong các tài liệu được mã hóa không?
Không, GroupDocs.Parser không thể tìm kiếm trong các tài liệu được mã hóa hoặc bảo vệ bằng mật khẩu.
### GroupDocs.Parser có hỗ trợ OCR (Nhận dạng ký tự quang học) không?
Không, GroupDocs.Parser không thực hiện OCR. Nó dựa vào việc trích xuất văn bản từ cấu trúc bên trong của tài liệu.
### Tôi có thể tìm kiếm các mẫu phức tạp bằng cách sử dụng biểu thức thông thường không?
Có, GroupDocs.Parser hỗ trợ các biểu thức chính quy đầy đủ, cho phép khớp mẫu phức tạp trong tài liệu.
### Những định dạng tài liệu nào được hỗ trợ để trích xuất văn bản?
GroupDocs.Parser hỗ trợ nhiều định dạng, bao gồm PDF, DOCX, XLSX, PPTX, v.v.
### GroupDocs.Parser có tương thích với .NET Core không?
Có, GroupDocs.Parser tương thích với .NET Core để phát triển đa nền tảng.