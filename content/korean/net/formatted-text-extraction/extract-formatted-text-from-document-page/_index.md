---
title: 문서 페이지에서 서식 있는 텍스트 추출
linktitle: 문서 페이지에서 서식 있는 텍스트 추출
second_title: GroupDocs.Parser .NET API
description: .NET용 GroupDocs.Parser를 사용하여 문서 페이지에서 서식 있는 텍스트를 추출합니다. 효율적이고 안정적인 텍스트 추출 솔루션.
weight: 11
url: /ko/net/formatted-text-extraction/extract-formatted-text-from-document-page/
---
## 소개
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 문서 페이지에서 서식 있는 텍스트를 추출하는 과정을 안내합니다. 이 라이브러리를 사용하면 PDF, Word, Excel 등과 같은 다양한 문서 형식에서 텍스트를 효율적으로 구문 분석하고 추출할 수 있습니다.
## 전제 조건
시작하기 전에 다음 사항이 있는지 확인하세요.
- 시스템에 Visual Studio가 설치되어 있습니다.
- C# 프로그래밍에 대한 기본 지식.
-  .NET 라이브러리용 GroupDocs.Parser. 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/parser/net/).

## 네임스페이스 가져오기
먼저 필요한 네임스페이스를 C# 프로젝트로 가져오는 것부터 시작합니다.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## 1단계: 파서 클래스 인스턴스 생성
 인스턴스를 생성하여 시작합니다.`Parser` 샘플 파일의 경로를 제공하여 클래스를 생성합니다.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // 코드는 여기에 들어갈 것입니다
}
```
## 2단계: 서식 있는 텍스트 추출이 지원되는지 확인
텍스트 추출을 진행하기 전에 문서가 서식 있는 텍스트 추출을 지원하는지 확인하세요.
```csharp
if (!parser.Features.FormattedText)
{
    Console.WriteLine("Document does not support formatted text extraction.");
    return;
}
```
## 3단계: 문서 정보 가져오기
페이지 수와 같은 문서에 대한 정보를 검색합니다.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## 4단계: 문서 페이지 반복 및 서식 있는 텍스트 추출
문서의 각 페이지를 반복하고 지정된 옵션(예: Markdown 형식)을 사용하여 서식 있는 텍스트를 추출합니다.
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    
    using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Markdown)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## 결론
이제 .NET용 GroupDocs.Parser를 사용하여 문서 페이지에서 서식 있는 텍스트를 추출하는 방법을 알았습니다. 이 라이브러리는 다양한 파일 형식에서 텍스트를 추출하기 위한 강력하고 사용하기 쉬운 솔루션을 제공합니다.

## FAQ
### GroupDocs.Parser는 다양한 파일 형식을 처리할 수 있나요?
예, GroupDocs.Parser는 PDF, DOCX, XLSX, PPTX 등을 포함한 광범위한 문서 형식을 지원합니다.
### GroupDocs.Parser는 .NET Core와 호환되나요?
예, GroupDocs.Parser는 .NET Core 및 .NET Framework를 지원합니다.
### GroupDocs.Parser는 추출 중에 텍스트 서식을 유지합니까?
예, GroupDocs.Parser는 텍스트를 추출할 때 스타일 및 글꼴과 같은 서식을 유지할 수 있습니다.
### GroupDocs.Parser를 사용하여 이미지와 메타데이터를 추출할 수 있나요?
예, GroupDocs.Parser를 사용하면 문서에서 이미지, 메타데이터 및 텍스트를 추출할 수 있습니다.
### GroupDocs.Parser에 대한 지원을 받으려면 어떻게 해야 합니까?
 에서 지원을 받으실 수 있습니다.[GroupDocs.Parser 포럼](https://forum.groupdocs.com/c/parser/17).