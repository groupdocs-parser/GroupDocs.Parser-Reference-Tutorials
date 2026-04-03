---
date: '2026-02-06'
description: Aprenda a visualizar arquivos Excel e converter xlsx para png usando
  o GroupDocs.Parser para Java. Este tutorial cobre a configuração, a implementação
  e aplicações práticas.
keywords:
- GroupDocs.Parser
- Java
- Document Processing
title: Como pré-visualizar arquivos Excel com GroupDocs.Parser em Java
type: docs
url: /pt/java/page-preview-generation/generate-spreadsheet-previews-groupdocs-parser-java/
weight: 1
---

# Como visualizar arquivos Excel com GroupDocs.Parser em Java

Se você está procurando **como preview Excel** planilhas programaticamente, chegou ao lugar certo. Neste guia, vamos percorrer a criação de visualizações de imagem (PNG) a partir de livros de trabalho `.xlsx` usando GroupDocs.Parser para Java — perfeito para gerar miniaturas rápidas, compartilhar capturas de tela ou construir um recurso de visualização de documentos em sua aplicação.

## Respostas rápidas
- **O que significa “preview Excel”?** Gerar arquivos de imagem (por exemplo, PNG) que representam cada página da planilha.  
- **Qual formato é recomendado?** PNG oferece qualidade sem perdas e funciona bem para miniaturas da web.  
- **Preciso de uma licença?** Um teste gratuito funciona para desenvolvimento; uma licença comercial é necessária para produção.  
- **Posso alterar a resolução da imagem?** Sim — ajuste o DPI em `PreviewOptions`.  
- **É possível visualizar outros formatos?** GroupDocs.Parser também suporta PDF, Word e muitos tipos de imagem.

## O que é “como preview Excel” com GroupDocs.Parser?
GroupDocs.Parser lê livros de trabalho Excel, renderiza cada planilha como uma página visual e permite que você transmita essas páginas para arquivos de imagem. Isso elimina a necessidade de interoperação com o Office ou conversores de terceiros.

## Por que usar GroupDocs.Parser para visualizações de Excel?
- **Sem necessidade de instalação do Office** – funciona em qualquer ambiente Java server‑side.  
- **Suporta arquivos grandes** – transmite páginas uma a uma, mantendo o uso de memória baixo.  
- **Saída de alta qualidade** – controle sobre DPI, formato e opções de renderização.  
- **Flexibilidade entre formatos** – a mesma API funciona para PDFs, documentos Word e mais.

## Pré-requisitos
- **Java Development Kit** (8 +).  
- **IDE** such as IntelliJ IDEA or Eclipse.  
- **GroupDocs.Parser for Java SDK** – download from [here](https://releases.groupdocs.com/parser/java/).  
- **Sample Excel file** (`.xlsx`) you want to preview.  
- **Maven or Gradle** (optional) for dependency management.

## Importar Pacotes
Essas importações dão acesso ao parser, opções de visualização e utilitários de manipulação de streams.

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

## Guia passo a passo para gerar visualizações de páginas de planilha

### Etapa 1: Inicializar a instância do Parser
Crie um objeto `Parser` apontando para o seu livro de trabalho Excel. O bloco *try‑with‑resources* garante que o parser seja fechado automaticamente.

```java
try (Parser parser = new Parser("path/to/your/sample.xlsx")) {
    // Your subsequent code will go here
}
```

> **Dica profissional:** Use um caminho absoluto ou configure uma pasta de recursos para evitar `FileNotFoundException`.

### Etapa 2: Preparar suas opções de visualização
Defina como cada página será salva. A implementação `ICreatePageStream` retorna um novo `FileOutputStream` para cada página da planilha.

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

> Esta etapa é onde você **converte xlsx para png** — o stream grava os dados PNG no disco.

### Etapa 3: Anexar um delegate para capturar informações de renderização
Se precisar de detalhes sobre cada planilha renderizada (por exemplo, dimensões, nome da planilha), registre um callback.

```java
final PageRenderInfo[] renderInfoHolder = {null}; // to store info

previewOptions.setPreviewPageRender(new IPreviewPageRender() {
    @Override
    public void previewPageRender(PageRenderInfo pageRenderInfo) {
        renderInfoHolder[0] = pageRenderInfo;
    }
});
```

### Etapa 4: Especificar o formato de saída e DPI
Selecione PNG como formato de imagem e defina um DPI que equilibre qualidade e tamanho do arquivo.

```java
previewOptions.setPreviewFormat(PreviewFormats.Png); // PNG images
previewOptions.setDpi(150); // Higher DPI for better clarity
```

> Ajuste o DPI se precisar de miniaturas menores (por exemplo, 96) ou impressões de alta resolução (por exemplo, 300).

### Etapa 5: Gerar as visualizações
Com tudo configurado, chame `generatePreview`. O SDK iterará sobre cada planilha e invocará o stream que você forneceu.

```java
parser.generatePreview(previewOptions);
```

### Etapa 6: Definir o helper `getOutputPath()`
Este método cria um nome de arquivo baseado no número da página (planilha). Sinta-se à vontade para personalizar a estrutura de pastas.

```java
private static String getOutputPath(int pageNumber) {
    return "output/preview_page_" + pageNumber + ".png"; // Custom path
}
```

> **Erro comum:** Esquecer de criar o diretório `output` previamente causará um `IOException`. Crie-o programaticamente ou certifique-se de que ele exista.

## Exemplo completo em funcionamento (Simplificado)

Abaixo está uma versão compacta que reúne todas as partes. Ela demonstra o fluxo de trabalho **create excel page preview** do início ao fim.

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

Execute este trecho, e você encontrará uma série de arquivos `preview_page_1.png`, `preview_page_2.png`, … na pasta `output` — cada um representando uma planilha do livro de trabalho Excel original.

## Problemas comuns e soluções

| Problema | Causa | Correção |
|----------|-------|----------|
| **Nenhuma imagem gerada** | `getOutputPath` retorna um diretório inválido | Certifique-se de que a pasta de destino exista ou crie-a com `new File("output").mkdirs();` |
| **Erro de falta de memória em arquivos enormes** | Carregando todo o livro de trabalho de uma vez | Use a abordagem de streaming (como mostrado) e processe as páginas uma de cada vez |
| **DPI incorreto** | `setDpi` não chamado ou definido como padrão (96) | Chame `previewOptions.setDpi(seuValorDesejado);` antes de `generatePreview` |
| **Formato não suportado** | Tentando visualizar um `.xlsx` corrompido | Valide o arquivo com o Excel ou use `Parser.isSupported` antes do processamento |

## Perguntas Frequentes

**Q: Posso gerar visualizações para PDFs e imagens usando GroupDocs.Parser?**  
A: Sim, a mesma API funciona para PDFs, documentos Word e muitos formatos de imagem.

**Q: Como altero o formato da imagem de saída?**  
A: Chame `previewOptions.setPreviewFormat(PreviewFormats.Jpeg)` (ou `Gif`, `Bmp`, etc.).

**Q: O desempenho é uma preocupação com livros de trabalho muito grandes?**  
A: O SDK transmite páginas, o que mantém o uso de memória baixo. Para arquivos massivos, considere processar em lotes paralelos.

**Q: Como posso lidar com erros durante a geração de visualizações?**  
A: Envolva o código em blocos try‑catch (como mostrado) e registre os detalhes da exceção. Certifique‑se de que os streams sejam fechados no bloco `finally` se não estiver usando try‑with‑resources.

**Q: A biblioteca requer que o Microsoft Office esteja instalado?**  
A: Não. GroupDocs.Parser é uma solução Java pura e funciona em qualquer plataforma que suporte Java 8+.

## Conclusão
Agora você tem um método completo e pronto para produção para **how to preview Excel** workbooks e **convert xlsx to png** usando GroupDocs.Parser. Ajuste o DPI, a pasta de saída ou o formato da imagem para atender às necessidades do seu projeto, e integre este trecho em fluxos de trabalho maiores de gerenciamento de documentos.

Pronto para o próximo passo? Explore a [documentação](https://docs.groupdocs.com/parser/java/) oficial para opções avançadas de renderização, arquivos protegidos por senha e técnicas de processamento em lote.

---

**Última atualização:** 2026-02-06  
**Testado com:** GroupDocs.Parser 23.11 (mais recente no momento da escrita)  
**Autor:** GroupDocs