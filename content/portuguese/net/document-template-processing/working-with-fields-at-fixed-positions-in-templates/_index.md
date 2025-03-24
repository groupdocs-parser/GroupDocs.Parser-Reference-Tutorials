---
title: Trabalhando com campos em posições fixas em modelos
linktitle: Trabalhando com campos em posições fixas em modelos
second_title: API GroupDocs.Parser .NET
description: Aprenda como extrair dados de documentos usando GroupDocs.Parser for .NET. Tutorial abrangente com exemplos de código.
weight: 11
url: /pt/net/document-template-processing/working-with-fields-at-fixed-positions-in-templates/
---

# Trabalhando com campos em posições fixas em modelos

## Introdução
Neste tutorial, exploraremos como trabalhar com campos em posições fixas em modelos usando GroupDocs.Parser for .NET. GroupDocs.Parser é uma poderosa biblioteca de análise de documentos que permite aos desenvolvedores extrair dados de vários formatos de documentos, como PDF, Word, Excel e muito mais. Especificamente, nos concentraremos na definição e utilização de campos de modelo para extrair informações direcionadas com base em suas posições fixas.
## Pré-requisitos
Antes de começarmos, certifique-se de ter o seguinte:
- Compreensão básica do desenvolvimento em C# e .NET.
- Visual Studio instalado em seu sistema.
- Biblioteca GroupDocs.Parser para .NET instalada. Você pode baixá-lo em[aqui](https://releases.groupdocs.com/parser/net/).
- Exemplos de arquivos de documentos para teste.

## Importar namespaces
Comece incluindo os namespaces necessários em seu projeto C#:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Etapa 1: definir um campo de modelo
Primeiro, defina um campo com uma posição fixa dentro de um modelo. Este campo representa a área da qual os dados serão extraídos.
```csharp
TemplateField field = new TemplateField(
    new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))),
    "FromCompany");
```
Aqui:
- `Rectangle` especifica a posição e o tamanho do campo.
- `Point(35, 135)` representa as coordenadas do canto superior esquerdo.
- `Size(100, 10)` define a largura e a altura do campo.
- `"FromCompany"` é o nome atribuído a este campo.
## Etapa 2: crie um modelo
Construa um modelo usando o campo definido.
```csharp
Template template = new Template(new TemplateItem[] { field });
```
 O`Template` objeto contém os campos definidos.
## Etapa 3: analisar o documento usando o modelo
 Instancie o`Parser` class com o caminho do documento de destino e, em seguida, analise o documento usando o modelo criado.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    DocumentData data = parser.ParseByTemplate(template);
    // Iterar através dos dados extraídos
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
Aqui:
- `Parser` é inicializado com o caminho do arquivo do documento de amostra.
- `ParseByTemplate` método é usado para extrair dados com base no modelo fornecido.
-  Os dados extraídos são acessados usando`DocumentData`onde cada item corresponde a um campo definido.

## Conclusão
Neste tutorial, abordamos o processo de trabalhar com campos em posições fixas em modelos usando GroupDocs.Parser for .NET. Ao definir modelos com posições de campo específicas, os desenvolvedores podem extrair com precisão dados direcionados de vários formatos de documentos.

## Perguntas frequentes
### O GroupDocs.Parser é compatível com todos os formatos de documento?
 GroupDocs.Parser oferece suporte a uma ampla variedade de formatos de arquivo, incluindo PDF, Microsoft Word, Excel, PowerPoint e muito mais. Consulte o[documentação](https://tutorials.groupdocs.com/parser/net/) para obter uma lista detalhada.
### Como posso obter uma licença temporária para GroupDocs.Parser?
 Você pode obter uma licença temporária para fins de teste em[aqui](https://purchase.groupdocs.com/temporary-license/).
### Onde posso encontrar suporte para GroupDocs.Parser?
 Para assistência técnica e discussões, visite o[Fórum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).
### Posso experimentar o GroupDocs.Parser antes de comprar?
 Sim, você pode explorar a biblioteca com uma avaliação gratuita disponível[aqui](https://releases.groupdocs.com/).
### Como posso adquirir uma licença para GroupDocs.Parser?
 Para comprar uma licença, visite o[página de compra](https://purchase.groupdocs.com/buy).