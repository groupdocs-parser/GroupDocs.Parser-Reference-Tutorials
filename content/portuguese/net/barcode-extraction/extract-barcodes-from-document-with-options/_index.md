---
title: Extraia códigos de barras do documento com opções
linktitle: Extraia códigos de barras do documento com opções
second_title: API GroupDocs.Parser .NET
description: Aprenda como extrair códigos de barras de documentos usando GroupDocs.Parser for .NET. Tutorial abrangente com exemplos de código e perguntas frequentes.
weight: 14
url: /pt/net/barcode-extraction/extract-barcodes-from-document-with-options/
type: docs
---
# Extraia códigos de barras do documento com opções

## Introdução
Neste tutorial, percorreremos o processo de extração de códigos de barras de um documento usando GroupDocs.Parser for .NET. GroupDocs.Parser é uma biblioteca poderosa que permite extrair texto, metadados e códigos de barras de vários formatos de documentos, como PDF, Microsoft Word, Excel e muito mais.
## Pré-requisitos
Antes de começar, certifique-se de ter os seguintes pré-requisitos em vigor:
1. Ambiente de desenvolvimento: certifique-se de ter o Visual Studio instalado em sua máquina.
2.  Biblioteca GroupDocs.Parser: Baixe e instale a biblioteca GroupDocs.Parser for .NET em[aqui](https://releases.groupdocs.com/parser/net/).
3. Documento de amostra: Prepare um documento de amostra (por exemplo, PDF, DOCX) contendo códigos de barras para extração.

## Importar namespaces
Primeiro, você precisa importar os namespaces necessários para seu projeto C# para utilizar as funcionalidades GroupDocs.Parser.
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using System;
using System.Collections.Generic;
```
## Etapa 1: crie uma instância da classe analisador
 Para começar, crie uma instância do`Parser` class passando o caminho para seu documento de amostra.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Código a ser adicionado nas próximas etapas
}
```
## Etapa 2: verifique o suporte para extração de código de barras
 A seguir, verifique se o documento suporta extração de código de barras usando o`Features` propriedade do`Parser` instância.
```csharp
if (!parser.Features.Barcodes)
{
    Console.WriteLine("Document doesn't support barcode extraction.");
    return;
}
```
## Etapa 3: definir opções de extração de código de barras
 Agora, especifique as opções para extração de código de barras usando`BarcodeOptions`. Você pode definir parâmetros como modos de qualidade e tipos de código de barras.
```csharp
BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```
## Etapa 4: extrair códigos de barras do documento
 Use o`GetBarcodes` método do`Parser` classe para extrair códigos de barras com base nas opções definidas.
```csharp
IEnumerable<PageBarcodeArea> barcodes = parser.GetBarcodes(options);
```
## Etapa 5: iterar e exibir códigos de barras extraídos
Por fim, percorra os códigos de barras extraídos e exiba o índice e os valores da página.
```csharp
foreach (PageBarcodeArea barcode in barcodes)
{
    Console.WriteLine("Page: " + barcode.Page.Index.ToString());
    Console.WriteLine("Value: " + barcode.Value);
}
```

## Conclusão
 Neste tutorial, aprendemos como extrair códigos de barras de um documento usando GroupDocs.Parser for .NET. Este processo envolve a criação de um`Parser` por exemplo, definindo opções de extração e iterando pelos códigos de barras extraídos. GroupDocs.Parser simplifica a tarefa de extração de código de barras de vários formatos de documentos, permitindo o processamento eficiente de documentos em seus aplicativos .NET.

## Perguntas frequentes
### O GroupDocs.Parser pode extrair códigos de barras de documentos PDF?
Sim, GroupDocs.Parser suporta extração de código de barras de documentos PDF junto com outros formatos como DOCX, XLSX, etc.
### Quais tipos de código de barras o GroupDocs.Parser suporta?
GroupDocs.Parser oferece suporte a vários tipos de códigos de barras, incluindo códigos QR, Código 39, Código 128 e muito mais.
### O GroupDocs.Parser requer uma licença para uso comercial?
 Sim, é necessária uma licença válida para uso comercial. Você pode obter uma licença de[aqui](https://purchase.groupdocs.com/buy).
### O GroupDocs.Parser é adequado para processamento em lote de documentos?
Sim, o GroupDocs.Parser pode lidar com eficiência com o processamento em lote de documentos para extração de texto, recuperação de metadados e extração de código de barras.
### Onde posso encontrar suporte técnico para GroupDocs.Parser?
 Você pode obter suporte técnico ou tirar dúvidas no[Fórum GroupDocs](https://forum.groupdocs.com/c/parser/17).