---
title: 템플릿의 연결된 위치에서 필드 작업
linktitle: 템플릿의 연결된 위치에서 필드 작업
second_title: GroupDocs.Parser .NET API
description: .NET용 GroupDocs.Parser를 사용하여 문서에서 데이터를 효율적으로 추출하는 방법을 알아보세요. 코드 예제가 포함된 단계별 튜토리얼입니다.
weight: 12
url: /ko/net/document-template-processing/working-with-fields-at-linked-positions-in-templates/
---

# 템플릿의 연결된 위치에서 필드 작업

## 소개
.NET용 GroupDocs.Parser는 문서 구문 분석 및 데이터 추출 작업을 용이하게 하도록 설계된 강력한 라이브러리입니다. PDF, DOCX, XLSX 등을 포함한 광범위한 파일 형식을 지원합니다. 주요 기능 중 하나는 템플릿 기반 데이터 추출로, 이를 통해 문서 내의 필드를 정의하고 사전 정의된 템플릿을 기반으로 특정 데이터를 추출할 수 있습니다.
## 전제 조건
시작하기 전에 다음 사항이 있는지 확인하세요.
- C# 프로그래밍에 대한 기본 이해
- 시스템에 설치된 Visual Studio
-  .NET 라이브러리용 GroupDocs.Parser(다운로드:[여기](https://releases.groupdocs.com/parser/net/))
- 작업할 샘플 문서 파일

## 네임스페이스 가져오기
C# 프로젝트에 필요한 네임스페이스를 포함하는 것부터 시작하세요.
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## 1단계: 템플릿 필드 정의
먼저 정규식과 연결된 위치를 사용하여 템플릿 필드를 정의합니다.
```csharp
// 정규식으로 필드 정의
TemplateField field = new TemplateField(
    new TemplateRegexPosition("Tax"),
    "Tax");
// 특정 위치 설정으로 연결된 필드 정의
TemplateField linkedField = new TemplateField(
    new TemplateLinkedPosition(
        "Tax",
        new Size(100, 20),
        new TemplateLinkedPositionEdges(false, false, true, false)),
    "TaxValue");
```
## 2단계: 템플릿 만들기
다음으로 정의된 필드가 포함된 템플릿을 만듭니다.
```csharp
// 정의된 필드를 사용하여 템플릿 만들기
Template template = new Template(new TemplateItem[] { field, linkedField });
```
## 3단계: 템플릿을 사용하여 문서 구문 분석
 이제 초기화하세요.`Parser` 클래스를 생성하고 템플릿을 사용하여 문서를 구문 분석합니다.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // 템플릿을 기준으로 문서를 구문 분석합니다.
    DocumentData data = parser.ParseByTemplate(template);
    // 추출된 데이터를 반복하고 결과를 인쇄합니다.
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

## 결론
.NET용 GroupDocs.Parser는 템플릿을 사용하여 문서에서 구조화된 데이터를 추출하는 프로세스를 단순화합니다. 필드를 정의하고 템플릿을 적용하면 관련 정보를 효율적으로 추출할 수 있어 문서 처리 업무의 자동화 및 생산성이 향상됩니다.

## FAQ
### GroupDocs.Parser는 암호화된 PDF 파일에서 데이터를 추출할 수 있습니까?
예, GroupDocs.Parser는 구문 분석 중에 암호를 제공하여 암호화된 PDF 파일 구문 분석을 지원합니다.
### 템플릿 기반 추출에는 어떤 파일 형식이 지원됩니까?
GroupDocs.Parser는 PDF, DOCX, XLSX, PPTX, TXT 등을 포함한 광범위한 파일 형식을 지원합니다.
### GroupDocs.Parser에 사용할 수 있는 평가판이 있습니까?
 예, 다음에서 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/).
### 문서 일괄 처리에 GroupDocs.Parser를 사용할 수 있습니까?
예, GroupDocs.Parser를 사용하면 일괄 처리를 통해 여러 문서를 동시에 구문 분석할 수 있습니다.
### GroupDocs.Parser에 대한 기술 지원은 어디서 받을 수 있나요?
 기술 지원을 요청하고 커뮤니티에 참여할 수 있습니다.[GroupDocs 포럼](https://forum.groupdocs.com/c/parser/17).