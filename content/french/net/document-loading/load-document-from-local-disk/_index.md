---
title: Charger un document à partir du disque local
linktitle: Charger un document à partir du disque local
second_title: API GroupDocs.Parser .NET
description: Découvrez comment extraire du texte de différents formats de documents à l'aide de GroupDocs.Parser pour .NET. Extraction de texte simple et efficace avec C#.
weight: 11
url: /fr/net/document-loading/load-document-from-local-disk/
---

# Charger un document à partir du disque local

## Introduction
Dans ce didacticiel, nous explorerons comment utiliser GroupDocs.Parser pour .NET pour extraire du texte à partir de documents. GroupDocs.Parser est une bibliothèque puissante qui permet aux développeurs d'analyser divers formats de documents et d'extraire le contenu du texte par programme. Nous couvrirons les étapes nécessaires pour démarrer l'extraction de texte à l'aide de cette bibliothèque.
## Conditions préalables
Avant de commencer, assurez-vous que les conditions préalables suivantes sont installées :
- Visual Studio installé sur votre système.
- Connaissance de base du langage de programmation C#.
-  Bibliothèque GroupDocs.Parser pour .NET installée (télécharger[ici](https://releases.groupdocs.com/parser/net/)).

## Importer des espaces de noms
Tout d’abord, vous devez importer les espaces de noms nécessaires dans votre projet C# :
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```
## Étape 1 : Charger le document à partir du disque local
 Commencez par charger un document depuis votre disque local. Remplacer`"Your Sample File"` avec le chemin d'accès à votre document cible.
```csharp
// Définir le chemin du fichier
string filePath = "Your Sample File";
// Créez une instance de la classe Parser avec le filePath
using (Parser parser = new Parser(filePath))
{
    // Extraire le texte dans le lecteur
    using (TextReader reader = parser.GetText())
    {
        //Imprimer le texte extrait du document
        // Si l'extraction de texte n'est pas prise en charge, le lecteur sera nul
        Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
    }
}
```
## Explication des étapes
1. Définition du chemin du fichier : commencez par spécifier le chemin d'accès au document dont vous souhaitez extraire le texte (`filePath` variable).
2.  Création d'une instance d'analyseur : instancier le`Parser` classe en réussissant le`filePath`.
3.  Extraire du texte : utilisez le`GetText()` méthode du`Parser` exemple pour obtenir un`TextReader` objet contenant le texte extrait du document.
4.  Lecture du texte extrait : utilisez le`ReadToEnd()` méthode du`TextReader` pour récupérer l'intégralité du contenu textuel extrait du document.
5.  Gestion des formats non pris en charge : si le format du document ne prend pas en charge l'extraction de texte, le`reader` l'objet sera`null`, et vous pouvez gérer ce scénario en conséquence.

## Conclusion
Dans ce didacticiel, nous avons couvert les étapes initiales pour extraire le texte d'un document à l'aide de GroupDocs.Parser pour .NET. Cette bibliothèque offre des fonctionnalités étendues pour l'analyse de documents, permettant aux développeurs de travailler efficacement avec différents formats de fichiers au sein de leurs applications.

## FAQ
### GroupDocs.Parser est-il compatible avec tous les formats de documents ?
GroupDocs.Parser prend en charge un large éventail de formats, notamment les PDF, les documents Microsoft Office (Word, Excel, PowerPoint), etc.
### Puis-je extraire des métadonnées avec du texte à l’aide de GroupDocs.Parser ?
Oui, GroupDocs.Parser permet l'extraction à la fois du contenu textuel et des métadonnées des formats de documents pris en charge.
### Où puis-je trouver plus de ressources et d’assistance pour GroupDocs.Parser ?
 Visiter le[Documentation GroupDocs.Parser](https://tutorials.groupdocs.com/parser/net/) pour une référence détaillée sur l'API et explorez le[Forum GroupDocs](https://forum.groupdocs.com/c/parser/17) pour le soutien de la communauté.
### Comment puis-je obtenir une licence temporaire pour GroupDocs.Parser ?
 Vous pouvez demander un[permis temporaire](https://purchase.groupdocs.com/temporary-license/) à des fins d’évaluation et de test.
### Existe-t-il un essai gratuit disponible pour GroupDocs.Parser ?
 Oui, vous pouvez télécharger un[essai gratuit](https://releases.groupdocs.com/) version de GroupDocs.Parser.