---
title: Extraire les hyperliens du document
linktitle: Extraire les hyperliens du document
second_title: API GroupDocs.Parser .NET
description: Découvrez comment extraire des hyperliens à partir de documents à l’aide de GroupDocs.Parser pour .NET. Améliorez vos applications C# avec ce guide simple.
weight: 10
url: /fr/net/hyperlink-extraction/extract-hyperlinks-from-document/
---

# Extraire les hyperliens du document

## Introduction
Dans ce didacticiel, nous approfondirons les puissantes capacités de GroupDocs.Parser pour .NET, une bibliothèque polyvalente qui permet aux développeurs d'extraire facilement des hyperliens à partir de documents. L'extraction de liens hypertextes est une exigence courante dans le traitement de documents, en particulier lorsqu'il s'agit de fichiers texte tels que des documents PDF ou Word. En utilisant GroupDocs.Parser, vous pouvez identifier et extraire efficacement les hyperliens ainsi que leurs URL associées à partir de différents formats de documents.
## Conditions préalables
Avant de poursuivre ce didacticiel, assurez-vous de disposer des prérequis suivants :
- Connaissance de base de la programmation C#
- Visual Studio installé sur votre système
-  Bibliothèque GroupDocs.Parser pour .NET, téléchargeable[ici](https://releases.groupdocs.com/parser/net/)
## Importer des espaces de noms
Pour commencer, importez les espaces de noms nécessaires dans votre projet C# :
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```

Maintenant, décomposons chaque exemple en plusieurs étapes pour vous guider tout au long du processus d'extraction de lien hypertexte à l'aide de GroupDocs.Parser pour .NET :
## Étape 1 : Créer une instance de la classe Parser
 Tout d’abord, instanciez le`Parser` class en fournissant le chemin d’accès à votre exemple de document :
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Votre code pour l'extraction de lien hypertexte ira ici
}
```
 Remplacer`"YourSampleFile.docx"` avec le chemin d'accès à votre document cible.
## Étape 2 : Vérifiez la prise en charge de l’extraction de liens hypertexte
Avant d'extraire des hyperliens, il est important de vérifier si le format du document prend en charge l'extraction d'hyperliens :
```csharp
if (!parser.Features.Hyperlinks)
{
    Console.WriteLine("Document doesn't support hyperlink extraction.");
    return;
}
```
Cette étape garantit que l’extraction de liens hypertextes est réalisable pour le document donné.
## Étape 3 : Extraire les hyperliens
 Procédez à l'extraction des hyperliens du document à l'aide du`GetHyperlinks()` méthode:
```csharp
IEnumerable<PageHyperlinkArea> hyperlinks = parser.GetHyperlinks();
```
 Cette ligne récupère une collection de`PageHyperlinkArea` objets contenant des informations de lien hypertexte.
## Étape 4 : Itérer sur les hyperliens extraits
Parcourez la collection de liens hypertextes extraits et récupérez leur texte et leur URL :
```csharp
foreach (PageHyperlinkArea hyperlink in hyperlinks)
{
    // Imprimer le texte du lien hypertexte
    Console.WriteLine(hyperlink.Text);
    
    // Imprimer l'URL du lien hypertexte
    Console.WriteLine(hyperlink.Url);
    Console.WriteLine(); // Ajoute une ligne vide pour plus de lisibilité
}
```
En itérant sur`hyperlinks` collection, vous pouvez accéder et imprimer le texte et l’URL de chaque lien hypertexte.
## Conclusion
Dans ce didacticiel, nous avons exploré comment extraire des hyperliens à partir de documents à l'aide de GroupDocs.Parser pour .NET. En tirant parti des fonctionnalités fournies par cette bibliothèque, les développeurs peuvent intégrer sans effort des capacités d'extraction de liens hypertexte dans leurs applications C#.

## FAQ
### GroupDocs.Parser peut-il gérer l’extraction de liens hypertextes à partir de différents formats de documents ?
Oui, GroupDocs.Parser prend en charge l'extraction de liens hypertexte à partir d'un large éventail de formats de fichiers, notamment PDF, Word, Excel, PowerPoint, etc.
### Existe-t-il un essai gratuit disponible pour GroupDocs.Parser ?
 Oui, vous pouvez accéder à un essai gratuit de GroupDocs.Parser[ici](https://releases.groupdocs.com/).
### Où puis-je trouver de la documentation pour GroupDocs.Parser ?
 Une documentation détaillée pour GroupDocs.Parser peut être trouvée[ici](https://tutorials.groupdocs.com/parser/net/).
### Comment puis-je obtenir une licence temporaire pour GroupDocs.Parser ?
 Vous pouvez obtenir une licence temporaire pour GroupDocs.Parser[ici](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs offre-t-il une assistance pour le dépannage ?
 Oui, vous pouvez demander de l'aide et de l'aide au dépannage sur GroupDocs[forum](https://forum.groupdocs.com/c/parser/17).