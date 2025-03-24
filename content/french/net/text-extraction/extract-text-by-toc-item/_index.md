---
title: Extraire le texte par élément de la table des matières (TOC)
linktitle: Extraire le texte par élément de la table des matières (TOC)
second_title: API GroupDocs.Parser .NET
description: Extrayez le texte par table des matières (TOC) à l'aide de GroupDocs.Parser pour .NET. Apprenez des techniques efficaces d’analyse de documents pour l’extraction de données structurées.
weight: 15
url: /fr/net/text-extraction/extract-text-by-toc-item/
---

# Extraire le texte par élément de la table des matières (TOC)

## Introduction
Dans ce didacticiel, nous explorerons comment utiliser GroupDocs.Parser pour .NET pour extraire du texte basé sur les éléments de la table des matières (TOC) des documents. GroupDocs.Parser est un outil puissant qui permet une analyse et une extraction efficaces de documents.
## Conditions préalables
Avant de poursuivre ce didacticiel, assurez-vous de disposer des prérequis suivants :
1. Visual Studio : installez Visual Studio IDE sur votre système.
2.  GroupDocs.Parser pour .NET : téléchargez et installez GroupDocs.Parser pour .NET à partir de[ici](https://releases.groupdocs.com/parser/net/).
3. Un exemple de document avec table des matières : préparez un document (par exemple, PDF, DOCX) contenant une table des matières.

## Importation d'espaces de noms
Tout d’abord, incluez les espaces de noms nécessaires dans votre projet C# :
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
```
## Étape 1 : Créer une instance de la classe Parser
 Instancier le`Parser` class avec le chemin d'accès à votre exemple de document :
```csharp
using (Parser parser = new Parser("YourSampleFileWithToc"))
{
    // Continuez avec les étapes suivantes ici...
}
```
## Étape 2 : Extraire la table des matières (TOC)
Obtenez les éléments de la table des matières (TOC) du document :
```csharp
IEnumerable<TocItem> tocItems = parser.GetToc();
if (tocItems == null)
{
    Console.WriteLine("Table of contents extraction isn't supported");
    return;
}
```
## Étape 3 : Parcourir les éléments de la table des matières et extraire le texte
Parcourez chaque élément de la table des matières et extrayez le texte correspondant :
```csharp
foreach (TocItem tocItem in tocItems)
{
    using (TextReader reader = tocItem.ExtractText())
    {
        Console.WriteLine("----");
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Conclusion
Ce didacticiel a montré comment extraire le texte d'un document basé sur des éléments de table des matières (TOC) à l'aide de GroupDocs.Parser pour .NET. En suivant les étapes décrites, vous pouvez analyser et extraire efficacement le contenu spécifique de vos documents par programmation.

## FAQ
### Quels formats de fichiers GroupDocs.Parser prend-il en charge ?
GroupDocs.Parser prend en charge un large éventail de formats de documents, notamment PDF, Microsoft Word (DOC/DOCX), Excel (XLS/XLSX), PowerPoint (PPT/PPTX), etc.
### Puis-je extraire des données structurées telles que des tableaux ou des images à l'aide de GroupDocs.Parser ?
Oui, GroupDocs.Parser fournit des API pour extraire des données structurées telles que des tableaux, des images et des métadonnées à partir de divers types de documents.
### GroupDocs.Parser est-il adapté aux documents volumineux ?
GroupDocs.Parser est optimisé pour gérer efficacement des documents volumineux, permettant une extraction transparente du contenu de fichiers volumineux.
### Comment puis-je obtenir une assistance technique pour GroupDocs.Parser ?
 Vous pouvez demander une assistance technique et interagir avec la communauté à[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).
### GroupDocs propose-t-il un essai gratuit pour évaluation ?
Oui, vous pouvez télécharger une version d'essai gratuite de GroupDocs.Parser à partir de[ici](https://releases.groupdocs.com/).