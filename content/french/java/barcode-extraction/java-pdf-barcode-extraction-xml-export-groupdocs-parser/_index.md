---
date: '2026-10-12'
description: Apprenez comment extraire un QR d'un PDF en Java en utilisant GroupDocs.Parser
  et exporter les données du code-barres au format XML pour le traitement en aval.
keywords:
- extract QR from PDF
- how to read QR
- read QR codes Java
- parse QR codes Java
- PDF QR code extraction
lastmod: '2026-10-12'
og_description: Apprenez comment extraire un QR d'un PDF en Java en utilisant GroupDocs.Parser
  et exporter les données du code-barres au format XML pour le traitement en aval.
og_image_alt: Guide showing Java code that extracts QR codes from PDF files with GroupDocs.Parser
  and saves results as XML
og_title: Comment extraire un QR d'un PDF en Java avec GroupDocs.Parser
schemas:
- author: GroupDocs
  dateModified: '2026-10-12'
  description: Learn how to extract QR from PDF in Java using GroupDocs.Parser and
    export the barcode data to XML for downstream processing.
  headline: How to extract QR from PDF in Java with GroupDocs.Parser
  type: TechArticle
- description: Learn how to extract QR from PDF in Java using GroupDocs.Parser and
    export the barcode data to XML for downstream processing.
  name: How to extract QR from PDF in Java with GroupDocs.Parser
  steps:
  - name: verify barcode support
    text: 'Before attempting extraction, confirm that the document format supports
      barcode scanning: *Explanation:* This guard prevents runtime errors on unsupported
      file types.'
  - name: configure barcode options (read QR codes Java)
    text: '`BarcodeOptions` is a configuration object that lets you specify which
      barcode symbologies to detect, set the scanning quality mode, and fine‑tune
      parameters such as detection thresholds, ensuring optimal performance for the
      target QR codes. *Explanation:* `QualityMode.Low` speeds up processing; swi'
  - name: extract the QR data
    text: '`parser.getBarcodes(options)` scans the document using the provided `BarcodeOptions`
      and returns a collection of `PageBarcodeArea` objects, each encapsulating the
      decoded QR value, the page number, and the exact coordinates of the barcode
      within the page, allowing precise downstream handling. *Expla'
  - name: initialise the XML exporter
    text: '`XmlExporter` is a utility class that transforms a collection of barcode
      objects into a well‑structured XML document, automatically generating elements
      for each barcode with attributes for page index, position, and decoded value,
      which can then be saved or streamed to other systems. *Explanation:* T'
  - name: write the XML file
    text: 'Save the extracted QR information to disk: *Explanation:* The resulting
      `data.xml` contains one `<Barcode>` element per QR code, with attributes for
      page number, coordinates, and decoded value.'
  type: HowTo
- questions:
  - answer: Yes, the library supports barcode extraction from common image formats
      (PNG, JPEG, TIFF).
    question: Can I extract barcodes from image files using GroupDocs.Parser?
  - answer: QR, Code 39, Code 128, DataMatrix, PDF417, and many more. Refer to the
      API docs for the full list.
    question: What barcode formats are recognized?
  - answer: 'Pass the password to the `Parser` constructor: `new Parser(filePath,
      "password")`.'
    question: How should I handle password‑protected PDFs?
  - answer: The trial provides full functionality but adds a watermark to extracted
      data. For production, acquire a commercial license.
    question: Is the trial version sufficient for production testing?
  - answer: Create multiple `BarcodeOptions` instances or pass an array of types to
      scan for all needed formats in one pass.
    question: What if my PDF contains both QR and linear barcodes?
  type: FAQPage
tags:
- extract QR
- GroupDocs.Parser
- Java PDF processing
- barcode extraction
- XML export
title: Comment extraire un QR d'un PDF en Java avec GroupDocs.Parser
type: docs
url: /fr/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Comment extraire le QR d'un PDF en Java avec GroupDocs.Parser

Dans les flux de travail modernes, **extraction du QR à partir de PDF** peut transformer un goulot d'étranglement de saisie manuelle en une chaîne entièrement automatisée. Que vous manipuliez des manifestes d'expédition, des reçus de vente au détail ou des catalogues de produits, extraire rapidement et de manière fiable les informations QR est essentiel pour les systèmes en aval. Ce tutoriel vous guide à travers l’utilisation de **GroupDocs.Parser for Java** pour lire les codes QR (et autres codes-barres) depuis des PDF et exporter les résultats vers un fichier XML propre que votre ERP, votre inventaire ou votre plateforme d’analyse peut consommer.

## Réponses rapides
- **Que fait GroupDocs.Parser pour Java ?** Il lit les fichiers PDF et extrait des données structurées telles que les codes-barres, les tableaux et le texte.  
- **Comment extraire les codes QR ?** Configurez `BarcodeOptions` avec le type QR et appelez `parser.getBarcodes()`.  
- **Puis-je lire les codes QR en Java ?** Oui — définissez le type de code-barres sur `"QR"` dans les options.  
- **Ai-je besoin d'une licence ?** Un essai fonctionne pour les tests ; une licence commerciale est requise pour la production.  
- **Quelle version de Java est requise ?** Java 8 ou supérieur est recommandé.

## Qu’est-ce que « extraire le QR d’un PDF » dans le contexte du traitement PDF ?
L'extraction du QR d'un PDF consiste à analyser chaque page à la recherche de graphiques encodés en QR, décoder les données intégrées et les renvoyer dans un format adapté aux programmes. GroupDocs.Parser abstrait l'analyse d'image de bas niveau afin que vous puissiez vous concentrer sur la logique métier plutôt que sur la manipulation des pixels.

## Pourquoi utiliser GroupDocs.Parser pour l'extraction de QR ?
GroupDocs.Parser prend en charge **plus de 30 formats d'entrée** et peut traiter des PDF jusqu'à **500 Mo** sans charger le fichier complet en mémoire, offrant des résultats haute précision même sur des scans basse résolution. Vous pouvez choisir `QualityMode.Low` pour la rapidité ou `QualityMode.High` pour une précision maximale, et la même API fonctionne pour les PDF, les images et les documents Office, éliminant le besoin de multiples bibliothèques.

## Prérequis
- **GroupDocs.Parser pour Java** (version 25.5 ou ultérieure).  
- Maven ou téléchargement manuel du JAR.  
- Environnement de développement Java 8+ (IntelliJ IDEA, Eclipse ou tout autre éditeur).  

## Configuration de GroupDocs.Parser pour Java
### Utilisation de Maven
Ajoutez le dépôt GroupDocs et la dépendance à votre `pom.xml` :

```xml
<repositories>
    <repository>
        <id>repository.groupdocs.com</id>
        <name>GroupDocs Repository</name>
        <url>https://releases.groupdocs.com/parser/java/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-parser</artifactId>
        <version>25.5</version>
    </dependency>
</dependencies>
```

```xml
<repositories>
    <repository>
        <id>repository.groupdocs.com</id>
        <name>GroupDocs Repository</name>
        <url>https://releases.groupdocs.com/parser/java/</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-parser</artifactId>
        <version>25.5</version>
    </dependency>
</dependencies>
```

### Téléchargement direct
Sinon, téléchargez le JAR le plus récent depuis [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

#### Étapes d'obtention de licence
- **Essai gratuit :** essai de 30 jours avec l'ensemble complet des fonctionnalités.  
- **Licence temporaire :** demandez une clé temporaire pour une évaluation prolongée.  
- **Achat :** obtenez une licence commerciale pour les déploiements en production.

### Initialisation et configuration de base
Créez une instance `Parser` qui pointe vers le PDF que vous souhaitez analyser :

`Parser` est la classe principale de GroupDocs.Parser qui représente un document et fournit des méthodes pour extraire du contenu tel que du texte, des tableaux et des codes-barres.  

```java
import com.groupdocs.parser.Parser;

class BarcodeExtractor {
    public static void main(String[] args) {
        // Initialize Parser object with the path to your PDF document.
        try (Parser parser = new Parser("YOUR_DOCUMENT_DIRECTORY")) {
            // Additional setup and usage will follow in the next sections.
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## Comment lire les codes QR dans les PDF Java avec GroupDocs.Parser
Lire les codes QR dans les PDF Java avec GroupDocs.Parser implique de créer une instance de parser, de configurer les options de code-barres pour cibler les types QR, d'appeler la méthode d'extraction de code-barres, puis de gérer les objets code-barres retournés. Le processus est simple, fonctionne sur n'importe quelle page PDF et renvoie les valeurs décodées ainsi que les métadonnées de position pour un traitement ultérieur.

### Étape 1 : vérifier la prise en charge des codes-barres
Avant d'essayer l'extraction, confirmez que le format du document prend en charge le scan de codes-barres :

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*Explication :* Cette vérification empêche les erreurs d'exécution sur les types de fichiers non pris en charge.

### Étape 2 : configurer les options de code-barres (lecture des codes QR en Java)
`BarcodeOptions` est un objet de configuration qui vous permet de spécifier quelles symbologies de code-barres détecter, de définir le mode de qualité du scan et d'ajuster finement des paramètres tels que les seuils de détection, garantissant des performances optimales pour les codes QR ciblés.  

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*Explication :* `QualityMode.Low` accélère le traitement ; passez à `High` si vous avez besoin d'une précision supplémentaire. L'argument `"QR"` indique au moteur de rechercher uniquement les codes-barres de type QR.

### Étape 3 : extraire les données QR
`parser.getBarcodes(options)` analyse le document en utilisant les `BarcodeOptions` fournies et renvoie une collection d'objets `PageBarcodeArea`, chacun encapsulant la valeur QR décodée, le numéro de page et les coordonnées exactes du code-barres dans la page, permettant une gestion précise en aval.  

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*Explication :* `parser.getBarcodes` renvoie une collection itérable d'objets `PageBarcodeArea`, chacun contenant la valeur QR décodée et son emplacement sur la page.

## Exportation des données extraites vers XML
### Étape 4 : initialiser l'exportateur XML
`XmlExporter` est une classe utilitaire qui transforme une collection d'objets code-barres en un document XML bien structuré, générant automatiquement des éléments pour chaque code-barres avec des attributs d'index de page, de position et de valeur décodée, qui peuvent ensuite être enregistrés ou diffusés vers d'autres systèmes.  

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*Explication :* Le `XmlExporter` gère la sérialisation des objets code-barres en XML standard, prêt pour l'intégration avec les systèmes ERP ou d'inventaire.

### Étape 5 : écrire le fichier XML
Enregistrez les informations QR extraites sur le disque :

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*Explication :* Le `data.xml` résultant contient un élément `<Barcode>` par code QR, avec des attributs pour le numéro de page, les coordonnées et la valeur décodée.

## Applications pratiques
1. **Gestion des stocks :** remplissage automatique des bases de données de stock en lisant les tags QR sur les PDF de livraisons entrantes.  
2. **Visibilité de la chaîne d'approvisionnement :** suivez les colis en temps réel en extrayant les identifiants QR intégrés aux documents logistiques.  
3. **Tickets de caisse :** récupérez les informations promotionnelles ou de garantie à partir des codes QR imprimés sur les tickets numériques.

## Considérations de performance
- **Gestion de la mémoire :** pour les PDF très volumineux, traitez les pages en flux plutôt que de charger le fichier complet en mémoire.  
- **Sélection du QualityMode :** utilisez `Low` pour le traitement en masse ; passez à `High` lorsqu'il s'agit de scans basse résolution.  
- **Mises à jour de la bibliothèque :** maintenez GroupDocs.Parser à jour pour profiter des dernières améliorations de performance et des corrections de bugs.

## Problèmes courants et dépannage
| Symptôme | Cause probable | Solution |
|----------|----------------|----------|
| Aucun code-barres retourné | Type de code-barres incorrect spécifié | Modifiez `"QR"` en le type approprié (par ex., `"CODE_128"`). |
| Erreur de mémoire insuffisante sur de gros PDF | Document entier chargé en une fois | Traitez les pages individuellement ou augmentez la taille du tas JVM (`-Xmx2g`). |
| Fichier XML vide | `exportBarcodes` appelé avant l'extraction | Assurez-vous que `parser.getBarcodes(options)` renvoie des données avant l'exportation. |

## Questions fréquemment posées
**Q : Puis-je extraire des codes-barres à partir de fichiers image avec GroupDocs.Parser ?**  
R : Oui, la bibliothèque prend en charge l'extraction de codes-barres à partir des formats d'image courants (PNG, JPEG, TIFF).

**Q : Quels formats de codes-barres sont reconnus ?**  
R : QR, Code 39, Code 128, DataMatrix, PDF417, et bien d'autres. Consultez la documentation de l'API pour la liste complète.

**Q : Comment gérer les PDF protégés par mot de passe ?**  
R : Passez le mot de passe au constructeur `Parser` : `new Parser(filePath, "password")`.

**Q : La version d'essai suffit‑elle pour les tests en production ?**  
R : L'essai offre toutes les fonctionnalités mais ajoute un filigrane aux données extraites. Pour la production, obtenez une licence commerciale.

**Q : Que faire si mon PDF contient à la fois des QR et des codes-barres linéaires ?**  
R : Créez plusieurs instances de `BarcodeOptions` ou passez un tableau de types pour scanner tous les formats nécessaires en une seule passe.

---

**Dernière mise à jour :** 2026-10-12  
**Testé avec :** GroupDocs.Parser 25.5  
**Auteur :** GroupDocs  

## Ressources
- [Documentation Java de GroupDocs.Parser](https://docs.groupdocs.com/parser/java/)
- [Référence API](https://reference.groupdocs.com/parser/java)
- [Télécharger GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [Référentiel GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Forum de support gratuit](https://forum.groupdocs.com/c/parser)
- [Demande de licence temporaire](https://purchase.groupdocs.com/temporary-license/)

## Tutoriels associés

- [Extraire le code-barres PDF avec GroupDocs Parser Java](/parser/java/barcode-extraction/extract-barcode-pdf-groupdocs-parser-java/)
- [Comment charger un PDF depuis une URL avec GroupDocs.Parser pour Java](/parser/java/document-loading/)
- [Extraire les données de formulaire PDF avec GroupDocs.Parser en Java](/parser/java/form-extraction/groupdocs-parser-java-pdf-form-extraction/)