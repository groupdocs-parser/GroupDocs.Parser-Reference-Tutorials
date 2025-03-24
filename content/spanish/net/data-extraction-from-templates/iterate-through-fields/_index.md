---
title: Iterar a través de campos
linktitle: Iterar a través de campos
second_title: API GroupDocs.Parser .NET
description: Aprenda a extraer datos estructurados de documentos utilizando GroupDocs.Parser para .NET. Mejore sus aplicaciones .NET con capacidades de extracción de datos de documentos.
weight: 11
url: /es/net/data-extraction-from-templates/iterate-through-fields/
---

# Iterar a través de campos

## Introducción
GroupDocs.Parser para .NET es una potente biblioteca que permite a los desarrolladores extraer datos de varios formatos de documentos como PDF, Microsoft Word, Excel y PowerPoint. Este tutorial lo guiará a través del proceso de uso de GroupDocs.Parser para recorrer los campos del documento y extraer datos específicos usando plantillas. Al final de este tutorial, podrá extraer de manera eficiente datos estructurados de documentos en sus aplicaciones .NET.
## Requisitos previos
Antes de comenzar, asegúrese de tener configurados los siguientes requisitos previos:
- Conocimientos básicos de programación en C#.
- Visual Studio instalado en su máquina.
- Biblioteca GroupDocs.Parser para .NET instalada y referenciada en su proyecto.

## Importar espacios de nombres
Para comenzar, agregue los espacios de nombres necesarios a su archivo C#:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
Dividamos el proceso en instrucciones paso a paso.
## Paso 1: definir campos de plantilla
Primero, defina los campos que desea extraer del documento utilizando expresiones regulares.
```csharp
// Definir un campo de "precio"
TemplateField priceField = new TemplateField(
    new TemplateRegexPosition("\\$\\d+(.\\d+)?"),
    "Price");
// Definir un campo de "correo electrónico"
TemplateField emailField = new TemplateField(
    new TemplateRegexPosition("[a-z]+\\@[a-z]+\\.[a-z]+"),
    "Email");
// Crear una plantilla con campos definidos
Template template = new Template(new TemplateItem[] { priceField, emailField });
```
En este paso, hemos definido dos campos: uno para extraer precios (identificados por el signo del dólar y los dígitos) y otro para extraer direcciones de correo electrónico.
## Paso 2: analizar el documento
 A continuación, utilice el`Parser` clase para analizar el documento utilizando la plantilla definida.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Analizar el documento por plantilla.
    DocumentData data = parser.ParseByTemplate(template);
    // Iterar a través de los datos extraídos
    for (int i = 0; i < data.Count; i++)
    {
        // Imprimir nombre del campo
        Console.Write(data[i].Name + ": ");
        // Compruebe si el área extraída es texto
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```
 Aquí inicializamos el`Parser` con la ruta a su documento de muestra y luego analice el documento usando la plantilla definida. Luego recorremos los datos extraídos e imprimimos los nombres de los campos junto con el texto extraído.
## Conclusión
En este tutorial, exploramos cómo usar GroupDocs.Parser para .NET para extraer datos específicos de documentos usando plantillas. Al aprovechar las expresiones regulares y las plantillas, puede extraer de manera eficiente información estructurada de varios formatos de documentos. Experimente con diferentes plantillas y tipos de documentos para satisfacer sus necesidades de extracción específicas.

## Preguntas frecuentes
### ¿Puede GroupDocs.Parser extraer datos de documentos escaneados?
Sí, GroupDocs.Parser puede extraer texto y metadatos de documentos PDF escaneados y con capacidad de búsqueda.
### ¿GroupDocs.Parser es compatible con aplicaciones .NET Core?
Sí, GroupDocs.Parser admite .NET Core junto con .NET Framework.
### ¿Qué formatos de documentos admite GroupDocs.Parser?
GroupDocs.Parser admite una amplia gama de formatos, incluidos PDF, Microsoft Word, Excel, PowerPoint y más.
### ¿Cómo puedo manejar documentos grandes con GroupDocs.Parser?
GroupDocs.Parser ofrece opciones para extraer datos de páginas o secciones específicas de documentos grandes, lo que garantiza un procesamiento eficiente.
### ¿Puedo utilizar GroupDocs.Parser sólo para extracción de texto?
Sí, puede extraer contenido de texto sin formato de documentos utilizando GroupDocs.Parser sin necesidad de aplicar un formato complejo.