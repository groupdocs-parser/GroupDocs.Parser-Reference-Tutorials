---
title: Extraer texto de la página en modo sin formato
linktitle: Extraer texto de la página en modo sin formato
second_title: API GroupDocs.Parser .NET
description: Aprenda a extraer texto eficiente de páginas de documentos utilizando Groupdocs.Parser para .NET en este completo tutorial.
weight: 17
url: /es/net/text-extraction/extract-text-from-page-in-raw-mode/
---

# Extraer texto de la página en modo sin formato

## Introducción
En este tutorial, aprenderá a utilizar Groupdocs.Parser para .NET para extraer texto de páginas de documentos en modo sin formato. Esta biblioteca proporciona herramientas eficientes para analizar y extraer contenido de varios formatos de archivos, lo que permite a los desarrolladores incorporar la extracción de texto de documentos en sus aplicaciones .NET.
## Requisitos previos
Antes de comenzar, asegúrese de tener los siguientes requisitos previos:
- Conocimientos básicos de programación en C# y .NET.
- Visual Studio instalado en su máquina
- Acceso a la biblioteca Groupdocs.Parser para .NET
- Archivo de documento de muestra para pruebas.

## Importar espacios de nombres
Comience por incluir los espacios de nombres necesarios en su proyecto C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Paso 1: inicializar el analizador
 Primero, cree una instancia del`Parser` class proporcionando la ruta a su archivo de documento de muestra.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Tu código aquí
}
```
## Paso 2: recuperar la información del documento
 Recuperar información sobre el documento usando`GetDocumentInfo()` método.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
```
## Paso 3: iterar sobre páginas y extraer texto
Itere a través de cada página del documento y extraiga el contenido del texto.
```csharp
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Extraer texto de la página
    using (TextReader reader = parser.GetText(p, new TextOptions(true)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Conclusión
Ahora ha aprendido a utilizar Groupdocs.Parser para .NET para extraer texto de páginas de documentos en modo sin formato. Esta puede ser una característica poderosa para aplicaciones que necesitan analizar o procesar contenido de texto de varios formatos de archivo.

## Preguntas frecuentes
### ¿Groupdocs.Parser para .NET es compatible con todos los formatos de archivo?
Groupdocs.Parser admite una amplia gama de formatos de archivo, incluidos PDF, DOCX, XLSX, PPTX, EPUB y más.
### ¿Puedo extraer metadatos junto con texto usando esta biblioteca?
Sí, Groupdocs.Parser le permite extraer texto y metadatos de los documentos.
### ¿Existe una versión de prueba disponible para probar?
 Sí, puedes descargar una versión de prueba gratuita desde[aquí](https://releases.groupdocs.com/).
### ¿Cómo puedo obtener soporte técnico para Groupdocs.Parser?
 Para asistencia técnica, visite el[Foro Groupdocs.Parser](https://forum.groupdocs.com/c/parser/17).
### ¿Dónde puedo comprar una licencia de Groupdocs.Parser para .NET?
 Puedes comprar una licencia[aquí](https://purchase.groupdocs.com/buy).