---
title: PDF에서 이미지 추출
linktitle: PDF에서 이미지 추출
second_title: GroupDocs.Parser .NET API
description: .NET용 GroupDocs.Parser를 사용하여 PDF 문서에서 이미지를 추출하는 방법을 알아보세요. 코드 예제가 포함된 단계별 가이드입니다.
weight: 12
url: /ko/net/pdf-processing/extract-images-from-pdf/
---

# PDF에서 이미지 추출

## 소개
이 튜토리얼에서는 .NET용 GroupDocs.Parser를 사용하여 PDF 문서에서 이미지를 추출하는 방법을 살펴보겠습니다. GroupDocs.Parser는 개발자가 .NET 환경에서 PDF, DOCX, PPTX 등을 포함한 다양한 문서 형식으로 작업할 수 있도록 하는 강력한 라이브러리입니다. 다음 단계를 따르면 PDF 파일에서 이미지를 쉽게 추출할 수 있습니다.
## 전제 조건
시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
- 시스템에 설치된 Visual Studio
- C# 프로그래밍에 대한 기본 지식
-  .NET 라이브러리용 GroupDocs.Parser(다운로드[여기](https://releases.groupdocs.com/parser/net/))

## 네임스페이스 가져오기
시작하려면 C# 코드 파일에 필요한 네임스페이스를 포함합니다.
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## 1단계: 파서 클래스 인스턴스 생성
 먼저,`Parser`샘플 PDF 파일의 경로를 제공하여 클래스를 제공합니다.
```csharp
// Parser 클래스의 인스턴스 생성
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // 이미지를 추출하는 코드가 여기에 들어갑니다.
}
```
## 2단계: PDF에서 이미지 추출
 내`using` 블록, 활용`GetImages` 의 방법`Parser` PDF 문서에서 이미지 모음을 검색하는 인스턴스입니다.
```csharp
// PDF에서 이미지 추출
IEnumerable<PageImageArea> images = parser.GetImages();
```
## 3단계: 이미지 저장 옵션 구성
추출된 이미지를 저장하는 방법을 지정하는 옵션을 정의합니다. 여기서는 이미지를 PNG 형식으로 저장하겠습니다.
```csharp
// 이미지를 PNG 형식으로 저장하는 옵션 만들기
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## 4단계: 추출된 이미지를 반복하고 저장
 다음의 각 이미지를 반복합니다.`images` 수집하여 순차적으로 PNG 파일로 저장합니다.
```csharp
int imageNumber = 0;
foreach (PageImageArea image in images)
{
    // 이미지를 PNG 파일로 저장
    image.Save(imageNumber.ToString() + ".png", options);
    imageNumber++;
}
```

## 결론
이 튜토리얼에서는 .NET용 GroupDocs.Parser를 사용하여 PDF 문서에서 이미지를 추출하는 방법을 시연했습니다. 다음 단계를 수행하면 이미지 추출 기능을 .NET 애플리케이션에 원활하게 통합할 수 있습니다.

## FAQ
### GroupDocs.Parser는 다른 문서 형식과 호환됩니까?
예, GroupDocs.Parser는 PDF, DOCX, XLSX, PPTX 등을 포함한 광범위한 문서 형식을 지원합니다.
### 이미지 추출 옵션을 수정할 수 있나요?
전적으로! GroupDocs.Parser는 이미지 형식, 품질 설정 등 이미지 추출을 사용자 정의할 수 있는 다양한 옵션을 제공합니다.
### GroupDocs.Parser를 상업적으로 사용하려면 라이센스가 필요합니까?
 예, 프로덕션 환경에서 GroupDocs.Parser를 사용하려면 상용 라이센스가 필요합니다. 더 알아보기[여기](https://purchase.groupdocs.com/buy).
### 추가 지원이나 지원은 어디서 찾을 수 있나요?
 GroupDocs.Parser를 방문하세요.[법정](https://forum.groupdocs.com/c/parser/17) 지역 사회의 지원과 지도를 위해.
### GroupDocs.Parser에 대한 무료 평가판이 있습니까?
 예, 다음에서 무료 평가판을 얻을 수 있습니다.[여기](https://releases.groupdocs.com/) GroupDocs.Parser의 기능을 탐색합니다.