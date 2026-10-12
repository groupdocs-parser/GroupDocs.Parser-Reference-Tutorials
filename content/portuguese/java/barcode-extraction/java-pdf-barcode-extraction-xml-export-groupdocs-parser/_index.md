---
date: '2026-10-12'
description: Aprenda como extrair QR de PDF em Java usando GroupDocs.Parser e exportar
  os dados do código de barras para XML para processamento posterior.
keywords:
- extract QR from PDF
- how to read QR
- read QR codes Java
- parse QR codes Java
- PDF QR code extraction
lastmod: '2026-10-12'
og_description: Aprenda como extrair QR de PDF em Java usando GroupDocs.Parser e exportar
  os dados do código de barras para XML para processamento posterior.
og_image_alt: Guide showing Java code that extracts QR codes from PDF files with GroupDocs.Parser
  and saves results as XML
og_title: Como extrair QR de PDF em Java com GroupDocs.Parser
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
title: Como extrair QR de PDF em Java com GroupDocs.Parser
type: docs
url: /pt/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Como extrair QR de PDF em Java com GroupDocs.Parser

Em fluxos de trabalho empresariais modernos, **extraindo QR de PDF** pode transformar um gargalo manual de entrada de dados em um pipeline totalmente automatizado. Seja lidando com manifestos de remessa, recibos de varejo ou catálogos de produtos, extrair informações de QR rapidamente e de forma confiável é essencial para sistemas downstream. Este tutorial orienta você a usar **GroupDocs.Parser for Java** para ler códigos QR (e outros códigos de barras) de PDFs e exportar os resultados para um arquivo XML limpo que seu ERP, inventário ou plataforma de análise pode consumir.

## Respostas rápidas
- **O que o GroupDocs.Parser for Java faz?** Ele lê arquivos PDF e extrai dados estruturados como códigos de barras, tabelas e texto.  
- **Como extrair códigos QR?** Configure `BarcodeOptions` com o tipo QR e chame `parser.getBarcodes()`.  
- **Posso ler códigos QR em Java?** Sim—defina o tipo de código de barras como `"QR"` nas opções.  
- **Preciso de uma licença?** Uma versão de avaliação funciona para testes; uma licença comercial é necessária para produção.  
- **Qual versão do Java é necessária?** Java 8 ou superior é recomendado.

## O que significa “extrair QR de PDF” no contexto do processamento de PDF?
Extrair QR de PDF significa escanear cada página em busca de gráficos codificados em QR, decodificar os dados incorporados e retorná‑los em um formato amigável ao programa. O GroupDocs.Parser abstrai a análise de imagem de baixo nível para que você possa focar na lógica de negócios em vez de manipular pixels.

## Por que usar o GroupDocs.Parser para extração de QR?
O GroupDocs.Parser suporta **mais de 30 formatos de entrada** e pode processar PDFs de até **500 MB** sem carregar todo o arquivo na memória, entregando resultados de alta precisão mesmo em digitalizações de baixa resolução. Você pode escolher `QualityMode.Low` para velocidade ou `QualityMode.High` para máxima precisão, e a mesma API funciona para PDFs, imagens e documentos Office, eliminando a necessidade de múltiplas bibliotecas.

## Pré-requisitos
- **GroupDocs.Parser for Java** (versão 25.5 ou posterior).  
- Maven ou download manual do JAR.  
- Ambiente de desenvolvimento Java 8+ (IntelliJ IDEA, Eclipse ou qualquer editor).  

## Configurando o GroupDocs.Parser para Java
### Usando Maven
Adicione o repositório GroupDocs e a dependência ao seu `pom.xml`:

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

### Download direto
Alternativamente, faça o download do JAR mais recente em [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

#### Etapas de aquisição de licença
- **Teste gratuito:** avaliação de 30 dias com conjunto completo de recursos.  
- **Licença temporária:** solicite uma chave temporária para avaliação prolongada.  
- **Compra:** obtenha uma licença comercial para implantações em produção.

### Inicialização e configuração básicas
Crie uma instância `Parser` que aponta para o PDF que você deseja analisar:

`Parser` é a classe central no GroupDocs.Parser que representa um documento e fornece métodos para extrair conteúdo como texto, tabelas e códigos de barras.

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

## Como ler códigos QR em PDFs Java usando o GroupDocs.Parser
Ler códigos QR em PDFs Java com o GroupDocs.Parser envolve criar uma instância do parser, configurar opções de código de barras para focar nos tipos QR, invocar o método de extração de códigos de barras e, em seguida, manipular os objetos de código de barras retornados. O processo é simples, funciona em qualquer página de PDF e devolve os valores decodificados juntamente com metadados posicionais para processamento adicional.

### Etapa 1: verificar suporte a códigos de barras
Antes de tentar a extração, confirme que o formato do documento suporta a varredura de códigos de barras:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*Explicação:* Esta verificação evita erros em tempo de execução em tipos de arquivo não suportados.

### Etapa 2: configurar opções de código de barras (ler códigos QR Java)
`BarcodeOptions` é um objeto de configuração que permite especificar quais simbologias de código de barras detectar, definir o modo de qualidade da varredura e ajustar parâmetros como limites de detecção, garantindo desempenho ideal para os códigos QR alvo.

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*Explicação:* `QualityMode.Low` acelera o processamento; troque para `High` se precisar de maior precisão. O argumento `"QR"` indica ao motor que procure apenas códigos de barras do tipo QR.

### Etapa 3: extrair os dados QR
`parser.getBarcodes(options)` escaneia o documento usando as `BarcodeOptions` fornecidas e retorna uma coleção de objetos `PageBarcodeArea`, cada um encapsulando o valor QR decodificado, o número da página e as coordenadas exatas do código de barras na página, permitindo um tratamento preciso downstream.

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*Explicação:* `parser.getBarcodes` retorna uma coleção iterável de objetos `PageBarcodeArea`, cada um contendo o valor QR decodificado e sua localização na página.

## Exportando dados extraídos para XML
### Etapa 4: inicializar o exportador XML
`XmlExporter` é uma classe utilitária que transforma uma coleção de objetos de código de barras em um documento XML bem estruturado, gerando automaticamente elementos para cada código de barras com atributos de índice de página, posição e valor decodificado, que podem então ser salvos ou transmitidos para outros sistemas.

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*Explicação:* O `XmlExporter` lida com a serialização de objetos de código de barras em XML padrão, pronto para integração com sistemas ERP ou de inventário.

### Etapa 5: gravar o arquivo XML
Salve as informações QR extraídas no disco:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*Explicação:* O `data.xml` resultante contém um elemento `<Barcode>` por código QR, com atributos para número da página, coordenadas e valor decodificado.

## Aplicações práticas
1. **Gestão de inventário:** Preencher automaticamente bancos de dados de estoque lendo tags QR em PDFs de remessas recebidas.  
2. **Visibilidade da cadeia de suprimentos:** Rastrear pacotes em tempo real extraindo identificadores QR incorporados em documentos logísticos.  
3. **Recibos de varejo:** Extrair informações promocionais ou de garantia de códigos QR impressos em recibos digitais.

## Considerações de desempenho
- **Gerenciamento de memória:** Para PDFs muito grandes, processe as páginas de forma streaming ao invés de carregar o arquivo inteiro na memória.  
- **Seleção de QualityMode:** Use `Low` para processamento em lote; troque para `High` ao lidar com digitalizações de baixa resolução.  
- **Atualizações da biblioteca:** Mantenha o GroupDocs.Parser atualizado para aproveitar as últimas melhorias de desempenho e correções de bugs.

## Problemas comuns & solução de problemas
| Sintoma | Causa provável | Correção |
|---------|----------------|----------|
| Nenhum código de barras retornado | Tipo de código de barras errado especificado | Altere `"QR"` para o tipo apropriado (por exemplo, `"CODE_128"`). |
| Erro de falta de memória em PDFs grandes | Documento inteiro carregado de uma vez | Processar páginas individualmente ou aumentar o tamanho do heap JVM (`-Xmx2g`). |
| Arquivo XML vazio | `exportBarcodes` chamado antes da extração | Garanta que `parser.getBarcodes(options)` retorne dados antes de exportar. |

## Perguntas frequentes
**Q: Posso extrair códigos de barras de arquivos de imagem usando o GroupDocs.Parser?**  
A: Sim, a biblioteca suporta extração de códigos de barras de formatos de imagem comuns (PNG, JPEG, TIFF).

**Q: Quais formatos de código de barras são reconhecidos?**  
A: QR, Code 39, Code 128, DataMatrix, PDF417 e muitos outros. Consulte a documentação da API para a lista completa.

**Q: Como devo lidar com PDFs protegidos por senha?**  
A: Passe a senha ao construtor `Parser`: `new Parser(filePath, "password")`.

**Q: A versão de avaliação é suficiente para testes em produção?**  
A: A avaliação fornece funcionalidade completa, mas adiciona uma marca d'água aos dados extraídos. Para produção, adquira uma licença comercial.

**Q: E se meu PDF contiver tanto QR quanto códigos de barras lineares?**  
A: Crie múltiplas instâncias `BarcodeOptions` ou passe um array de tipos para escanear todos os formatos necessários em uma única passagem.

---

**Última atualização:** 2026-10-12  
**Testado com:** GroupDocs.Parser 25.5  
**Autor:** GroupDocs  

## Recursos
- [Documentação do GroupDocs.Parser Java](https://docs.groupdocs.com/parser/java/)
- [Referência da API](https://reference.groupdocs.com/parser/java)
- [Download do GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [Repositório no GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Fórum de suporte gratuito](https://forum.groupdocs.com/c/parser)
- [Aplicação de licença temporária](https://purchase.groupdocs.com/temporary-license/)

## Tutoriais relacionados

- [Extract Barcode Pdf Groupdocs Parser Java](/parser/java/barcode-extraction/extract-barcode-pdf-groupdocs-parser-java/)
- [How to Load PDF from URL with GroupDocs.Parser for Java](/parser/java/document-loading/)
- [Extract PDF Form Data with GroupDocs.Parser in Java](/parser/java/form-extraction/groupdocs-parser-java-pdf-form-extraction/)