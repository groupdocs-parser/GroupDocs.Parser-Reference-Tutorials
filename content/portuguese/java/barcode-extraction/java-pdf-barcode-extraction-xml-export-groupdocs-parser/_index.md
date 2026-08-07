---
date: '2026-02-19'
description: Aprenda a ler códigos QR em PDFs Java usando o GroupDocs.Parser e exportar
  os dados do código de barras para XML.
keywords:
- Java PDF barcode extraction
- GroupDocs.Parser for Java
- XML export from PDF
title: Como ler códigos QR em PDFs Java com o GroupDocs.Parser
type: docs
url: /pt/java/barcode-extraction/java-pdf-barcode-extraction-xml-export-groupdocs-parser/
weight: 1
---

# Como Ler Códigos QR em PDFs Java com GroupDocs.Parser

Nos fluxos de trabalho empresariais modernos, **como ler QR** códigos de documentos PDF pode fazer a diferença entre um gargalo de entrada manual de dados e um pipeline totalmente automatizado. Seja lidando com manifestos de remessa, recibos de varejo ou catálogos de produtos, extrair informações de QR rapidamente e de forma confiável é essencial. Este tutorial orienta você a usar **GroupDocs.Parser for Java** para ler códigos QR (e outros códigos de barras) de PDFs e exportar os resultados para um arquivo XML limpo que os sistemas downstream podem consumir.

## Respostas Rápidas
- **O que o GroupDocs.Parser for Java faz?** Ele lê arquivos PDF e extrai dados estruturados, como códigos de barras.  
- **Como extrair códigos QR?** Configurando `BarcodeOptions` com o tipo QR e chamando `parser.getBarcodes()`.  
- **Posso ler códigos QR em Java?** Sim—defina o tipo de código de barras como `"QR"` nas opções.  
- **Preciso de licença?** Um trial funciona para testes; uma licença comercial é necessária para produção.  
- **Qual versão do Java é necessária?** Java 8 ou superior é recomendado.

## O que significa “como ler QR” no contexto do processamento de PDF?
Ler códigos QR de PDFs significa escanear cada página em busca de gráficos codificados em QR, decodificar os dados incorporados e retorná‑los em um formato amigável ao programa. O GroupDocs.Parser abstrai a análise de imagem de baixo nível para que você possa focar na lógica de negócios em vez de manipulação de pixels.

## Por que usar o GroupDocs.Parser para extração de QR?
- **Alta precisão:** Algoritmos de processamento de imagem embutidos lidam com digitalizações de baixa resolução.  
- **Opções de desempenho:** Escolha `QualityMode.Low` para velocidade ou `QualityMode.High` para precisão máxima.  
- **Suporte a múltiplos formatos:** Funciona com PDFs, imagens e até documentos Office, permitindo reutilizar a mesma base de código para diferentes tipos de arquivos.

## Pré‑requisitos
- **GroupDocs.Parser for Java** (versão 25.5 ou posterior).  
- Maven ou download manual do JAR.  
- Ambiente de desenvolvimento Java 8+ (IntelliJ IDEA, Eclipse ou qualquer editor).  

## Configurando o GroupDocs.Parser para Java
### Usando Maven
Add the GroupDocs repository and dependency to your `pom.xml`:

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

### Download Direto
Alternatively, download the latest JAR from [GroupDocs.Parser for Java releases](https://releases.groupdocs.com/parser/java/).

#### Etapas de Aquisição de Licença
- **Teste Gratuito:** trial de 30 dias com conjunto completo de recursos.  
- **Licença Temporária:** Solicite uma chave temporária para avaliação estendida.  
- **Compra:** Obtenha uma licença comercial para implantações em produção.

### Inicialização e Configuração Básicas
Create a `Parser` instance that points to the PDF you want to analyze:

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

## Como ler códigos QR em PDFs Java usando GroupDocs.Parser
### Etapa 1: Verificar Suporte a Código de Barras
Before attempting extraction, confirm that the document format supports barcode scanning:

```java
if (!parser.getFeatures().isBarcodes()) {
    System.out.println("Document does not support barcode extraction.");
    return; // Exit if the document does not support barcode extraction
}
```

*Explicação:* Esta verificação impede erros em tempo de execução em tipos de arquivo não suportados.

### Etapa 2: Configurar Opções de Código de Barras (Ler códigos QR Java)
Set the scanning quality and specify that you’re interested in QR codes:

```java
import com.groupdocs.parser.options.BarcodeOptions;
import com.groupdocs.parser.options.QualityMode;

BarcodeOptions options = new BarcodeOptions(QualityMode.Low, QualityMode.Low, "QR");
```

*Explicação:* `QualityMode.Low` acelera o processamento; troque para `High` se precisar de maior precisão. O argumento `"QR"` indica ao motor que procure apenas códigos de barras do tipo QR.

### Etapa 3: Extrair os Dados QR
Pull the barcode information from every page of the PDF:

```java
import com.groupdocs.parser.data.PageBarcodeArea;
import java.util.List;

Iterable<PageBarcodeArea> barcodes = parser.getBarcodes(options);
```

*Explicação:* `parser.getBarcodes` retorna uma coleção iterável de objetos `PageBarcodeArea`, cada um contendo o valor QR decodificado e sua localização na página.

## Exportando Dados Extraídos para XML
### Etapa 4: Inicializar o Exportador XML
Create an exporter that will transform the barcode collection into a well‑structured XML file:

```java
import com.groupdocs.parser.export.XmlExporter;

XmlExporter exporter = new XmlExporter();
```

*Explicação:* O `XmlExporter` lida com a serialização de objetos de código de barras em XML padrão, pronto para integração com sistemas ERP ou de inventário.

### Etapa 5: Gravar o Arquivo XML
Save the extracted QR information to disk:

```java
exporter.exportBarcodes(barcodes, "YOUR_OUTPUT_DIRECTORY/data.xml");
```

*Explicação:* O `data.xml` resultante contém um elemento `<Barcode>` por código QR, com atributos para número da página, coordenadas e valor decodificado.

## Aplicações Práticas
1. **Gestão de Inventário:** Preencher automaticamente bancos de dados de estoque lendo tags QR em PDFs de remessas recebidas.  
2. **Visibilidade da Cadeia de Suprimentos:** Rastrear pacotes em tempo real extraindo identificadores QR incorporados em documentos logísticos.  
3. **Recibos de Varejo:** Obter informações promocionais ou de garantia de códigos QR impressos em recibos digitais.

## Considerações de Desempenho
- **Gerenciamento de Memória:** Para PDFs muito grandes, processe páginas de forma streaming ao invés de carregar todo o arquivo na memória.  
- **Seleção de QualityMode:** Use `Low` para processamento em lote; troque para `High` ao lidar com digitalizações de baixa resolução.  
- **Atualizações da Biblioteca:** Mantenha o GroupDocs.Parser atualizado para aproveitar as últimas melhorias de desempenho e correções de bugs.

## Problemas Comuns & Solução de Problemas
| Sintoma | Causa Provável | Correção |
|---------|----------------|----------|
| Nenhum código de barras retornado | Tipo de código de barras errado especificado | Altere `"QR"` para o tipo apropriado (ex.: `"CODE_128"`). |
| Erro de falta de memória em PDFs grandes | Documento inteiro carregado de uma vez | Processar páginas individualmente ou aumentar o tamanho do heap JVM (`-Xmx2g`). |
| Arquivo XML vazio | `exportBarcodes` chamado antes da extração | Garanta que `parser.getBarcodes(options)` retorne dados antes de exportar. |

## Perguntas Frequentes
**Q: Posso extrair códigos de barras de arquivos de imagem usando GroupDocs.Parser?**  
A: Sim, a biblioteca suporta extração de códigos de barras de formatos de imagem comuns (PNG, JPEG, TIFF).

**Q: Quais formatos de código de barras são reconhecidos?**  
A: QR, Code 39, Code 128, DataMatrix, PDF417 e muitos outros. Consulte a documentação da API para a lista completa.

**Q: Como devo lidar com PDFs protegidos por senha?**  
A: Passe a senha ao construtor `Parser`: `new Parser(filePath, "password")`.

**Q: A versão trial é suficiente para testes em produção?**  
A: O trial fornece funcionalidade completa, mas adiciona uma marca d'água aos dados extraídos. Para produção, adquira uma licença comercial.

**Q: E se meu PDF contiver tanto QR quanto códigos de barras lineares?**  
A: Crie múltiplas instâncias de `BarcodeOptions` ou passe um array de tipos para escanear todos os formatos necessários em uma única passagem.

---

**Última Atualização:** 2026-02-19  
**Testado com:** GroupDocs.Parser 25.5  
**Autor:** GroupDocs  

## Recursos
- [Documentação do GroupDocs.Parser Java](https://docs.groupdocs.com/parser/java/)
- [Referência da API](https://reference.groupdocs.com/parser/java)
- [Download do GroupDocs.Parser](https://releases.groupdocs.com/parser/java/)
- [Repositório no GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java)
- [Fórum de Suporte Gratuito](https://forum.groupdocs.com/c/parser)
- [Aplicação de Licença Temporária](https://purchase.groupdocs.com/temporary-license/)