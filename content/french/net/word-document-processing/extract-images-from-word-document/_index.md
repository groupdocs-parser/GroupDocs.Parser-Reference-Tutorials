---
title: Extraire des images d'un document Word
linktitle: Extraire des images d'un document Word
second_title: API GroupDocs.Parser .NET
description: Découvrez comment extraire des images d'un document Word à l'aide de GroupDocs.Parser pour .NET. Ce didacticiel fournit des conseils étape par étape pour intégrer l'image dans votre .NET.
weight: 11
url: /fr/net/word-document-processing/extract-images-from-word-document/
---
## Introduction
Dans ce didacticiel, vous apprendrez à extraire des images d'un document Word à l'aide de GroupDocs.Parser pour .NET. GroupDocs.Parser est une puissante bibliothèque .NET qui vous permet d'analyser et d'extraire du texte, des métadonnées, des images et bien plus encore à partir de divers formats de documents, notamment Word (DOCX).
## Conditions préalables
Avant de commencer, assurez-vous d'avoir configuré les conditions préalables suivantes :
- Visual Studio installé sur votre ordinateur.
- Connaissance de base de la programmation C#.
- GroupDocs.Parser pour la bibliothèque .NET installée. Vous pouvez le télécharger depuis[ici](https://releases.groupdocs.com/parser/net/).
## Importer des espaces de noms
Tout d'abord, vous devez importer les espaces de noms nécessaires dans votre projet C# pour utiliser les fonctionnalités de GroupDocs.Parser :
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
Maintenant, décomposons le processus d'extraction d'images d'un document Word en étapes simples :
## Étape 1 : Créer une instance de la classe Parser
 Vous commencerez par créer une instance de`Parser`classe, fournissant le chemin d’accès à votre document Word en entrée.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Le code pour l'extraction d'images va ici
}
```
## Étape 2 : Extraire les images du document Word
 Ensuite, utilisez le`GetImages()` méthode du`Parser` objet pour extraire des images du document.
```csharp
IEnumerable<PageImageArea> images = parser.GetImages();
```
## Étape 3 : définir les options d'enregistrement des images
Spécifiez les options d'enregistrement des images extraites. Par exemple, vous pouvez choisir le format d'image (par exemple, PNG) et configurer d'autres paramètres.
```csharp
ImageOptions options = new ImageOptions(ImageFormat.Png);
```
## Étape 4 : Parcourir les images extraites et enregistrer
Parcourez chaque image extraite et enregistrez-la dans un fichier en utilisant les options spécifiées.
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
Dans ce didacticiel, vous avez appris à extraire des images d'un document Word à l'aide de GroupDocs.Parser pour .NET. En suivant ces étapes, vous pouvez facilement intégrer des fonctionnalités d'analyse de documents et d'extraction d'images dans vos applications .NET.

## FAQ
### GroupDocs.Parser peut-il extraire des images d’autres formats de documents que Word ?
Oui, GroupDocs.Parser prend en charge divers formats de documents, notamment PDF, PowerPoint, Excel, etc.
### Comment puis-je obtenir une licence temporaire pour GroupDocs.Parser ?
 Vous pouvez obtenir une licence temporaire à des fins de test auprès de[ici](https://purchase.groupdocs.com/temporary-license/).
### Où puis-je trouver plus de documentation sur GroupDocs.Parser pour .NET ?
 Vous pouvez vous référer à la documentation complète[ici](https://tutorials.groupdocs.com/parser/net/).
### Existe-t-il un essai gratuit disponible pour GroupDocs.Parser ?
 Oui, vous pouvez explorer les fonctionnalités de GroupDocs.Parser avec un essai gratuit disponible[ici](https://releases.groupdocs.com/).
### Comment puis-je obtenir de l’aide ou poser des questions relatives à GroupDocs.Parser ?
 Vous pouvez poster vos requêtes sur le[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).