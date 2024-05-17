---
title: Extraia texto da página em PDF no modo Raw
linktitle: Extraia texto da página em PDF no modo Raw
second_title: API GroupDocs.Parser .NET
description: Extraia texto de PDFs usando GroupDocs.Parser em C#. Aprenda a extração eficiente de texto em PDF com esta poderosa biblioteca .NET.
type: docs
weight: 16
url: /pt/net/pdf-processing/extract-text-from-page-in-pdf-in-raw-mode/
---
## Introdução
Neste tutorial, exploraremos como usar GroupDocs.Parser for .NET para extrair texto de páginas em documentos PDF usando o modo bruto. GroupDocs.Parser é uma ferramenta poderosa que permite aos desenvolvedores trabalhar com vários formatos de documentos de forma programática.
## Pré-requisitos
Antes de iniciar este tutorial, certifique-se de ter o seguinte:
- Visual Studio instalado em sua máquina.
- Conhecimento básico de programação C#.
- Biblioteca GroupDocs.Parser for .NET, que você pode[baixe aqui](https://releases.groupdocs.com/parser/net/).
- Um arquivo PDF de amostra para fins de teste.

## Importar namespaces
Primeiro, certifique-se de importar os namespaces necessários em seu projeto C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Etapa 1: crie uma instância da classe analisador
 Para começar, instancie o`Parser`class fornecendo o caminho para seu arquivo PDF de amostra.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Seu código vai aqui
}
```
## Etapa 2: obter informações do documento e iterar nas páginas
Em seguida, recupere as informações do documento e repita cada página para extrair o texto.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Seu código para extração de texto vai aqui
}
```
## Etapa 3: Extraia o texto de cada página
 Dentro do loop, use o`GetText` método para extrair texto de cada página e imprimi-lo.
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## Conclusão
 Neste tutorial, aprendemos como extrair texto de páginas PDF em modo bruto usando GroupDocs.Parser for .NET. Este processo envolve a criação de um`Parser` por exemplo, obter informações do documento, iterar cada página e extrair texto usando o`GetText` método.

## Perguntas frequentes
### O que é GroupDocs.Parser para .NET?
GroupDocs.Parser for .NET é uma API de análise de documentos que permite aos desenvolvedores extrair texto, metadados e outras informações de vários formatos de arquivo de forma programática.
### Como faço o download do GroupDocs.Parser para .NET?
 Você pode baixar a biblioteca do[Site GroupDocs](https://releases.groupdocs.com/parser/net/).
### Existe um teste gratuito disponível?
 Sim, você pode acessar uma avaliação gratuita do GroupDocs.Parser for .NET em[aqui](https://releases.groupdocs.com/).
### Onde posso encontrar suporte para GroupDocs.Parser for .NET?
 Para assistência técnica e apoio comunitário, visite o[Fórum GroupDocs](https://forum.groupdocs.com/c/parser/17).
### Como posso adquirir uma licença do GroupDocs.Parser for .NET?
 Você pode comprar uma licença no[página de compra](https://purchase.groupdocs.com/buy) ou adquirir uma licença temporária[aqui](https://purchase.groupdocs.com/temporary-license/).