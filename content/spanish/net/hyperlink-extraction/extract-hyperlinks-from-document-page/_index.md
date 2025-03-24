---
title: Extraer hipervínculos de la página del documento
linktitle: Extraer hipervínculos de la página del documento
second_title: API GroupDocs.Parser .NET
description: Aprenda a extraer hipervínculos de documentos utilizando GroupDocs.Parser para .NET. Guía paso a paso para la extracción de hipervínculos en C#.
weight: 11
url: /es/net/hyperlink-extraction/extract-hyperlinks-from-document-page/
---

# Extraer hipervínculos de la página del documento

## Introducción
En este tutorial, exploraremos cómo usar GroupDocs.Parser para .NET para extraer hipervínculos de documentos paso a paso. GroupDocs.Parser es una potente biblioteca que permite a los desarrolladores analizar varios formatos de documentos y extraer texto, metadatos y otros elementos.
## Requisitos previos
Antes de comenzar, asegúrese de tener lo siguiente:
- Visual Studio: instale Visual Studio en su máquina de desarrollo.
-  Biblioteca GroupDocs.Parser: descargue y consulte la biblioteca GroupDocs.Parser. Puedes obtenerlo de[aquí](https://releases.groupdocs.com/parser/net/).
- Documento de muestra: prepare un documento de muestra (p. ej., DOCX, PDF) que contenga hipervínculos para realizar pruebas.

## Importar espacios de nombres
Primero, incluya los espacios de nombres necesarios para utilizar las funcionalidades de GroupDocs.Parser:
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Paso 1: crear una instancia del analizador
 Instanciar el`Parser` class con la ruta a su documento de muestra.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // El código va aquí...
}
```
## Paso 2: verifique la compatibilidad con la extracción de hipervínculos
Asegúrese de que el documento admita la extracción de hipervínculos antes de continuar.
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
## Paso 3: recuperar la información del documento
Obtenga información básica sobre el documento y compruebe si contiene páginas.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Paso 4: iterar sobre las páginas del documento
Iterar a través de cada página del documento.
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Extraer hipervínculos de la página actual
    IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks(pageIndex);
    // Iterar sobre hipervínculos extraídos
    foreach (PageHyperlinkArea hyperlink in hyperlinks)
    {
        Console.WriteLine($"Hyperlink Text: {hyperlink.Text}");
        Console.WriteLine($"Hyperlink URL: {hyperlink.Url}");
        Console.WriteLine(); // Línea en blanco para facilitar la lectura
    }
}
```

## Conclusión
En este tutorial, cubrimos los conceptos básicos del uso de GroupDocs.Parser para .NET para extraer hipervínculos de documentos. Aprendió a inicializar el analizador, verificar la compatibilidad con hipervínculos, recuperar información del documento e iterar a través de las páginas del documento para extraer hipervínculos de manera eficiente.

## Preguntas frecuentes
### ¿Puedo extraer hipervínculos de diferentes formatos de documentos?
Sí, GroupDocs.Parser admite varios formatos como DOCX, PDF, PPTX, etc., para la extracción de hipervínculos.
### ¿GroupDocs.Parser es fácil de integrar en aplicaciones .NET existentes?
Por supuesto, GroupDocs.Parser está diseñado para ser sencillo y puede integrarse fácilmente en sus proyectos .NET.
### ¿Puedo extraer otros metadatos junto con hipervínculos usando GroupDocs.Parser?
Sí, además de los hipervínculos, puedes extraer texto, imágenes y metadatos de documentos utilizando esta biblioteca.
### ¿GroupDocs.Parser maneja documentos cifrados o protegidos con contraseña?
GroupDocs.Parser puede analizar documentos protegidos con contraseña si se proporciona la contraseña.
### ¿Existe una versión de prueba disponible para probar antes de comprar?
 Sí, puedes descargar una versión de prueba gratuita.[aquí](https://releases.groupdocs.com/).