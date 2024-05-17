---
title: Tìm kiếm văn bản có điểm nổi bật
linktitle: Tìm kiếm văn bản có điểm nổi bật
second_title: API GroupDocs.Parser .NET
description: Tìm hiểu cách tìm kiếm và đánh dấu văn bản trong tài liệu bằng GroupDocs.Parser cho .NET. Trích xuất những hiểu biết có giá trị một cách hiệu quả.
type: docs
weight: 24
url: /vi/net/text-extraction/search-text-with-highlights/
---
## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ khám phá cách sử dụng GroupDocs.Parser cho .NET để tìm kiếm văn bản trong tài liệu và đánh dấu kết quả tìm kiếm. GroupDocs.Parser là một thư viện mạnh mẽ cho phép bạn làm việc với nhiều định dạng tài liệu khác nhau và trích xuất văn bản, siêu dữ liệu, v.v.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn có những điều sau:
1.  GroupDocs.Parser for .NET: Tải xuống và cài đặt thư viện từ[đây](https://releases.groupdocs.com/parser/net/).
2. IDE: Sử dụng Visual Studio hoặc bất kỳ IDE ưa thích nào để phát triển .NET.
3. Tệp mẫu: Chuẩn bị một tài liệu mẫu (ví dụ: PDF, DOCX) để tìm kiếm văn bản.

## Nhập không gian tên
Trước tiên, hãy bắt đầu bằng cách nhập các vùng tên cần thiết trong dự án .NET của bạn:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Bước 1: Tạo phiên bản trình phân tích cú pháp
 Bắt đầu bằng việc khởi tạo`Parser` class bằng đường dẫn đến tệp mẫu của bạn:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Mã của bạn ở đây
}
```
## Bước 2: Xác định các tùy chọn đánh dấu
 Chỉ định la`HighlightOptions` để định cấu hình cách đánh dấu kết quả tìm kiếm. Ví dụ: đặt cửa sổ ngữ cảnh gồm 15 ký tự:
```csharp
HighlightOptions highlightOptions = new HighlightOptions(15);
```
## Bước 3: Tìm kiếm văn bản
Bây giờ, thực hiện tìm kiếm văn bản trong tài liệu. Cung cấp từ khóa bạn muốn tìm kiếm (ví dụ: "lorem"):
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("lorem", new SearchOptions(true, false, false, highlightOptions));
```
## Bước 4: Xử lý kết quả tìm kiếm
Lặp lại qua các kết quả tìm kiếm và hiển thị văn bản tìm thấy cùng với những điểm nổi bật:
```csharp
if (searchResults != null)
{
    foreach (SearchResult result in searchResults)
    {
        Console.WriteLine($"{result.LeftHighlightItem.Text}{result.Text}{result.RightHighlightItem.Text}");
    }
}
else
{
    Console.WriteLine("Search isn't supported");
}
```

## Phần kết luận
Trong hướng dẫn này, bạn đã học cách sử dụng GroupDocs.Parser cho .NET để tìm kiếm văn bản trong tài liệu và đánh dấu kết quả tìm kiếm. Chức năng này có thể cực kỳ hữu ích cho việc trích xuất và phân tích văn bản trong các ứng dụng .NET của bạn.

## Câu hỏi thường gặp
### GroupDocs.Parser có phù hợp để xử lý các định dạng tài liệu khác nhau không?
Có, GroupDocs.Parser hỗ trợ nhiều định dạng tài liệu bao gồm PDF, DOCX, XLSX, PPTX, v.v.
### Tôi có thể sử dụng GroupDocs.Parser để trích xuất siêu dữ liệu từ tài liệu không?
Tuyệt đối! GroupDocs.Parser cho phép bạn trích xuất siêu dữ liệu, văn bản và dữ liệu có cấu trúc từ tài liệu.
### Tôi có thể tìm hỗ trợ hoặc đặt câu hỏi về GroupDocs.Parser ở đâu?
 Bạn có thể ghé thăm[Diễn đàn GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) cho bất kỳ truy vấn liên quan đến hỗ trợ.
### Có bản dùng thử miễn phí cho GroupDocs.Parser không?
 Có, bạn có thể truy cập một[dùng thử miễn phí](https://releases.groupdocs.com/) của GroupDocs.Parser để đánh giá các tính năng của nó.
### Làm cách nào tôi có thể mua giấy phép cho GroupDocs.Parser?
 Bạn có thể mua giấy phép từ[đây](https://purchase.groupdocs.com/buy) và cũng có được giấy phép tạm thời[đây](https://purchase.groupdocs.com/temporary-license/).