---
title: Trích xuất mã vạch từ tài liệu với các tùy chọn
linktitle: Trích xuất mã vạch từ tài liệu với các tùy chọn
second_title: API GroupDocs.Parser .NET
description: Tìm hiểu cách trích xuất mã vạch từ tài liệu bằng GroupDocs.Parser cho .NET. Hướng dẫn toàn diện với các ví dụ về mã và câu hỏi thường gặp.
weight: 14
url: /vi/net/barcode-extraction/extract-barcodes-from-document-with-options/
---

# Trích xuất mã vạch từ tài liệu với các tùy chọn

## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ tìm hiểu quy trình trích xuất mã vạch từ tài liệu bằng GroupDocs.Parser cho .NET. GroupDocs.Parser là một thư viện mạnh mẽ cho phép bạn trích xuất văn bản, siêu dữ liệu và mã vạch từ nhiều định dạng tài liệu khác nhau như PDF, Microsoft Word, Excel, v.v.
## Điều kiện tiên quyết
Trước khi bắt đầu, hãy đảm bảo bạn có sẵn các điều kiện tiên quyết sau:
1. Môi trường phát triển: Đảm bảo bạn đã cài đặt Visual Studio trên máy của mình.
2.  Thư viện GroupDocs.Parser: Tải xuống và cài đặt thư viện GroupDocs.Parser cho .NET từ[đây](https://releases.groupdocs.com/parser/net/).
3. Tài liệu mẫu: Chuẩn bị một tài liệu mẫu (ví dụ: PDF, DOCX) có chứa mã vạch để trích xuất.

## Nhập không gian tên
Trước tiên, bạn cần nhập các vùng tên cần thiết vào dự án C# của mình để sử dụng các chức năng GroupDocs.Parser.
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using System;
using System.Collections.Generic;
```
## Bước 1: Tạo một phiên bản của lớp trình phân tích cú pháp
 Để bắt đầu, hãy tạo một phiên bản của`Parser` class bằng cách chuyển đường dẫn đến tài liệu mẫu của bạn.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Mã sẽ được thêm vào trong các bước tiếp theo
}
```
## Bước 2: Kiểm tra hỗ trợ trích xuất mã vạch
 Tiếp theo, hãy kiểm tra xem tài liệu có hỗ trợ trích xuất mã vạch hay không bằng cách sử dụng`Features` tài sản của`Parser` ví dụ.
```csharp
if (!parser.Features.Barcodes)
{
    Console.WriteLine("Document doesn't support barcode extraction.");
    return;
}
```
## Bước 3: Xác định các tùy chọn trích xuất mã vạch
 Bây giờ, hãy chỉ định các tùy chọn để trích xuất mã vạch bằng cách sử dụng`BarcodeOptions`. Bạn có thể đặt các thông số như chế độ chất lượng và loại mã vạch.
```csharp
BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```
## Bước 4: Trích xuất mã vạch từ tài liệu
 Sử dụng`GetBarcodes` phương pháp của`Parser` lớp để trích xuất mã vạch dựa trên các tùy chọn được xác định.
```csharp
IEnumerable<PageBarcodeArea> barcodes = parser.GetBarcodes(options);
```
## Bước 5: Lặp lại và hiển thị mã vạch được trích xuất
Cuối cùng, lặp lại các mã vạch được trích xuất và hiển thị chỉ mục cũng như giá trị trang của chúng.
```csharp
foreach (PageBarcodeArea barcode in barcodes)
{
    Console.WriteLine("Page: " + barcode.Page.Index.ToString());
    Console.WriteLine("Value: " + barcode.Value);
}
```

## Phần kết luận
 Trong hướng dẫn này, chúng ta đã học cách trích xuất mã vạch từ tài liệu bằng GroupDocs.Parser cho .NET. Quá trình này bao gồm việc tạo ra một`Parser` ví dụ, xác định các tùy chọn trích xuất và lặp lại các mã vạch được trích xuất. GroupDocs.Parser đơn giản hóa tác vụ trích xuất mã vạch từ các định dạng tài liệu khác nhau, cho phép xử lý tài liệu hiệu quả trong các ứng dụng .NET của bạn.

## Câu hỏi thường gặp
### GroupDocs.Parser có thể trích xuất mã vạch từ tài liệu PDF không?
Có, GroupDocs.Parser hỗ trợ trích xuất mã vạch từ tài liệu PDF cùng với các định dạng khác như DOCX, XLSX, v.v.
### GroupDocs.Parser hỗ trợ những loại mã vạch nào?
GroupDocs.Parser hỗ trợ nhiều loại mã vạch khác nhau bao gồm mã QR, Mã 39, Mã 128, v.v.
### GroupDocs.Parser có yêu cầu giấy phép sử dụng thương mại không?
 Có, cần có giấy phép hợp lệ để sử dụng cho mục đích thương mại. Bạn có thể lấy giấy phép từ[đây](https://purchase.groupdocs.com/buy).
### GroupDocs.Parser có phù hợp để xử lý hàng loạt tài liệu không?
Có, GroupDocs.Parser có thể xử lý hiệu quả việc xử lý hàng loạt tài liệu để trích xuất văn bản, truy xuất siêu dữ liệu và trích xuất mã vạch.
### Tôi có thể tìm hỗ trợ kỹ thuật cho GroupDocs.Parser ở đâu?
 Bạn có thể nhận được hỗ trợ kỹ thuật hoặc đặt câu hỏi trên[diễn đàn GroupDocs](https://forum.groupdocs.com/c/parser/17).