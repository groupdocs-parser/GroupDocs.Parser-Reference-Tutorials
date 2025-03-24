---
title: Buscar texto con resaltados
linktitle: Buscar texto con resaltados
second_title: API GroupDocs.Parser .NET
description: Aprenda a buscar y resaltar texto en documentos usando GroupDocs.Parser para .NET. Extraiga información valiosa de manera eficiente.
weight: 24
url: /es/net/text-extraction/search-text-with-highlights/
---
## Introducción
En este tutorial, exploraremos cómo usar GroupDocs.Parser para .NET para buscar texto dentro de un documento y resaltar los resultados de la búsqueda. GroupDocs.Parser es una poderosa biblioteca que le permite trabajar con varios formatos de documentos y extraer texto, metadatos y más.
## Requisitos previos
Antes de comenzar, asegúrese de tener lo siguiente:
1.  GroupDocs.Parser para .NET: descargue e instale la biblioteca desde[aquí](https://releases.groupdocs.com/parser/net/).
2. IDE: utilice Visual Studio o cualquier IDE preferido para el desarrollo de .NET.
3. Archivo de muestra: prepare un documento de muestra (por ejemplo, PDF, DOCX) para la búsqueda de texto.

## Importar espacios de nombres
Primero, comience importando los espacios de nombres necesarios en su proyecto .NET:
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Paso 1: crear una instancia del analizador
 Comience por crear una instancia del`Parser` clase con la ruta a su archivo de muestra:
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Tu código aquí
}
```
## Paso 2: definir opciones de resaltado
 Especifica el`HighlightOptions` para configurar cómo se deben resaltar los resultados de la búsqueda. Por ejemplo, configurando una ventana de contexto de 15 caracteres:
```csharp
HighlightOptions highlightOptions = new HighlightOptions(15);
```
## Paso 3: buscar texto
Ahora, realice una búsqueda de texto dentro del documento. Proporcione la palabra clave que desea buscar (por ejemplo, "lorem"):
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("lorem", new SearchOptions(true, false, false, highlightOptions));
```
## Paso 4: Procesar los resultados de la búsqueda
Repita los resultados de la búsqueda y muestre el texto encontrado junto con los aspectos destacados:
```csharp
if (searchResults != null)
{
    foreach (SearchResult result in searchResults)
    {
        Console.WriteLine($"{result.LeftHighlightItem.Text}{result.Text}{result.RightHighlightItem.Text}");
    }
}
else
{
    Console.WriteLine("Search isn't supported");
}
```

## Conclusión
En este tutorial, aprendió a usar GroupDocs.Parser para .NET para buscar texto dentro de documentos y resaltar los resultados de la búsqueda. Esta funcionalidad puede resultar inmensamente útil para la extracción y análisis de texto en sus aplicaciones .NET.

## Preguntas frecuentes
### ¿GroupDocs.Parser es adecuado para procesar varios formatos de documentos?
Sí, GroupDocs.Parser admite una amplia gama de formatos de documentos, incluidos PDF, DOCX, XLSX, PPTX y más.
### ¿Puedo utilizar GroupDocs.Parser para extraer metadatos de documentos?
¡Absolutamente! GroupDocs.Parser le permite extraer metadatos, texto y datos estructurados de documentos.
### ¿Dónde puedo encontrar soporte o hacer preguntas sobre GroupDocs.Parser?
 Puedes visitar el[Foro GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) para cualquier consulta relacionada con el soporte.
### ¿Existe una prueba gratuita disponible para GroupDocs.Parser?
 Sí, puedes acceder a un[prueba gratis](https://releases.groupdocs.com/) de GroupDocs.Parser para evaluar sus características.
### ¿Cómo puedo adquirir una licencia para GroupDocs.Parser?
 Puede adquirir una licencia en[aquí](https://purchase.groupdocs.com/buy) y también obtener licencias temporales[aquí](https://purchase.groupdocs.com/temporary-license/).