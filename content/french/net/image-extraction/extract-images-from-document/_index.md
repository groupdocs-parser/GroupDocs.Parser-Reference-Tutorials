---
title: Extraire des images d'un document
linktitle: Extraire des images d'un document
second_title: API GroupDocs.Parser .NET
description: Extrayez facilement des images de documents à l'aide de GroupDocs.Parser pour .NET. Vos capacités de traitement de documents et rationalisez efficacement les tâches d’extraction d’images.
type: docs
weight: 11
url: /fr/net/image-extraction/extract-images-from-document/
---
## Introduction
Dans ce didacticiel, nous explorerons comment extraire des images de documents à l'aide de GroupDocs.Parser pour .NET. GroupDocs.Parser est une bibliothèque puissante qui permet aux développeurs d'extraire du texte, des métadonnées, des images et bien plus encore à partir de divers formats de documents.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir configuré les conditions préalables suivantes :
- Visual Studio : installez Visual Studio sur votre ordinateur.
-  GroupDocs.Parser pour .NET : téléchargez et installez GroupDocs.Parser à partir du[page de téléchargement](https://releases.groupdocs.com/parser/net/).
- Exemple de document : préparez un exemple de document (PDF, DOCX, etc.) à partir duquel vous souhaitez extraire des images.

## Importer des espaces de noms
Commencez par importer les espaces de noms nécessaires dans votre projet C# :
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Étape 1 : Créer une instance de la classe Parser
 Tout d'abord, créez une instance de`Parser` classe en fournissant le chemin d’accès à votre exemple de document.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Votre code va ici
}
```
 Remplacer`"YourSampleFile.pdf"` avec le chemin d'accès à votre fichier de document.
## Étape 2 : Extraire les images du document
 Ensuite, extrayez les images du document à l'aide du`GetImages()` méthode.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
 Le`GetImages()` La méthode renvoie une collection de`PageImageArea` objets représentant des images trouvées dans le document.
## Étape 3 : Vérifiez la prise en charge de l’extraction d’images
Avant de parcourir les images, vérifiez si l'extraction d'images est prise en charge pour le document.
```csharp
if (images == null)
{
    Console.WriteLine("Images extraction isn't supported");
    return;
}
```
Cette étape garantit que le document contient des images extractibles.
## Étape 4 : Itérer sur les images extraites
Maintenant, parcourez les images extraites pour accéder à des informations détaillées sur chaque image, telles que l'index de la page, les coordonnées du rectangle et le type d'image.
```csharp
foreach (PageImageArea image in images)
{
    Console.WriteLine($"Page: {image.Page.Index}, Rectangle: {image.Rectangle}, Type: {image.FileType}");
}
```
Cette boucle imprime des informations sur chaque image extraite, y compris son emplacement et son type.

## Conclusion
Dans ce didacticiel, nous avons appris à utiliser GroupDocs.Parser pour .NET pour extraire des images de documents par programmation. En suivant ces étapes, vous pouvez intégrer de manière transparente la fonctionnalité d'extraction d'images de documents dans vos applications .NET.

## FAQ
### GroupDocs.Parser peut-il extraire des images de tous les formats de documents ?
GroupDocs.Parser prend en charge l'extraction d'images à partir de divers formats, notamment PDF, DOCX, XLSX, etc.
### Existe-t-il un essai gratuit disponible pour GroupDocs.Parser ?
 Oui, vous pouvez accéder à un essai gratuit de GroupDocs.Parser à partir du[site web](https://releases.groupdocs.com/).
### Où puis-je trouver de la documentation pour GroupDocs.Parser ?
 Une documentation détaillée pour GroupDocs.Parser peut être trouvée[ici](https://reference.groupdocs.com/parser/net/).
### Comment puis-je obtenir une licence temporaire pour GroupDocs.Parser ?
 Vous pouvez obtenir une licence temporaire auprès du[page de licence temporaire](https://purchase.groupdocs.com/temporary-license/).
### Où puis-je obtenir de l’aide pour GroupDocs.Parser ?
 Pour obtenir une assistance et une assistance techniques, visitez le[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).