---
title: Extraire le texte formaté de la page du document
linktitle: Extraire le texte formaté de la page du document
second_title: API GroupDocs.Parser .NET
description: Extrayez le texte formaté des pages de document à l'aide de GroupDocs.Parser pour .NET. Solution d'extraction de texte efficace et fiable.
weight: 11
url: /fr/net/formatted-text-extraction/extract-formatted-text-from-document-page/
---

# Extraire le texte formaté de la page du document

## Introduction
Dans ce didacticiel, nous vous guiderons tout au long du processus d'extraction de texte formaté à partir de pages de document à l'aide de GroupDocs.Parser pour .NET. Cette bibliothèque vous permet d'analyser et d'extraire efficacement du texte à partir de divers formats de documents tels que PDF, Word, Excel, etc.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
- Visual Studio installé sur votre système.
- Connaissance de base de la programmation C#.
-  GroupDocs.Parser pour la bibliothèque .NET. Vous pouvez le télécharger[ici](https://releases.groupdocs.com/parser/net/).

## Importer des espaces de noms
Tout d’abord, commencez par importer les espaces de noms nécessaires dans votre projet C#.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Parser.Options;
```
## Étape 1 : Créer une instance de la classe Parser
 Commencez par créer une instance de`Parser` classe en fournissant le chemin d’accès à votre exemple de fichier.
```csharp
using (Parser parser = new Parser("YourSampleFile.pdf"))
{
    // Le code ira ici
}
```
## Étape 2 : Vérifiez si l’extraction de texte formaté est prise en charge
Avant de procéder à l'extraction de texte, vérifiez si le document prend en charge l'extraction de texte formaté.
```csharp
if (!parser.Features.FormattedText)
{
    Console.WriteLine("Document does not support formatted text extraction.");
    return;
}
```
## Étape 3 : obtenir des informations sur le document
Récupérez des informations sur le document, telles que le nombre de pages.
```csharp
IDocumentInfo documentInfo = parser.GetDocumentInfo();
if (documentInfo.PageCount == 0)
{
    Console.WriteLine("Document has no pages.");
    return;
}
```
## Étape 4 : Parcourir les pages du document et extraire le texte formaté
Parcourez chaque page du document et extrayez le texte formaté à l'aide des options spécifiées (par exemple, le format Markdown).
```csharp
for (int p = 0; p < documentInfo.PageCount; p++)
{
    Console.WriteLine($"Page {p + 1}/{documentInfo.PageCount}");
    
    using (TextReader reader = parser.GetFormattedText(p, new FormattedTextOptions(FormattedTextMode.Markdown)))
    {
        Console.WriteLine(reader.ReadToEnd());
    }
}
```

## Conclusion
Vous savez maintenant comment extraire du texte formaté à partir de pages de document à l'aide de GroupDocs.Parser pour .NET. Cette bibliothèque fournit une solution puissante et facile à utiliser pour l'extraction de texte à partir de différents formats de fichiers.

## FAQ
### GroupDocs.Parser peut-il gérer différents formats de fichiers ?
Oui, GroupDocs.Parser prend en charge un large éventail de formats de documents, notamment PDF, DOCX, XLSX, PPTX, etc.
### GroupDocs.Parser est-il compatible avec .NET Core ?
Oui, GroupDocs.Parser prend en charge .NET Core et .NET Framework.
### GroupDocs.Parser préserve-t-il le formatage du texte lors de l'extraction ?
Oui, GroupDocs.Parser peut conserver le formatage tel que les styles et les polices lors de l'extraction du texte.
### Puis-je extraire des images et des métadonnées à l’aide de GroupDocs.Parser ?
Oui, GroupDocs.Parser permet l'extraction d'images, de métadonnées et de texte à partir de documents.
### Comment puis-je obtenir de l’aide pour GroupDocs.Parser ?
 Vous pouvez bénéficier du soutien du[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17).