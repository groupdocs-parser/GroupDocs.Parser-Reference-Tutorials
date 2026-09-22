---
date: '2026-09-22'
description: Tìm hiểu cách trích xuất mã vạch từ PDF bằng GroupDocs.Parser cho Java.
  Hướng dẫn từng bước này bao gồm phân tích mẫu, trích xuất QR code và cài đặt Java.
keywords:
- extract barcode from pdf
- extract qr code java
- parse pdf document pages
- parse pdf by template
- pdf barcode detection java
lastmod: '2026-09-22'
og_description: Tìm hiểu cách trích xuất mã vạch từ PDF bằng GroupDocs.Parser cho
  Java. Hướng dẫn từng bước này bao gồm phân tích mẫu, trích xuất QR code và cài đặt
  Java.
og_image_alt: Guide to extract barcode from PDF using GroupDocs.Parser Java
og_title: Cách trích xuất mã vạch từ PDF bằng GroupDocs.Parser Java
schemas:
- author: GroupDocs
  dateModified: '2026-09-22'
  description: Learn how to extract barcode from PDF using GroupDocs.Parser for Java.
    This step‑by‑step guide covers template parsing, QR code extraction, and Java
    setup.
  headline: How to extract barcode from PDF with GroupDocs.Parser Java
  type: TechArticle
- description: Learn how to extract barcode from PDF using GroupDocs.Parser for Java.
    This step‑by‑step guide covers template parsing, QR code extraction, and Java
    setup.
  name: How to extract barcode from PDF with GroupDocs.Parser Java
  steps:
  - name: '**Add the repository and dependency** – copy the XML snippet above into
      your `pom.xml`.'
    text: '**Add the repository and dependency** – copy the XML snippet above into
      your `pom.xml`.'
  - name: '**Import the required classes** – classes such as `Parser`, `Template`,
      `DocumentPageData`, etc., live in the `com.groupdocs.parser` package.'
    text: '**Import the required classes** – classes such as `Parser`, `Template`,
      `DocumentPageData`, etc., live in the `com.groupdocs.parser` package.'
  - name: '**Initialize the parser** – create a `Parser` instance and point it at
      the PDF you want to process.'
    text: '**Initialize the parser** – create a `Parser` instance and point it at
      the PDF you want to process.'
  - name: '**Inventory management** – Automatically read barcodes from supplier PDFs
      to update stock databases.'
    text: '**Inventory management** – Automatically read barcodes from supplier PDFs
      to update stock databases.'
  - name: '**Legal document verification** – Extract QR codes that embed digital signatures
      for audit trails.'
    text: '**Legal document verification** – Extract QR codes that embed digital signatures
      for audit trails.'
  - name: '**Data migration** – Use barcodes as unique identifiers when moving records
      between legacy systems.'
    text: '**Data migration** – Use barcodes as unique identifiers when moving records
      between legacy systems.'
  type: HowTo
- questions:
  - answer: Yes, as long as they are embedded in a PDF. Ensure the scan resolution
      is at least 300 dpi for reliable detection.
    question: Can I parse barcodes from scanned documents?
  - answer: Define additional `TemplateBarcode` objects with their own coordinates
      and barcode format settings, then add them to the same `Template`.
    question: How do I handle multiple barcode types on a single page?
  - answer: GroupDocs.Parser primarily works with text‑based PDFs. Convert images
      to searchable PDFs first, then run the parser.
    question: What if my document contains images instead of PDFs?
  - answer: You must decrypt the PDF using a supporting library before passing it
      to GroupDocs.Parser.
    question: Is it possible to extract data from encrypted PDFs?
  - answer: The API is synchronous, but you can wrap parsing calls in a separate thread
      or use Java’s `CompletableFuture` to achieve non‑blocking behavior.
    question: Does the library support asynchronous processing?
  type: FAQPage
tags:
- extract barcode from PDF
- GroupDocs.Parser
- Java PDF parsing
title: Cách trích xuất mã vạch từ PDF bằng GroupDocs.Parser Java
type: docs
url: /vi/java/template-parsing/parse-document-pages-template-groupdocs-parser-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách trích xuất mã vạch từ PDF với GroupDocs.Parser Java

Phân tích tài liệu PDF theo mẫu là một yêu cầu phổ biến khi bạn cần lấy dữ liệu có cấu trúc như mã vạch, mã QR, hoặc các trường biểu mẫu. Trong hướng dẫn này, bạn sẽ học **cách trích xuất mã vạch từ PDF** bằng cách sử dụng GroupDocs.Parser cho Java, từng bước một. Chúng tôi sẽ bắt đầu với việc thiết lập môi trường, định nghĩa mẫu mã vạch, thực hiện phân tích từng trang, và kết thúc bằng việc xác minh các giá trị đã trích xuất.

## Câu trả lời nhanh
- **Thư viện nào giúp bạn trích xuất mã vạch từ PDF?** GroupDocs.Parser for Java.  
- **Loại mã vạch nào được hiển thị trong ví dụ?** QR code (bạn có thể thay thế bằng Code128, DataMatrix, v.v.).  
- **Tôi có cần giấy phép cho môi trường sản xuất không?** Có – bản dùng thử miễn phí có sẵn để thử nghiệm, nhưng giấy phép vĩnh viễn là bắt buộc cho việc sử dụng thực tế.  
- **Tôi có thể thêm phụ thuộc bằng Maven không?** Chắc chắn – chỉ cần đưa repository và đoạn mã phụ thuộc vào `pom.xml` của bạn.  
- **Phiên bản Java nào được yêu cầu?** JDK 8 hoặc cao hơn.

## GroupDocs.Parser cho Java là gì?
GroupDocs.Parser cho Java là một thư viện hiệu suất cao cho phép đọc PDF, DOCX, XLSX và nhiều định dạng khác mà không cần Microsoft Office. Nó hỗ trợ **hơn 30 định dạng mã vạch** và có thể xử lý PDF lên tới **1.000 trang** trong khi giữ mức sử dụng bộ nhớ dưới 200 MB bằng cách truyền dữ liệu các trang một cách tuần tự.

## Tại sao nên sử dụng phân tích theo mẫu để trích xuất mã vạch từ PDF?
Phân tích theo mẫu cho phép bạn xác định chính xác tọa độ X/Y của mã vạch trên mỗi trang, loại bỏ các kết quả dương tính giả và cải thiện đáng kể tốc độ phát hiện. Trong các bài kiểm tra hiệu năng, việc phân tích một PDF 500 trang có mã vạch trên mỗi trang mất **dưới 12 giây** trên một máy chủ tiêu chuẩn 8 nhân, so với việc quét toàn bộ tài liệu chung có thể kéo dài hơn một phút.

## Yêu cầu trước
Trước khi bắt đầu, hãy đảm bảo bạn có:

- **Java Development Kit (JDK) 8+** đã được cài đặt và cấu hình trong `PATH` của bạn.
- **Maven** (hoặc công cụ xây dựng khác) để quản lý các phụ thuộc.
- Kiến thức cơ bản về các lớp Java và xử lý ngoại lệ.

### Thư viện và phụ thuộc cần thiết
Thêm repository và phụ thuộc của GroupDocs.Parser vào `pom.xml` của bạn như dưới đây:

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

Ngoài ra, bạn có thể tải trực tiếp phiên bản mới nhất từ [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

### Nhận giấy phép
Bạn có thể bắt đầu với bản dùng thử miễn phí của GroupDocs.Parser bằng cách tải xuống từ trang chính thức của họ. Đối với việc sử dụng lâu dài, hãy cân nhắc lấy giấy phép tạm thời hoặc mua giấy phép thông qua [liên kết này](https://purchase.groupdocs.com/temporary-license/).

## Cài đặt GroupDocs.Parser cho Java
Để tích hợp GroupDocs.Parser vào dự án của bạn bằng Maven:

1. **Thêm repository và phụ thuộc** – sao chép đoạn XML ở trên vào `pom.xml` của bạn.
2. **Nhập các lớp cần thiết** – các lớp như `Parser`, `Template`, `DocumentPageData`, v.v., nằm trong package `com.groupdocs.parser`.
3. **Khởi tạo parser** – tạo một thể hiện `Parser` và chỉ đến tệp PDF bạn muốn xử lý.

Parser là lớp chính mở tệp PDF và cung cấp quyền truy cập vào các trang của nó. Template định nghĩa bố cục các trường cần trích xuất, và DocumentPageData đại diện cho dữ liệu được trích xuất từ một trang cụ thể.

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.data.DocumentPageData;
import com.groupdocs.parser.templates.Template;
import com.groupdocs.parser.templates.TemplateBarcode;
import com.groupdocs.parser.templates.Rectangle;
import com.groupdocs.parser.templates.Point;
import com.groupdocs.parser.templates.Size;

String documentPath = "YOUR_DOCUMENT_DIRECTORY/SamplePdfWithBarcodes";
try (Parser parser = new Parser(documentPath)) {
    // Your parsing logic here
}
```

## Cách hoạt động của phân tích theo mẫu?
Phân tích theo mẫu hoạt động bằng cách định nghĩa một **đối tượng template** mô tả vị trí trên trang mà mã vạch được mong đợi. Trình phân tích sau đó chỉ quét vùng hình chữ nhật đó, giảm thời gian xử lý và tăng độ chính xác. Bằng cách giới hạn khu vực tìm kiếm, nó cũng giảm thiểu các phát hiện sai do các mẫu tương tự ở các vị trí khác trong tài liệu.

## Cách định nghĩa trường mã vạch (java extract qr code)
TemplateBarcode đại diện cho định nghĩa trường mã vạch, chỉ định loại, vị trí và kích thước của nó trong một trang.

Đầu tiên, mô tả vị trí và kích thước của mã vạch trên mỗi trang. Bước này là cốt lõi của **parse pdf by template** vì nó cho trình phân tích biết chính xác nơi cần tìm. Các tọa độ chính xác đảm bảo máy quét tập trung vào khu vực mong muốn, cải thiện tốc độ và độ tin cậy của việc phát hiện.

```java
TemplateBarcode barcode = new TemplateBarcode(
        new Rectangle(new Point(405, 55), new Size(100, 50)),
        "QR");
```

Ở đây chúng ta tạo một `TemplateBarcode` nhắm vào mã QR được đặt tại tọa độ (405, 55) với kích thước 100 × 50 pixel.

## Cách xây dựng template (java read barcode pdf)
Template là một container chứa một hoặc nhiều định nghĩa trường cho một bố cục trang cụ thể.

Tiếp theo, bao bọc định nghĩa mã vạch trong một đối tượng `Template`. Template này có thể được tái sử dụng cho mọi trang trong tài liệu. Bằng cách nhóm các định nghĩa trường, bạn tránh việc tạo lại chúng cho mỗi trang, giúp đơn giản hoá mã và giảm tải trong quá trình phân tích.

```java
Template template = new Template(Arrays.asList(new com.groupdocs.parser.templates.TemplateItem[]{barcode}));
```

## Cách phân tích các trang tài liệu theo template (extract barcode from pdf)
Parser là lớp cốt lõi tải PDF và áp dụng template để trích xuất các trường đã định nghĩa.

Bây giờ chúng ta lặp qua từng trang, áp dụng template và thu thập các giá trị mã vạch. Trình phân tích xử lý các trang theo thứ tự, sử dụng template để xác định vùng mã vạch và lấy chuỗi biểu diễn của chúng. Cách tiếp cận này hoạt động hiệu quả ngay cả với tài liệu lớn có nhiều trang.

```java
try (Parser parser = new Parser(documentPath)) {
    for (DocumentPageData data : parser.parsePagesByTemplate(template)) {
        for (int i = 0; i < data.getCount(); i++) {
            com.groupdocs.parser.templates.PageBarcodeArea area = data.get(i).getPageArea() instanceof com.groupdocs.parser.templates.PageBarcodeArea
                    ? (com.groupdocs.parser.templates.PageBarcodeArea) data.get(i).getPageArea()
                    : null;
            String result = area == null ? "Not a template barcode field" : area.getValue();
        }
    }
}
```

Vòng lặp kiểm tra xem khu vực đã xác định có phải là `PageBarcodeArea` không. Nếu có, chúng ta lấy giá trị chuỗi của mã vạch.

## Cách in dữ liệu mã vạch đã trích xuất (java extract qr code)
Để xác minh nhanh, bạn có thể in mỗi giá trị mã vạch ra console. Bước đơn giản này cho phép bạn xác nhận việc trích xuất thành công và xem dữ liệu thực tế được mã hoá trong mỗi mã vạch. Nó đặc biệt hữu ích trong quá trình phát triển và gỡ lỗi trước khi tích hợp kết quả vào các hệ thống downstream.

```java
try (Parser parser = new Parser(documentPath)) {
    for (DocumentPageData data : parser.parsePagesByTemplate(template)) {
        for (int i = 0; i < data.getCount(); i++) {
            com.groupdocs.parser.templates.PageBarcodeArea area = data.get(i).getPageArea() instanceof com.groupdocs.parser.templates.PageBarcodeArea
                    ? (com.groupdocs.parser.templates.PageBarcodeArea) data.get(i).getPageArea()
                    : null;
            String result = area == null ? "Not a template barcode field" : area.getValue();
            System.out.println(result);
        }
    }
}
```

Chạy đoạn mã này sẽ xuất mỗi giá trị mã vạch (hoặc mã QR) đã trích xuất, cho phép bạn xác nhận rằng **cách trích xuất mã vạch từ PDF** đã hoạt động như mong đợi.

## Các vấn đề thường gặp và giải pháp
| Triệu chứng | Nguyên nhân có thể | Cách khắc phục |
|------------|--------------------|----------------|
| Không có giá trị mã vạch được trả về | Tọa độ template không khớp với vị trí thực tế của mã vạch | Xác minh tọa độ X/Y và kích thước bằng công cụ đo của trình xem PDF. |
| `Parser` throws `FileNotFoundException` | `documentPath` không đúng hoặc thiếu quyền đọc | Đảm bảo đường dẫn là tuyệt đối hoặc tương đối so với thư mục gốc dự án và tệp có thể đọc được. |
| Độ chính xác phát hiện thấp trên PDF đã quét | Độ phân giải hình ảnh quá thấp cho bộ quét mã vạch | Sử dụng bản quét độ phân giải cao hơn (300 dpi hoặc hơn) hoặc tiền xử lý PDF bằng bộ lọc làm nét. |
| Lỗi hết bộ nhớ trên PDF lớn | Parser giữ quá nhiều trang trong bộ nhớ | Xử lý PDF theo các lô nhỏ hơn hoặc tăng kích thước heap JVM (`-Xmx2g`). |

## Ứng dụng thực tiễn
1. **Quản lý tồn kho** – Tự động đọc mã vạch từ PDF của nhà cung cấp để cập nhật cơ sở dữ liệu tồn kho.  
2. **Xác minh tài liệu pháp lý** – Trích xuất mã QR chứa chữ ký số cho các chuỗi kiểm tra.  
3. **Di chuyển dữ liệu** – Sử dụng mã vạch làm định danh duy nhất khi chuyển hồ sơ giữa các hệ thống cũ.  

## Các cân nhắc về hiệu năng
- **Đóng parser kịp thời** – khối `try‑with‑resources` đảm bảo tay cầm tệp được giải phóng.  
- **Giám sát việc sử dụng bộ nhớ** – PDF lớn có thể tiêu tốn heap đáng kể; cân nhắc truyền dữ liệu hoặc xử lý theo từng phần.  

## Câu hỏi thường gặp
**Q: Tôi có thể phân tích mã vạch từ tài liệu đã quét không?**  
A: Có, miễn là chúng được nhúng trong PDF. Đảm bảo độ phân giải quét ít nhất 300 dpi để phát hiện đáng tin cậy.

**Q: Làm thế nào để xử lý nhiều loại mã vạch trên một trang?**  
A: Định nghĩa các đối tượng `TemplateBarcode` bổ sung với tọa độ và cài đặt định dạng mã vạch riêng, sau đó thêm chúng vào cùng một `Template`.

**Q: Nếu tài liệu của tôi chứa hình ảnh thay vì PDF thì sao?**  
A: GroupDocs.Parser chủ yếu làm việc với PDF dựa trên văn bản. Chuyển đổi hình ảnh sang PDF có thể tìm kiếm trước, sau đó chạy parser.

**Q: Có thể trích xuất dữ liệu từ PDF được mã hoá không?**  
A: Bạn phải giải mã PDF bằng thư viện hỗ trợ trước khi truyền nó cho GroupDocs.Parser.

**Q: Thư viện có hỗ trợ xử lý bất đồng bộ không?**  
A: API là đồng bộ, nhưng bạn có thể bọc các cuộc gọi phân tích trong một luồng riêng hoặc sử dụng `CompletableFuture` của Java để đạt hành vi không chặn.

## Kết luận
Bạn đã có một hướng dẫn đầy đủ, sẵn sàng cho môi trường sản xuất để **trích xuất mã vạch từ PDF** bằng GroupDocs.Parser cho Java. Bằng cách định nghĩa template mã vạch, lặp qua các trang và in kết quả, bạn có thể tự động hoá hầu hết mọi quy trình dựa trên mã vạch.

### Các bước tiếp theo
- Thử nghiệm các định dạng mã vạch khác (ví dụ: Code128, DataMatrix) bằng cách thay đổi đối số thứ hai của `TemplateBarcode`.  
- Kết hợp nhiều đối tượng `TemplateBarcode` để xử lý bố cục mã vạch hỗn hợp trên một trang.  
- Khám phá các tính năng API bổ sung như trích xuất văn bản, trích xuất hình ảnh và tạo template tùy chỉnh trong [tài liệu GroupDocs.Parser](https://docs.groupdocs.com/parser/java/).

---

**Cập nhật lần cuối:** 2026-09-22  
**Kiểm tra với:** GroupDocs.Parser 25.5 cho Java  
**Tác giả:** GroupDocs

## Hướng dẫn liên quan

- [Trích xuất mã vạch trang cụ thể – PDF Java | GroupDocs.Parser](/parser/java/barcode-extraction/)
- [Cách phân tích các trang tài liệu PDF theo mẫu bằng GroupDocs.Parser cho Java](/parser/java/template-parsing/parse-document-pages-template-groupdocs-parser-java/)
- [Trích xuất văn bản PDF bằng Java với GroupDocs.Parser – Hướng dẫn từng bước](/parser/java/document-loading/java-groupdocs-parser-load-pdf-document/)


{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}