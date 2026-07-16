---
date: '2026-07-16'
description: Apprenez comment créer une miniature de feuille de calcul Java avec GroupDocs.Parser,
  preview Excel sans Office, et render Excel sheets as images. Ce guide couvre setup,
  implementation, et practical use cases.
keywords:
- create spreadsheet thumbnail java
- preview excel without office
- render excel sheets as images
lastmod: '2026-07-16'
og_description: Créer une miniature de feuille de calcul Java avec GroupDocs.Parser—preview
  Excel sans Office et render Excel sheets as images. Suivez ce guide step‑by‑step
  pour générer des previews PNG efficacement.
og_image_alt: 'Developer guide: Create spreadsheet thumbnail Java using GroupDocs.Parser'
og_title: Créer une miniature de feuille de calcul Java avec GroupDocs.Parser
schemas:
- author: GroupDocs
  dateModified: '2026-07-16'
  description: Learn how to create spreadsheet thumbnail Java with GroupDocs.Parser,
    preview Excel without Office, and render Excel sheets as images. This guide covers
    setup, implementation, and practical use cases.
  headline: Create Spreadsheet Thumbnail Java Using GroupDocs.Parser
  type: TechArticle
- description: Learn how to create spreadsheet thumbnail Java with GroupDocs.Parser,
    preview Excel without Office, and render Excel sheets as images. This guide covers
    setup, implementation, and practical use cases.
  name: Create Spreadsheet Thumbnail Java Using GroupDocs.Parser
  steps:
  - name: Initialize the Parser Instance
    text: '`Parser` is GroupDocs.Parser''s core class that provides read access to
      spreadsheet files and enables page‑wise rendering. Create a `Parser` object
      pointing at your Excel workbook. The *try‑with‑resources* block ensures the
      parser is closed automatically. > **Pro tip:** Use an absolute path or config'
  - name: Prepare Your Preview Options
    text: '`PreviewOptions` configures rendering parameters such as output format
      and DPI. `ICreatePageStream` is a callback interface that supplies an output
      stream for each generated page. Define how each page will be saved. The `ICreatePageStream`
      implementation returns a fresh `FileOutputStream` for every '
  - name: Attach a Delegate to Capture Render Info
    text: If you need details about each rendered sheet (e.g., dimensions, sheet name),
      register a callback.
  - name: Specify Output Format and DPI
    text: Select PNG as the image format and set a DPI that balances quality and file
      size. > Adjust the DPI if you need smaller thumbnails (e.g., 96) or high‑resolution
      prints (e.g., 300).
  - name: Generate the Previews
    text: With everything configured, call `generatePreview`. The SDK will iterate
      over each worksheet and invoke the stream you supplied.
  - name: Define the `getOutputPath()` Helper
    text: '`getOutputPath()` builds a file name based on the page (sheet) number and
      returns the full path for the output image. Feel free to customize the folder
      structure. > **Common pitfall:** Forgetting to create the `output` directory
      beforehand will cause an `IOException`. Create it programmatically or e'
  type: HowTo
- questions:
  - answer: Yes, the same API works for PDFs, Word documents, and many image formats.
    question: Can I generate previews for PDFs and images using GroupDocs.Parser?
  - answer: Call `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (or `Gif`,
      `Bmp`, etc.).
    question: How do I change the output image format?
  - answer: The SDK streams pages, which keeps memory usage low. For massive files,
      consider processing in parallel batches.
    question: Is performance a concern with very large workbooks?
  - answer: Wrap the code in try‑catch blocks (as shown) and log the exception details.
      Ensure streams are closed in the `finally` block if you’re not using try‑with‑resources.
    question: How can I handle errors during preview generation?
  - answer: No. GroupDocs.Parser is a pure Java solution and works on any platform
      that supports Java 8+.
    question: Does the library require Microsoft Office to be installed?
  type: FAQPage
tags:
- create spreadsheet thumbnail
- GroupDocs.Parser
- Java preview excel
- excel to png
- document processing
title: Créer une miniature de feuille de calcul Java avec GroupDocs.Parser
type: docs
url: /fr/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# Créer une vignette de feuille de calcul Java avec GroupDocs.Parser

Si vous cherchez à **créer des vignettes de feuilles de calcul Java**, vous êtes au bon endroit. Dans ce guide, nous expliquerons comment générer des aperçus PNG de haute qualité à partir de classeurs `.xlsx` à l’aide de GroupDocs.Parser pour Java — parfait pour des vignettes rapides, partager des instantanés ou créer une fonctionnalité d’aperçu de document dans votre application. La solution fonctionne sans installation de Microsoft Office et s’adapte aux classeurs volumineux tout en maintenant une faible utilisation de la mémoire.

## Réponses rapides
- **Que signifie « preview Excel » ?** Génération de fichiers image (par ex., PNG) représentant chaque page de feuille de calcul.  
- **Quel format est recommandé ?** PNG offre une qualité sans perte et convient bien aux vignettes web.  
- **Ai‑je besoin d’une licence ?** Un essai gratuit suffit pour le développement ; une licence commerciale est requise pour la production.  
- **Puis‑je modifier la résolution de l’image ?** Oui — ajustez le DPI dans `PreviewOptions`.  
- **Est‑il possible d’apercevoir d’autres formats ?** GroupDocs.Parser prend également en charge PDF, Word et de nombreux types d’images.

## Qu’est‑ce que « how to preview Excel » avec GroupDocs.Parser ?
Chargez votre classeur Excel et rendez chaque feuille sous forme d’image PNG sans nécessiter Microsoft Office. GroupDocs.Parser diffuse les pages une à une, produisant des vignettes sans perte qui peuvent être enregistrées sur le disque ou renvoyées via HTTP, ce qui le rend idéal pour les services d’aperçu basés sur le web.

GroupDocs.Parser lit les classeurs Excel, rend chaque feuille sous forme de page visuelle, et vous permet de diffuser ces pages vers des fichiers image. Cela élimine le besoin d’interopérabilité Office ou de convertisseurs tiers.

## Pourquoi utiliser GroupDocs.Parser pour les aperçus Excel ?
Vous devriez utiliser GroupDocs.Parser car il fonctionne sur n’importe quel serveur Java, ne nécessite aucune installation d’Office, gère les classeurs volumineux avec une faible consommation de mémoire, et produit des images PNG sans perte avec un DPI configurable. Le SDK prend en charge **plus de 100 formats d’entrée et de sortie**, peut traiter un classeur de 200 pages en moins de 3 secondes, et maintient l’utilisation de la mémoire en dessous de 50 Mo par feuille.

- **Aucune installation d’Office requise** – fonctionne sur tout environnement Java côté serveur.  
- **Prend en charge les gros fichiers** – diffuse les pages une par une, maintenant une faible utilisation de la mémoire.  
- **Sortie de haute qualité** – contrôle du DPI, du format et des options de rendu.  
- **Flexibilité multi‑format** – la même API fonctionne pour les PDF, les documents Word, et plus encore.

## Prérequis
- **Kit de développement Java** (8 +).  
- **IDE** tel qu’IntelliJ IDEA ou Eclipse.  
- **GroupDocs.Parser for Java SDK** – télécharger depuis [ici](https://releases.groupdocs.com/parser/java/).  
- **Documentation** – voir la [documentation officielle](https://docs.groupdocs.com/parser/java/).  
- **Fichier Excel d’exemple** (`.xlsx`) que vous souhaitez prévisualiser.  
- **Maven ou Gradle** (optionnel) pour la gestion des dépendances.

## Importer les packages
Ces importations vous donnent accès au parseur, aux options d’aperçu et aux utilitaires de gestion de flux.

```java
import com.groupdocs.parser.Parser;
import com.groupdocs.parser.options.PreviewOptions;
import com.groupdocs.parser.options.PreviewFormats;
import com.groupdocs.parser.options.ICreatePageStream;
import com.groupdocs.parser.options.IPreviewPageRender;
import com.groupdocs.parser.results.PageRenderInfo;
import java.io.FileOutputStream;
import java.io.OutputStream;
import java.io.IOException;
```

## Guide étape par étape pour générer des aperçus de pages de feuille de calcul

### Étape 1 : Initialiser l’instance du parseur
`Parser` est la classe principale de GroupDocs.Parser qui fournit un accès en lecture aux fichiers de feuille de calcul et permet le rendu page par page.  
Créez un objet `Parser` pointant vers votre classeur Excel. Le bloc *try‑with‑resources* garantit que le parseur est fermé automatiquement.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **Astuce :** Utilisez un chemin absolu ou configurez un dossier de ressources pour éviter `FileNotFoundException`.

### Étape 2 : Préparer vos options d’aperçu
`PreviewOptions` configure les paramètres de rendu tels que le format de sortie et le DPI.  
`ICreatePageStream` est une interface de rappel qui fournit un flux de sortie pour chaque page générée. Définissez comment chaque page sera enregistrée. L’implémentation de `ICreatePageStream` renvoie un nouveau `FileOutputStream` pour chaque page de feuille de calcul.

```java
PreviewOptions previewOptions = new PreviewOptions(new ICreatePageStream() {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        try {
            String outputPath = getOutputPath(pageNumber); // define this method later
            return new FileOutputStream(outputPath);
        } catch (IOException ex) {
            throw new RuntimeException("Error creating output stream", ex);
        }
    }
});
```

> Cette étape est celle où vous **convertissez xlsx en png** — le flux écrit les données PNG sur le disque.

### Étape 3 : Attacher un délégué pour capturer les informations de rendu
Si vous avez besoin de détails sur chaque feuille rendue (par ex., dimensions, nom de la feuille), enregistrez un rappel.

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### Étape 4 : Spécifier le format de sortie et le DPI
Sélectionnez PNG comme format d’image et définissez un DPI qui équilibre qualité et taille du fichier.

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> Ajustez le DPI si vous avez besoin de vignettes plus petites (par ex., 96) ou d’impressions haute résolution (par ex., 300).

### Étape 5 : Générer les aperçus
Une fois tout configuré, appelez `generatePreview`. Le SDK parcourra chaque feuille de calcul et invoquera le flux que vous avez fourni.

```java
parser.generatePreview(previewOptions);
```

### Étape 6 : Définir l’aide‑mémoire `getOutputPath()`
`getOutputPath()` construit un nom de fichier basé sur le numéro de page (feuille) et renvoie le chemin complet pour l’image de sortie. N’hésitez pas à personnaliser la structure du dossier.

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **Erreur courante :** Oublier de créer le répertoire `output` au préalable entraînera une `IOException`. Créez‑le programmétiquement ou assurez‑vous qu’il existe.

## Exemple complet fonctionnel (simplifié)

Voici une version compacte qui assemble tous les éléments. Elle démontre le flux de travail **create spreadsheet thumbnail Java** du début à la fin.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    final PageRenderInfo[] renderInfoHolder = {null};

    PreviewOptions options = new PreviewOptions(new ICreatePageStream() {
        @Override
        public OutputStream createPageStream(int pageNumber) {
            try {
                return new FileOutputStream(getOutputPath(pageNumber));
            } catch (IOException e) {
                throw new RuntimeException(e);
            }
        }
    });

    options.setPreviewPageRender(pageRenderInfo -> {
        renderInfoHolder[0] = pageRenderInfo;
    });
    options.setPreviewFormat(PreviewFormats.Png);
    options.setDpi(150);

    parser.generatePreview(options);
} catch (Exception e) {
    e.printStackTrace();
}
```

Exécutez cet extrait, et vous trouverez une série de fichiers `preview_page_1.png`, `preview_page_2.png`, … dans le dossier `output` — chacun représentant une feuille du classeur Excel original.

## Problèmes courants et solutions
| Problème | Cause | Solution |
|----------|-------|----------|
| **Aucune image générée** | `getOutputPath` renvoie un répertoire invalide | Assurez‑vous que le dossier cible existe ou créez‑le avec `new File("output").mkdirs();` |
| **Erreur de mémoire insuffisante sur de gros fichiers** | Chargement du classeur complet en une fois | Utilisez l’approche de diffusion (comme montré) et traitez les pages une à une |
| **DPI incorrect** | `setDpi` non appelé ou réglé sur la valeur par défaut (96) | Appelez `previewOptions.setDpi(votreValeurSouhaitée);` avant `generatePreview` |
| **Format non pris en charge** | Tentative d’aperçu d’un `.xlsx` corrompu | Validez le fichier avec Excel ou utilisez `Parser.isSupported` avant le traitement |

## Questions fréquentes

**Q : Puis‑je générer des aperçus pour les PDF et les images avec GroupDocs.Parser ?**  
**R :** Oui, la même API fonctionne pour les PDF, les documents Word et de nombreux formats d’image.

**Q : Comment changer le format d’image de sortie ?**  
**R :** Appelez `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (ou `Gif`, `Bmp`, etc.).

**Q : La performance est‑elle un problème avec des classeurs très volumineux ?**  
**R :** Le SDK diffuse les pages, ce qui maintient une faible utilisation de la mémoire. Pour les fichiers massifs, envisagez de traiter les pages en lots parallèles.

**Q : Comment gérer les erreurs lors de la génération d’aperçus ?**  
**R :** Enveloppez le code dans des blocs try‑catch (comme montré) et consignez les détails de l’exception. Assurez‑vous que les flux sont fermés dans le bloc `finally` si vous n’utilisez pas le try‑with‑resources.

**Q : La bibliothèque nécessite‑t‑elle l’installation de Microsoft Office ?**  
**R :** Non. GroupDocs.Parser est une solution pure Java et fonctionne sur toute plateforme supportant Java 8+.

---

**Dernière mise à jour :** 2026-07-16  
**Testé avec :** GroupDocs.Parser 23.11 (dernière version au moment de la rédaction)  
**Auteur :** GroupDocs

## Tutoriels associés

- [Comment générer un aperçu – Tutoriels de génération d’aperçus de pages de document pour GroupDocs.Parser Java](/parser/java/page-preview-generation/)
- [Analyser Excel Java avec GroupDocs.Parser : Guide complet](/parser/java/getting-started/mastering-document-parsing-java-groupdocs-parser/)
- [Comment extraire le texte brut des feuilles Excel avec GroupDocs.Parser pour Java : Guide étape par étape](/parser/java/text-extraction/extract-raw-text-excel-groupdocs-parser-java/)