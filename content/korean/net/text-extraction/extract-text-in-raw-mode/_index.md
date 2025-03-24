---
title: 원시 모드에서 텍스트 추출
linktitle: 원시 모드에서 텍스트 추출
second_title: GroupDocs.Parser .NET API
description: .NET용 GroupDocs.Parser를 사용하여 문서에서 텍스트를 추출하는 방법을 알아보세요. .NET 애플리케이션 내에서 쉽고 효율적이며 원활한 텍스트 추출이 가능합니다.
weight: 19
url: /ko/net/text-extraction/extract-text-in-raw-mode/
---

# 원시 모드에서 텍스트 추출

## 소개
이 튜토리얼에서는 .NET용 GroupDocs.Parser를 활용하여 다양한 문서 형식에서 텍스트를 효율적으로 추출하는 방법을 살펴보겠습니다. GroupDocs.Parser는 개발자가 PDF, Word, Excel, PowerPoint 등과 같은 문서에서 텍스트와 메타데이터를 추출하여 .NET 응용 프로그램 내에서 텍스트 추출 작업을 단순화할 수 있는 강력한 라이브러리입니다.
## 전제 조건
이 튜토리얼을 시작하기 전에 다음 전제 조건이 설정되어 있는지 확인하세요.
- 컴퓨터에 설치된 Visual Studio 또는 기타 .NET 개발 환경.
- C# 프로그래밍 언어에 대한 기본 지식.
- .NET 라이브러리용 GroupDocs.Parser에 액세스합니다.

## 네임스페이스 가져오기
먼저 C# 프로젝트에서 GroupDocs.Parser에 필요한 네임스페이스를 가져와야 합니다.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## 1단계: GroupDocs.Parser 초기화
 텍스트 추출을 시작하려면`Parser`클래스, 샘플 문서에 대한 경로 전달:
```csharp
using (Parser parser = new Parser("YourSampleFile"))
{
    // 여기에서 텍스트 추출을 계속하세요.
}
```
## 2단계: 원시 텍스트 추출
 내`using` 블록, 사용`GetText` 방법`TextOptions` 문서에서 원시 텍스트를 추출하려면 다음을 수행하십시오.
```csharp
using (TextReader reader = parser.GetText(new TextOptions(true)))
{
    // 문서의 텍스트를 계속해서 읽으세요
}
```
## 3단계: 문서에서 텍스트 읽기
 이제`TextReader` 문서에서 추출된 텍스트를 읽는 객체:
```csharp
string extractedText = reader.ReadToEnd();
Console.WriteLine(extractedText);
```

## 결론
다음 단계를 수행하면 .NET용 GroupDocs.Parser를 사용하여 문서에서 원시 텍스트를 효과적으로 추출할 수 있습니다. 이 자습서에서는 원활한 텍스트 추출을 위해 .NET 애플리케이션 내에서 이 라이브러리를 활용하는 데 대한 기본 가이드를 제공합니다.

## FAQ
### GroupDocs.Parser는 어떤 파일 형식을 지원합니까?
GroupDocs.Parser는 PDF, Microsoft Word, Excel, PowerPoint 등을 포함한 광범위한 파일 형식을 지원합니다.
### GroupDocs.Parser를 사용하여 텍스트와 함께 메타데이터를 추출할 수 있습니까?
예, GroupDocs.Parser를 사용하면 지원되는 문서 형식에서 텍스트와 메타데이터를 모두 추출할 수 있습니다.
### GroupDocs.Parser는 .NET Core와 호환되나요?
예, GroupDocs.Parser는 기존 .NET Framework와 함께 .NET Core와 호환됩니다.
### GroupDocs.Parser는 암호로 보호된 문서를 처리합니까?
예, GroupDocs.Parser는 올바른 비밀번호가 제공되면 비밀번호로 보호된 문서를 처리할 수 있습니다.
### GroupDocs.Parser를 내 웹 응용 프로그램에 통합할 수 있습니까?
확실히 GroupDocs.Parser는 .NET 기술을 사용하여 개발된 웹 응용 프로그램에 완벽하게 통합될 수 있습니다.