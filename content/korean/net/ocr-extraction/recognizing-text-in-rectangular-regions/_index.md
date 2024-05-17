---
title: 직사각형 영역의 텍스트 인식
linktitle: 직사각형 영역의 텍스트 인식
second_title: GroupDocs.Parser .NET API
description: OCR 기능이 있는 .NET용 GroupDocs.Parser를 사용하여 문서의 특정 영역에서 텍스트를 인식하는 방법을 알아보세요.
type: docs
weight: 14
url: /ko/net/ocr-extraction/recognizing-text-in-rectangular-regions/
---
## 소개
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 문서의 특정 직사각형 영역 내의 텍스트를 인식하는 방법을 살펴보겠습니다. GroupDocs.Parser는 개발자가 PDF, Word, Excel 및 PowerPoint를 포함한 다양한 파일 형식에서 텍스트, 메타데이터 등을 추출할 수 있는 강력한 라이브러리입니다.
## 전제 조건
시작하기 전에 다음이 설정되어 있는지 확인하세요.
-  .NET용 GroupDocs.Parser: 다음에서 라이브러리를 다운로드하고 설치합니다.[여기](https://releases.groupdocs.com/parser/net/).
- 개발 환경: Visual Studio 또는 기타 .NET IDE.
- 샘플 문서: 인식할 텍스트가 포함된 샘플 파일(예: PDF, DOCX)이 있습니다.

## 네임스페이스 가져오기
먼저 필요한 네임스페이스를 C# 코드로 가져와야 합니다.
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using System.Linq;
using System.Text;
using Aspose.OCR;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 1단계: 파서 설정 초기화
 설정부터 시작하세요.`ParserSettings` OCR 커넥터로. 여기서는 Aspose OCR 온프레미스 커넥터를 사용하겠습니다.
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## 2단계: 파서 인스턴스 생성
 다음으로 인스턴스화`Parser` 이전에 정의된 설정이 있는 클래스:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // 코드는 여기서 계속됩니다
}
```
 바꾸다`"YourSampleFile.pdf"` 문서의 경로와 함께.
## 3단계: OCR 직사각형 정의
 텍스트 인식이 수행될 문서 내에서 직사각형을 정의합니다. 예를 들어, 다음에서 시작하는 직사각형`(0, 0)` 너비가 있는`400` 그리고 키`200`:
```csharp
OcrOptions ocrOptions = new OcrOptions(new Data.Rectangle(0, 0, 400, 200));
```
## 4단계: 텍스트 인식 옵션 구성
 만들다`TextOptions` 정의된 직사각형과 함께 OCR 사용법을 지정하려면:
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## 5단계: OCR을 사용하여 텍스트 추출
 사용`GetText` 의 방법`Parser` 구성된 인스턴스`TextOptions`:
```csharp
using (TextReader reader = parser.GetText(options))
{
    // 추출된 텍스트를 읽거나 '지원되지 않는' 사례를 처리합니다.
    Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
}
```

## 결론
이 자습서에서는 .NET용 GroupDocs.Parser를 활용하여 OCR을 사용하여 문서의 특정 직사각형 영역에서 텍스트를 추출하는 방법을 시연했습니다. 이 프로세스는 자동화된 텍스트 추출 작업을 위해 추가로 사용자 정의하고 다양한 애플리케이션에 통합할 수 있습니다.

## FAQ
### GroupDocs.Parser는 스캔한 문서에서 텍스트를 추출할 수 있습니까?
예, GroupDocs.Parser는 스캔한 문서에서 텍스트를 추출하기 위한 OCR(광학 문자 인식)을 지원합니다.
### GroupDocs.Parser는 어떤 파일 형식을 지원합니까?
GroupDocs.Parser는 PDF, DOCX, XLSX, PPTX 등을 포함한 광범위한 파일 형식을 지원합니다.
### 텍스트 추출이 지원되지 않는 문서는 어떻게 처리하나요?
 다음을 사용하여 텍스트 추출이 지원되는지 확인할 수 있습니다.`TextReader` 다음이 반환한 인스턴스`parser.GetText(options)`.
### GroupDocs.Parser는 대규모 텍스트 추출 작업에 적합합니까?
예, GroupDocs.Parser는 대규모 텍스트 추출 작업을 효율적으로 처리하도록 설계되었습니다.
### GroupDocs.Parser 관련 문제에 대한 지원은 어디서 받을 수 있나요?
 지원 및 토론을 원하시면 다음 사이트를 방문하세요.[GroupDocs.Parser 포럼](https://forum.groupdocs.com/c/parser/17).