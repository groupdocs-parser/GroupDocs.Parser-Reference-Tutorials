---
date: '2026-01-29'
description: 學習如何在 Java 中使用 Aspose.OCR 和 GroupDocs.Parser 從圖像提取文字，並高效轉換掃描文件的文字。
keywords:
- Java OCR text recognition
- Aspose OCR Java
- GroupDocs Parser for Java
title: 在 Java 中使用 Aspose.OCR 與 GroupDocs.Parser 提取圖像文字
type: docs
url: /zh-hant/java/ocr-integration/java-ocr-text-recognition-aspose-groupdocs-parser-guide/
weight: 1
---

# 使用 Aspose.OCR 與 GroupDocs.Parser 在 Java 中從圖像提取文字

您是否在尋找一種高效的方式，於 Java 應用程式中 **從圖像提取文字**？在數位時代，將文件的照片轉換為可搜尋、可編輯的文字已成為必備功能。本教學將完整說明如何結合 Aspose.OCR 與 GroupDocs.Parser for Java，讓您可靠地將掃描文件的文字轉換為可使用的字串。

我們將涵蓋從設定函式庫到辨識特定文字區域的全部步驟，並展示此整合在實務情境中的優勢。

## 快速答覆
- **哪個函式庫負責 OCR？** Aspose.OCR 提供高精度的光學字符辨識。
- **哪個元件負責解析結果？** GroupDocs.Parser 從 OCR 輸出中提取結構化資料。
- **最低 Java 版本？** JDK 8 或更新版本。
- **需要授權嗎？** 試用版可用於測試；完整授權可解鎖全部功能。
- **可以處理串流嗎？** 可以——兩個函式庫皆支援圖像串流，用於 Web 上傳。

## 什麼是「從圖像提取文字」？
從圖像提取文字指的是將視覺字符（例如掃描頁面或收據照片）轉換為純文字，讓程式碼能夠操作、搜尋或儲存。OCR（光學字符辨識）引擎會分析像素模式、辨識字形，並輸出 Unicode 字串。

## 為什麼要將 Aspose.OCR 與 GroupDocs.Parser 結合？
- **準確度：** Aspose.OCR 提供業界領先的辨識率。
- **彈性：** GroupDocs.Parser 能處理 OCR 輸出，偵測頁面版面，並回傳如表格或表單欄位等結構化結果。
- **串流友好：** 兩個函式庫皆可直接使用 `InputStream`，非常合接收圖像上傳的 Web 服務。

## 前置條件
- **Java 開發套件：** 已安裝 JDK 8 以上。
- **Maven：** 推薦的建置工具（或手動管理 JAR）。
- **Aspose OCR 函式庫：** 將 JAR 加入專案。
- **GroupDocs.Parser for Java：** 透過 Maven（見下方）或下載 JAR。
- **基本 Java 知識：** 串流、例外與集合的處理。

## 設定 GroupDocs.Parser for Java

### Maven 設定
將儲存庫與相依性加入 `pom.xml`：

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

### 直接下載
若不使用 Maven，可從 [GroupDocs Releases](https://releases.groupdocs.com/parser/java/) 取得最新 JAR。

### 取得授權
有效授權可解鎖 Aspose OCR 與 GroupDocs.Parser 的完整功能。您可以先使用免費試用版，或於供應商網站購買永久授權。

#### 基本初始化與設定
1. **為 Aspose OCR 設定授權：**  
   ```java
   import com.aspose.ocr.License;
   
   // Initialize and set the Aspose OCR license
   License license = new License();
   license.setLicense("YOUR_LICENSE_PATH/AsposeOcrLicensePath");
   ```
2. **初始化 GroupDocs.Parser：** 確認 parser JAR 已在 classpath 中；基本使用不需額外程式碼。

## 實作指南

### 功能：從圖像串流辨識文字
此方法讓您直接將 `InputStream`（例如上傳的檔案）傳入 OCR 引擎，並取得辨識後的文字。

#### 概觀
此流程會將輸入串流轉換為 `BufferedImage`，設定可選的辨識區域，然後呼叫 Aspose OCR 的 `RecognizePage` 方法。

#### 步驟說明程式碼

1. **建立 AsposeOCR 實例：**  
   ```java
   import com.aspose.ocr.AsposeOCR;
   
   AsposeOCR api = new AsposeOCR();
   ```

2. **將圖像串流讀入 BufferedImage：**  
   ```java
   import java.awt.image.BufferedImage;
   import javax.imageio.ImageIO;
   
   BufferedImage image = ImageIO.read(imageStream);
   ```

3. **設定辨識參數（可選的區域選取）：**  
   ```java
   import com.aspose.ocr.RecognitionSettings;
   
   RecognitionSettings settings = new RecognitionSettings();
   
   // Example: limit OCR to a specific rectangle
   if (options != null && options.getRectangle() != null) {
       ArrayList<Rectangle> areas = new ArrayList<>();
       areas.add(new Rectangle(
           (int) options.getRectangle().getLeft(),
           (int) options.getRectangle().getTop(),
           (int) options.getRectangle().getSize().getWidth(),
           (int) options.getRectangle().getSize().getHeight()));
       settings.setRecognitionAreas(areas);
   }
   ```

4. **執行辨識並處理警告：**  
   ```java
   import com.aspose.ocr.RecognitionResult;
   
   RecognitionResult result = api.RecognizePage(image, settings);
   
   if (options != null && options.getHandler() != null) {
       options.getHandler().onWarnings(pageIndex, result.warnings);
   }
   
   return result.recognitionText;
   ```

### 功能：從圖像串流辨識文字區塊
當您需要取得每個文字區塊（例如表單的各欄位）時，可啟用區域偵測。

#### 概觀
設定 `detectAreas` 後，Aspose OCR 會回傳每個辨識片段的邊界矩形，您即可將其對映至資料模型。

#### 步驟說明程式碼

1. **啟用區域偵測：**  
   ```java
   RecognitionSettings settings = new RecognitionSettings();
   settings.setDetectAreas(true);
   ```

2. **（可選）定義特定區域** – 若只關心圖像的某些部分，可沿用前一節的矩形邏輯。

3. **執行 OCR 並收集區域資訊：**  
   ```java
   import java.awt.Rectangle;
   import java.util.ArrayList;
   
   ArrayList<PageTextArea> areas = new ArrayList<>();
   for (int i = 0; i < result.recognitionAreasRectangles.size(); i++) {
       Rectangle rect = result.recognitionAreasRectangles.get(i);
       String text = result.recognitionText;
   
       areas.add(new PageTextArea(
           text,
           new Page(pageIndex, pageSize),
           new Rectangle(
               new Point(rect.getX(), rect.getY()),
               new Size(rect.getWidth(), rect.getHeight()))));
   }
   
   return areas;
   ```

## 實務應用
- **文件管理系統：** 為掃描的 PDF 建立索引，讓使用者可搜尋全文。
- **自動化資料輸入：** 從拍攝的收據或表單中抽取欄位。
- **內容數位化：** 將印刷書籍或手冊轉換為可搜尋的電子書。

## 效能考量
- **批次處理：** 將圖像分批處理，以減少 JVM 開銷。
- **圖像品質：** 較高 DPI（300 dpi 以上）可顯著提升準確度。
- **記憶體管理：** 及時釋放 `BufferedImage` 物件，特別是在大量處理時。

## 常見問題與除錯
| 症狀 | 可能原因 | 解決方式 |
|------|----------|----------|
| 文字雜亂 | 低解析度圖像 | 使用較高解析度的掃描（≥300 dpi） |
| 沒有返回文字 | 圖像格式錯誤（例如 CMYK） | 轉換為 RGB 後再進行 OCR |
| 記憶體不足錯誤 | 圖像過大 | 分割為較小區塊處理或增大 JVM 堆積大小 |

## 常見問答

**Q: 如何在 Maven 專案中安裝 Aspose OCR？**  
A: 將 Aspose OCR 相依性加入 `pom.xml`（參考供應商的 Maven 儲存庫），或從 Aspose 官方網站下載 JAR，放入 classpath。

**Q: 能否從多頁 PDF 提取文字？**  
A: 可以。先將每頁 PDF 轉為圖像（例如使用 Aspose.PDF），再將產生的串流餵入上述 OCR 方法。

**Q: 此方法能處理手寫文字嗎？**  
A: Aspose OCR 主要針對印刷文字。若需辨識手寫，建議使用專門的手寫辨識服務。

**Q: 生產環境是否必須購買授權？**  
A: 試用授權可用於評估，完整授權則會移除浮水印並解鎖所有商業功能。

**Q: 如何提升特定語言的辨識準確度？**  
A: 在 `RecognitionSettings` 中設定語言（例如 `settings.setLanguage(Language.Spanish);`），以協助引擎辨識。

## 結論
結合 Aspose.OCR 的強大辨識引擎與 GroupDocs.Parser 的彈性解析能力，您現在擁有一套可靠的 **從圖像提取文字** 解決方案，能將 **掃描文件文字** 轉換為結構化資料。請自行調整設定，將程式碼整合至服務層，讓文件工作流程變得全程可搜尋且自動化。

---

**最後更新：** 2026-01-29  
**測試環境：** Aspose.OCR 23.12、GroupDocs.Parser 25.5  
**作者：** Aspose  

---