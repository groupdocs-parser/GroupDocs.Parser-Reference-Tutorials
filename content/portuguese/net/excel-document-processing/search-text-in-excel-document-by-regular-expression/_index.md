---
title: Pesquisar texto em documento Excel por expressão regular
linktitle: Pesquisar texto em documento Excel por expressão regular
second_title: API GroupDocs.Parser .NET
description: Aprenda como pesquisar texto em documentos Excel usando expressões regulares com GroupDocs.Parser for .NET. Execute pesquisas de texto avançadas com eficiência.
weight: 17
url: /pt/net/excel-document-processing/search-text-in-excel-document-by-regular-expression/
type: docs
---
# Pesquisar texto em documento Excel por expressão regular

## Introdução
Neste tutorial, exploraremos como utilizar GroupDocs.Parser for .NET para pesquisar padrões de texto específicos em documentos Excel usando expressões regulares. GroupDocs.Parser é uma biblioteca poderosa que permite aos desenvolvedores extrair texto e metadados de vários formatos de documentos, incluindo planilhas como Excel. Aproveitando expressões regulares, podemos realizar pesquisas de texto avançadas com eficiência.
## Pré-requisitos
Antes de começar, certifique-se de ter a seguinte configuração:
1. Visual Studio: instale o Visual Studio ou outro IDE compatível para desenvolvimento .NET.
2.  GroupDocs.Parser for .NET: Baixe e instale a biblioteca de[aqui](https://releases.groupdocs.com/parser/net/).
3. Arquivo Excel de amostra: prepare um arquivo Excel de amostra que contenha o texto que você deseja pesquisar.

## Importar namespaces
Primeiro, inclua os namespaces necessários para usar GroupDocs.Parser em seu projeto:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Etapa 1: crie uma instância da classe analisador
 Comece criando uma instância do`Parser` class, passando o caminho do seu documento Excel como parâmetro.
```csharp
// Crie uma instância da classe Parser
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // O código continua aqui...
}
```
## Etapa 2: realizar pesquisa de expressão regular
 Dentro do`using` bloco, execute uma pesquisa de texto usando um padrão de expressão regular.
```csharp
//Pesquise com uma expressão regular com correspondência de maiúsculas e minúsculas
IEnumerable<SearchResult> searchResults = parser.Search("\\sthe\\s", new SearchOptions(true, false, true));
```
- Explicação do padrão Regex:
  - `\\sthe\\s`: este padrão regex procura a palavra "o" (diferencia maiúsculas de minúsculas) cercada por espaços em branco.
## Etapa 3: iterar nos resultados da pesquisa
Em seguida, percorra os resultados da pesquisa para acessar cada ocorrência correspondente.
```csharp
// Iterar nos resultados da pesquisa
foreach (SearchResult result in searchResults)
{
    // Imprima a posição e o texto encontrado
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
- Saída:
  - Este loop imprimirá cada ocorrência do padrão de texto especificado junto com sua posição no documento.

## Conclusão
Neste tutorial, aprendemos como usar GroupDocs.Parser for .NET para realizar uma pesquisa de expressão regular em documentos Excel. Seguindo essas etapas, você pode integrar recursos avançados de pesquisa de texto em seus aplicativos .NET com eficiência.

## Perguntas frequentes
### O GroupDocs.Parser pode extrair dados de outros formatos de documentos além do Excel?
Sim, GroupDocs.Parser oferece suporte a vários formatos de documento, incluindo Word, PDF, PowerPoint e muito mais.
### Existe um teste gratuito disponível para GroupDocs.Parser?
 Sim, você pode baixar uma avaliação gratuita em[aqui](https://releases.groupdocs.com/).
### Onde posso encontrar suporte ou fazer perguntas sobre GroupDocs.Parser?
 Visite a[Fórum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17)para apoio e discussões.
### Como posso adquirir uma licença para GroupDocs.Parser?
 Você pode comprar uma licença de[aqui](https://purchase.groupdocs.com/buy).
### Posso obter uma licença temporária para fins de teste?
 Sim, você pode obter uma licença temporária[aqui](https://purchase.groupdocs.com/temporary-license/).