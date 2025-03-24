---
title: Extraire le texte d'une page dans un PDF en mode brut
linktitle: Extraire le texte d'une page dans un PDF en mode brut
second_title: API GroupDocs.Parser .NET
description: Extrayez le texte des PDF à l'aide de GroupDocs.Parser en C#. Apprenez à extraire efficacement du texte PDF avec cette puissante bibliothèque .NET.
weight: 16
url: /fr/net/pdf-processing/extract-text-from-page-in-pdf-in-raw-mode/
---

# Extraire le texte d'une page dans un PDF en mode brut

## Introduction
Dans ce didacticiel, nous verrons comment utiliser GroupDocs.Parser pour .NET pour extraire le texte des pages de documents PDF en mode brut. GroupDocs.Parser est un outil puissant qui permet aux développeurs de travailler avec différents formats de documents par programme.
## Conditions préalables
Avant de commencer ce didacticiel, assurez-vous d'avoir les éléments suivants :
- Visual Studio installé sur votre ordinateur.
- Connaissance de base de la programmation C#.
- Bibliothèque GroupDocs.Parser pour .NET, que vous pouvez[télécharger ici](https://releases.groupdocs.com/parser/net/).
- Un exemple de fichier PDF à des fins de test.

## Importer des espaces de noms
Tout d’abord, assurez-vous d’importer les espaces de noms nécessaires dans votre projet C# :
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Étape 1 : Créer une instance de la classe Parser
 Pour commencer, instanciez le`Parser`classe en fournissant le chemin d’accès à votre exemple de fichier PDF.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Votre code va ici
}
```
## Étape 2 : obtenir des informations sur le document et parcourir les pages
Ensuite, récupérez les informations du document et parcourez chaque page pour extraire le texte.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
for (int p = 0; p < documentInfo.RawPageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.RawPageCount}");
    // Votre code pour l'extraction de texte va ici
}
```
## Étape 3 : Extraire le texte de chaque page
 Dans la boucle, utilisez le`GetText` méthode pour extraire le texte de chaque page et l’imprimer.
```csharp
using (TextReader reader = parser.GetText(p, new TextOptions(true)))
{
    Console.WriteLine(reader.ReadToEnd());
}
```

## Conclusion
 Dans ce didacticiel, nous avons appris à extraire du texte de pages PDF en mode brut à l'aide de GroupDocs.Parser pour .NET. Ce processus consiste à créer un`Parser` Par exemple, obtenir des informations sur le document, parcourir chaque page et extraire du texte à l'aide de l'outil`GetText` méthode.

## FAQ
### Qu’est-ce que GroupDocs.Parser pour .NET ?
GroupDocs.Parser pour .NET est une API d'analyse de documents qui permet aux développeurs d'extraire du texte, des métadonnées et d'autres informations à partir de divers formats de fichiers par programme.
### Comment télécharger GroupDocs.Parser pour .NET ?
 Vous pouvez télécharger la bibliothèque à partir du[Site Web GroupDocs](https://releases.groupdocs.com/parser/net/).
### Existe-t-il un essai gratuit disponible ?
 Oui, vous pouvez accéder à un essai gratuit de GroupDocs.Parser pour .NET à partir de[ici](https://releases.groupdocs.com/).
### Où puis-je trouver de l’assistance pour GroupDocs.Parser pour .NET ?
 Pour une assistance technique et un soutien communautaire, visitez le[Forum GroupDocs](https://forum.groupdocs.com/c/parser/17).
### Comment puis-je acheter une licence pour GroupDocs.Parser pour .NET ?
 Vous pouvez acheter une licence auprès du[page d'achat](https://purchase.groupdocs.com/buy) ou acquérir une licence temporaire[ici](https://purchase.groupdocs.com/temporary-license/).