---
title: Excel 문서에서 텍스트를 HTML로 추출
linktitle: Excel 문서에서 텍스트를 HTML로 추출
second_title: GroupDocs.Parser .NET API
description: Excel 문서에서 텍스트를 추출하고 .NET용 GroupDocs.Parser를 사용하여 HTML로 변환하는 방법을 알아보세요.
weight: 13
url: /ko/net/excel-document-processing/extract-text-from-excel-document-as-html/
---
## 소개
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 Excel 문서에서 텍스트를 추출하고 HTML 형식으로 변환하는 방법을 살펴보겠습니다. GroupDocs.Parser는 개발자가 다양한 문서 형식으로 작업하여 텍스트와 메타데이터를 효율적으로 추출할 수 있는 강력한 라이브러리입니다.
## 전제 조건
시작하기 전에 다음이 설정되어 있는지 확인하세요.
- 시스템에 Visual Studio가 설치되어 있습니다.
- C# 프로그래밍에 대한 기본 이해.
-  .NET용 GroupDocs.Parser 라이브러리. 다음에서 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/parser/net/).
## 네임스페이스 가져오기
GroupDocs.Parser 기능에 액세스하려면 C# 프로젝트에 필요한 네임스페이스를 포함하는 것부터 시작하세요.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 1단계: 파서 클래스 인스턴스 생성
 먼저 인스턴스화`Parser` Excel 문서의 경로를 제공하여 클래스를 생성합니다.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // 추가 코드는 여기에 표시됩니다.
}
```
 바꾸다`"YourSampleFile.xlsx"` Excel 파일의 경로와 함께.
## 2단계: 텍스트를 HTML로 추출
 내`using` 블록`Parser` 예를 들어`GetFormattedText` HTML 모드에서 서식 있는 텍스트를 추출하는 방법입니다.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        // 추가 코드는 여기에 표시됩니다.
    }
}
```
## 3단계: 추출된 HTML 텍스트 읽기 및 인쇄
 다음으로, 추출된 HTML 텍스트를 읽습니다.`TextReader` 그리고 콘솔에 출력해보세요.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.Html)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```
이 코드가 실행되면 Excel 문서에서 텍스트를 추출하여 콘솔에 HTML 형식으로 표시합니다.
## 결론
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 Excel 문서에서 텍스트를 추출하고 HTML 형식으로 변환하는 방법을 배웠습니다. 이 라이브러리는 다양한 문서 형식으로 작업할 수 있는 간단한 방법을 제공하므로 개발자는 애플리케이션에서 텍스트 추출 작업을 효율적으로 처리할 수 있습니다.

## FAQ
### GroupDocs.Parser는 Excel 외에 다른 문서 형식을 처리할 수 있습니까?
예, GroupDocs.Parser는 PDF, Word, PowerPoint 등을 포함한 광범위한 파일 형식을 지원합니다.
### GroupDocs.Parser는 .NET Core와 호환되나요?
예, GroupDocs.Parser는 .NET Framework 및 .NET Core 모두와 호환됩니다.
### GroupDocs.Parser는 텍스트 추출 중에 서식을 유지합니까?
예, GroupDocs.Parser는 텍스트 추출 중에 글꼴, 스타일, 레이아웃과 같은 서식을 보존할 수 있습니다.
### GroupDocs.Parser를 사용하여 문서에서 메타데이터를 추출할 수 있습니까?
예, GroupDocs.Parser를 사용하면 지원되는 문서 유형에서 작성자, 생성 날짜 등과 같은 메타데이터를 추출할 수 있습니다.
### GroupDocs.Parser에 대한 무료 평가판이 있습니까?
 예, 다음에서 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/).