---
title: Extraire des tableaux d'un document
linktitle: Extraire des tableaux d'un document
second_title: API GroupDocs.Parser .NET
description: Découvrez comment extraire des tableaux de documents à l'aide de Groupdocs.Parser pour .NET. Suivez-nous pour un guide détaillé sur l’intégration de cette fonctionnalité.
weight: 10
url: /fr/net/table-extraction/extract-tables-from-document/
---

# Extraire des tableaux d'un document

## Introduction
Groupdocs.Parser pour .NET est une bibliothèque complète qui facilite l'analyse de documents, vous permettant d'extraire des informations précieuses telles que des tableaux, du texte, des métadonnées et bien plus encore à partir de documents. Dans ce didacticiel, nous nous concentrons spécifiquement sur l'extraction de tableaux à partir de documents à l'aide de l'API Groupdocs.Parser.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
- Visual Studio installé sur votre système.
- .NET Framework ou .NET Core installé.
- Connaissance de base de la programmation C#.

## Importer des espaces de noms
Tout d’abord, vous devez importer les espaces de noms nécessaires pour accéder aux classes et méthodes Groupdocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
using GroupDocs.Parser.Templates;
```
## Étape 1 : Créer une instance de la classe Parser
 Initialisez une nouvelle instance du`Parser` classe en fournissant le chemin d’accès à votre exemple de document.
```csharp
using (Parser parser = new Parser("YourSampleFile.docx"))
{
    // Votre code va ici
}
```
## Étape 2 : Vérifier la prise en charge de l'extraction de table
 Vérifiez si le document prend en charge l'extraction de table à l'aide de l'outil`Features` propriété du`Parser` classe.
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document doesn't support table extraction.");
    return;
}
```
## Étape 3 : Définir la disposition du tableau
Définissez la disposition des tableaux que vous souhaitez extraire à l'aide de`TemplateTableLayout`. Spécifiez les largeurs de colonnes et les hauteurs de lignes en fonction de la structure de votre document.
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },
    new double[] { 325, 340, 365, 395 });
```
## Étape 4 : Définir les options d'extraction de table
 Créer`PageTableAreaOptions` avec la mise en page définie pour spécifier comment les tables doivent être extraites.
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Étape 5 : Extraire les tableaux
 Utiliser le`GetTables` méthode du`Parser` classe pour extraire les tables du document en fonction des options spécifiées.
```csharp
IEnumerable<PageTableArea> tables = parser.GetTables(options);
```
## Étape 6 : Itérer et accéder aux données de la table
Parcourez les tables extraites et leurs lignes et colonnes respectives pour accéder aux données des cellules.
```csharp
foreach (PageTableArea table in tables)
{
    for (int row = 0; row < table.RowCount; row++)
    {
        for (int column = 0; column < table.ColumnCount; column++)
        {
            PageTableAreaCell cell = table[row, column];
            if (cell != null)
            {
                Console.Write(cell.Text);
                Console.Write(" | ");
            }
        }
        Console.WriteLine();
    }
    Console.WriteLine();
}
```
## Conclusion
Dans ce didacticiel, nous avons expliqué comment utiliser Groupdocs.Parser pour .NET pour extraire efficacement des tableaux de documents. En tirant parti des capacités de cette bibliothèque, vous pouvez intégrer l'extraction de tables dans vos applications .NET de manière transparente.

## FAQ
### Groupdocs.Parser peut-il gérer différents formats de documents ?
Oui, Groupdocs.Parser prend en charge un large éventail de formats de documents, notamment DOCX, PDF, XLSX, etc.
### Existe-t-il une version d'essai disponible pour Groupdocs.Parser pour .NET ?
 Oui, vous pouvez télécharger un essai gratuit à partir de[ici](https://releases.groupdocs.com/).
### Comment puis-je obtenir de l'aide pour les requêtes liées à Groupdocs.Parser ?
 Vous pouvez visiter le[Forum Groupdocs.Parser](https://forum.groupdocs.com/c/parser/17) à l'aide.
### Où puis-je acheter une licence pour Groupdocs.Parser ?
 Vous pouvez acheter une licence auprès de[ici](https://purchase.groupdocs.com/buy).
### Comment puis-je obtenir une licence temporaire à des fins d'évaluation ?
 Vous pouvez obtenir un permis temporaire[ici](https://purchase.groupdocs.com/temporary-license/).