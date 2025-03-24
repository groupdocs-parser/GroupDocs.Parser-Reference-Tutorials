---
title: 옵션을 사용하여 특정 영역에서 텍스트 추출
linktitle: 옵션을 사용하여 특정 영역에서 텍스트 추출
second_title: GroupDocs.Parser .NET API
description: .NET용 GroupDocs.Parser를 사용하여 문서의 특정 영역에서 텍스트를 추출하는 방법을 알아보세요. 이 튜토리얼을 통해 고급 텍스트 추출 옵션을 살펴보세요.
weight: 14
url: /ko/net/text-extraction/extract-text-from-specific-areas-with-options/
---
## 소개
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 사용자 정의 가능한 옵션을 사용하여 문서 내의 특정 영역에서 텍스트를 추출하는 방법을 살펴보겠습니다. GroupDocs.Parser는 개발자가 다양한 문서 형식의 텍스트를 쉽게 구문 분석하고 추출할 수 있게 해주는 강력한 라이브러리입니다.
## 전제 조건
코딩을 시작하기 전에 다음 사항이 있는지 확인하세요.
1. 개발 환경: Visual Studio 또는 기타 .NET 개발 IDE를 설치합니다.
2.  GroupDocs.Parser 라이브러리: 다음에서 .NET용 GroupDocs.Parser를 다운로드하고 설치합니다.[여기](https://releases.groupdocs.com/parser/net/).
3. 샘플 파일: 텍스트를 추출할 샘플 문서(예: PDF, DOCX 등)를 준비합니다.

## 네임스페이스 가져오기
먼저 GroupDocs.Parser 클래스 및 메서드에 액세스하는 데 필요한 네임스페이스를 가져와야 합니다.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 1단계: 파서 클래스 인스턴스 생성
 인스턴스를 초기화합니다.`Parser` 샘플 파일의 경로를 제공하여 클래스를 생성합니다.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // 텍스트 영역 추출을 위한 코드가 여기에 표시됩니다.
}
```
## 2단계: 텍스트 영역 추출 옵션 정의
 만들다`PageTextAreaOptions` 텍스트 추출 기준을 지정합니다.
```csharp
PageTextAreaOptions options = new PageTextAreaOptions("\\s[a-z]{2}\\s", new Rectangle(new Point(0, 0), new Size(300, 100)));
```
이 예에서는 다음과 같습니다.
- `"\\s[a-z]{2}\\s"` 소문자만 포함된 텍스트 영역과 일치시키는 정규식 패턴입니다.
- `new Rectangle(new Point(0, 0), new Size(300, 100))` 텍스트를 추출할 페이지의 직사각형(위치 및 크기)을 정의합니다.
## 3단계: 텍스트 영역 추출
정의된 옵션을 사용하여 지정된 기준에 맞는 텍스트 영역을 추출합니다.
```csharp
IEnumerable<PageTextArea> areas = parser.GetTextAreas(options);
```
## 4단계: 추출된 텍스트 영역 확인 및 반복
텍스트 영역 추출이 지원되는지 확인한 후 추출된 영역을 반복합니다.
```csharp
if (areas == null)
{
    Console.WriteLine("Page text areas extraction isn't supported");
    return;
}
foreach (PageTextArea a in areas)
{
    Console.WriteLine(string.Format("Page: {0}, R: {1}, Text: {2}", a.Page.Index, a.Rectangle, a.Text));
}
```

## 결론
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 문서 내의 특정 영역에서 텍스트를 추출하는 방법을 다루었습니다. 이 라이브러리는 다양한 문서 형식을 구문 분석하는 광범위한 기능을 제공하므로 텍스트 추출 작업에 유용한 도구입니다.

## FAQ
### GroupDocs.Parser는 스캔한 문서에서 텍스트를 추출할 수 있습니까?
예, GroupDocs.Parser는 스캔한 문서에 대해 OCR 기반 텍스트 추출을 지원합니다.
### GroupDocs.Parser는 여러 문서 형식과 호환됩니까?
예, PDF, DOCX, XLSX, PPTX 및 기타 널리 사용되는 형식에서 텍스트를 구문 분석하고 추출할 수 있습니다.
### GroupDocs.Parser는 .NET Core에 대한 지원을 제공합니까?
예, GroupDocs.Parser는 .NET Core 및 .NET Framework와 호환됩니다.
### GroupDocs.Parser를 사용하여 텍스트와 함께 메타데이터를 추출할 수 있습니까?
예, 문서에서 텍스트 콘텐츠와 메타데이터를 모두 추출할 수 있습니다.
### GroupDocs.Parser에 사용할 수 있는 평가판이 있습니까?
 예, 다음에서 무료 평가판을 받을 수 있습니다.[여기](https://releases.groupdocs.com/).