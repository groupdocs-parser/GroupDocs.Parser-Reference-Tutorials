---
title: 원시 모드의 PDF 페이지에서 텍스트 추출
linktitle: 원시 모드의 PDF 페이지에서 텍스트 추출
second_title: GroupDocs.Parser .NET API
description: C#에서 GroupDocs.Parser를 사용하여 PDF에서 텍스트를 추출합니다. 이 강력한 .NET 라이브러리를 사용하여 효율적인 PDF 텍스트 추출에 대해 알아보세요.
type: docs
weight: 16
url: /ko/net/pdf-processing/extract-text-from-page-in-pdf-in-raw-mode/
---
## 소개
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 원시 모드를 사용하여 PDF 문서의 페이지에서 텍스트를 추출하는 방법을 살펴보겠습니다. GroupDocs.Parser는 개발자가 프로그래밍 방식으로 다양한 문서 형식으로 작업할 수 있도록 하는 강력한 도구입니다.
## 전제 조건
이 튜토리얼을 시작하기 전에 다음 사항이 있는지 확인하세요.
- 컴퓨터에 Visual Studio가 설치되어 있습니다.
- C# 프로그래밍에 대한 기본 지식.
- .NET 라이브러리용 GroupDocs.Parser[여기서 다운로드하세요](https://releases.groupdocs.com/parser/net/).
- 테스트용 샘플 PDF 파일입니다.

## 네임스페이스 가져오기
먼저 C# 프로젝트에서 필요한 네임스페이스를 가져와야 합니다.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 1단계: 파서 클래스 인스턴스 생성
 시작하려면 인스턴스화하세요.`Parser`샘플 PDF 파일의 경로를 제공하여 클래스를 제공합니다.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // 귀하의 코드는 여기에 있습니다
}
```
## 2단계: 문서 정보 가져오기 및 페이지 반복
다음으로 문서 정보를 검색하고 각 페이지를 반복하여 텍스트를 추출합니다.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // 텍스트 추출을 위한 코드가 여기에 표시됩니다.
}
```
## 3단계: 각 페이지에서 텍스트 추출
 루프 내에서`GetText` 각 페이지에서 텍스트를 추출하여 인쇄하는 방법입니다.
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## 결론
 이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 원시 모드에서 PDF 페이지에서 텍스트를 추출하는 방법을 배웠습니다. 이 프로세스에는`Parser` 예를 들어, 문서 정보를 얻고, 각 페이지를 반복하고,`GetText` 방법.

## FAQ
### .NET용 GroupDocs.Parser란 무엇입니까?
.NET용 GroupDocs.Parser는 개발자가 프로그래밍 방식으로 다양한 파일 형식에서 텍스트, 메타데이터 및 기타 정보를 추출할 수 있는 문서 구문 분석 API입니다.
### .NET용 GroupDocs.Parser를 어떻게 다운로드합니까?
 라이브러리는 다음에서 다운로드할 수 있습니다.[GroupDocs 웹사이트](https://releases.groupdocs.com/parser/net/).
### 무료 평가판이 제공되나요?
 예, 다음에서 .NET용 GroupDocs.Parser 무료 평가판에 액세스할 수 있습니다.[여기](https://releases.groupdocs.com/).
### .NET용 GroupDocs.Parser에 대한 지원은 어디서 찾을 수 있나요?
 기술 지원 및 커뮤니티 지원을 받으려면 다음을 방문하세요.[GroupDocs 포럼](https://forum.groupdocs.com/c/parser/17).
### .NET용 GroupDocs.Parser 라이센스를 어떻게 구매할 수 있나요?
 다음에서 라이센스를 구입할 수 있습니다.[구매 페이지](https://purchase.groupdocs.com/buy) 아니면 임시면허를 취득하세요.[여기](https://purchase.groupdocs.com/temporary-license/).