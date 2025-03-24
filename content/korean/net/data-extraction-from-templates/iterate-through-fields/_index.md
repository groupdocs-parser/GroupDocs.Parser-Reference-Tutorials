---
title: 필드 반복
linktitle: 필드 반복
second_title: GroupDocs.Parser .NET API
description: .NET용 GroupDocs.Parser를 사용하여 문서에서 구조화된 데이터를 추출하는 방법을 알아보세요. 문서 데이터 추출 기능으로 .NET 애플리케이션을 강화하세요.
weight: 11
url: /ko/net/data-extraction-from-templates/iterate-through-fields/
---

# 필드 반복

## 소개
.NET용 GroupDocs.Parser는 개발자가 PDF, Microsoft Word, Excel 및 PowerPoint와 같은 다양한 문서 형식에서 데이터를 추출할 수 있는 강력한 라이브러리입니다. 이 튜토리얼에서는 GroupDocs.Parser를 사용하여 문서 필드를 반복하고 템플릿을 사용하여 특정 데이터를 추출하는 과정을 안내합니다. 이 자습서를 마치면 .NET 애플리케이션의 문서에서 구조화된 데이터를 효율적으로 추출할 수 있게 됩니다.
## 전제 조건
시작하기 전에 다음 전제 조건이 설정되어 있는지 확인하세요.
- C# 프로그래밍에 대한 기본 지식.
- 컴퓨터에 Visual Studio가 설치되어 있습니다.
- .NET 라이브러리용 GroupDocs.Parser가 프로젝트에 설치되고 참조됩니다.

## 네임스페이스 가져오기
시작하려면 C# 파일에 필요한 네임스페이스를 추가하세요.
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
프로세스를 단계별 지침으로 나누어 보겠습니다.
## 1단계: 템플릿 필드 정의
먼저 정규식을 사용하여 문서에서 추출하려는 필드를 정의합니다.
```csharp
// "가격" 필드 정의
TemplateField priceField = new TemplateField(
    new TemplateRegexPosition("\\$\\d+(.\\d+)?"),
    "Price");
// "이메일" 필드 정의
TemplateField emailField = new TemplateField(
    new TemplateRegexPosition("[a-z]+\\@[a-z]+\\.[a-z]+"),
    "Email");
// 정의된 필드가 있는 템플릿 만들기
Template template = new Template(new TemplateItem[] { priceField, emailField });
```
이 단계에서는 두 개의 필드를 정의했습니다. 하나는 가격(달러 기호와 숫자로 식별됨) 추출용이고 다른 하나는 이메일 주소 추출용입니다.
## 2단계: 문서 분석
 다음으로`Parser` 정의된 템플릿을 사용하여 문서를 구문 분석하는 클래스입니다.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // 템플릿을 기준으로 문서를 구문 분석합니다.
    DocumentData data = parser.ParseByTemplate(template);
    // 추출된 데이터를 통해 반복
    for (int i = 0; i < data.Count; i++)
    {
        // 필드 이름 인쇄
        Console.Write(data[i].Name + ": ");
        // 추출된 영역이 텍스트인지 확인
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
 여기서는`Parser` 샘플 문서의 경로를 입력한 다음 정의된 템플릿을 사용하여 문서를 구문 분석합니다. 그런 다음 추출된 데이터를 반복하고 추출된 텍스트와 함께 필드 이름을 인쇄합니다.
## 결론
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 템플릿을 사용하여 문서에서 특정 데이터를 추출하는 방법을 살펴보았습니다. 정규식과 템플릿을 활용하면 다양한 문서 형식에서 구조화된 정보를 효율적으로 추출할 수 있습니다. 특정 추출 요구 사항에 맞게 다양한 템플릿과 문서 유형을 실험해 보세요.

## FAQ
### GroupDocs.Parser는 스캔한 문서에서 데이터를 추출할 수 있습니까?
예, GroupDocs.Parser는 스캔한 PDF 문서와 검색 가능한 PDF 문서 모두에서 텍스트와 메타데이터를 추출할 수 있습니다.
### GroupDocs.Parser는 .NET Core 애플리케이션과 호환됩니까?
예, GroupDocs.Parser는 .NET Framework와 함께 .NET Core를 지원합니다.
### GroupDocs.Parser는 어떤 문서 형식을 지원합니까?
GroupDocs.Parser는 PDF, Microsoft Word, Excel, PowerPoint 등을 포함한 광범위한 형식을 지원합니다.
### GroupDocs.Parser를 사용하여 대용량 문서를 어떻게 처리할 수 있나요?
GroupDocs.Parser는 대용량 문서의 특정 페이지나 섹션에서 데이터를 추출하는 옵션을 제공하여 효율적인 처리를 보장합니다.
### 텍스트 추출에만 GroupDocs.Parser를 사용할 수 있습니까?
예, 복잡한 서식을 적용할 필요 없이 GroupDocs.Parser를 사용하여 문서에서 일반 텍스트 콘텐츠를 추출할 수 있습니다.