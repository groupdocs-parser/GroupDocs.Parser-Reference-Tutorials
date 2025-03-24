---
title: 로컬 디스크에서 문서 로드
linktitle: 로컬 디스크에서 문서 로드
second_title: GroupDocs.Parser .NET API
description: .NET용 GroupDocs.Parser를 사용하여 다양한 문서 형식에서 텍스트를 추출하는 방법을 알아보세요. C#을 사용한 쉽고 효율적인 텍스트 추출.
weight: 11
url: /ko/net/document-loading/load-document-from-local-disk/
---

# 로컬 디스크에서 문서 로드

## 소개
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 문서에서 텍스트를 추출하는 방법을 살펴보겠습니다. GroupDocs.Parser는 개발자가 다양한 문서 형식을 구문 분석하고 프로그래밍 방식으로 텍스트 콘텐츠를 추출할 수 있는 강력한 라이브러리입니다. 이 라이브러리를 사용하여 텍스트 추출을 시작하는 데 필요한 단계를 다루겠습니다.
## 전제 조건
시작하기 전에 다음 필수 구성 요소가 설치되어 있는지 확인하세요.
- 시스템에 Visual Studio가 설치되어 있습니다.
- C# 프로그래밍 언어에 대한 기본 지식.
-  .NET 라이브러리용 GroupDocs.Parser 설치(다운로드[여기](https://releases.groupdocs.com/parser/net/)).

## 네임스페이스 가져오기
먼저 필요한 네임스페이스를 C# 프로젝트로 가져와야 합니다.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```
## 1단계: 로컬 디스크에서 문서 로드
 로컬 디스크에서 문서를 로드하는 것부터 시작하세요. 바꾸다`"Your Sample File"` 대상 문서의 경로와 함께.
```csharp
// 파일 경로 설정
string filePath = "Your Sample File";
// filePath를 사용하여 Parser 클래스의 인스턴스를 만듭니다.
using (Parser parser = new Parser(filePath))
{
    // 리더로 텍스트 추출
    using (TextReader reader = parser.GetText())
    {
        //문서에서 추출된 텍스트를 인쇄합니다.
        // 텍스트 추출이 지원되지 않으면 판독기는 null이 됩니다.
        Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
    }
}
```
## 단계 설명
1. 파일 경로 설정: 텍스트를 추출하려는 문서의 경로를 지정하여 시작합니다(`filePath` 변하기 쉬운).
2.  파서 인스턴스 생성: 인스턴스화`Parser` 수업을 통과하여`filePath`.
3.  텍스트 추출:`GetText()` 의 방법`Parser` 인스턴스를 얻기 위해`TextReader` 문서에서 추출된 텍스트가 포함된 개체입니다.
4.  추출된 텍스트 읽기:`ReadToEnd()` 의 방법`TextReader` 문서에서 추출된 전체 텍스트 내용을 검색합니다.
5.  지원되지 않는 형식 처리: 문서 형식이 텍스트 추출을 지원하지 않는 경우`reader` 객체는 될 것이다`null`, 이에 따라 이 시나리오를 처리할 수 있습니다.

## 결론
이 자습서에서는 .NET용 GroupDocs.Parser를 사용하여 문서에서 텍스트를 추출하는 초기 단계를 다루었습니다. 이 라이브러리는 문서 구문 분석을 위한 광범위한 기능을 제공하므로 개발자는 애플리케이션 내에서 다양한 파일 형식으로 효율적으로 작업할 수 있습니다.

## FAQ
### GroupDocs.Parser는 모든 문서 형식과 호환됩니까?
GroupDocs.Parser는 PDF, Microsoft Office 문서(Word, Excel, PowerPoint) 등을 포함한 광범위한 형식을 지원합니다.
### GroupDocs.Parser를 사용하여 텍스트와 함께 메타데이터를 추출할 수 있습니까?
예, GroupDocs.Parser를 사용하면 지원되는 문서 형식에서 텍스트 콘텐츠와 메타데이터를 모두 추출할 수 있습니다.
### GroupDocs.Parser에 대한 추가 리소스와 지원은 어디서 찾을 수 있나요?
 방문하다[GroupDocs.Parser 문서](https://tutorials.groupdocs.com/parser/net/) 자세한 API 참조를 확인하고[GroupDocs 포럼](https://forum.groupdocs.com/c/parser/17) 지역 사회 지원을 위해.
### GroupDocs.Parser의 임시 라이센스를 얻으려면 어떻게 해야 합니까?
 다음을 요청할 수 있습니다.[임시면허](https://purchase.groupdocs.com/temporary-license/) 평가 및 테스트 목적으로.
### GroupDocs.Parser에 대한 무료 평가판이 있습니까?
 예, 다음을 다운로드할 수 있습니다.[무료 시험판](https://releases.groupdocs.com/) GroupDocs.Parser 버전입니다.