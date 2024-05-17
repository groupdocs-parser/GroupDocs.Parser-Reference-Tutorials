---
title: Rechercher du texte dans un document Word par mot-clé
linktitle: Rechercher du texte dans un document Word par mot-clé
second_title: API GroupDocs.Parser .NET
description: Découvrez comment rechercher du texte dans des documents Word à l'aide de GroupDocs.Parser pour .NET. Extrayez efficacement des mots-clés spécifiques.
type: docs
weight: 18
url: /fr/net/word-document-processing/search-text-in-word-document-by-keyword/
---
## Introduction
Dans ce didacticiel, nous verrons comment utiliser GroupDocs.Parser pour .NET pour rechercher du texte spécifique dans un document Word à l'aide de C#. GroupDocs.Parser est une bibliothèque puissante qui permet aux développeurs d'extraire du texte et des métadonnées de divers formats de documents, y compris des documents Word.
## Conditions préalables
Avant de commencer, assurez-vous de disposer des prérequis suivants :
1. Environnement de développement : installez Visual Studio ou un autre IDE compatible.
2.  Bibliothèque GroupDocs.Parser : téléchargez et installez la bibliothèque GroupDocs.Parser pour .NET à partir du[site web](https://releases.groupdocs.com/parser/net/).
3. Exemple de document Word : préparez un exemple de document Word à utiliser pour la recherche de texte.

## Importer des espaces de noms
Commencez par importer les espaces de noms nécessaires dans votre projet C# :
```csharp
using System;
using System.Collections.Generic;
using System.Text;
using GroupDocs.Parser.Data;
```
## Étape 1 : Créer une instance de la classe Parser
 Tout d'abord, créez une instance de`Parser` classe en transmettant le chemin d’accès à votre exemple de document Word.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Le code va ici
}
```
## Étape 2 : Rechercher un mot-clé
 Ensuite, utilisez le`Search` méthode du`Parser` classe pour rechercher un mot-clé spécifique dans le document.
```csharp
IEnumerable<SearchResult> searchResults = parser.Search("keyword");
```
 Remplacer`"keyword"` avec le texte que vous souhaitez rechercher dans le document.
## Étape 3 : Parcourir les résultats de recherche
 Parcourez les résultats de la recherche à l'aide d'un`foreach` boucle pour accéder à chacun`SearchResult` objet.
```csharp
foreach (SearchResult result in searchResults)
{
    //Code pour gérer chaque résultat de recherche
}
```
## Étape 4 : Accéder aux détails des résultats de la recherche
 Dans la boucle, vous pouvez accéder à la position et au texte de chaque résultat de recherche en utilisant le`Position` et`Text` propriétés du`SearchResult` objet.
```csharp
foreach (SearchResult result in searchResults)
{
    Console.WriteLine($"At {result.Position}: {result.Text}");
}
```
Cet extrait de code imprime l'index (`Position`) et le texte trouvé (`Text`) pour chaque résultat de recherche vers la console.

## Conclusion
Dans ce didacticiel, vous avez appris à utiliser GroupDocs.Parser pour .NET pour rechercher du texte spécifique dans un document Word. Cette bibliothèque offre un moyen pratique d'extraire et de manipuler le contenu de divers formats de documents par programmation.

## FAQ
### GroupDocs.Parser peut-il gérer d’autres formats de documents que Word ?
Oui, GroupDocs.Parser prend en charge un large éventail de formats, notamment PDF, Excel, PowerPoint, etc.
### GroupDocs.Parser est-il compatible avec .NET Core ?
Oui, GroupDocs.Parser est compatible avec .NET Framework et .NET Core.
### Comment puis-je obtenir une licence temporaire pour GroupDocs.Parser ?
 Vous pouvez demander une licence temporaire auprès du[Page d'achat de GroupDocs](https://purchase.groupdocs.com/temporary-license/).
### Où puis-je trouver une assistance supplémentaire ou poser des questions sur GroupDocs.Parser ?
 Visiter le[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) pour le soutien et les discussions de la communauté.
### Puis-je essayer GroupDocs.Parser gratuitement avant d’acheter ?
 Oui, vous pouvez télécharger une version d'essai gratuite à partir du[Page des versions de GroupDocs](https://releases.groupdocs.com/).