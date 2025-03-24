---
title: Obter campo por nome
linktitle: Obter campo por nome
second_title: API GroupDocs.Parser .NET
description: Aprenda como extrair campos de dados específicos de documentos usando GroupDocs.Parser for .NET. Guia passo a passo com exemplos de código.
weight: 10
url: /pt/net/data-extraction-from-templates/get-field-by-name/
---
## Introdução
Neste tutorial, exploraremos como aproveitar o GroupDocs.Parser for .NET para extrair campos de dados específicos, como preços e e-mails de documentos. Esta poderosa biblioteca simplifica as tarefas de análise de documentos, tornando-a ideal para diversas necessidades de extração de dados.
## Pré-requisitos
Antes de mergulhar no tutorial, certifique-se de ter os seguintes pré-requisitos:
- Visual Studio instalado em seu sistema.
- Conhecimento básico de programação C#.
-  Baixe e instale GroupDocs.Parser para .NET em[esse link](https://releases.groupdocs.com/parser/net/).

## Importar namespaces
Comece importando os namespaces necessários para seu projeto C#:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Etapa 1: definir campos de modelo
Primeiro, definiremos os campos do modelo para extração de dados. Neste exemplo, criaremos campos para capturar preços e emails.
```csharp
// Defina um campo "preço"
TemplateField priceField = new TemplateField(
    new TemplateRegexPosition("\\$\\d+(.\\d+)?"),
    "Price");
// Defina um campo "e-mail"
TemplateField emailField = new TemplateField(
    new TemplateRegexPosition("[a-z]+\\@[a-z]+\\.[a-z]+"),
    "Email");
// Crie um modelo
Template template = new Template(new TemplateItem[] { priceField, emailField });
```
## Etapa 2: analisar documento usando modelo
A seguir, analisaremos um documento usando o modelo definido.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Analise o documento pelo modelo
    DocumentData data = parser.ParseByTemplate(template);
    // Imprimir preços
    Console.WriteLine("Prices:");
    foreach (FieldData field in data.GetFieldsByName("Price"))
    {
        PageTextArea area = field.PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
    // Imprimir e-mails
    Console.WriteLine("Emails:");
    foreach (FieldData field in data.GetFieldsByName("Email"))
    {
        PageTextArea area = field.PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

## Conclusão
Neste tutorial, aprendemos como usar GroupDocs.Parser for .NET para extrair campos de dados específicos de documentos. Ao definir modelos e utilizar os recursos de análise da biblioteca, os desenvolvedores podem recuperar com eficiência dados estruturados, como preços e e-mails, de vários formatos de documentos.

## Perguntas frequentes
### Posso analisar diferentes tipos de documentos com GroupDocs.Parser for .NET?
Sim, GroupDocs.Parser oferece suporte à análise de vários formatos de documentos, como PDF, DOCX, PPTX e muito mais.
### O GroupDocs.Parser é adequado para processamento de documentos em grande escala?
Com certeza, GroupDocs.Parser é otimizado para desempenho e pode lidar com grandes volumes de documentos com eficiência.
### Como posso integrar GroupDocs.Parser em meu aplicativo .NET?
Você pode integrar facilmente GroupDocs.Parser referenciando a biblioteca em seu projeto do Visual Studio e importando os namespaces necessários.
### O GroupDocs.Parser oferece suporte para extração de imagens ou metadados?
Sim, GroupDocs.Parser oferece APIs para extrair imagens, texto e metadados de documentos.
### Existe um fórum da comunidade para usuários do GroupDocs.Parser?
 Sim, você pode procurar ajuda e interagir com outros usuários no fórum GroupDocs.Parser[aqui](https://forum.groupdocs.com/c/parser/17).