---
date: '2026-02-19'
description: Apprenez à lire les codes QR dans les PDF Java en utilisant GroupDocs.Parser
  et à exporter les données du code‑barres au format XML.
keywords:
- Java PDF barcode extraction
- GroupDocs.Parser for Java
- XML export from PDF
title: Comment lire les codes QR dans les PDF Java avec GroupDocs.Parser
type: docs
url: /fr/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Comment lire les codes QR dans les PDF Java avec GroupDocs.Parser

Dans les flux de travail modernes, **comment lire les QR** codes à partir de documents PDF peut faire la différence entre un goulot d'étranglement de saisie manuelle et une chaîne entièrement automatisée. Que vous traitiez des manifestes d'expédition, des reçus de vente au détail ou des catalogues de produits, extraire rapidement et de manière fiable les informations QR est essentiel. Ce tutoriel vous guide dans l'utilisation de **GroupDocs.Parser for Java** pour lire les codes QR (et d'autres codes-barres) à partir de PDF et exporter les résultats vers un fichier XML propre que les systèmes en aval peuvent consommer.

## Réponses rapides
- **Que fait GroupDocs.Parser for Java ?** Il lit les fichiers PDF et extrait des données structurées telles que les codes-barres.  
- **Comment extraire les codes QR ?** En configurant `BarcodeOptions` avec le type QR et en appelant `parser.getBarcodes()`.  
- **Puis-je lire les codes QR en Java ?** Oui — définissez le type de code-barres sur `"QR"` dans les options.  
- **Ai-je besoin d'une licence ?** Un essai fonctionne pour les tests ; une licence commerciale est requise pour la production.  
- **Quelle version de Java est requise ?** Java 8 ou supérieure est recommandée.

## Qu'est‑ce que « comment lire les QR » dans le contexte du traitement PDF ?
Lire les codes QR à partir de PDF signifie scanner chaque page à la recherche de graphiques encodés en QR, décoder les données intégrées et les renvoyer dans un format exploitable par le programme. GroupDocs.Parser abstrait l'analyse d'image de bas niveau afin que vous puissiez vous concentrer sur la logique métier plutôt que sur la manipulation des pixels.

## Pourquoi utiliser GroupDocs.Parser pour l'extraction de QR ?
- **Haute précision :** Les algorithmes de traitement d'image intégrés gèrent les scans à basse résolution.  
- **Options de performance :** Choisissez `QualityMode.Low` pour la rapidité ou `QualityMode.High` pour une précision maximale.  
- **Support multi‑format :** Fonctionne avec les PDF, les images et même les documents Office, vous permettant de réutiliser la même base de code pour différents types de fichiers.

## Prérequis
- **GroupDocs.Parser for Java** (version 25.5 ou ultérieure).  
- Maven ou téléchargement manuel du JAR.  
- Environnement de développement Java 8+ (IntelliJ IDEA, Eclipse ou tout éditeur).  

## Configuration de GroupDocs.Parser pour Java
### Utilisation de Maven
Ajoutez le dépôt GroupDocs et la dépendance à votre `pom.xml` :

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
Sinon, téléchargez le JAR le plus récent depuis [GroupDocs.Parser Java Documentation](https://releases.groupdocs.com/parser/java/).

#### Étapes d'obtention de licence
- **Essai gratuit :** Essai de 30 jours avec l'ensemble complet des fonctionnalités.  
- **Licence temporaire :** Demandez une clé temporaire pour une évaluation prolongée.  
- **Achat :** Obtenez une licence commerciale pour les déploiements en production.

### Initialisation et configuration de base
Créez une instance `Parser` qui pointe vers le PDF que vous souhaitez analyser :

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

## Comment lire les codes QR dans les PDF Java en utilisant GroupDocs.Parser
### Étape 1 : Vérifier la prise en charge des codes-barres
Avant d'essayer l'extraction, confirmez que le format du document prend en charge le scan des codes-barres :

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*Explication :* Cette vérification empêche les erreurs d'exécution sur les types de fichiers non pris en charge.

### Étape 2 : Configurer les options de code-barres (Lire les codes QR en Java)
Définissez la qualité du scan et indiquez que vous vous intéressez aux codes QR :

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*Explication :* `QualityMode.Low` accélère le traitement ; passez à `High` si vous avez besoin d'une précision supplémentaire. L'argument `"QR"` indique au moteur de ne rechercher que les codes-barres de type QR.

### Étape 3 : Extraire les données QR
Récupérez les informations de code-barres de chaque page du PDF :

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*Explication :* `parser.getBarcodes` renvoie une collection itérable d'objets `PageBarcodeArea`, chacun contenant la valeur QR décodée et sa localisation sur la page.

## Exportation des données extraites vers XML
### Étape 4 : Initialiser l'exportateur XML
Créez un exportateur qui transformera la collection de codes-barres en un fichier XML bien structuré :

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*Explication :* Le `XmlExporter` gère la sérialisation des objets code-barres en XML standard, prêt pour l'intégration avec les systèmes ERP ou d'inventaire.

### Étape 5 : Écrire le fichier XML
Enregistrez les informations QR extraites sur le disque :

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*Explication :* Le `data.xml` résultant contient un élément `<Barcode>` par code QR, avec des attributs pour le numéro de page, les coordonnées et la valeur décodée.

## Applications pratiques
1. **Gestion des stocks :** Remplir automatiquement les bases de données de stock en lisant les tags QR sur les PDF d'expédition entrants.  
2. **Visibilité de la chaîne d'approvisionnement :** Suivre les colis en temps réel en extrayant les identifiants QR intégrés aux documents logistiques.  
3. **Reçus de vente au détail :** Extraire les informations promotionnelles ou de garantie à partir des codes QR imprimés sur les reçus numériques.

## Considérations de performance
- **Gestion de la mémoire :** Pour les PDF très volumineux, traitez les pages de manière flux plutôt que de charger le fichier complet en mémoire.  
- **Sélection du QualityMode :** Utilisez `Low` pour le traitement en masse ; passez à `High` lorsque vous traitez des scans à basse résolution.  
- **Mises à jour de la bibliothèque :** Maintenez GroupDocs.Parser à jour pour profiter des dernières améliorations de performance et corrections de bugs.

## Problèmes courants et dépannage
| Symptom | Cause probable | Solution |
|---------|----------------|----------|
| Aucun code-barres retourné | Type de code-barres incorrect spécifié | Changez `"QR"` pour le type approprié (par ex., `"CODE_128"`). |
| Erreur de mémoire insuffisante sur de gros PDF | Document entier chargé d'un coup | Traitez les pages individuellement ou augmentez la taille du tas JVM (`-Xmx2g`). |
| Fichier XML vide | `exportBarcodes` appelé avant l'extraction | Assurez‑vous que `parser.getBarcodes(options)` renvoie des données avant l'exportation. |

## Questions fréquemment posées
**Q: Puis-je extraire des codes-barres à partir de fichiers image en utilisant GroupDocs.Parser ?**  
R : Oui, la bibliothèque prend en charge l'extraction de codes-barres à partir des formats d'image courants (PNG, JPEG, TIFF).

**Q: Quels formats de codes-barres sont reconnus ?**  
R : QR, Code 39, Code 128, DataMatrix, PDF417, et bien d'autres. Consultez la documentation API pour la liste complète.

**Q: Comment gérer les PDF protégés par mot de passe ?**  
R : Transmettez le mot de passe au constructeur `Parser` : `new Parser(filePath, "password")`.

**Q: La version d'essai suffit‑elle pour les tests en production ?**  
R : L'essai offre toutes les fonctionnalités mais ajoute un filigrane aux données extraites. Pour la production, obtenez une licence commerciale.

**Q: Que faire si mon PDF contient à la fois des QR et des codes-barres linéaires ?**  
R : Créez plusieurs instances `BarcodeOptions` ou passez un tableau de types pour scanner tous les formats nécessaires en une seule passe.

---

**Dernière mise à jour :** 2026-02-19  
**Testé avec :** GroupDocs.Parser 25.5  
**Auteur :** GroupDocs  

## Ressources
- [Documentation Java de GroupDocs.Parser](https://docs.groupdocs.com/parser/java/)
- [Référence API](https://reference.groupdocs.com/parser/java)
- [Télécharger GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [Dépôt GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Forum de support gratuit](https://forum.groupdocs.com/c/parser)
- [Demande de licence temporaire](https://purchase.groupdocs.com/temporary-license/)

---