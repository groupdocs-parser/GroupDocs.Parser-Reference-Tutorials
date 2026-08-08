---
date: '2026-07-16'
description: Tìm hiểu cách tạo ảnh thu nhỏ bảng tính Java với GroupDocs.Parser, xem
  trước Excel mà không cần Office, và chuyển đổi các sheet Excel thành hình ảnh. Hướng
  dẫn này bao gồm cài đặt, triển khai và các trường hợp sử dụng thực tế.
keywords:
- create spreadsheet thumbnail java
- preview excel without office
- render excel sheets as images
lastmod: '2026-07-16'
og_description: Tạo ảnh thu nhỏ bảng tính Java với GroupDocs.Parser—xem trước Excel
  mà không cần Office và chuyển đổi các sheet Excel thành hình ảnh. Thực hiện theo
  hướng dẫn từng bước này để tạo các bản xem trước PNG một cách hiệu quả.
og_image_alt: 'Developer guide: Create spreadsheet thumbnail Java using GroupDocs.Parser'
og_title: Tạo ảnh thu nhỏ bảng tính Java bằng GroupDocs.Parser
schemas:
- author: GroupDocs
  dateModified: '2026-07-16'
  description: Learn how to create spreadsheet thumbnail Java with GroupDocs.Parser,
    preview Excel without Office, and render Excel sheets as images. This guide covers
    setup, implementation, and practical use cases.
  headline: Create Spreadsheet Thumbnail Java Using GroupDocs.Parser
  type: TechArticle
- description: Learn how to create spreadsheet thumbnail Java with GroupDocs.Parser,
    preview Excel without Office, and render Excel sheets as images. This guide covers
    setup, implementation, and practical use cases.
  name: Create Spreadsheet Thumbnail Java Using GroupDocs.Parser
  steps:
  - name: Initialize the Parser Instance
    text: '`Parser` is GroupDocs.Parser''s core class that provides read access to
      spreadsheet files and enables page‑wise rendering. Create a `Parser` object
      pointing at your Excel workbook. The *try‑with‑resources* block ensures the
      parser is closed automatically. > **Pro tip:** Use an absolute path or config'
  - name: Prepare Your Preview Options
    text: '`PreviewOptions` configures rendering parameters such as output format
      and DPI. `ICreatePageStream` is a callback interface that supplies an output
      stream for each generated page. Define how each page will be saved. The `ICreatePageStream`
      implementation returns a fresh `FileOutputStream` for every '
  - name: Attach a Delegate to Capture Render Info
    text: If you need details about each rendered sheet (e.g., dimensions, sheet name),
      register a callback.
  - name: Specify Output Format and DPI
    text: Select PNG as the image format and set a DPI that balances quality and file
      size. > Adjust the DPI if you need smaller thumbnails (e.g., 96) or high‑resolution
      prints (e.g., 300).
  - name: Generate the Previews
    text: With everything configured, call `generatePreview`. The SDK will iterate
      over each worksheet and invoke the stream you supplied.
  - name: Define the `getOutputPath()` Helper
    text: '`getOutputPath()` builds a file name based on the page (sheet) number and
      returns the full path for the output image. Feel free to customize the folder
      structure. > **Common pitfall:** Forgetting to create the `output` directory
      beforehand will cause an `IOException`. Create it programmatically or e'
  type: HowTo
- questions:
  - answer: Yes, the same API works for PDFs, Word documents, and many image formats.
    question: Can I generate previews for PDFs and images using GroupDocs.Parser?
  - answer: Call `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (or `Gif`,
      `Bmp`, etc.).
    question: How do I change the output image format?
  - answer: The SDK streams pages, which keeps memory usage low. For massive files,
      consider processing in parallel batches.
    question: Is performance a concern with very large workbooks?
  - answer: Wrap the code in try‑catch blocks (as shown) and log the exception details.
      Ensure streams are closed in the `finally` block if you’re not using try‑with‑resources.
    question: How can I handle errors during preview generation?
  - answer: No. GroupDocs.Parser is a pure Java solution and works on any platform
      that supports Java 8+.
    question: Does the library require Microsoft Office to be installed?
  type: FAQPage
tags:
- create spreadsheet thumbnail
- GroupDocs.Parser
- Java preview excel
- excel to png
- document processing
title: Tạo ảnh thu nhỏ bảng tính Java bằng GroupDocs.Parser
type: docs
url: /vi/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# Tạo Thu nhỏ Bảng tính Java bằng GroupDocs.Parser

Nếu bạn đang tìm cách **create spreadsheet thumbnail Java**, bạn đã đến đúng nơi. Trong hướng dẫn này, chúng tôi sẽ trình bày cách tạo các bản xem trước PNG chất lượng cao từ các workbook `.xlsx` bằng GroupDocs.Parser cho Java — lý tưởng cho các hình thu nhỏ nhanh, chia sẻ ảnh chụp màn hình, hoặc xây dựng tính năng xem trước tài liệu trong ứng dụng của bạn. Giải pháp hoạt động mà không cần cài đặt Microsoft Office và có thể mở rộng cho các workbook lớn trong khi giữ mức sử dụng bộ nhớ thấp.

## Câu trả lời nhanh
- **“preview Excel” có nghĩa là gì?** Tạo các tệp hình ảnh (ví dụ: PNG) đại diện cho mỗi trang worksheet.  
- **Định dạng nào được đề xuất?** PNG cung cấp chất lượng không mất dữ liệu và hoạt động tốt cho các hình thu nhỏ trên web.  
- **Tôi có cần giấy phép không?** Bản dùng thử miễn phí hoạt động cho việc phát triển; giấy phép thương mại là bắt buộc cho môi trường sản xuất.  
- **Tôi có thể thay đổi độ phân giải hình ảnh không?** Có — điều chỉnh DPI trong `PreviewOptions`.  
- **Có thể xem trước các định dạng khác không?** GroupDocs.Parser cũng hỗ trợ PDF, Word và nhiều loại hình ảnh.

## “how to preview Excel” là gì với GroupDocs.Parser?
Tải workbook Excel của bạn và render mỗi sheet thành hình ảnh PNG mà không cần Microsoft Office. GroupDocs.Parser truyền các trang một lần một, tạo ra các hình thu nhỏ không mất dữ liệu có thể lưu vào đĩa hoặc trả về qua HTTP, rất phù hợp cho các dịch vụ xem trước dựa trên web.

GroupDocs.Parser đọc các workbook Excel, render mỗi sheet thành một trang hình ảnh, và cho phép bạn truyền các trang đó thành các tệp hình ảnh. Điều này loại bỏ nhu cầu sử dụng Office interop hoặc các bộ chuyển đổi của bên thứ ba.

## Tại sao nên sử dụng GroupDocs.Parser cho việc xem trước Excel?
Bạn nên sử dụng GroupDocs.Parser vì nó hoạt động trên bất kỳ máy chủ Java nào, không cần cài đặt Office, xử lý các workbook lớn với bộ nhớ thấp, và tạo ra các hình ảnh PNG không mất dữ liệu với DPI có thể cấu hình. SDK hỗ trợ **hơn 100 định dạng đầu vào và đầu ra**, có thể xử lý một workbook 200 trang trong vòng dưới 3 giây, và giữ mức sử dụng bộ nhớ dưới 50 MB cho mỗi sheet.

- **Không cần cài đặt Office** – chạy trên bất kỳ môi trường Java phía máy chủ nào.  
- **Hỗ trợ tệp lớn** – truyền các trang từng cái một, giữ mức sử dụng bộ nhớ thấp.  
- **Đầu ra chất lượng cao** – kiểm soát DPI, định dạng và các tùy chọn render.  
- **Linh hoạt đa định dạng** – cùng một API hoạt động cho PDF, tài liệu Word và nhiều hơn nữa.

## Yêu cầu trước
- **Java Development Kit** (8 +).  
- **IDE** như IntelliJ IDEA hoặc Eclipse.  
- **GroupDocs.Parser for Java SDK** – tải xuống từ [tại đây](https://releases.groupdocs.com/parser/java/).  
- **Documentation** – xem [tài liệu](https://docs.groupdocs.com/parser/java/) chính thức.  
- **Sample Excel file** (`.xlsx`) bạn muốn xem trước.  
- **Maven hoặc Gradle** (tùy chọn) để quản lý phụ thuộc.

## Nhập các gói
Các import này cung cấp cho bạn quyền truy cập vào parser, các tùy chọn preview và tiện ích xử lý stream.

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.options.PreviewOptions;
import com.groupdocs.parser.options.PreviewFormats;
import com.groupdocs.parser.options.ICreatePageStream;
import com.groupdocs.parser.options.IPreviewPageRender;
import com.groupdocs.parser.results.PageRenderInfo;
import java.io.FileOutputStream;
import java.io.OutputStream;
import java.io.IOException;
```

## Hướng dẫn từng bước để tạo các bản xem trước trang Bảng tính

### Bước 1: Khởi tạo đối tượng Parser
`Parser` là lớp cốt lõi của GroupDocs.Parser cung cấp quyền đọc các tệp bảng tính và cho phép render theo trang.  
Tạo một đối tượng `Parser` trỏ tới workbook Excel của bạn. Khối *try‑with‑resources* đảm bảo parser được đóng tự động.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **Mẹo:** Sử dụng đường dẫn tuyệt đối hoặc cấu hình thư mục tài nguyên để tránh `FileNotFoundException`.

### Bước 2: Chuẩn bị các tùy chọn Preview
`PreviewOptions` cấu hình các tham số render như định dạng đầu ra và DPI.  
`ICreatePageStream` là giao diện callback cung cấp một output stream cho mỗi trang được tạo. Xác định cách mỗi trang sẽ được lưu. Implementations của `ICreatePageStream` trả về một `FileOutputStream` mới cho mỗi trang worksheet.

```java
PreviewOptions previewOptions = new PreviewOptions(new ICreatePageStream() {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        try {
            String outputPath = getOutputPath(pageNumber); // define this method later
            return new FileOutputStream(outputPath);
        } catch (IOException ex) {
            throw new RuntimeException("Error creating output stream", ex);
        }
    }
});
```

> Bước này là nơi bạn **convert xlsx to png** — stream ghi dữ liệu PNG vào đĩa.

### Bước 3: Gắn delegate để lấy thông tin render
Nếu bạn cần chi tiết về mỗi sheet đã render (ví dụ: kích thước, tên sheet), đăng ký một callback.

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### Bước 4: Chỉ định định dạng đầu ra và DPI
Chọn PNG làm định dạng hình ảnh và đặt DPI sao cho cân bằng giữa chất lượng và kích thước tệp.

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> Điều chỉnh DPI nếu bạn cần các hình thu nhỏ nhỏ hơn (ví dụ: 96) hoặc in chất lượng cao (ví dụ: 300).

### Bước 5: Tạo các bản xem trước
Khi mọi thứ đã được cấu hình, gọi `generatePreview`. SDK sẽ lặp qua mỗi worksheet và gọi stream mà bạn đã cung cấp.

```java
parser.generatePreview(previewOptions);
```

### Bước 6: Định nghĩa hàm trợ giúp `getOutputPath()`
`getOutputPath()` tạo tên tệp dựa trên số trang (sheet) và trả về đường dẫn đầy đủ cho hình ảnh đầu ra. Bạn có thể tùy chỉnh cấu trúc thư mục.

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **Cạm bẫy thường gặp:** Quên tạo thư mục `output` trước sẽ gây ra `IOException`. Tạo nó bằng chương trình hoặc đảm bảo nó tồn tại.

## Ví dụ làm việc đầy đủ (đơn giản hoá)

Dưới đây là phiên bản gọn gàng kết hợp tất cả các phần lại với nhau. Nó minh họa quy trình **create spreadsheet thumbnail Java** từ đầu đến cuối.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    final PageRenderInfo[] renderInfoHolder = {null};

    PreviewOptions options = new PreviewOptions(new ICreatePageStream() {
        @Override
        public OutputStream createPageStream(int pageNumber) {
            try {
                return new FileOutputStream(getOutputPath(pageNumber));
            } catch (IOException e) {
                throw new RuntimeException(e);
            }
        }
    });

    options.setPreviewPageRender(pageRenderInfo -> {
        renderInfoHolder[0] = pageRenderInfo;
    });
    options.setPreviewFormat(PreviewFormats.Png);
    options.setDpi(150);

    parser.generatePreview(options);
} catch (Exception e) {
    e.printStackTrace();
}
```

Chạy đoạn mã này, và bạn sẽ thấy một loạt các tệp `preview_page_1.png`, `preview_page_2.png`, … trong thư mục `output` — mỗi tệp đại diện cho một sheet từ workbook Excel gốc.

## Các vấn đề thường gặp & Giải pháp

| Vấn đề | Nguyên nhân | Giải pháp |
|-------|-------------|-----------|
| **Không tạo được hình ảnh** | `getOutputPath` trả về thư mục không hợp lệ | Đảm bảo thư mục đích tồn tại hoặc tạo nó bằng `new File("output").mkdirs();` |
| **Lỗi hết bộ nhớ khi xử lý tệp lớn** | Tải toàn bộ workbook cùng một lúc | Sử dụng cách streaming (như đã trình bày) và xử lý các trang từng cái một |
| **DPI không đúng** | `setDpi` không được gọi hoặc để mặc định (96) | Gọi `previewOptions.setDpi(giáTrịBạnMuốn);` trước `generatePreview` |
| **Định dạng không được hỗ trợ** | Cố gắng xem trước một `.xlsx` bị hỏng | Xác thực tệp bằng Excel hoặc sử dụng `Parser.isSupported` trước khi xử lý |

## Câu hỏi thường gặp

**Q: Tôi có thể tạo bản xem trước cho PDF và hình ảnh bằng GroupDocs.Parser không?**  
A: Có, cùng một API hoạt động cho PDF, tài liệu Word và nhiều định dạng hình ảnh.

**Q: Làm thế nào để thay đổi định dạng hình ảnh đầu ra?**  
A: Gọi `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (hoặc `Gif`, `Bmp`, v.v.).

**Q: Hiệu năng có phải là vấn đề với các workbook rất lớn không?**  
A: SDK truyền các trang, giúp giữ mức sử dụng bộ nhớ thấp. Đối với các tệp khổng lồ, hãy cân nhắc xử lý theo các lô song song.

**Q: Làm sao để xử lý lỗi trong quá trình tạo bản xem trước?**  
A: Bao bọc mã trong các khối try‑catch (như đã minh họa) và ghi lại chi tiết ngoại lệ. Đảm bảo các stream được đóng trong khối `finally` nếu bạn không sử dụng try‑with‑resources.

**Q: Thư viện có yêu cầu cài đặt Microsoft Office không?**  
A: Không. GroupDocs.Parser là giải pháp thuần Java và hoạt động trên bất kỳ nền tảng nào hỗ trợ Java 8+.

---

**Cập nhật lần cuối:** 2026-07-16  
**Kiểm thử với:** GroupDocs.Parser 23.11 (phiên bản mới nhất tại thời điểm viết)  
**Tác giả:** GroupDocs

## Hướng dẫn liên quan

- [Cách tạo Preview – Hướng dẫn tạo trang xem trước tài liệu cho GroupDocs.Parser Java](/parser/java/page-preview-generation/)
- [Phân tích Excel Java với GroupDocs.Parser: Hướng dẫn đầy đủ](/parser/java/getting-started/mastering-document-parsing-java-groupdocs-parser/)
- [Cách trích xuất văn bản thô từ các sheet Excel bằng GroupDocs.Parser cho Java: Hướng dẫn từng bước](/parser/java/text-extraction/extract-raw-text-excel-groupdocs-parser-java/)