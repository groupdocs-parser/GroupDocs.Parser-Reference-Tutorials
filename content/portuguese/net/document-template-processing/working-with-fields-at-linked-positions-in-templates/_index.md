---
title: Trabalhando com campos em posições vinculadas em modelos
linktitle: Trabalhando com campos em posições vinculadas em modelos
second_title: API GroupDocs.Parser .NET
description: Aprenda como extrair dados de documentos com eficiência usando GroupDocs.Parser for .NET. Tutorial passo a passo com exemplos de código.
weight: 12
url: /pt/net/document-template-processing/working-with-fields-at-linked-positions-in-templates/
type: docs
---
# Trabalhando com campos em posições vinculadas em modelos

## Introdução
GroupDocs.Parser for .NET é uma biblioteca robusta projetada para facilitar tarefas de análise de documentos e extração de dados. Ele suporta uma ampla variedade de formatos de arquivo, incluindo PDF, DOCX, XLSX e muito mais. Um de seus principais recursos é a extração de dados baseada em modelos, que permite definir campos em um documento e extrair dados específicos com base nesses modelos predefinidos.
## Pré-requisitos
Antes de começarmos, certifique-se de ter o seguinte:
- Compreensão básica da programação C#
- Visual Studio instalado em seu sistema
-  Biblioteca GroupDocs.Parser para .NET (download em[aqui](https://releases.groupdocs.com/parser/net/))
- Exemplos de arquivos de documentos para trabalhar

## Importando Namespaces
Comece incluindo os namespaces necessários em seu projeto C#:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Etapa 1: definir campos de modelo
Primeiro, defina os campos do modelo usando expressões regulares e posições vinculadas:
```csharp
// Defina um campo com uma expressão regular
TemplateField field = new TemplateField(
    new TemplateRegexPosition("Tax"),
    "Tax");
// Defina um campo vinculado com configurações de posição específicas
TemplateField linkedField = new TemplateField(
    new TemplateLinkedPosition(
        "Tax",
        new Size(100, 20),
        new TemplateLinkedPositionEdges(false, false, true, false)),
    "TaxValue");
```
## Etapa 2: crie um modelo
A seguir, crie um modelo contendo os campos definidos:
```csharp
// Crie um modelo com os campos definidos
Template template = new Template(new TemplateItem[] { field, linkedField });
```
## Etapa 3: analisar documento com modelo
 Agora, inicialize o`Parser` class e analise o documento usando o modelo:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Analise o documento pelo modelo
    DocumentData data = parser.ParseByTemplate(template);
    // Iterar através dos dados extraídos e imprimir resultados
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

## Conclusão
GroupDocs.Parser for .NET simplifica o processo de extração de dados estruturados de documentos usando modelos. Ao definir campos e aplicar modelos, você pode extrair informações relevantes de forma eficiente, aumentando a automação e a produtividade nas tarefas de processamento de documentos.

## Perguntas frequentes
### O GroupDocs.Parser pode extrair dados de arquivos PDF criptografados?
Sim, GroupDocs.Parser oferece suporte à análise de arquivos PDF criptografados, fornecendo a senha durante a análise.
### Quais formatos de arquivo são suportados para extração baseada em modelo?
GroupDocs.Parser oferece suporte a uma ampla variedade de formatos de arquivo, incluindo PDF, DOCX, XLSX, PPTX, TXT e muito mais.
### Existe uma versão de teste disponível para GroupDocs.Parser?
 Sim, você pode baixar uma versão de avaliação gratuita em[aqui](https://releases.groupdocs.com/).
### Posso usar GroupDocs.Parser para processamento em lote de documentos?
Sim, GroupDocs.Parser permite o processamento em lote para analisar vários documentos simultaneamente.
### Onde posso obter suporte técnico para GroupDocs.Parser?
 Você pode procurar suporte técnico e interagir com a comunidade em[Fórum GroupDocs](https://forum.groupdocs.com/c/parser/17).