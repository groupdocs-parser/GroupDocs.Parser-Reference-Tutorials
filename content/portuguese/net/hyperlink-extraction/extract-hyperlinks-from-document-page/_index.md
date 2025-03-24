---
title: Extraia hiperlinks da página do documento
linktitle: Extraia hiperlinks da página do documento
second_title: API GroupDocs.Parser .NET
description: Aprenda como extrair hiperlinks de documentos usando GroupDocs.Parser for .NET. Guia passo a passo para extração de hiperlink em C#.
weight: 11
url: /pt/net/hyperlink-extraction/extract-hyperlinks-from-document-page/
---
## Introdução
Neste tutorial, exploraremos como usar GroupDocs.Parser for .NET para extrair hiperlinks de documentos passo a passo. GroupDocs.Parser é uma biblioteca poderosa que permite aos desenvolvedores analisar vários formatos de documentos e extrair texto, metadados e outros elementos.
## Pré-requisitos
Antes de começarmos, certifique-se de ter o seguinte:
- Visual Studio: instale o Visual Studio em sua máquina de desenvolvimento.
-  Biblioteca GroupDocs.Parser: baixe e faça referência à biblioteca GroupDocs.Parser. Você pode obtê-lo de[aqui](https://releases.groupdocs.com/parser/net/).
- Documento de amostra: Prepare um documento de amostra (por exemplo, DOCX, PDF) contendo hiperlinks para teste.

## Importar namespaces
Primeiro, inclua os namespaces necessários para usar as funcionalidades do GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Etapa 1: criar uma instância do analisador
 Instancie o`Parser` class pelo caminho para seu documento de amostra.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // O código vai aqui...
}
```
## Etapa 2: verifique o suporte para extração de hiperlink
Certifique-se de que o documento suporte a extração de hiperlink antes de continuar.
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
## Etapa 3: recuperar informações do documento
Obtenha informações básicas sobre o documento e verifique se ele contém páginas.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Etapa 4: Iterar nas páginas do documento
Itere em cada página do documento.
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Extraia hiperlinks da página atual
    IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks(pageIndex);
    // Iterar sobre hiperlinks extraídos
    foreach (PageHyperlinkArea hyperlink in hyperlinks)
    {
        Console.WriteLine($"Hyperlink Text: {hyperlink.Text}");
        Console.WriteLine($"Hyperlink URL: {hyperlink.Url}");
        Console.WriteLine(); // Linha em branco para facilitar a leitura
    }
}
```

## Conclusão
Neste tutorial, cobrimos os fundamentos do uso do GroupDocs.Parser for .NET para extrair hiperlinks de documentos. Você aprendeu como inicializar o analisador, verificar o suporte de hiperlinks, recuperar informações do documento e iterar pelas páginas do documento para extrair hiperlinks com eficiência.

## Perguntas frequentes
### Posso extrair hiperlinks de diferentes formatos de documentos?
Sim, GroupDocs.Parser suporta vários formatos como DOCX, PDF, PPTX, etc., para extração de hiperlinks.
### O GroupDocs.Parser é fácil de integrar em aplicativos .NET existentes?
Com certeza, GroupDocs.Parser foi projetado para ser simples e pode ser facilmente integrado aos seus projetos .NET.
### Posso extrair outros metadados junto com hiperlinks usando GroupDocs.Parser?
Sim, além de hiperlinks, você pode extrair textos, imagens e metadados de documentos usando esta biblioteca.
### O GroupDocs.Parser lida com documentos criptografados ou protegidos por senha?
GroupDocs.Parser pode analisar documentos protegidos por senha se a senha for fornecida.
### Existe uma versão de teste disponível para testar antes de comprar?
 Sim, você pode baixar uma versão de avaliação gratuita[aqui](https://releases.groupdocs.com/).