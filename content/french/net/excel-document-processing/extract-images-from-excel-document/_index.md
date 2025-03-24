---
title: Extraire des images d'un document Excel
linktitle: Extraire des images d'un document Excel
second_title: API GroupDocs.Parser .NET
description: Découvrez comment extraire des images de documents Excel à l'aide de GroupDocs.Parser pour .NET. Guide étape par étape avec des exemples de code.
weight: 10
url: /fr/net/excel-document-processing/extract-images-from-excel-document/
---
## Introduction
Dans ce didacticiel, vous apprendrez à extraire des images d'un document Excel à l'aide de GroupDocs.Parser pour .NET. GroupDocs.Parser est une bibliothèque puissante qui vous permet d'analyser et d'extraire du texte, des métadonnées et des images de divers formats de documents, y compris des fichiers Excel.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir configuré les conditions préalables suivantes :
1. Environnement de développement : installez Visual Studio ou tout autre environnement de développement .NET préféré.
2.  Bibliothèque GroupDocs.Parser : téléchargez et référencez la bibliothèque GroupDocs.Parser. Vous pouvez obtenir la bibliothèque depuis[ici](https://releases.groupdocs.com/parser/net/).
3. Exemple de fichier Excel : préparez un exemple de fichier Excel à partir duquel vous souhaitez extraire des images.
## Importer des espaces de noms
Incluez les espaces de noms nécessaires dans votre projet :
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Suivez ces étapes pour extraire des images d'un document Excel :
## Étape 1 : instancier la classe Parser
 Tout d'abord, créez une instance de`Parser` classe en fournissant le chemin d’accès à votre fichier Excel.
```csharp
using (Parser parser = new Parser("YourSampleFile.xlsx"))
{
    // Votre code ici...
}
```
## Étape 2 : Récupérer des images du document Excel
 Utilisez le`GetImages()` méthode pour extraire des images du fichier Excel.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## Étape 3 : Définir les options d’extraction d’images
Spécifiez le format d'image et d'autres options pour enregistrer les images extraites. Par exemple, pour enregistrer des images au format PNG :
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## Étape 4 : Itérer et enregistrer des images
Parcourez les images extraites et enregistrez chaque image dans un fichier.
```csharp
int imageNumber = 0;
foreach (PageImageArea image in images)
{
    // Enregistrez l'image dans un fichier PNG
    image.Save(imageNumber.ToString() + ".png", options);
    imageNumber++;
}
```
## Conclusion
Dans ce didacticiel, vous avez appris à utiliser GroupDocs.Parser pour .NET pour extraire des images d'un document Excel. En suivant ces étapes, vous pouvez intégrer efficacement des fonctionnalités d'extraction d'images dans vos applications .NET.

## FAQ
### Q : GroupDocs.Parser peut-il extraire des images d’autres formats de documents qu’Excel ?
R : Oui, GroupDocs.Parser prend en charge un large éventail de formats de documents, notamment Word, PowerPoint, PDF, etc.
### Q : Comment puis-je obtenir de l'aide ou de l'aide pour l'intégration de GroupDocs.Parser ?
 R : Pour obtenir de l'aide et de l'aide, visitez le[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).
### Q : L'utilisation de GroupDocs.Parser est-elle gratuite ?
 R : GroupDocs.Parser propose un essai gratuit, mais pour une utilisation continue, vous devrez peut-être acheter une licence. Vérifier la[prix et licences](https://purchase.groupdocs.com/buy)détails.
### Q : Puis-je essayer GroupDocs.Parser avant d'acheter une licence ?
 R : Oui, vous pouvez obtenir un[essai gratuit](https://releases.groupdocs.com/) pour évaluer GroupDocs.Parser.
### Q : Où puis-je trouver une documentation détaillée pour GroupDocs.Parser ?
 R : Reportez-vous au document complet[Documentation](https://tutorials.groupdocs.com/parser/net/) pour des informations détaillées sur l’utilisation de GroupDocs.Parser.