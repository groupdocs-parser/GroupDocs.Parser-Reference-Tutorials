---
title: OCR 처리
linktitle: OCR 처리
second_title: GroupDocs.Parser .NET API
description: .NET용 GroupDocs.Parser를 사용하여 OCR을 처리하는 방법을 알아보세요. 이미지와 스캔한 문서에서 텍스트를 효율적으로 추출합니다.
weight: 11
url: /ko/net/ocr-extraction/handling-ocr/
type: docs
---
# OCR 처리

## 소개
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 OCR(광학 문자 인식) 작업을 효율적으로 처리하는 방법을 살펴보겠습니다. 이 라이브러리는 문서에서 텍스트를 추출하는 강력한 도구를 제공하며, OCR을 사용하면 이미지나 스캔한 문서에서도 텍스트를 추출할 수 있습니다. 프로세스를 단계별로 살펴보겠습니다.
## 전제 조건
시작하기 전에 다음이 설정되어 있는지 확인하세요.
- .NET 라이브러리용 GroupDocs.Parser: 다음에서 라이브러리를 다운로드하세요.[여기](https://releases.groupdocs.com/parser/net/).
- 샘플 파일: 텍스트를 추출하려는 샘플 파일(문서 또는 이미지)을 준비합니다.
- C# 및 .NET 환경에 대한 기본 지식.

## 네임스페이스 가져오기
먼저 .NET 애플리케이션에서 GroupDocs.Parser 기능을 사용하려면 필요한 네임스페이스를 가져와야 합니다.
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
## 1단계: OCR 커넥터를 사용하여 파서 설정 만들기
 초기화`ParserSettings` OCR 커넥터를 사용한 클래스입니다. 예를 들어 온프레미스에서 Aspose OCR을 사용합니다.
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## 2단계: OCR 옵션 구성
 설정`OcrEventHandler` OCR 처리 중 경고를 처리합니다.
```csharp
OcrEventHandler handler = new OcrEventHandler();
OcrOptions ocrOptions = new OcrOptions(handler);
```
## 3단계: 텍스트 추출 옵션 구성
 만들다`TextOptions` OCR 기반 텍스트 추출을 활성화합니다.
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## 4단계: OCR을 사용하여 텍스트 추출
 인스턴스화`Parser` 설정으로 클래스를 지정하고 OCR을 사용하여 텍스트를 추출합니다.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    using (TextReader reader = parser.GetText(options))
    {
        if (reader == null)
        {
            Console.WriteLine("Text extraction isn't supported.");
        }
        else
        {
            Console.WriteLine(reader.ReadToEnd());
        }
    }
    if (handler.HasWarnings)
    {
        Console.WriteLine("The following warnings occurred during text recognition:");
        foreach (string w in handler.Warnings)
        {
            Console.WriteLine("\t* " + w);
        }
    }
    else
    {
        Console.WriteLine("Text recognition was performed without any warnings.");
    }
}
```

## 결론
다음 단계를 수행하면 .NET용 GroupDocs.Parser를 활용하여 응용 프로그램 내에서 OCR 작업을 효과적으로 처리할 수 있습니다. 이 라이브러리가 제공하는 강력한 기능을 사용하면 이미지나 스캔한 문서에서 텍스트를 원활하게 추출할 수 있습니다.

## FAQ
### .NET용 GroupDocs.Parser는 다른 파일 형식과 호환됩니까?
예, GroupDocs.Parser는 PDF, DOCX, PPTX, XLSX, 이미지(JPEG, PNG, TIFF) 등을 포함한 광범위한 파일 형식을 지원합니다.
### 상업용 프로젝트에서 .NET용 GroupDocs.Parser를 사용할 수 있습니까?
예, 라이센스를 구매한 후 .NET용 GroupDocs.Parser를 상용 응용 프로그램에 통합할 수 있습니다.
### GroupDocs.Parser는 암호화되거나 암호로 보호된 파일을 처리합니까?
GroupDocs.Parser는 암호로 보호된 PDF 문서에서 텍스트를 구문 분석하고 추출할 수 있습니다.
### .NET용 GroupDocs.Parser에 사용할 수 있는 평가판이 있습니까?
 예, 다음에서 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/).
### .NET용 GroupDocs.Parser와 관련된 지원을 찾거나 질문을 할 수 있는 곳은 어디입니까?
 당신은 방문 할 수 있습니다[GroupDocs.Parser 포럼](https://forum.groupdocs.com/c/parser/17) 지원 문의나 토론을 위해.