---
title: Extrair tabelas do documento
linktitle: Extrair tabelas do documento
second_title: API GroupDocs.Parser .NET
description: Aprenda como extrair tabelas de documentos usando Groupdocs.Parser for .NET. Acompanhe para obter um guia detalhado sobre como integrar essa funcionalidade.
type: docs
weight: 10
url: /pt/net/table-extraction/extract-tables-from-document/
---
## Introdução
Groupdocs.Parser for .NET é uma biblioteca abrangente que facilita a análise de documentos, permitindo extrair informações valiosas como tabelas, texto, metadados e muito mais de documentos. Neste tutorial, nos concentramos especificamente na extração de tabelas de documentos usando a API Groupdocs.Parser.
## Pré-requisitos
Antes de começarmos, certifique-se de ter o seguinte:
- Visual Studio instalado em seu sistema.
- .NET Framework ou .NET Core instalado.
- Conhecimento básico de programação C#.

## Importar namespaces
Primeiro, você precisa importar os namespaces necessários para acessar as classes e métodos Groupdocs.Parser.
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
 Inicialize uma nova instância do`Parser` class fornecendo o caminho para seu documento de amostra.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Seu código vai aqui
}
```
## Etapa 2: verifique o suporte para extração de tabela
 Verifique se o documento suporta extração de tabela usando o`Features` propriedade do`Parser` aula.
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document doesn't support table extraction.");
    return;
}
```
## Etapa 3: definir o layout da tabela
Defina o layout das tabelas que você deseja extrair usando`TemplateTableLayout`. Especifique as larguras das colunas e as alturas das linhas com base na estrutura do seu documento.
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },
    new double[] { 325, 340, 365, 395 });
```
## Etapa 4: definir opções de extração de tabela
 Criar`PageTableAreaOptions` com o layout definido para especificar como as tabelas devem ser extraídas.
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Etapa 5: extrair tabelas
 Utilize o`GetTables` método do`Parser` classe para extrair tabelas do documento com base nas opções especificadas.
```csharp
IEnumerable<PageTableArea> tables = parser.GetTables(options);
```
## Etapa 6: Iterar e acessar os dados da tabela
Itere pelas tabelas extraídas e suas respectivas linhas e colunas para acessar os dados da célula.
```csharp
foreach (PageTableArea table in tables)
{
    for (int row = 0; row < table.RowCount; row++)
    {
        for (int column = 0; column < table.ColumnCount; column++)
        {
            PageTableAreaCell cell = table[row, column];
            if (cell != null)
            {
                Console.Write(cell.Text);
                Console.Write(" | ");
            }
        }
        Console.WriteLine();
    }
    Console.WriteLine();
}
```
## Conclusão
Neste tutorial, abordamos como usar Groupdocs.Parser for .NET para extrair tabelas de documentos com eficiência. Aproveitando os recursos desta biblioteca, você pode integrar perfeitamente a extração de tabelas em seus aplicativos .NET.

## Perguntas frequentes
### O Groupdocs.Parser pode lidar com diferentes formatos de documentos?
Sim, Groupdocs.Parser oferece suporte a uma ampla variedade de formatos de documentos, incluindo DOCX, PDF, XLSX e muito mais.
### Existe uma versão de teste disponível para Groupdocs.Parser for .NET?
 Sim, você pode baixar uma avaliação gratuita em[aqui](https://releases.groupdocs.com/).
### Como posso obter suporte para consultas relacionadas ao Groupdocs.Parser?
 Você pode visitar o[Fórum Groupdocs.Parser](https://forum.groupdocs.com/c/parser/17) para assistência.
### Onde posso comprar uma licença para Groupdocs.Parser?
 Você pode comprar uma licença de[aqui](https://purchase.groupdocs.com/buy).
### Como posso obter uma licença temporária para efeitos de avaliação?
 Você pode obter uma licença temporária[aqui](https://purchase.groupdocs.com/temporary-license/).