---
title: Extraia texto da página no modo Raw
linktitle: Extraia texto da página no modo Raw
second_title: API GroupDocs.Parser .NET
description: Aprenda a extração eficiente de texto de páginas de documentos usando Groupdocs.Parser for .NET neste tutorial abrangente.
type: docs
weight: 17
url: /pt/net/text-extraction/extract-text-from-page-in-raw-mode/
---
## Introdução
Neste tutorial, você aprenderá como usar Groupdocs.Parser for .NET para extrair texto de páginas de documentos em modo bruto. Esta biblioteca fornece ferramentas eficientes para analisar e extrair conteúdo de vários formatos de arquivo, permitindo que os desenvolvedores incorporem a extração de texto de documentos em seus aplicativos .NET.
## Pré-requisitos
Antes de começar, certifique-se de ter os seguintes pré-requisitos:
- Conhecimento básico de programação C# e .NET
- Visual Studio instalado em sua máquina
- Acesso à biblioteca Groupdocs.Parser para .NET
- Exemplo de arquivo de documento para teste

## Importar namespaces
Comece incluindo os namespaces necessários em seu projeto C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Etapa 1: inicializar o analisador
 Primeiro, crie uma instância do`Parser` class fornecendo o caminho para seu arquivo de documento de amostra.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Seu código aqui
}
```
## Etapa 2: recuperar informações do documento
 Recuperar informações sobre o documento usando`GetDocumentInfo()` método.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## Etapa 3: iterar nas páginas e extrair texto
Itere em cada página do documento e extraia o conteúdo do texto.
```csharp
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Extraia o texto da página
    using (TextReader reader = parser.GetText(p, new TextOptions(true)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Conclusão
Agora você aprendeu como usar Groupdocs.Parser for .NET para extrair texto de páginas de documentos em modo bruto. Este pode ser um recurso poderoso para aplicativos que precisam analisar ou processar conteúdo de texto de vários formatos de arquivo.

## Perguntas frequentes
### O Groupdocs.Parser for .NET é compatível com todos os formatos de arquivo?
Groupdocs.Parser oferece suporte a uma ampla variedade de formatos de arquivo, incluindo PDF, DOCX, XLSX, PPTX, EPUB e muito mais.
### Posso extrair metadados junto com texto usando esta biblioteca?
Sim, Groupdocs.Parser permite extrair texto e metadados de documentos.
### Existe uma versão de teste disponível para teste?
 Sim, você pode baixar uma versão de avaliação gratuita em[aqui](https://releases.groupdocs.com/).
### Como posso obter suporte técnico para Groupdocs.Parser?
 Para assistência técnica, visite o[Fórum Groupdocs.Parser](https://forum.groupdocs.com/c/parser/17).
### Onde posso adquirir uma licença do Groupdocs.Parser for .NET?
 Você pode comprar uma licença[aqui](https://purchase.groupdocs.com/buy).