---
title: Charger un document à partir d'un flux
linktitle: Charger un document à partir d'un flux
second_title: API GroupDocs.Parser .NET
description: Découvrez comment extraire du texte de différents formats de documents dans .NET à l'aide de GroupDocs.Parser. Guide étape par étape avec des exemples de code.
weight: 12
url: /fr/net/document-loading/load-document-from-stream/
---
## Introduction
Dans le domaine du traitement de documents dans les applications .NET, l’extraction de texte à partir de différents formats de fichiers est une exigence courante. GroupDocs.Parser pour .NET offre une solution puissante pour analyser et extraire de manière transparente le texte d'une gamme diversifiée de documents. Ce didacticiel vous guidera tout au long du processus d'utilisation de GroupDocs.Parser pour extraire le texte des documents étape par étape.
## Conditions préalables
Avant de vous lancer dans l'utilisation de GroupDocs.Parser pour .NET, assurez-vous d'avoir la configuration suivante :
- Environnement de développement : Visual Studio ou tout autre environnement de développement .NET.
-  Package GroupDocs.Parser pour .NET : téléchargez et installez la bibliothèque GroupDocs.Parser pour .NET à partir de[ici](https://releases.groupdocs.com/parser/net/).
- Exemples de documents : préparez des exemples de documents pour l'extraction de texte.
## Importation d'espaces de noms
Commencez par importer les espaces de noms nécessaires dans votre projet .NET pour accéder aux fonctionnalités GroupDocs.Parser.
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
```

Les étapes suivantes montrent comment extraire le texte d'un document à l'aide de GroupDocs.Parser à partir d'un flux.
## Étape 1 : Charger le document à partir du flux
```csharp
// Créer le flux
using (Stream stream = File.OpenRead("YourSampleFile.docx"))
{
    // Créer une instance de la classe Parser avec le flux
    using (Parser parser = new Parser(stream))
    {
        // Extraire le texte dans le lecteur
        using (TextReader reader = parser.GetText())
        {
            // Imprimer le texte du document
            // Si l'extraction de texte n'est pas prise en charge, le lecteur sera nul
            Console.WriteLine(reader == null ? "Text extraction isn't supported" : reader.ReadToEnd());
        }
    }
}
```
Dans cet exemple :
- Nous ouvrons un flux de fichiers pour le fichier de document (`YourSampleFile.docx`).
-  Initialiser un`Parser` exemple avec le flux.
-  Utiliser`parser.GetText()` pour récupérer un`TextReader` contenant le texte extrait.
- Imprimez le texte extrait ou un message si l'extraction de texte n'est pas prise en charge pour le format de document.
## Conclusion
GroupDocs.Parser pour .NET simplifie l'extraction de texte à partir de divers formats de documents, permettant aux développeurs de traiter et d'utiliser efficacement le contenu textuel dans leurs applications. En suivant les étapes décrites dans ce didacticiel, vous pouvez intégrer de manière transparente les fonctionnalités d'extraction de texte de document dans vos projets .NET.

## FAQ
### Quels formats de documents sont pris en charge par GroupDocs.Parser pour .NET ?
GroupDocs.Parser prend en charge une large gamme de formats de documents, notamment DOCX, PDF, XLSX, PPTX, EPUB, etc.
### GroupDocs.Parser peut-il extraire des images ou des métadonnées de documents ?
Oui, GroupDocs.Parser peut extraire des images, des métadonnées et du texte de différents types de documents.
### GroupDocs.Parser est-il compatible avec les applications .NET Core ?
Oui, GroupDocs.Parser est compatible avec les applications .NET Framework et .NET Core.
### Comment puis-je obtenir une licence temporaire pour GroupDocs.Parser ?
 Vous pouvez obtenir une licence temporaire auprès de[ici](https://purchase.groupdocs.com/temporary-license/).
### Où puis-je trouver plus d’assistance ou de documentation pour GroupDocs.Parser ?
 Pour une assistance supplémentaire, visitez le[Forum GroupDocs.Parser](https://forum.groupdocs.com/c/parser/17) ou se référer au[Documentation](https://tutorials.groupdocs.com/parser/net/).
