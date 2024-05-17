---
title: Extraia texto formatado da página do documento
linktitle: Extraia texto formatado da página do documento
second_title: API GroupDocs.Parser .NET
description: Extraia texto formatado de páginas de documentos usando GroupDocs.Parser for .NET. Solução de extração de texto eficiente e confiável.
type: docs
weight: 11
url: /pt/net/formatted-text-extraction/extract-formatted-text-from-document-page/
---
## Introdução
Neste tutorial, orientaremos você no processo de extração de texto formatado de páginas de documentos usando GroupDocs.Parser for .NET. Esta biblioteca permite analisar e extrair texto com eficiência de vários formatos de documentos, como PDF, Word, Excel e muito mais.
## Pré-requisitos
Antes de começarmos, certifique-se de ter o seguinte:
- Visual Studio instalado em seu sistema.
- Conhecimento básico de programação C#.
-  Biblioteca GroupDocs.Parser para .NET. Você pode baixá-lo[aqui](https://releases.groupdocs.com/parser/net/).

## Importar namespaces
Primeiro, comece importando os namespaces necessários para o seu projeto C#.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Etapa 1: crie uma instância da classe analisador
 Comece criando uma instância do`Parser` class fornecendo o caminho para seu arquivo de amostra.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // O código irá aqui
}
```
## Etapa 2: verifique se a extração de texto formatado é compatível
Antes de prosseguir com a extração de texto, verifique se o documento suporta extração de texto formatado.
```csharp
if (!parser.Features.FormattedText)
{
    Console.WriteLine("Document does not support formatted text extraction.");
    return;
}
```
## Etapa 3: Obtenha informações do documento
Recuperar informações sobre o documento, como o número de páginas.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Etapa 4: iterar nas páginas do documento e extrair o texto formatado
Itere cada página do documento e extraia o texto formatado usando opções específicas (por exemplo, formato Markdown).
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    
    using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Markdown)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Conclusão
Agora você sabe como extrair texto formatado de páginas de documentos usando GroupDocs.Parser for .NET. Esta biblioteca fornece uma solução poderosa e fácil de usar para extração de texto de vários formatos de arquivo.

## Perguntas frequentes
### O GroupDocs.Parser pode lidar com diferentes formatos de arquivo?
Sim, GroupDocs.Parser oferece suporte a uma ampla variedade de formatos de documentos, incluindo PDF, DOCX, XLSX, PPTX e muito mais.
### O GroupDocs.Parser é compatível com o .NET Core?
Sim, GroupDocs.Parser oferece suporte a .NET Core e .NET Framework.
### O GroupDocs.Parser preserva a formatação do texto durante a extração?
Sim, GroupDocs.Parser pode reter formatação como estilos e fontes ao extrair texto.
### Posso extrair imagens e metadados usando GroupDocs.Parser?
Sim, GroupDocs.Parser permite a extração de imagens, metadados e texto de documentos.
### Como posso obter suporte para GroupDocs.Parser?
 Você pode obter suporte do[Fórum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).