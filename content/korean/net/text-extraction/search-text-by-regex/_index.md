---
title: 정규식으로 텍스트 검색(Regex)
linktitle: 정규식으로 텍스트 검색(Regex)
second_title: GroupDocs.Parser .NET API
description: .NET용 GroupDocs.Parser를 사용하여 문서에서 정규식을 사용하여 텍스트를 검색하는 방법을 알아보세요. 특정 콘텐츠를 손쉽게 추출하세요.
weight: 23
url: /ko/net/text-extraction/search-text-by-regex/
---

# 정규식으로 텍스트 검색(Regex)

## 소개
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 문서 내에서 정규식(Regex)으로 텍스트를 검색하는 방법을 살펴보겠습니다. GroupDocs.Parser는 개발자가 PDF, DOCX, XLSX 등과 같은 다양한 파일 형식에서 텍스트와 메타데이터를 추출할 수 있는 강력한 라이브러리입니다. 정규식을 사용하여 텍스트를 검색하는 것은 문서 내에서 패턴이나 특정 콘텐츠를 효율적으로 찾는 데 특히 유용합니다.
## 전제 조건
이 튜토리얼을 시작하기 전에 다음 사항을 확인하세요.
1. Visual Studio: .NET 개발용 Visual Studio IDE를 설치합니다.
2.  .NET용 GroupDocs.Parser: 다음에서 .NET용 GroupDocs.Parser를 다운로드하고 설치합니다.[여기](https://releases.groupdocs.com/parser/net/).
3. 샘플 파일: 검색 기능을 테스트하기 위한 샘플 문서(PDF, DOCX 등)를 준비합니다.

## 네임스페이스 가져오기
먼저 C# 코드에 필요한 네임스페이스를 포함하는 것부터 시작합니다.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 1단계: 파서 클래스 인스턴스 생성
 인스턴스화`Parser` 샘플 파일의 경로를 제공하여 클래스를 지정합니다.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // 코드는 여기에 표시됩니다.
}
```
 바꾸다`"YourSampleFile.pdf"` 실제 파일의 경로와 함께.
## 2단계: 정규식을 사용하여 검색
정규식 패턴을 사용하여 검색을 정의하고 실행합니다. 예를 들어 문서 내에서 숫자 시퀀스(예: 정수)를 찾으려면 다음을 수행하세요.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("[0-9]+", new SearchOptions(true, false, true));
```
 이 예에서는`[0-9]+` 하나 이상의 숫자와 일치하는 정규식 패턴입니다.
## 3단계: 검색 지원 확인
문서 유형에 대해 검색 작업이 지원되는지 확인하십시오.
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported");
    return;
}
```
## 4단계: 검색 결과 반복
검색 결과를 반복하고 각 일치 항목을 처리합니다.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
이 루프는 문서 내에서 찾은 위치와 일치하는 텍스트를 인쇄합니다.

## 결론
결론적으로, .NET용 GroupDocs.Parser를 활용하면 다양한 문서 형식에서 정규식을 사용하여 효율적인 텍스트 검색이 가능합니다. 이 가이드를 따르면 개발자는 문서 구문 분석 및 정규식 기반 텍스트 추출을 .NET 애플리케이션에 원활하게 통합할 수 있습니다.

## FAQ
### GroupDocs.Parser는 암호화된 문서 내에서 검색할 수 있습니까?
아니요, GroupDocs.Parser는 암호화되거나 암호로 보호된 문서 내에서 검색할 수 없습니다.
### GroupDocs.Parser는 OCR(광학 문자 인식)을 지원합니까?
아니요, GroupDocs.Parser는 OCR을 수행하지 않습니다. 문서의 내부 구조에서 텍스트를 추출하는 데 의존합니다.
### 정규식을 사용하여 복잡한 패턴을 검색할 수 있나요?
예, GroupDocs.Parser는 완전한 정규식을 지원하여 문서 내에서 복잡한 패턴 일치를 가능하게 합니다.
### 텍스트 추출이 지원되는 문서 형식은 무엇입니까?
GroupDocs.Parser는 PDF, DOCX, XLSX, PPTX 등을 포함한 광범위한 형식을 지원합니다.
### GroupDocs.Parser는 .NET Core와 호환되나요?
예, GroupDocs.Parser는 크로스 플랫폼 개발을 위해 .NET Core와 호환됩니다.