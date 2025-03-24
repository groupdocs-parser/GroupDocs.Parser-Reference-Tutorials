---
title: Buscar texto por expresión regular (Regex)
linktitle: Buscar texto por expresión regular (Regex)
second_title: API GroupDocs.Parser .NET
description: Aprenda a buscar texto usando expresiones regulares en documentos usando GroupDocs.Parser para .NET. Extraiga contenido específico sin esfuerzo.
weight: 23
url: /es/net/text-extraction/search-text-by-regex/
---

# Buscar texto por expresión regular (Regex)

## Introducción
En este tutorial, profundizaremos en el uso de GroupDocs.Parser para .NET para buscar texto por expresión regular (Regex) dentro de documentos. GroupDocs.Parser es una potente biblioteca que permite a los desarrolladores extraer texto y metadatos de varios formatos de archivos como PDF, DOCX, XLSX y más. La búsqueda de texto mediante expresiones regulares es particularmente útil para encontrar patrones o contenido específico dentro de documentos de manera eficiente.
## Requisitos previos
Antes de sumergirse en este tutorial, asegúrese de tener lo siguiente:
1. Visual Studio: instale Visual Studio IDE para el desarrollo de .NET.
2.  GroupDocs.Parser para .NET: descargue e instale GroupDocs.Parser para .NET desde[aquí](https://releases.groupdocs.com/parser/net/).
3. Archivo de muestra: prepare un documento de muestra (PDF, DOCX, etc.) para probar la funcionalidad de búsqueda.

## Importar espacios de nombres
Primero, comience incluyendo los espacios de nombres necesarios en su código C#:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Paso 1: crear una instancia de la clase Parser
 Instanciar el`Parser` clase proporcionando la ruta a su archivo de muestra:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // El código va aquí.
}
```
 Reemplazar`"YourSampleFile.pdf"` con la ruta a su archivo real.
## Paso 2: buscar usando expresiones regulares
Defina y ejecute la búsqueda utilizando un patrón de expresión regular. Por ejemplo, para buscar secuencias numéricas (por ejemplo, números enteros) dentro del documento:
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("[0-9]+", new SearchOptions(true, false, true));
```
 En este ejemplo,`[0-9]+` es un patrón de expresión regular que coincide con uno o más dígitos.
## Paso 3: consulte el soporte de búsqueda
Verifique si la operación de búsqueda es compatible con el tipo de documento:
```csharp
if (searchResults == null)
{
    Console.WriteLine("Search isn't supported");
    return;
}
```
## Paso 4: iterar sobre los resultados de la búsqueda
Repita los resultados de la búsqueda y procese cada coincidencia:
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Este bucle imprimirá la posición y el texto coincidente que se encuentra dentro del documento.

## Conclusión
En conclusión, aprovechar GroupDocs.Parser para .NET permite una búsqueda de texto eficiente utilizando expresiones regulares en varios formatos de documentos. Siguiendo esta guía, los desarrolladores pueden integrar perfectamente el análisis de documentos y la extracción de texto basada en expresiones regulares en sus aplicaciones .NET.

## Preguntas frecuentes
### ¿Puede GroupDocs.Parser buscar en documentos cifrados?
No, GroupDocs.Parser no puede buscar en documentos cifrados o protegidos con contraseña.
### ¿GroupDocs.Parser admite OCR (reconocimiento óptico de caracteres)?
No, GroupDocs.Parser no realiza OCR. Se basa en la extracción de texto de la estructura interna del documento.
### ¿Puedo buscar patrones complejos usando expresiones regulares?
Sí, GroupDocs.Parser admite expresiones regulares completas, lo que permite la coincidencia de patrones complejos dentro de los documentos.
### ¿Qué formatos de documentos son compatibles con la extracción de texto?
GroupDocs.Parser admite una amplia gama de formatos, incluidos PDF, DOCX, XLSX, PPTX y más.
### ¿GroupDocs.Parser es compatible con .NET Core?
Sí, GroupDocs.Parser es compatible con .NET Core para desarrollo multiplataforma.