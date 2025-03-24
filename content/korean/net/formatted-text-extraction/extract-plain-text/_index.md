---
title: 일반 텍스트 추출
linktitle: 일반 텍스트 추출
second_title: GroupDocs.Parser .NET API
description: .NET용 GroupDocs.Parser를 사용하여 문서에서 일반 텍스트를 추출하는 방법을 알아보세요. 애플리케이션에 텍스트 추출을 통합하는 쉬운 단계입니다.
weight: 14
url: /ko/net/formatted-text-extraction/extract-plain-text/
---

# 일반 텍스트 추출

## 소개
이 튜토리얼에서는 .NET용 GroupDocs.Parser를 사용하여 다양한 문서 형식에서 일반 텍스트를 추출하는 방법을 살펴보겠습니다. GroupDocs.Parser는 개발자가 원활하게 문서 작업을 수행하고 텍스트와 메타데이터를 효율적으로 추출할 수 있게 해주는 강력한 라이브러리입니다. 이 가이드는 .NET 애플리케이션 내에서 이 라이브러리를 통합하고 활용하는 데 필요한 단계를 안내합니다.
## 전제 조건
시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1. Visual Studio: 개발 컴퓨터에 Visual Studio를 설치합니다.
2.  GroupDocs.Parser 라이브러리: 다음에서 .NET용 GroupDocs.Parser를 다운로드하고 설치합니다.[다운로드 페이지](https://releases.groupdocs.com/parser/net/).
3. 샘플 문서: 텍스트 추출을 위한 샘플 문서(예: DOCX, PDF, TXT)를 준비합니다.

## 네임스페이스 가져오기
먼저 C# 프로젝트에 필요한 네임스페이스를 포함하여 GroupDocs.Parser의 기능에 액세스합니다.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## 1단계: 파서 초기화
 인스턴스를 생성합니다.`Parser` 샘플 문서의 경로를 지정하여 클래스를 지정하세요.
```csharp
using (Parser parser = new Parser("path_to_your_sample_file"))
{
    // 텍스트 추출을 위한 코드가 여기에 표시됩니다.
}
```
## 2단계: 서식 있는 텍스트 추출
 내`using` 블록`Parser` 다음을 사용하여 서식이 지정된 텍스트를 추출합니다.`GetFormattedText` 방법`PlainText` 방법.
```csharp
using (TextReader reader = parser.GetFormattedText(new FormattedTextOptions(FormattedTextMode.PlainText)))
{
    // 추출된 텍스트를 읽고 처리하는 코드
}
```
## 3단계: 추출된 텍스트 읽기
 사용`TextReader` 추출된 일반 텍스트를 읽고 출력하는 인스턴스입니다.
```csharp
string extractedText = reader.ReadToEnd();
Console.WriteLine(extractedText);
```

## 결론
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 문서에서 일반 텍스트를 추출하는 기본 사항을 다루었습니다. 다음 단계를 수행하면 텍스트 추출 기능을 .NET 애플리케이션에 원활하게 통합할 수 있습니다.

## FAQ
### GroupDocs.Parser는 여러 문서 형식과 호환됩니까?
예, GroupDocs.Parser는 DOCX, PDF, TXT 등을 포함한 광범위한 문서 형식을 지원합니다.
### GroupDocs.Parser를 사용하여 텍스트와 함께 메타데이터를 추출할 수 있습니까?
물론, GroupDocs.Parser를 사용하면 텍스트 콘텐츠와 작성자, 생성 날짜 등과 같은 메타데이터를 모두 추출할 수 있습니다.
### GroupDocs.Parser에 대한 무료 평가판이 있습니까?
 예, GroupDocs.Parser 무료 평가판에 액세스할 수 있습니다.[여기](https://releases.groupdocs.com/).
### GroupDocs.Parser에 대한 기술 지원은 어디서 찾을 수 있나요?
 기술 지원이 필요하면 GroupDocs.Parser를 방문하세요.[법정](https://forum.groupdocs.com/c/parser/17).
### GroupDocs.Parser의 임시 라이센스를 얻으려면 어떻게 해야 합니까?
 임시 라이센스를 얻으려면 GroupDocs.Parser를 방문하십시오.[임시 라이센스 페이지](https://purchase.groupdocs.com/temporary-license/).