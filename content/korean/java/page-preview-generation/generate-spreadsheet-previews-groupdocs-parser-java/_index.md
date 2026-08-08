---
date: '2026-07-16'
description: GroupDocs.Parser를 사용하여 Java 스프레드시트 썸네일을 만드는 방법을 배우고, Office 없이 Excel을
  preview하고, Excel 시트를 이미지로 render하는 방법을 알아보세요. 이 가이드는 setup, implementation 및 practical
  use cases를 다룹니다.
keywords:
- create spreadsheet thumbnail java
- preview excel without office
- render excel sheets as images
lastmod: '2026-07-16'
og_description: GroupDocs.Parser와 함께 Java 스프레드시트 썸네일을 만들고—Office 없이 Excel을 preview하고
  Excel 시트를 이미지로 render합니다. 효율적으로 PNG preview를 생성하기 위한 단계별 가이드를 따라보세요.
og_image_alt: 'Developer guide: Create spreadsheet thumbnail Java using GroupDocs.Parser'
og_title: GroupDocs.Parser를 사용한 Java 스프레드시트 썸네일 만들기
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
title: GroupDocs.Parser를 사용한 Java 스프레드시트 썸네일 만들기
type: docs
url: /ko/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# GroupDocs.Parser를 사용한 Java 스프레드시트 썸네일 만들기

Java **스프레드시트 썸네일 만들기** 프로그램을 찾고 계시다면, 올바른 곳에 오셨습니다. 이 가이드에서는 GroupDocs.Parser for Java를 사용하여 `.xlsx` 워크북에서 고품질 PNG 미리보기를 생성하는 방법을 단계별로 안내합니다—빠른 썸네일, 스냅샷 공유, 또는 애플리케이션에 문서 미리보기 기능을 구축하는 데 완벽합니다. 이 솔루션은 Microsoft Office 설치 없이 작동하며, 메모리 사용량을 낮게 유지하면서 대용량 워크북을 확장할 수 있습니다.

## 빠른 답변
- **“preview Excel”이란 무엇인가요?** 각 워크시트 페이지를 나타내는 이미지 파일(PNG 등)을 생성하는 것입니다.  
- **추천 포맷은 무엇인가요?** PNG는 무손실 품질을 제공하며 웹 썸네일에 적합합니다.  
- **라이선스가 필요합니까?** 무료 체험은 개발에 사용할 수 있으며, 운영 환경에서는 상용 라이선스가 필요합니다.  
- **이미지 해상도를 변경할 수 있나요?** 예—`PreviewOptions`에서 DPI를 조정하세요.  
- **다른 포맷도 미리볼 수 있나요?** GroupDocs.Parser는 PDF, Word 및 다양한 이미지 형식도 지원합니다.

## GroupDocs.Parser와 함께 “Excel 미리보기”란 무엇인가요?

Microsoft Office 없이 Excel 워크북을 로드하고 각 시트를 PNG 이미지로 렌더링합니다. GroupDocs.Parser는 페이지를 하나씩 스트리밍하여 손실 없는 썸네일을 생성하며, 이를 디스크에 저장하거나 HTTP를 통해 반환할 수 있어 웹 기반 미리보기 서비스에 이상적입니다.

GroupDocs.Parser는 Excel 워크북을 읽고 각 시트를 시각적인 페이지로 렌더링하며, 해당 페이지들을 이미지 파일로 스트리밍할 수 있게 합니다. 이를 통해 Office 연동이나 타사 변환기가 필요하지 않습니다.

## Excel 미리보기에 GroupDocs.Parser를 사용하는 이유

GroupDocs.Parser를 사용해야 하는 이유는 Java 서버 어디서든 동작하고, Office 설치가 필요 없으며, 대용량 워크북을 낮은 메모리 사용량으로 처리하고, DPI를 설정할 수 있는 무손실 PNG 이미지를 생성하기 때문입니다. SDK는 **100개 이상의 입력 및 출력 포맷**을 지원하며, 200페이지 워크북을 3초 이하로 처리하고, 시트당 메모리 사용량을 50 MB 이하로 유지합니다.

- **Office 설치가 필요 없음** – 모든 서버‑사이드 Java 환경에서 실행됩니다.  
- **대용량 파일 지원** – 페이지를 하나씩 스트리밍하여 메모리 사용량을 낮게 유지합니다.  
- **고품질 출력** – DPI, 포맷 및 렌더링 옵션을 제어할 수 있습니다.  
- **다중 포맷 유연성** – 동일한 API가 PDF, Word 문서 등에서도 작동합니다.

## 사전 요구 사항
- **Java Development Kit** (8 +).  
- **IDE** (IntelliJ IDEA 또는 Eclipse 등).  
- **GroupDocs.Parser for Java SDK** – [여기](https://releases.groupdocs.com/parser/java/)에서 다운로드하십시오.  
- **Documentation** – 공식 [문서](https://docs.groupdocs.com/parser/java/)을 참고하세요.  
- **샘플 Excel 파일** (`.xlsx`)을 미리보기 위해 사용합니다.  
- **Maven 또는 Gradle** (선택 사항) – 의존성 관리를 위해 사용합니다.

## 패키지 가져오기
다음 import 구문은 파서, 미리보기 옵션 및 스트림 처리 유틸리티에 접근할 수 있게 합니다.

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

## 스프레드시트 페이지 미리보기를 생성하는 단계별 가이드

### 단계 1: 파서 인스턴스 초기화
`Parser`는 스프레드시트 파일에 대한 읽기 접근을 제공하고 페이지 단위 렌더링을 가능하게 하는 GroupDocs.Parser의 핵심 클래스입니다.  
Excel 워크북을 가리키는 `Parser` 객체를 생성합니다. *try‑with‑resources* 블록은 파서를 자동으로 닫아줍니다.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **팁:** `FileNotFoundException`을 방지하려면 절대 경로를 사용하거나 리소스 폴더를 구성하세요.

### 단계 2: 미리보기 옵션 준비
`PreviewOptions`는 출력 포맷 및 DPI와 같은 렌더링 매개변수를 설정합니다.  
`ICreatePageStream`은 생성된 각 페이지에 대한 출력 스트림을 제공하는 콜백 인터페이스입니다. 각 페이지를 저장하는 방식을 정의합니다. `ICreatePageStream` 구현은 각 워크시트 페이지마다 새로운 `FileOutputStream`을 반환합니다.

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

> 이 단계가 **xlsx를 png로 변환**하는 부분이며, 스트림이 PNG 데이터를 디스크에 씁니다.

### 단계 3: 렌더링 정보를 캡처하기 위한 대리자 연결
각 렌더링된 시트에 대한 세부 정보(예: 크기, 시트 이름)가 필요하면 콜백을 등록하세요.

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### 단계 4: 출력 포맷 및 DPI 지정
이미지 포맷을 PNG로 선택하고 품질과 파일 크기의 균형을 맞추는 DPI를 설정합니다.

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> 더 작은 썸네일이 필요하면 DPI를 조정하세요(예: 96) 또는 고해상도 인쇄가 필요하면 DPI를 높이세요(예: 300).

### 단계 5: 미리보기 생성
모든 설정이 완료되면 `generatePreview`를 호출합니다. SDK는 각 워크시트를 순회하며 제공한 스트림을 호출합니다.

```java
parser.generatePreview(previewOptions);
```

### 단계 6: `getOutputPath()` 헬퍼 정의
`getOutputPath()`는 페이지(시트) 번호를 기반으로 파일 이름을 만들고 출력 이미지의 전체 경로를 반환합니다. 폴더 구조는 자유롭게 커스터마이즈하세요.

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **흔한 실수:** 사전에 `output` 디렉터리를 생성하지 않으면 `IOException`이 발생합니다. 프로그램matically 생성하거나 존재하는지 확인하세요.

## 전체 작업 예제 (단순화 버전)

아래는 모든 요소를 결합한 간결한 버전입니다. **Java 스프레드시트 썸네일 만들기** 워크플로우를 처음부터 끝까지 보여줍니다.

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

이 스니펫을 실행하면 `output` 폴더에 `preview_page_1.png`, `preview_page_2.png`, … 파일이 생성됩니다—각 파일은 원본 Excel 워크북의 시트를 나타냅니다.

## 일반적인 문제 및 해결책

| Issue | Cause | Fix |
|-------|-------|-----|
| **이미지가 생성되지 않음** | `getOutputPath`가 잘못된 디렉터리를 반환함 | 대상 폴더가 존재하는지 확인하거나 `new File("output").mkdirs();`로 생성하세요. |
| **대용량 파일에서 메모리 부족 오류** | 워크북을 한 번에 전체 로드함 | 스트리밍 방식을 사용하고(예시와 같이) 페이지를 하나씩 처리하세요. |
| **잘못된 DPI** | `setDpi`가 호출되지 않았거나 기본값(96)으로 설정됨 | `generatePreview` 호출 전에 `previewOptions.setDpi(yourDesiredValue);`를 호출하세요. |
| **지원되지 않는 형식** | 손상된 `.xlsx` 파일을 미리보려고 함 | 처리 전에 Excel로 파일을 검증하거나 `Parser.isSupported`를 사용하세요. |

## 자주 묻는 질문

**Q: GroupDocs.Parser를 사용해 PDF 및 이미지 미리보기를 생성할 수 있나요?**  
A: 예, 동일한 API가 PDF, Word 문서 및 다양한 이미지 형식에서도 작동합니다.

**Q: 출력 이미지 포맷을 어떻게 변경하나요?**  
A: `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)`(또는 `Gif`, `Bmp` 등)을 호출하세요.

**Q: 매우 큰 워크북의 성능이 문제인가요?**  
A: SDK는 페이지를 스트리밍하므로 메모리 사용량이 낮습니다. 대용량 파일의 경우 병렬 배치 처리을 고려하세요.

**Q: 미리보기 생성 중 오류를 어떻게 처리하나요?**  
A: 코드에 try‑catch 블록을 사용하고(예시와 같이) 예외 세부 정보를 로그에 기록하세요. try‑with‑resources를 사용하지 않을 경우 `finally` 블록에서 스트림을 닫는 것을 확인하세요.

**Q: 라이브러리를 사용하려면 Microsoft Office가 설치되어 있어야 하나요?**  
A: 아니요. GroupDocs.Parser는 순수 Java 솔루션으로 Java 8 이상을 지원하는 모든 플랫폼에서 작동합니다.

**마지막 업데이트:** 2026-07-16  
**테스트 환경:** GroupDocs.Parser 23.11 (작성 시 최신)  
**작성자:** GroupDocs

## 관련 튜토리얼

- [프리뷰 생성 방법 – GroupDocs.Parser Java 문서 페이지 프리뷰 생성 튜토리얼](/parser/java/page-preview-generation/)
- [GroupDocs.Parser와 함께 Excel Java 파싱: 완전 가이드](/parser/java/getting-started/mastering-document-parsing-java-groupdocs-parser/)
- [GroupDocs.Parser for Java를 사용해 Excel 시트에서 원시 텍스트 추출 방법: 단계별 가이드](/parser/java/text-extraction/extract-raw-text-excel-groupdocs-parser-java/)