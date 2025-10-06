---
title: Extraiga códigos de barras del documento con opciones
linktitle: Extraiga códigos de barras del documento con opciones
second_title: API GroupDocs.Parser .NET
description: Aprenda a extraer códigos de barras de documentos utilizando GroupDocs.Parser para .NET. Tutorial completo con ejemplos de código y preguntas frecuentes.
weight: 14
url: /es/net/barcode-extraction/extract-barcodes-from-document-with-options/
type: docs
---
# Extraiga códigos de barras del documento con opciones

## Introducción
En este tutorial, recorreremos el proceso de extracción de códigos de barras de un documento utilizando GroupDocs.Parser para .NET. GroupDocs.Parser es una poderosa biblioteca que le permite extraer texto, metadatos y códigos de barras de varios formatos de documentos como PDF, Microsoft Word, Excel y más.
## Requisitos previos
Antes de comenzar, asegúrese de cumplir con los siguientes requisitos previos:
1. Entorno de desarrollo: asegúrese de tener Visual Studio instalado en su máquina.
2.  Biblioteca GroupDocs.Parser: descargue e instale la biblioteca GroupDocs.Parser para .NET desde[aquí](https://releases.groupdocs.com/parser/net/).
3. Documento de muestra: prepare un documento de muestra (p. ej., PDF, DOCX) que contenga códigos de barras para su extracción.

## Importar espacios de nombres
Primero, debe importar los espacios de nombres necesarios a su proyecto C# para utilizar las funcionalidades de GroupDocs.Parser.
```csharp
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using System;
using System.Collections.Generic;
```
## Paso 1: crear una instancia de la clase Parser
 Para comenzar, cree una instancia del`Parser` clase pasando la ruta a su documento de muestra.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Código que se agregará en los próximos pasos.
}
```
## Paso 2: Verifique el soporte de extracción de códigos de barras
 A continuación, verifique si el documento admite la extracción de códigos de barras utilizando el`Features` propiedad de la`Parser` instancia.
```csharp
if (!parser.Features.Barcodes)
{
    Console.WriteLine("Document doesn't support barcode extraction.");
    return;
}
```
## Paso 3: definir las opciones de extracción de códigos de barras
 Ahora, especifique las opciones para la extracción de códigos de barras usando`BarcodeOptions`. Puede configurar parámetros como modos de calidad y tipos de códigos de barras.
```csharp
BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```
## Paso 4: extraiga códigos de barras del documento
 Utilizar el`GetBarcodes` método de la`Parser` clase para extraer códigos de barras según las opciones definidas.
```csharp
IEnumerable<PageBarcodeArea> barcodes = parser.GetBarcodes(options);
```
## Paso 5: iterar y mostrar códigos de barras extraídos
Finalmente, recorra los códigos de barras extraídos y muestre su índice de página y sus valores.
```csharp
foreach (PageBarcodeArea barcode in barcodes)
{
    Console.WriteLine("Page: " + barcode.Page.Index.ToString());
    Console.WriteLine("Value: " + barcode.Value);
}
```

## Conclusión
 En este tutorial, aprendimos cómo extraer códigos de barras de un documento usando GroupDocs.Parser para .NET. Este proceso implica la creación de un`Parser` Por ejemplo, definiendo opciones de extracción e iterando a través de los códigos de barras extraídos. GroupDocs.Parser simplifica la tarea de extracción de códigos de barras de varios formatos de documentos, lo que permite un procesamiento eficiente de documentos dentro de sus aplicaciones .NET.

## Preguntas frecuentes
### ¿Puede GroupDocs.Parser extraer códigos de barras de documentos PDF?
Sí, GroupDocs.Parser admite la extracción de códigos de barras de documentos PDF junto con otros formatos como DOCX, XLSX, etc.
### ¿Qué tipos de códigos de barras admite GroupDocs.Parser?
GroupDocs.Parser admite varios tipos de códigos de barras, incluidos códigos QR, Código 39, Código 128 y más.
### ¿GroupDocs.Parser requiere una licencia para uso comercial?
 Sí, se requiere una licencia válida para uso comercial. Puede obtener una licencia de[aquí](https://purchase.groupdocs.com/buy).
### ¿GroupDocs.Parser es adecuado para el procesamiento por lotes de documentos?
Sí, GroupDocs.Parser puede manejar de manera eficiente el procesamiento por lotes de documentos para la extracción de texto, recuperación de metadatos y extracción de códigos de barras.
### ¿Dónde puedo encontrar soporte técnico para GroupDocs.Parser?
 Puede obtener soporte técnico o hacer preguntas en el[Foro de documentos de grupo](https://forum.groupdocs.com/c/parser/17).