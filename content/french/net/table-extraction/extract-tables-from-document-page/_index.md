---
title: Extraire des tableaux de la page du document
linktitle: Extraire des tableaux de la page du document
second_title: API GroupDocs.Parser .NET
description: Découvrez comment extraire des tables de documents par programmation à l'aide de GroupDocs.Parser pour .NET. Ce didacticiel complet fournit des conseils étape par étape.
type: docs
weight: 11
url: /fr/net/table-extraction/extract-tables-from-document-page/
---
## Introduction
Dans ce didacticiel, nous allons explorer comment extraire des tableaux d'une page de document à l'aide de GroupDocs.Parser pour .NET. GroupDocs.Parser est une bibliothèque puissante qui permet aux développeurs de travailler avec différents formats de documents tels que PDF, DOCX, XLSX, etc. En tirant parti de ses fonctionnalités, nous pouvons extraire efficacement des données structurées telles que des tableaux de ces documents, ce qui nous permet de manipuler et d'analyser les informations par programme.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
- Visual Studio installé sur votre ordinateur.
- Compréhension de base du développement C# et .NET.
-  GroupDocs.Parser pour la bibliothèque .NET. Vous pouvez le télécharger depuis[ici](https://releases.groupdocs.com/parser/net/).
- Accès à un exemple de document (PDF, DOCX, etc.) contenant des tableaux à extraire.

## Importer des espaces de noms
Tout d’abord, commencez par importer les espaces de noms nécessaires dans votre projet C# :
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
 Instancier le`Parser` class en fournissant le chemin d’accès à votre exemple de document :
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    //Votre code continue ici...
}
```
## Étape 2 : Vérifier la prise en charge de l'extraction des tables de documents
Avant de continuer, vérifiez si le document prend en charge l'extraction de table :
```csharp
if (!parser.Features.Tables)
{
    Console.WriteLine("Document does not support table extraction.");
    return;
}
```
## Étape 3 : Définir la disposition du tableau
Définir la disposition des tableaux à extraire du document. Spécifiez les largeurs de colonnes et les hauteurs de lignes en fonction de la structure de votre document :
```csharp
TemplateTableLayout layout = new TemplateTableLayout(
    new double[] { 50, 95, 275, 415, 485, 545 },  // Largeurs de colonnes
    new double[] { 325, 340, 365, 395 });         // Hauteurs de rangée
```
## Étape 4 : configurer les options d'extraction de table
Créez des options pour l'extraction de table en utilisant la disposition spécifiée :
```csharp
PageTableAreaOptions options = new PageTableAreaOptions(layout);
```
## Étape 5 : Récupérer les informations du document
Récupérez des informations sur le document, y compris le nombre de pages :
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Étape 6 : Parcourir les pages du document
Parcourez chaque page du document pour extraire des tableaux :
```csharp
for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
{
    Console.WriteLine($"Page {pageIndex + 1}/{documentInfo.PageCount}");
    // Extraire les tableaux de la page actuelle
    IEnumerable<PageTableArea> tables = parser.GetTables(pageIndex, options);
    // Itérer sur les tables extraites
    foreach (PageTableArea table in tables)
    {
        // Parcourir les lignes du tableau
        for (int row = 0; row < table.RowCount; row++)
        {
            // Parcourir les colonnes du tableau
            for (int column = 0; column < table.ColumnCount; column++)
            {
                // Récupérer la cellule du tableau
                PageTableAreaCell cell = table[row, column];
                if (cell != null)
                {
                    // Imprimer le texte de la cellule du tableau
                    Console.Write(cell.Text);
                    Console.Write(" | ");
                }
            }
            Console.WriteLine();
        }
        Console.WriteLine();
    }
}
```

## Conclusion
Dans ce didacticiel, nous avons couvert le processus d'extraction de tableaux à partir de pages de document à l'aide de GroupDocs.Parser pour .NET. En suivant les étapes fournies, vous pouvez intégrer de manière transparente la fonctionnalité d'extraction de table dans vos applications .NET, permettant ainsi une gestion et une manipulation efficaces des données structurées dans les documents.

## FAQ
### GroupDocs.Parser peut-il extraire des tableaux de tous les types de documents ?
GroupDocs.Parser prend en charge divers formats de documents tels que PDF, DOCX, XLSX, etc., permettant l'extraction de tableaux à partir de types de fichiers compatibles.
### GroupDocs.Parser pour .NET est-il adapté au traitement de documents à grande échelle ?
Oui, GroupDocs.Parser est conçu pour gérer efficacement des documents volumineux, ce qui le rend adapté au traitement d'ensembles de données étendus.
### GroupDocs.Parser préserve-t-il le formatage lors de l'extraction de la table ?
Oui, GroupDocs.Parser conserve les détails de mise en forme tels que les bordures de cellules, les styles de texte et les alignements lors de l'extraction du tableau.
### Puis-je extraire des tableaux spécifiques en fonction de critères de contenu ?
GroupDocs.Parser offre des options flexibles pour cibler des tables spécifiques en fonction de modèles de mise en page ou de conditions de contenu pour l'extraction.
### GroupDocs.Parser est-il compatible avec .NET Core ?
Oui, GroupDocs.Parser est compatible avec les environnements .NET Framework et .NET Core.