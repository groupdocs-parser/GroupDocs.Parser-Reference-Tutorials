---
title: Extraia dados de formulários PDF
linktitle: Extraia dados de formulários PDF
second_title: API GroupDocs.Parser .NET
description: Aprenda como extrair dados de formulários PDF usando GroupDocs.Parser for .NET. Guia passo a passo com exemplos de código e perguntas frequentes.
weight: 11
url: /pt/net/pdf-processing/extract-data-from-pdf-forms/
type: docs
---
# Extraia dados de formulários PDF

## Introdução
Neste tutorial, exploraremos como utilizar GroupDocs.Parser for .NET para extrair dados de formulários PDF. GroupDocs.Parser é uma biblioteca poderosa que permite aos desenvolvedores trabalhar de forma eficiente com vários formatos de documentos, incluindo PDF, DOCX, XLSX e muito mais. Percorreremos as etapas necessárias para extrair campos específicos de um formulário PDF e lidar com os dados extraídos.
## Pré-requisitos
Antes de começarmos, certifique-se de ter os seguintes pré-requisitos:
- Conhecimento básico de programação C#.
- Visual Studio instalado em seu sistema.
- Biblioteca GroupDocs.Parser para .NET instalada. Você pode baixá-lo em[aqui](https://releases.groupdocs.com/parser/net/).

## Importar namespaces
Para começar, você precisará importar os namespaces necessários em seu projeto C#:
```csharp
using System;
using System.Linq;
using GroupDocs.Parser.Data;
```
## Etapa 1: inicializar o analisador
 Primeiro, crie uma instância do`Parser` class especificando o caminho para seu arquivo PDF de amostra:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // código para extração de dados irá aqui
}
```
## Etapa 2: extrair dados do documento PDF
 A seguir, dentro do`using` bloco, invoque o`ParseForm` método para extrair dados do documento PDF:
```csharp
DocumentData data = parser.ParseForm();
if (data == null)
{
    Console.WriteLine("Form extraction isn't supported.");
    return;
}
```
## Etapa 3: acessar dados de campo específicos
 Agora, defina um método`GetFieldText` para recuperar texto de um campo específico nos dados extraídos:
```csharp
private static string GetFieldText(DocumentData data, string fieldName)
{
    FieldData fieldData = data.GetFieldsByName(fieldName).FirstOrDefault();
    return fieldData != null && fieldData.PageArea is PageTextArea
        ? (fieldData.PageArea as PageTextArea).Text
        : null;
}
```
## Etapa 4: Crie um objeto de registro preliminar
 Depois de definir o`GetFieldText` método, use-o para preencher um`PreliminaryRecord` objeto com dados extraídos:
```csharp
PreliminaryRecord rec = new PreliminaryRecord();
rec.Name = GetFieldText(data, "Name");
rec.Model = GetFieldText(data, "Model");
rec.Time = GetFieldText(data, "Time");
rec.Description = GetFieldText(data, "Description");
```
## Etapa 5: Utilize os dados extraídos
Por fim, você pode usar os dados extraídos conforme necessário — seja salvando em um banco de dados, enviando como resposta da web ou exibindo-os:
```csharp
Console.WriteLine("Preliminary record");
Console.WriteLine("Name: {0}", rec.Name);
Console.WriteLine("Model: {0}", rec.Model);
Console.WriteLine("Time: {0}", rec.Time);
Console.WriteLine("Description: {0}", rec.Description);
```

## Conclusão
Neste tutorial, cobrimos os fundamentos da extração de dados de formulários PDF usando GroupDocs.Parser for .NET. Seguindo essas etapas, você pode recuperar com eficiência informações específicas de documentos PDF em seus aplicativos C#.

## Perguntas frequentes
### O GroupDocs.Parser é compatível com outros formatos de documento além do PDF?
Sim, GroupDocs.Parser oferece suporte a vários formatos, incluindo DOCX, XLSX, PPTX e muito mais.
### Posso extrair imagens e metadados usando GroupDocs.Parser?
Sim, GroupDocs.Parser permite a extração de imagens, metadados e texto de documentos.
### Onde posso encontrar suporte ou documentação adicional para GroupDocs.Parser?
 Você pode visitar o[Documentação GroupDocs.Parser](https://tutorials.groupdocs.com/parser/net/) para obter informações detalhadas e exemplos.
### Existe um teste gratuito disponível para GroupDocs.Parser?
 Sim, você pode acessar um[avaliação gratuita do GroupDocs.Parser](https://releases.groupdocs.com/) para explorar suas características.
### Como posso obter uma licença temporária para GroupDocs.Parser?
 Você pode adquirir um[licença temporária para GroupDocs.Parser](https://purchase.groupdocs.com/temporary-license/) para avaliar suas capacidades em seus projetos.