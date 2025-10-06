---
title: Extrair tabelas da página do documento
linktitle: Extrair tabelas da página do documento
second_title: API GroupDocs.Parser .NET
description: Aprenda como extrair tabelas de documentos programaticamente usando GroupDocs.Parser for .NET. Este tutorial abrangente fornece orientação passo a passo.
weight: 11
url: /pt/net/table-extraction/extract-tables-from-document-page/
type: docs
---
# Extrair tabelas da página do documento

## Introdução
Neste tutorial, exploraremos como extrair tabelas de uma página de documento usando GroupDocs.Parser for .NET. GroupDocs.Parser é uma biblioteca poderosa que permite aos desenvolvedores trabalhar com vários formatos de documentos, como PDF, DOCX, XLSX e muito mais. Ao aproveitar seus recursos, podemos extrair com eficiência dados estruturados, como tabelas, desses documentos, permitindo-nos manipular e analisar as informações de forma programática.
## Pré-requisitos
Antes de começar, certifique-se de ter o seguinte:
- Visual Studio instalado em sua máquina.
- Compreensão básica do desenvolvimento em C# e .NET.
-  Biblioteca GroupDocs.Parser para .NET. Você pode baixá-lo em[aqui](https://releases.groupdocs.com/parser/net/).
- Acesso a um documento modelo (PDF, DOCX, etc.) contendo tabelas para extração.

## Importar namespaces
Primeiro, comece importando os namespaces necessários em seu projeto C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using GroupDocs.Parser.Templates;
```
## Etapa 1: crie uma instância da classe analisador
 Instancie o`Parser` class fornecendo o caminho para seu documento de amostra:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //Seu código continua aqui...
}
```
## Etapa 2: Verifique o suporte para extração de tabela de documentos
Antes de prosseguir, verifique se o documento suporta extração de tabelas:
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document does not support table extraction.");
    return;
}
```
## Etapa 3: definir o layout da tabela
Defina o layout das tabelas a serem extraídas do documento. Especifique as larguras das colunas e as alturas das linhas de acordo com a estrutura do seu documento:
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },  // Larguras de coluna
    new double[] { 325, 340, 365, 395 });         // Alturas das linhas
```
## Etapa 4: configurar opções de extração de tabela
Crie opções para extração de tabela usando o layout especificado:
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Etapa 5: recuperar informações do documento
Obtenha informações sobre o documento, incluindo o número de páginas:
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Etapa 6: Iterar nas páginas do documento
Itere em cada página do documento para extrair tabelas:
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Extraia tabelas da página atual
    IEnumerable<PageTableArea> tables = parser.GetTables(pageIndex, options);
    // Iterar sobre tabelas extraídas
    foreach (PageTableArea table in tables)
    {
        // Iterar nas linhas da tabela
        for (int row = 0; row < table.RowCount; row++)
        {
            // Iterar nas colunas da tabela
            for (int column = 0; column < table.ColumnCount; column++)
            {
                // Obtenha a célula da tabela
                PageTableAreaCell cell = table[row, column];
                if (cell != null)
                {
                    // Imprima o texto da célula da tabela
                    Console.Write(cell.Text);
                    Console.Write(" | ");
                }
            }
            Console.WriteLine();
        }
        Console.WriteLine();
    }
}
```

## Conclusão
Neste tutorial, abordamos o processo de extração de tabelas de páginas de documentos usando GroupDocs.Parser for .NET. Seguindo as etapas fornecidas, você pode integrar perfeitamente a funcionalidade de extração de tabelas em seus aplicativos .NET, permitindo o manuseio e a manipulação eficientes de dados estruturados em documentos.

## Perguntas frequentes
### O GroupDocs.Parser pode extrair tabelas de todos os tipos de documentos?
GroupDocs.Parser oferece suporte a vários formatos de documentos como PDF, DOCX, XLSX e muito mais, permitindo a extração de tabelas de tipos de arquivos compatíveis.
### O GroupDocs.Parser for .NET é adequado para processamento de documentos em grande escala?
Sim, o GroupDocs.Parser foi projetado para lidar com documentos grandes com eficiência, tornando-o adequado para processar conjuntos de dados extensos.
### O GroupDocs.Parser preserva a formatação durante a extração da tabela?
Sim, GroupDocs.Parser retém detalhes de formatação, como bordas de células, estilos de texto e alinhamentos durante a extração da tabela.
### Posso extrair tabelas específicas com base em critérios de conteúdo?
GroupDocs.Parser oferece opções flexíveis para direcionar tabelas específicas com base em modelos de layout ou condições de conteúdo para extração.
### O GroupDocs.Parser é compatível com o .NET Core?
Sim, GroupDocs.Parser é compatível com ambientes .NET Framework e .NET Core.