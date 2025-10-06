---
title: Cargar documento desde URL
linktitle: Cargar documento desde URL
second_title: API GroupDocs.Parser .NET
description: Aprenda a extraer texto de documentos usando GroupDocs.Parser para .NET. Este tutorial cubre la carga de un documento desde una URL y la extracción de texto paso a paso.
weight: 13
url: /es/net/document-loading/load-document-from-url/
type: docs
---
# Cargar documento desde URL

## Introducción
En este tutorial, exploraremos cómo utilizar GroupDocs.Parser para .NET para extraer texto de documentos. GroupDocs.Parser es una poderosa herramienta para extraer texto, metadatos y otra información de varios formatos de documentos, como PDF, Word, Excel y más. Cubriremos el proceso de cargar un documento desde una URL y extraer su contenido de texto paso a paso.
## Requisitos previos
Antes de comenzar, asegúrese de tener configurados los siguientes requisitos previos:
1. Visual Studio: instale Visual Studio en su sistema.
2.  GroupDocs.Parser para .NET: descargue e instale GroupDocs.Parser para .NET desde[pagina de descarga](https://releases.groupdocs.com/parser/net/).
3. Comprensión básica de C#: familiaridad con el lenguaje de programación C#.

## Importar espacios de nombres
Comience incluyendo los espacios de nombres necesarios en su código C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

Primero, demostraremos cómo cargar un documento desde una URL y extraer su contenido de texto.
## Paso 1: especifique la URL del documento
Especifique la URL del documento del que desea extraer el texto:
```csharp
Uri uri = new Uri("https://www.bu.edu/csmet/files/2021/03/Getting-Started-with-SQLite.pdf");
```
## Paso 2: crear una instancia de analizador
 Instanciar el`Parser` clase con la URL del documento:
```csharp
using (Parser parser = new Parser(uri))
{
    // Tu código va aquí
}
```
## Paso 3: extraer texto del documento
 Dentro de`using`bloquear, usar`parser.GetText()` para extraer texto del documento:
```csharp
using (TextReader reader = parser.GetText())
{
    // Tu código va aquí
}
```
## Paso 4: muestre el texto extraído
Lea e imprima el texto extraído del documento:
```csharp
Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
```

## Conclusión
En este tutorial, cubrimos los conceptos básicos de la extracción de texto de un documento usando GroupDocs.Parser para .NET. Si sigue estos pasos, podrá integrar fácilmente capacidades de extracción de texto de documentos en sus aplicaciones C#.

## Preguntas frecuentes
### ¿GroupDocs.Parser es compatible con varios formatos de documentos?
Sí, GroupDocs.Parser admite una amplia gama de formatos de documentos, incluidos PDF, Word, Excel, PowerPoint y más.
### ¿Puedo extraer metadatos junto con texto usando GroupDocs.Parser?
Sí, GroupDocs.Parser le permite extraer metadatos, texto y otra información de los documentos.
### ¿Existe una versión de prueba disponible para GroupDocs.Parser?
 Sí, puede obtener una versión de prueba gratuita de GroupDocs.Parser en[aquí](https://releases.groupdocs.com/).
### ¿Dónde puedo encontrar documentación para GroupDocs.Parser?
 La documentación detallada para GroupDocs.Parser está disponible[aquí](https://tutorials.groupdocs.com/parser/net/).
### ¿Cómo puedo obtener soporte técnico para GroupDocs.Parser?
Puede buscar soporte técnico y hacer preguntas en el foro GroupDocs.Parser[aquí](https://forum.groupdocs.com/c/parser/17).