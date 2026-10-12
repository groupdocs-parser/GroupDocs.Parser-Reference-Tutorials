---
date: '2026-10-12'
description: Tìm hiểu cách trích xuất QR từ PDF trong Java bằng cách sử dụng GroupDocs.Parser
  và xuất dữ liệu mã vạch sang XML để xử lý tiếp theo.
keywords:
- extract QR from PDF
- how to read QR
- read QR codes Java
- parse QR codes Java
- PDF QR code extraction
lastmod: '2026-10-12'
og_description: Tìm hiểu cách trích xuất QR từ PDF trong Java bằng cách sử dụng GroupDocs.Parser
  và xuất dữ liệu mã vạch sang XML để xử lý tiếp theo.
og_image_alt: Guide showing Java code that extracts QR codes from PDF files with GroupDocs.Parser
  and saves results as XML
og_title: Cách trích xuất QR từ PDF trong Java với GroupDocs.Parser
schemas:
- author: GroupDocs
  dateModified: '2026-10-12'
  description: Learn how to extract QR from PDF in Java using GroupDocs.Parser and
    export the barcode data to XML for downstream processing.
  headline: How to extract QR from PDF in Java with GroupDocs.Parser
  type: TechArticle
- description: Learn how to extract QR from PDF in Java using GroupDocs.Parser and
    export the barcode data to XML for downstream processing.
  name: How to extract QR from PDF in Java with GroupDocs.Parser
  steps:
  - name: verify barcode support
    text: 'Before attempting extraction, confirm that the document format supports
      barcode scanning: *Explanation:* This guard prevents runtime errors on unsupported
      file types.'
  - name: configure barcode options (read QR codes Java)
    text: '`BarcodeOptions` is a configuration object that lets you specify which
      barcode symbologies to detect, set the scanning quality mode, and fine‑tune
      parameters such as detection thresholds, ensuring optimal performance for the
      target QR codes. *Explanation:* `QualityMode.Low` speeds up processing; swi'
  - name: extract the QR data
    text: '`parser.getBarcodes(options)` scans the document using the provided `BarcodeOptions`
      and returns a collection of `PageBarcodeArea` objects, each encapsulating the
      decoded QR value, the page number, and the exact coordinates of the barcode
      within the page, allowing precise downstream handling. *Expla'
  - name: initialise the XML exporter
    text: '`XmlExporter` is a utility class that transforms a collection of barcode
      objects into a well‑structured XML document, automatically generating elements
      for each barcode with attributes for page index, position, and decoded value,
      which can then be saved or streamed to other systems. *Explanation:* T'
  - name: write the XML file
    text: 'Save the extracted QR information to disk: *Explanation:* The resulting
      `data.xml` contains one `<Barcode>` element per QR code, with attributes for
      page number, coordinates, and decoded value.'
  type: HowTo
- questions:
  - answer: Yes, the library supports barcode extraction from common image formats
      (PNG, JPEG, TIFF).
    question: Can I extract barcodes from image files using GroupDocs.Parser?
  - answer: QR, Code 39, Code 128, DataMatrix, PDF417, and many more. Refer to the
      API docs for the full list.
    question: What barcode formats are recognized?
  - answer: 'Pass the password to the `Parser` constructor: `new Parser(filePath,
      "password")`.'
    question: How should I handle password‑protected PDFs?
  - answer: The trial provides full functionality but adds a watermark to extracted
      data. For production, acquire a commercial license.
    question: Is the trial version sufficient for production testing?
  - answer: Create multiple `BarcodeOptions` instances or pass an array of types to
      scan for all needed formats in one pass.
    question: What if my PDF contains both QR and linear barcodes?
  type: FAQPage
tags:
- extract QR
- GroupDocs.Parser
- Java PDF processing
- barcode extraction
- XML export
title: Cách trích xuất QR từ PDF trong Java với GroupDocs.Parser
type: docs
url: /vi/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Cách trích xuất QR từ PDF trong Java với GroupDocs.Parser

Trong các quy trình kinh doanh hiện đại, **trích xuất QR từ PDF** có thể biến nút thắt nhập liệu thủ công thành một quy trình tự động hoàn toàn. Cho dù bạn đang xử lý các bản kê vận chuyển, biên lai bán lẻ, hay danh mục sản phẩm, việc nhanh chóng và đáng tin cậy lấy thông tin QR là điều cần thiết cho các hệ thống downstream. Hướng dẫn này sẽ chỉ cho bạn cách sử dụng **GroupDocs.Parser for Java** để đọc mã QR (và các mã vạch khác) từ PDF và xuất kết quả ra một tệp XML sạch mà ERP, hệ thống quản lý tồn kho, hoặc nền tảng phân tích của bạn có thể tiêu thụ.

## Câu trả lời nhanh
- **GroupDocs.Parser for Java làm gì?** Nó đọc các tệp PDF và trích xuất dữ liệu có cấu trúc như mã vạch, bảng và văn bản.  
- **Cách trích xuất mã QR?** Cấu hình `BarcodeOptions` với loại QR và gọi `parser.getBarcodes()`.  
- **Tôi có thể đọc mã QR trong Java không?** Có—đặt loại mã vạch thành `"QR"` trong tùy chọn.  
- **Tôi có cần giấy phép không?** Bản dùng thử hoạt động cho việc thử nghiệm; giấy phép thương mại cần thiết cho môi trường sản xuất.  
- **Yêu cầu phiên bản Java nào?** Java 8 hoặc cao hơn được khuyến nghị.

## “Trích xuất QR từ PDF” là gì trong bối cảnh xử lý PDF?
Trích xuất QR từ PDF có nghĩa là quét mỗi trang để tìm các đồ họa được mã hoá QR, giải mã dữ liệu nhúng và trả về dưới dạng thân thiện với chương trình. GroupDocs.Parser trừu tượng hoá việc phân tích hình ảnh cấp thấp để bạn có thể tập trung vào logic kinh doanh thay vì thao tác pixel.

## Tại sao nên sử dụng GroupDocs.Parser để trích xuất QR?
GroupDocs.Parser hỗ trợ **hơn 30 định dạng đầu vào** và có thể xử lý PDF lên tới **500 MB** mà không cần tải toàn bộ tệp vào bộ nhớ, cung cấp kết quả độ chính xác cao ngay cả trên các bản quét độ phân giải thấp. Bạn có thể chọn `QualityMode.Low` để tăng tốc hoặc `QualityMode.High` để đạt độ chính xác tối đa, và cùng một API hoạt động cho PDF, hình ảnh và tài liệu Office, loại bỏ nhu cầu sử dụng nhiều thư viện.

## Yêu cầu trước
- **GroupDocs.Parser for Java** (phiên bản 25.5 trở lên).  
- Maven hoặc tải JAR thủ công.  
- Môi trường phát triển Java 8+ (IntelliJ IDEA, Eclipse, hoặc bất kỳ trình soạn thảo nào).  

## Cài đặt GroupDocs.Parser cho Java
### Sử dụng Maven
Thêm kho lưu trữ GroupDocs và phụ thuộc vào `pom.xml` của bạn:

```xml
<repositories>
    <repository>
        <id>repository.groupdocs.com</id>
        <name>GroupDocs Repository</name>
        <url>https://releases.groupdocs.com/parser/java/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-parser</artifactId>
        <version>25.5</version>
    </dependency>
</dependencies>
```

```xml
<repositories>
    <repository>
        <id>repository.groupdocs.com</id>
        <name>GroupDocs Repository</name>
        <url>https://releases.groupdocs.com/parser/java/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-parser</artifactId>
        <version>25.5</version>
    </dependency>
</dependencies>
```

### Tải trực tiếp
Hoặc, tải JAR mới nhất từ [phiên bản GroupDocs.Parser cho Java](https://releases.groupdocs.com/parser/java/).

#### Các bước lấy giấy phép
- **Dùng thử miễn phí:** Dùng thử 30 ngày với đầy đủ tính năng.  
- **Giấy phép tạm thời:** Yêu cầu khóa tạm thời để đánh giá kéo dài.  
- **Mua:** Nhận giấy phép thương mại cho triển khai sản xuất.

### Khởi tạo và cấu hình cơ bản
Tạo một thể hiện `Parser` trỏ tới PDF bạn muốn phân tích:

`Parser` là lớp cốt lõi trong GroupDocs.Parser đại diện cho một tài liệu và cung cấp các phương thức để trích xuất nội dung như văn bản, bảng và mã vạch.  

```java
import com.groupdocs.parser.Parser;

class BarcodeExtractor {
    public static void main(String[] args) {
        // Initialize Parser object with the path to your PDF document.
        try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY")) {
            // Additional setup and usage will follow in the next sections.
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## Cách đọc mã QR trong PDF Java bằng GroupDocs.Parser
Đọc mã QR trong PDF Java với GroupDocs.Parser bao gồm tạo một thể hiện parser, cấu hình tùy chọn mã vạch để nhắm mục tiêu loại QR, gọi phương thức trích xuất mã vạch, và sau đó xử lý các đối tượng mã vạch trả về. Quy trình này đơn giản, hoạt động trên bất kỳ trang PDF nào và trả về các giá trị đã giải mã cùng với siêu dữ liệu vị trí để xử lý tiếp.

### Bước 1: xác minh hỗ trợ mã vạch
Trước khi thực hiện trích xuất, hãy xác nhận rằng định dạng tài liệu hỗ trợ quét mã vạch:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*Giải thích:* Điều này ngăn ngừa lỗi thời gian chạy trên các loại tệp không được hỗ trợ.

### Bước 2: cấu hình tùy chọn mã vạch (đọc mã QR Java)
`BarcodeOptions` là một đối tượng cấu hình cho phép bạn chỉ định các ký hiệu mã vạch cần phát hiện, đặt chế độ chất lượng quét, và tinh chỉnh các tham số như ngưỡng phát hiện, đảm bảo hiệu suất tối ưu cho các mã QR mục tiêu.

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*Giải thích:* `QualityMode.Low` tăng tốc xử lý; chuyển sang `High` nếu bạn cần độ chính xác cao hơn. Tham số `"QR"` báo cho engine chỉ tìm kiếm các mã vạch loại QR.

### Bước 3: trích xuất dữ liệu QR
`parser.getBarcodes(options)` quét tài liệu bằng `BarcodeOptions` đã cung cấp và trả về một tập hợp các đối tượng `PageBarcodeArea`, mỗi đối tượng chứa giá trị QR đã giải mã, số trang và tọa độ chính xác của mã vạch trong trang, cho phép xử lý downstream chính xác.

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*Giải thích:* `parser.getBarcodes` trả về một tập hợp có thể lặp lại các đối tượng `PageBarcodeArea`, mỗi đối tượng chứa giá trị QR đã giải mã và vị trí của nó trên trang.

## Xuất dữ liệu đã trích xuất ra XML
### Bước 4: khởi tạo bộ xuất XML
`XmlExporter` là một lớp tiện ích chuyển đổi một tập hợp các đối tượng mã vạch thành tài liệu XML có cấu trúc tốt, tự động tạo các phần tử cho mỗi mã vạch với các thuộc tính cho chỉ mục trang, vị trí và giá trị đã giải mã, sau đó có thể lưu hoặc truyền tới các hệ thống khác.

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*Giải thích:* `XmlExporter` xử lý việc tuần tự hoá các đối tượng mã vạch thành XML chuẩn, sẵn sàng tích hợp với hệ thống ERP hoặc quản lý tồn kho.

### Bước 5: ghi tệp XML
Lưu thông tin QR đã trích xuất vào đĩa:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*Giải thích:* `data.xml` kết quả chứa một phần tử `<Barcode>` cho mỗi mã QR, với các thuộc tính cho số trang, tọa độ và giá trị đã giải mã.

## Ứng dụng thực tiễn
1. **Quản lý tồn kho:** Tự động điền cơ sở dữ liệu tồn kho bằng cách đọc thẻ QR trên PDF vận chuyển đến.  
2. **Tầm nhìn chuỗi cung ứng:** Theo dõi gói hàng trong thời gian thực bằng cách trích xuất các định danh QR nhúng trong tài liệu logistics.  
3. **Biên lai bán lẻ:** Lấy thông tin khuyến mãi hoặc bảo hành từ mã QR được in trên biên lai kỹ thuật số.

## Các cân nhắc về hiệu năng
- **Quản lý bộ nhớ:** Đối với PDF rất lớn, xử lý các trang theo dạng streaming thay vì tải toàn bộ tệp vào bộ nhớ.  
- **Lựa chọn QualityMode:** Sử dụng `Low` cho xử lý hàng loạt; chuyển sang `High` khi làm việc với các bản quét độ phân giải thấp.  
- **Cập nhật thư viện:** Giữ GroupDocs.Parser luôn cập nhật để hưởng lợi từ các cải tiến hiệu năng và sửa lỗi mới nhất.

## Các vấn đề thường gặp & khắc phục
| Triệu chứng | Nguyên nhân khả dĩ | Cách khắc phục |
|------------|---------------------|----------------|
| Không có mã vạch nào được trả về | Đã chỉ định loại mã vạch sai | Thay đổi `"QR"` thành loại phù hợp (ví dụ, `"CODE_128"`). |
| Lỗi hết bộ nhớ trên PDF lớn | Toàn bộ tài liệu được tải cùng một lúc | Xử lý từng trang riêng lẻ hoặc tăng kích thước heap JVM (`-Xmx2g`). |
| Tệp XML trống | `exportBarcodes` được gọi trước khi trích xuất | Đảm bảo `parser.getBarcodes(options)` trả về dữ liệu trước khi xuất. |

## Câu hỏi thường gặp
**Q: Tôi có thể trích xuất mã vạch từ tệp hình ảnh bằng GroupDocs.Parser không?**  
A: Có, thư viện hỗ trợ trích xuất mã vạch từ các định dạng hình ảnh phổ biến (PNG, JPEG, TIFF).

**Q: Các định dạng mã vạch nào được nhận dạng?**  
A: QR, Code 39, Code 128, DataMatrix, PDF417, và nhiều hơn nữa. Tham khảo tài liệu API để xem danh sách đầy đủ.

**Q: Tôi nên xử lý PDF có mật khẩu như thế nào?**  
A: Truyền mật khẩu vào hàm khởi tạo `Parser`: `new Parser(filePath, "password")`.

**Q: Phiên bản dùng thử có đủ cho việc thử nghiệm sản xuất không?**  
A: Bản dùng thử cung cấp đầy đủ chức năng nhưng thêm watermark vào dữ liệu đã trích xuất. Đối với sản xuất, hãy mua giấy phép thương mại.

**Q: Nếu PDF của tôi chứa cả mã QR và mã vạch tuyến tính thì sao?**  
A: Tạo nhiều thể hiện `BarcodeOptions` hoặc truyền một mảng các loại để quét tất cả các định dạng cần thiết trong một lần.

---

**Cập nhật lần cuối:** 2026-10-12  
**Kiểm thử với:** GroupDocs.Parser 25.5  
**Tác giả:** GroupDocs  

## Tài nguyên
- [tài liệu GroupDocs.Parser Java](https://docs.groupdocs.com/parser/java/)
- [tham chiếu API](https://reference.groupdocs.com/parser/java)
- [tải xuống GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [kho lưu trữ GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [diễn đàn hỗ trợ miễn phí](https://forum.groupdocs.com/c/parser)
- [đơn xin giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/)

## Hướng dẫn liên quan
- [Trích xuất mã vạch PDF GroupDocs Parser Java](/parser/java/barcode-extraction/extract-barcode-pdf-groupdocs-parser-java/)
- [Cách tải PDF từ URL bằng GroupDocs.Parser cho Java](/parser/java/document-loading/)
- [Trích xuất dữ liệu biểu mẫu PDF với GroupDocs.Parser trong Java](/parser/java/form-extraction/groupdocs-parser-java-pdf-form-extraction/)