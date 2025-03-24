---
title: Extraia hiperlinks do documento
linktitle: Extraia hiperlinks do documento
second_title: API GroupDocs.Parser .NET
description: Aprenda como extrair hiperlinks de documentos usando GroupDocs.Parser for .NET. Aprimore seus aplicativos C# com este guia simples.
weight: 10
url: /pt/net/hyperlink-extraction/extract-hyperlinks-from-document/
---

# Extraia hiperlinks do documento

## Introdução
Neste tutorial, nos aprofundaremos nos poderosos recursos do GroupDocs.Parser for .NET, uma biblioteca versátil que permite aos desenvolvedores extrair hiperlinks de documentos com facilidade. A extração de hiperlinks é um requisito comum no processamento de documentos, especialmente ao lidar com arquivos baseados em texto, como PDFs ou documentos do Word. Ao usar GroupDocs.Parser, você pode identificar e extrair com eficiência hiperlinks junto com seus URLs associados de vários formatos de documento.
## Pré-requisitos
Antes de prosseguir com este tutorial, certifique-se de ter os seguintes pré-requisitos:
- Conhecimento básico de programação C#
- Visual Studio instalado em seu sistema
-  Biblioteca GroupDocs.Parser for .NET, que pode ser baixada[aqui](https://releases.groupdocs.com/parser/net/)
## Importar namespaces
Para começar, importe os namespaces necessários para o seu projeto C#:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```

Agora, vamos dividir cada exemplo em várias etapas para guiá-lo através do processo de extração de hiperlink usando GroupDocs.Parser for .NET:
## Etapa 1: crie uma instância da classe analisador
 Primeiro, instancie o`Parser` class fornecendo o caminho para seu documento de amostra:
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Seu código para extração de hiperlink irá aqui
}
```
 Substituir`"YourSampleFile.docx"` com o caminho para o seu documento de destino.
## Etapa 2: verifique o suporte para extração de hiperlink
Antes de extrair hiperlinks, é importante verificar se o formato do documento suporta a extração de hiperlinks:
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
Esta etapa garante que a extração do hiperlink seja viável para o documento fornecido.
## Etapa 3: extrair hiperlinks
 Prossiga para extrair hiperlinks do documento usando o`GetHyperlinks()` método:
```csharp
IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks();
```
 Esta linha recupera uma coleção de`PageHyperlinkArea` objetos contendo informações de hiperlink.
## Etapa 4: iterar sobre hiperlinks extraídos
Itere pela coleção de hiperlinks extraídos e recupere seu texto e URL:
```csharp
foreach (PageHyperlinkArea hyperlink in hyperlinks)
{
    // Imprima o texto do hiperlink
    Console.WriteLine(hyperlink.Text);
    
    // Imprima o URL do hiperlink
    Console.WriteLine(hyperlink.Url);
    Console.WriteLine(); // Adiciona uma linha em branco para facilitar a leitura
}
```
Ao iterar sobre o`hyperlinks` coleção, você pode acessar e imprimir o texto e URL de cada hiperlink.
## Conclusão
Neste tutorial, exploramos como extrair hiperlinks de documentos usando GroupDocs.Parser for .NET. Aproveitando as funcionalidades fornecidas por esta biblioteca, os desenvolvedores podem integrar facilmente recursos de extração de hiperlinks em seus aplicativos C#.

## Perguntas frequentes
### O GroupDocs.Parser pode lidar com a extração de hiperlinks de vários formatos de documentos?
Sim, GroupDocs.Parser oferece suporte à extração de hiperlinks de uma ampla variedade de formatos de arquivo, incluindo PDF, Word, Excel, PowerPoint e muito mais.
### Existe um teste gratuito disponível para GroupDocs.Parser?
 Sim, você pode acessar uma avaliação gratuita do GroupDocs.Parser[aqui](https://releases.groupdocs.com/).
### Onde posso encontrar documentação para GroupDocs.Parser?
 Documentação detalhada para GroupDocs.Parser pode ser encontrada[aqui](https://tutorials.groupdocs.com/parser/net/).
### Como posso obter uma licença temporária para GroupDocs.Parser?
 Você pode obter uma licença temporária para GroupDocs.Parser[aqui](https://purchase.groupdocs.com/temporary-license/).
### O GroupDocs oferece suporte para solução de problemas?
 Sim, você pode buscar suporte e assistência para solução de problemas no GroupDocs[fórum](https://forum.groupdocs.com/c/parser/17).