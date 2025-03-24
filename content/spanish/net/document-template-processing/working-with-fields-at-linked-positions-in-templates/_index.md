---
title: Trabajar con campos en posiciones vinculadas en plantillas
linktitle: Trabajar con campos en posiciones vinculadas en plantillas
second_title: API GroupDocs.Parser .NET
description: Aprenda a extraer datos de manera eficiente de documentos usando GroupDocs.Parser para .NET. Tutorial paso a paso con ejemplos de código.
weight: 12
url: /es/net/document-template-processing/working-with-fields-at-linked-positions-in-templates/
---

# Trabajar con campos en posiciones vinculadas en plantillas

## Introducción
GroupDocs.Parser para .NET es una biblioteca sólida diseñada para facilitar las tareas de análisis de documentos y extracción de datos. Admite una amplia gama de formatos de archivo, incluidos PDF, DOCX, XLSX y más. Una de sus características clave es la extracción de datos basada en plantillas, que le permite definir campos dentro de un documento y extraer datos específicos en función de estas plantillas predefinidas.
## Requisitos previos
Antes de comenzar, asegúrese de tener lo siguiente:
- Comprensión básica de la programación en C#.
- Visual Studio instalado en su sistema
-  Biblioteca GroupDocs.Parser para .NET (descargar desde[aquí](https://releases.groupdocs.com/parser/net/))
- Archivos de documentos de muestra con los que trabajar

## Importando espacios de nombres
Comience por incluir los espacios de nombres necesarios en su proyecto C#:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Paso 1: definir campos de plantilla
Primero, defina los campos de la plantilla usando expresiones regulares y posiciones vinculadas:
```csharp
// Definir un campo con una expresión regular.
TemplateField field = new TemplateField(
    new TemplateRegexPosition("Tax"),
    "Tax");
// Definir un campo vinculado con configuraciones de posición específicas
TemplateField linkedField = new TemplateField(
    new TemplateLinkedPosition(
        "Tax",
        new Size(100, 20),
        new TemplateLinkedPositionEdges(false, false, true, false)),
    "TaxValue");
```
## Paso 2: crea una plantilla
A continuación, cree una plantilla que contenga los campos definidos:
```csharp
// Crear una plantilla con los campos definidos
Template template = new Template(new TemplateItem[] { field, linkedField });
```
## Paso 3: analizar el documento con la plantilla
 Ahora, inicializa el`Parser` clase y analizar el documento usando la plantilla:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Analizar el documento por plantilla.
    DocumentData data = parser.ParseByTemplate(template);
    // Iterar a través de los datos extraídos e imprimir los resultados
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

## Conclusión
GroupDocs.Parser para .NET simplifica el proceso de extracción de datos estructurados de documentos mediante plantillas. Al definir campos y aplicar plantillas, puede extraer de manera eficiente información relevante, mejorando la automatización y la productividad en las tareas de procesamiento de documentos.

## Preguntas frecuentes
### ¿Puede GroupDocs.Parser extraer datos de archivos PDF cifrados?
Sí, GroupDocs.Parser admite el análisis de archivos PDF cifrados proporcionando la contraseña durante el análisis.
### ¿Qué formatos de archivo son compatibles con la extracción basada en plantillas?
GroupDocs.Parser admite una amplia gama de formatos de archivo, incluidos PDF, DOCX, XLSX, PPTX, TXT y más.
### ¿Existe una versión de prueba disponible para GroupDocs.Parser?
 Sí, puedes descargar una versión de prueba gratuita desde[aquí](https://releases.groupdocs.com/).
### ¿Puedo utilizar GroupDocs.Parser para el procesamiento por lotes de documentos?
Sí, GroupDocs.Parser permite el procesamiento por lotes para analizar varios documentos al mismo tiempo.
### ¿Dónde puedo obtener soporte técnico para GroupDocs.Parser?
 Puede buscar soporte técnico e interactuar con la comunidad en[Foro de documentos de grupo](https://forum.groupdocs.com/c/parser/17).