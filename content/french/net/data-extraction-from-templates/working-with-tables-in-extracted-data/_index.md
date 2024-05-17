---
title: Travailler avec des tables dans des données extraites
linktitle: Travailler avec des tables dans des données extraites
second_title: API GroupDocs.Parser .NET
description: Découvrez comment extraire des données de table à partir de documents à l'aide de GroupDocs.Parser pour .NET. Analysez efficacement le contenu structuré avec des modèles prédéfinis.
type: docs
weight: 12
url: /fr/net/data-extraction-from-templates/working-with-tables-in-extracted-data/
---
## Introduction
Dans ce didacticiel, nous explorerons comment utiliser GroupDocs.Parser pour .NET pour extraire des données de tables dans des documents. GroupDocs.Parser est un outil puissant qui permet aux développeurs d'analyser et d'extraire du texte, des métadonnées et du contenu structuré à partir de divers formats de fichiers tels que PDF, DOCX, XLSX, etc. Plus précisément, nous nous concentrerons sur l’extraction efficace des données de table à l’aide de modèles prédéfinis.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir mis en place les éléments suivants :
- Visual Studio installé sur votre ordinateur.
- Compréhension de base du framework C# et .NET.
- Bibliothèque GroupDocs.Parser installée via le gestionnaire de packages NuGet.

## Importer des espaces de noms
Commencez par importer les espaces de noms nécessaires pour travailler avec GroupDocs.Parser et les fonctionnalités associées.
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Templates;
```
## Étape 1 : Créer un modèle de tableau
Pour extraire des données de tables, commencez par définir un modèle qui représente la structure de la table que vous souhaitez extraire. Spécifiez l'emplacement et les dimensions du tableau dans le document.
```csharp
// Définir les paramètres du tableau (emplacement et taille)
TemplateTableParameters parameters = new TemplateTableParameters(new Rectangle(new Point(35, 320), new Size(530, 55)), null);
// Créer un modèle de tableau avec des paramètres
TemplateTable table = new TemplateTable(parameters, "Details", null);
```
## Étape 2 : définir un modèle
Créez un modèle qui inclut le modèle de tableau que vous avez défini. Ce modèle guidera l'analyseur sur ce qu'il faut rechercher lors de l'extraction des données du tableau.
```csharp
// Créer un modèle avec le tableau
Template template = new Template(new TemplateItem[] { table });
```
## Étape 3 : analyser le document et extraire les données du tableau
Utilisez la classe Parser de GroupDocs.Parser pour analyser un document spécifique à l'aide du modèle que vous avez défini.
```csharp
// Spécifiez le chemin d'accès à votre exemple de fichier
string filePath = "YourSampleFile.pdf";
// Créer une instance de la classe Parser
using (Parser parser = new Parser(filePath))
{
    // Analyser le document par le modèle
    DocumentData data = parser.ParseByTemplate(template);
    // Itérer sur toutes les données extraites
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        // Vérifiez si le champ extrait est une table
        PageTableArea area = data[i].PageArea as PageTableArea;
        if (area == null)
        {
            continue;
        }
        // Itérer sur les lignes du tableau
        for (int row = 0; row < area.RowCount; row++)
        {
            // Itérer sur les colonnes du tableau
            for (int column = 0; column < area.ColumnCount; column++)
            {
                // Obtenez la valeur de la cellule
                PageTextArea cellValue = area[row, column].PageArea as PageTextArea;
                // Imprimer la valeur de la cellule (ou la chaîne vide si nulle)
                Console.Write(cellValue == null ? "" : cellValue.Text);
                // Imprimer un espace de tabulation entre les colonnes
                if (column > 0)
                {
                    Console.Write("\t");
                }
            }
            // Passer à la ligne suivante après avoir imprimé chaque ligne
            Console.WriteLine();
        }
    }
}
```

## Conclusion
Dans ce didacticiel, nous avons expliqué comment utiliser GroupDocs.Parser pour .NET pour extraire des données de table à partir de documents. En définissant des modèles et en utilisant des méthodes d'analyse, les développeurs peuvent extraire efficacement des données structurées telles que des tableaux à partir de différents formats de fichiers.

## FAQ
### GroupDocs.Parser est-il compatible avec tous les formats de documents ?
Oui, GroupDocs.Parser prend en charge un large éventail de formats de fichiers, notamment PDF, DOCX, XLSX, PPTX, etc.
### Puis-je extraire des données de régions spécifiques dans un document ?
Absolument, vous pouvez définir des modèles qui ciblent des zones spécifiques (comme les tableaux) dans un document à extraire.
### GroupDocs.Parser est-il adapté aux documents volumineux ?
Oui, GroupDocs.Parser est optimisé pour gérer efficacement des documents volumineux, permettant aux développeurs d'extraire des données de manière transparente.
### GroupDocs.Parser prend-il en charge l'extraction de texte ainsi que les données structurées ?
Oui, en plus de l'extraction de données structurées (comme les tableaux), GroupDocs.Parser peut extraire du texte brut et des métadonnées à partir de documents.
### Comment puis-je obtenir de l'aide ou de l'aide pour l'intégration de GroupDocs.Parser ?
 Pour obtenir de l'aide et des discussions, visitez le forum de la communauté GroupDocs[ici](https://forum.groupdocs.com/c/parser/17).