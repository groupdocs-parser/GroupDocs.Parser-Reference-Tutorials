---
title: Pesquisar texto por expressão regular (Regex)
linktitle: Pesquisar texto por expressão regular (Regex)
second_title: API GroupDocs.Parser .NET
description: Aprenda como pesquisar texto usando expressões regulares em documentos usando GroupDocs.Parser for .NET. Extraia conteúdo específico sem esforço.
weight: 23
url: /pt/net/text-extraction/search-text-by-regex/
---

# Pesquisar texto por expressão regular (Regex)

## Introdução
Neste tutorial, nos aprofundaremos no uso do GroupDocs.Parser for .NET para pesquisar texto por expressão regular (Regex) em documentos. GroupDocs.Parser é uma biblioteca poderosa que permite aos desenvolvedores extrair texto e metadados de vários formatos de arquivo, como PDF, DOCX, XLSX e muito mais. A pesquisa de texto usando expressões regulares é particularmente útil para encontrar padrões ou conteúdo específico em documentos de forma eficiente.
## Pré-requisitos
Antes de mergulhar neste tutorial, certifique-se de ter o seguinte:
1. Visual Studio: instale o IDE do Visual Studio para desenvolvimento .NET.
2.  GroupDocs.Parser for .NET: Baixe e instale GroupDocs.Parser for .NET em[aqui](https://releases.groupdocs.com/parser/net/).
3. Arquivo de amostra: prepare um documento de amostra (PDF, DOCX, etc.) para testar a funcionalidade de pesquisa.

## Importar namespaces
Primeiro, comece incluindo os namespaces necessários em seu código C#:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Etapa 1: crie uma instância da classe analisador
 Instancie o`Parser` class fornecendo o caminho para seu arquivo de amostra:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // O código vai aqui
}
```
 Substituir`"YourSampleFile.pdf"` com o caminho para o seu arquivo real.
## Etapa 2: pesquisa usando expressão regular
Defina e execute a pesquisa usando um padrão de expressão regular. Por exemplo, para encontrar sequências numéricas (por exemplo, inteiros) dentro do documento:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("[0-9]+", new SearchOptions(true, false, true));
```
 Neste exemplo,`[0-9]+` é um padrão de expressão regular que corresponde a um ou mais dígitos.
## Etapa 3: verifique o suporte de pesquisa
Verifique se a operação de pesquisa é suportada para o tipo de documento:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported");
    return;
}
```
## Etapa 4: iterar nos resultados da pesquisa
Itere pelos resultados da pesquisa e processe cada correspondência:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Este loop imprimirá a posição e o texto correspondente encontrado no documento.

## Conclusão
Concluindo, aproveitar o GroupDocs.Parser for .NET permite uma pesquisa de texto eficiente usando expressões regulares em vários formatos de documentos. Seguindo este guia, os desenvolvedores podem integrar perfeitamente a análise de documentos e a extração de texto baseada em regex em seus aplicativos .NET.

## Perguntas frequentes
### GroupDocs.Parser pode pesquisar em documentos criptografados?
Não, o GroupDocs.Parser não pode pesquisar documentos criptografados ou protegidos por senha.
### O GroupDocs.Parser oferece suporte a OCR (reconhecimento óptico de caracteres)?
Não, GroupDocs.Parser não executa OCR. Baseia-se na extração de texto da estrutura interna do documento.
### Posso procurar padrões complexos usando expressões regulares?
Sim, GroupDocs.Parser oferece suporte a expressões regulares completas, permitindo correspondência de padrões complexos em documentos.
### Quais formatos de documento são suportados para extração de texto?
GroupDocs.Parser oferece suporte a uma ampla variedade de formatos, incluindo PDF, DOCX, XLSX, PPTX e muito mais.
### O GroupDocs.Parser é compatível com o .NET Core?
Sim, GroupDocs.Parser é compatível com .NET Core para desenvolvimento de plataforma cruzada.