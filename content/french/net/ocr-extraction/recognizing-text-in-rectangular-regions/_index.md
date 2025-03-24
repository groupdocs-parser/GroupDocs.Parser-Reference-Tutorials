---
title: Reconnaissance du texte dans les régions rectangulaires
linktitle: Reconnaissance du texte dans les régions rectangulaires
second_title: API GroupDocs.Parser .NET
description: Découvrez comment reconnaître du texte dans des régions spécifiques de documents à l'aide de GroupDocs.Parser pour .NET avec fonctionnalités OCR.
weight: 14
url: /fr/net/ocr-extraction/recognizing-text-in-rectangular-regions/
---
## Introduction
Dans ce didacticiel, nous verrons comment utiliser GroupDocs.Parser pour .NET pour reconnaître le texte dans des régions rectangulaires spécifiques des documents. GroupDocs.Parser est une bibliothèque puissante qui permet aux développeurs d'extraire du texte, des métadonnées et bien plus encore à partir de divers formats de fichiers, notamment PDF, Word, Excel et PowerPoint.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir la configuration suivante :
-  GroupDocs.Parser pour .NET : téléchargez et installez la bibliothèque à partir de[ici](https://releases.groupdocs.com/parser/net/).
- Environnement de développement : Visual Studio ou tout autre IDE .NET.
- Exemple de document : disposez d'un exemple de fichier (par exemple, PDF, DOCX) contenant du texte à reconnaître.

## Importer des espaces de noms
Tout d'abord, vous devrez importer les espaces de noms nécessaires dans votre code C# :
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using System.Linq;
using System.Text;
using Aspose.OCR;
using GroupDocs.Parser.Data;
using GroupDocs.Parser.Options;
```
## Étape 1 : initialiser les paramètres de l'analyseur
 Commencez par configurer le`ParserSettings` avec le connecteur OCR. Ici, nous utiliserons le connecteur sur site Aspose OCR :
```csharp
ParserSettings settings = new ParserSettings(new AsposeOcrOnPremise());
```
## Étape 2 : Créer une instance d'analyseur
 Ensuite, instanciez le`Parser` classe avec les paramètres définis précédemment :
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf", settings))
{
    // Le code continue ici
}
```
 Remplacer`"YourSampleFile.pdf"` avec le chemin d'accès à votre document.
## Étape 3 : Définir le rectangle OCR
 Définissez un rectangle dans le document où la reconnaissance de texte sera effectuée. Par exemple, un rectangle commençant à`(0, 0)` avec largeur`400` et la hauteur`200`:
```csharp
OcrOptions ocrOptions = new OcrOptions(new Data.Rectangle(0, 0, 400, 200));
```
## Étape 4 : configurer les options de reconnaissance de texte
 Créer`TextOptions` pour spécifier l'utilisation de l'OCR avec le rectangle défini :
```csharp
TextOptions options = new TextOptions(false, true, ocrOptions);
```
## Étape 5 : Extraire le texte à l’aide de l’OCR
 Utilisez le`GetText` méthode du`Parser` instance avec le configuré`TextOptions`:
```csharp
using (TextReader reader = parser.GetText(options))
{
    // Lire le texte extrait ou gérer le cas « non pris en charge »
    Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
}
```

## Conclusion
Dans ce didacticiel, nous avons montré comment exploiter GroupDocs.Parser pour .NET pour extraire le texte de régions rectangulaires spécifiques dans des documents à l'aide de l'OCR. Ce processus peut être davantage personnalisé et intégré à diverses applications pour des tâches d'extraction de texte automatisées.

## FAQ
### GroupDocs.Parser peut-il extraire le texte des documents numérisés ?
Oui, GroupDocs.Parser prend en charge la reconnaissance optique de caractères (OCR) pour extraire le texte des documents numérisés.
### Quels formats de fichiers GroupDocs.Parser prend-il en charge ?
GroupDocs.Parser prend en charge un large éventail de formats de fichiers, notamment PDF, DOCX, XLSX, PPTX, etc.
### Comment puis-je gérer des documents qui ne sont pas pris en charge pour l'extraction de texte ?
 Vous pouvez vérifier si l'extraction de texte est prise en charge en utilisant`TextReader` instance renvoyée par`parser.GetText(options)`.
### GroupDocs.Parser est-il adapté aux tâches d’extraction de texte à grande échelle ?
Oui, GroupDocs.Parser est conçu pour gérer efficacement les tâches d'extraction de texte à grande échelle.
### Où puis-je obtenir de l’aide pour les problèmes liés à GroupDocs.Parser ?
 Pour obtenir de l'aide et des discussions, visitez le[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).