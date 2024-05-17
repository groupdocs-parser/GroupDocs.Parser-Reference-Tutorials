---
title: Iterar pelos campos
linktitle: Iterar pelos campos
second_title: API GroupDocs.Parser .NET
description: Aprenda como extrair dados estruturados de documentos usando GroupDocs.Parser for .NET. Aprimore seus aplicativos .NET com recursos de extração de dados de documentos.
type: docs
weight: 11
url: /pt/net/data-extraction-from-templates/iterate-through-fields/
---
## Introdução
GroupDocs.Parser for .NET é uma biblioteca poderosa que permite aos desenvolvedores extrair dados de vários formatos de documentos como PDF, Microsoft Word, Excel e PowerPoint. Este tutorial irá guiá-lo através do processo de uso do GroupDocs.Parser para iterar pelos campos do documento e extrair dados específicos usando modelos. Ao final deste tutorial, você será capaz de extrair com eficiência dados estruturados de documentos em seus aplicativos .NET.
## Pré-requisitos
Antes de começarmos, certifique-se de ter os seguintes pré-requisitos configurados:
- Conhecimento básico de programação C#.
- Visual Studio instalado em sua máquina.
- Biblioteca GroupDocs.Parser for .NET instalada e referenciada em seu projeto.

## Importar namespaces
Para começar, adicione os namespaces necessários ao seu arquivo C#:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
Vamos dividir o processo em instruções passo a passo.
## Etapa 1: definir campos de modelo
Primeiro, defina os campos que deseja extrair do documento usando expressões regulares.
```csharp
// Defina um campo "preço"
TemplateField priceField = new TemplateField(
    new TemplateRegexPosition("\\$\\d+(.\\d+)?"),
    "Price");
// Defina um campo "e-mail"
TemplateField emailField = new TemplateField(
    new TemplateRegexPosition("[a-z]+\\@[a-z]+\\.[a-z]+"),
    "Email");
// Crie um modelo com campos definidos
Template template = new Template(new TemplateItem[] { priceField, emailField });
```
Nesta etapa definimos dois campos: um para extração de preços (identificados pelo cifrão e dígitos) e outro para extração de endereços de e-mail.
## Etapa 2: analisar o documento
 A seguir, use o`Parser` class para analisar o documento usando o modelo definido.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Analise o documento pelo modelo
    DocumentData data = parser.ParseByTemplate(template);
    // Iterar através dos dados extraídos
    for (int i = 0; i < data.Count; i++)
    {
        // Imprimir nome do campo
        Console.Write(data[i].Name + ": ");
        // Verifique se a área extraída é texto
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
 Aqui inicializamos o`Parser` com o caminho para seu documento de amostra e, em seguida, analise o documento usando o modelo definido. Em seguida, iteramos pelos dados extraídos e imprimimos os nomes dos campos junto com o texto extraído.
## Conclusão
Neste tutorial, exploramos como usar GroupDocs.Parser for .NET para extrair dados específicos de documentos usando modelos. Ao aproveitar expressões regulares e modelos, você pode extrair com eficiência informações estruturadas de vários formatos de documentos. Experimente diferentes modelos e tipos de documentos para atender às suas necessidades específicas de extração.

## Perguntas frequentes
### GroupDocs.Parser pode extrair dados de documentos digitalizados?
Sim, o GroupDocs.Parser pode extrair texto e metadados de documentos PDF digitalizados e pesquisáveis.
### O GroupDocs.Parser é compatível com aplicativos .NET Core?
Sim, GroupDocs.Parser oferece suporte a .NET Core junto com .NET Framework.
### Quais formatos de documento o GroupDocs.Parser suporta?
GroupDocs.Parser oferece suporte a uma ampla variedade de formatos, incluindo PDF, Microsoft Word, Excel, PowerPoint e muito mais.
### Como posso lidar com documentos grandes com GroupDocs.Parser?
GroupDocs.Parser oferece opções para extrair dados de páginas ou seções específicas de documentos grandes, garantindo um processamento eficiente.
### Posso usar GroupDocs.Parser apenas para extração de texto?
Sim, você pode extrair conteúdo de texto simples de documentos usando GroupDocs.Parser sem a necessidade de formatação complexa.