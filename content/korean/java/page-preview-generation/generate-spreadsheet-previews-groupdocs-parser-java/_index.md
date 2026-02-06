---
date: '2026-02-06'
description: GroupDocs.Parser for Java를 사용하여 Excel 파일을 미리 보고 xlsx를 PNG로 변환하는 방법을 배웁니다.
  이 튜토리얼은 설정, 구현 및 실용적인 적용 사례를 다룹니다.
keywords:
- GroupDocs.Parser
- Java
- Document Processing
title: Java에서 GroupDocs.Parser를 사용하여 Excel 파일 미리보기하는 방법
type: docs
url: /ko/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# GroupDocs.Parser를 사용한 Java에서 Excel 파일 미리보기 방법

프로그래밍 방식으로 **Excel 미리보기** 방법을 찾고 있다면, 여기가 바로 정답입니다. 이 가이드에서는 GroupDocs.Parser for Java를 사용해 `.xlsx` 워크북에서 이미지 미리보기(PNG)를 만드는 과정을 단계별로 안내합니다—빠른 썸네일 생성, 스냅샷 공유, 혹은 애플리케이션에 문서 미리보기 기능을 구축하는 데 적합합니다.

## Quick Answers
- **“Excel 미리보기”가 무엇을 의미하나요?** 각 워크시트 페이지를 나타내는 이미지 파일(PNG 등)을 생성하는 것입니다.  
- **추천 포맷은 무엇인가요?** PNG는 무손실 품질을 제공하며 웹 썸네일에 적합합니다.  
- **라이선스가 필요합니까?** 무료 체험판은 개발에 사용할 수 있으며, 프로덕션에서는 상용 라이선스가 필요합니다.  
- **이미지 해상도를 변경할 수 있나요?** 예—`PreviewOptions`에서 DPI를 조정하면 됩니다.  
- **다른 포맷도 미리볼 수 있나요?** GroupDocs.Parser는 PDF, Word 및 다양한 이미지 타입도 지원합니다.

## GroupDocs.Parser를 사용한 “Excel 미리보기”란?
GroupDocs.Parser는 Excel 워크북을 읽어 각 시트를 시각적인 페이지로 렌더링하고, 해당 페이지들을 이미지 파일로 스트리밍할 수 있게 해줍니다. 이를 통해 Office 연동이나 타사 변환 도구가 필요하지 않게 됩니다.

## 왜 Excel 미리보기에 GroupDocs.Parser를 사용해야 할까요?
- **Office 설치 불필요** – 모든 서버‑사이드 Java 환경에서 실행됩니다.  
- **대용량 파일 지원** – 페이지를 하나씩 스트리밍하여 메모리 사용량을 최소화합니다.  
- **고품질 출력** – DPI, 포맷 및 렌더링 옵션을 제어할 수 있습니다.  
- **다양한 포맷 유연성** – 동일 API로 PDF, Word 문서 등도 처리할 수 있습니다.

## Prerequisites
- **Java Development Kit** (8 이상).  
- **IDE** (IntelliJ IDEA 또는 Eclipse 등).  
- **GroupDocs.Parser for Java SDK** – **[here](https://releases.groupdocs.com/parser/java/)**에서 다운로드하세요.  
- **미리보기할** 샘플 Excel 파일(`.xlsx`).  
- **Maven 또는 Gradle**(선택 사항) – 의존성 관리를 위해.

## Import Packages
다음 import 구문을 통해 parser, preview 옵션 및 스트림 처리 유틸리티에 접근할 수 있습니다.

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

## Step‑by‑Step Guide to Generate Spreadsheet Page Previews

### Step 1: Initialize the Parser Instance
`Parser` 객체를 생성하여 Excel 워크북을 지정합니다. *try‑with‑resources* 블록을 사용하면 parser가 자동으로 닫히게 됩니다.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **팁:** `FileNotFoundException`을 방지하려면 절대 경로나 리소스 폴더를 설정하세요.

### Step 2: Prepare Your Preview Options
각 페이지를 저장하는 방식을 정의합니다. `ICreatePageStream` 구현은 각 워크시트 페이지마다 새로운 `FileOutputStream`을 반환합니다.

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

> 이 단계가 **xlsx를 png로 변환**하는 부분이며, 스트림이 PNG 데이터를 디스크에 기록합니다.

### Step 3: Attach a Delegate to Capture Render Info
각 렌더링된 시트에 대한 상세 정보(예: 크기, 시트 이름)가 필요하면 콜백을 등록합니다.

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### Step 4: Specify Output Format and DPI
이미지 포맷을 PNG로 선택하고, 품질과 파일 크기의 균형을 맞추는 DPI를 설정합니다.

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> 썸네일을 더 작게(예: 96) 만들거나 고해상도 인쇄(예: 300)가 필요하면 DPI를 조정하세요.

### Step 5: Generate the Previews
모든 설정이 완료되면 `generatePreview`를 호출합니다. SDK가 각 워크시트를 순회하며 제공한 스트림을 호출합니다.

```java
parser.generatePreview(previewOptions);
```

### Step 6: Define the `getOutputPath()` Helper
이 메서드는 페이지(시트) 번호를 기반으로 파일 이름을 생성합니다. 폴더 구조는 **자유롭게** 커스터마이즈하세요.

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **흔한 실수:** `output` 디렉터리를 미리 생성하지 않으면 `IOException`이 발생합니다. 프로그램matically 생성하거나 존재 여부를 확인하세요.

## 전체 작업 예제 (간소화 버전)

아래는 모든 요소를 연결한 간결한 버전입니다. **Excel 페이지 미리보기 생성** 워크플로우를 처음부터 끝까지 보여줍니다.

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

이 스니펫을 실행하면 `output` 폴더에 `preview_page_1.png`, `preview_page_2.png` 등 일련의 파일이 생성됩니다—각 파일은 원본 Excel 워크북의 시트를 나타냅니다.

## 일반적인 문제 및 해결책
| 문제 | 원인 | 해결책 |
|-------|-------|-----|
| **이미지가 생성되지 않음** | `getOutputPath`가 잘못된 디렉터리를 반환함 | 대상 폴더가 존재하는지 확인하거나 `new File("output").mkdirs();` 로 생성하세요. |
| **대용량 파일에서 메모리 부족 오류** | 워크북을 한 번에 모두 로드함 | 스트리밍 방식(예시와 같이)을 사용하고 페이지를 한 번에 하나씩 처리하세요. |
| **잘못된 DPI** | `setDpi`를 호출하지 않았거나 기본값(96)으로 설정됨 | `generatePreview` 호출 전에 `previewOptions.setDpi(원하는값);`을 호출하세요. |
| **지원되지 않는 포맷** | 손상된 `.xlsx` 파일을 미리보려 함 | Excel로 파일을 검증하거나 처리 전에 `Parser.isSupported`를 사용하세요. |

## 자주 묻는 질문

**Q: GroupDocs.Parser를 사용해 PDF와 이미지도 미리볼 수 있나요?**  
A: 예, 동일 API가 PDF, Word 문서 및 다양한 이미지 포맷에도 적용됩니다.

**Q: 출력 이미지 포맷을 어떻게 변경하나요?**  
A: `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)`(또는 `Gif`, `Bmp` 등) 를 호출하면 됩니다.

**Q: 매우 큰 워크북의 성능이 문제될까요?**  
A: SDK가 페이지를 스트리밍하므로 메모리 사용량이 낮습니다. 대용량 파일의 경우 병렬 배치 처리 등을 고려하세요.

**Q: 미리보기 생성 중 오류를 어떻게 처리하나요?**  
A: 코드에 (예시와 같이) try‑catch 블록을 사용하고 예외 상세 정보를 로그에 남깁니다. try‑with‑resources를 사용하지 않을 경우 `finally` 블록에서 스트림을 닫아야 합니다.

**Q: 라이브러리를 사용하려면 Microsoft Office가 설치되어 있어야 하나요?**  
A: 아닙니다. GroupDocs.Parser는 순수 Java 솔루션으로 Java 8 이상을 지원하는 모든 플랫폼에서 동작합니다.

## 결론
이제 GroupDocs.Parser를 사용해 **Excel 워크북을 미리보기**하고 **xlsx를 png로 변환**하는 완전한 프로덕션 수준의 방법을 갖추었습니다. 프로젝트 요구에 맞게 DPI, 출력 폴더, 이미지 포맷을 조정하고, 이 코드를 더 큰 문서 관리 워크플로에 통합하세요.

다음 단계가 준비되셨나요? 고급 렌더링 옵션, 비밀번호 보호 파일, 배치 처리 기술 등에 대해서는 공식 [documentation](https://docs.groupdocs.com/parser/java/)을 확인하세요.

---

**마지막 업데이트:** 2026-02-06  
**테스트 환경:** GroupDocs.Parser 23.11 (작성 시 최신 버전)  
**작성자:** GroupDocs