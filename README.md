# 🎲 桌遊規則百科

這是我的 RAG 對話機器人作業，使用 Colab、AISuite、
Groq 和 Gradio 製作。

玩桌遊時，有時候會忘記規則，或不知道某個情況該怎麼處理。
所以我想做一個像桌友一樣的機器人，可以教學，也能查詢規則。

## 收錄桌遊

- 拉密 Rummikub
- 說書人 Dixit
- 矮人礦坑 Saboteur

資料根據指定的官方規則書整理，只收錄基本遊戲，
不混用其他版本、擴充包、變體或自訂玩法。

## 使用方式

1. 選擇想詢問的桌遊。
2. 輸入玩法或規則問題。
3. 按下「搜尋並回答」。
4. 查看回答、文件引用、版本與來源頁碼。

問「怎麼玩」時，會介紹完整入門玩法。
資料不足時，會說明目前無法確認，不自行編造規則。

機器人的角色是幽默、有耐心的桌友。
目前每次提問獨立處理，沒有多輪對話記憶。

## 系統流程

官方規則書 → 整理 TXT → RAG01 建立向量資料庫
→ RAG02 從網址下載 → 搜尋選定桌遊的文件
→ Groq 根據文件回答 → Gradio 顯示結果

## 檔案說明

| 檔案 | 內容 |
| --- | --- |
| rag-data.zip | RAG01 匯出的向量資料庫套件，提供 RAG02 下載載入 |

rag-data.zip 包含：
- index.faiss：向量搜尋索引
- documents.json：規則正文及來源、版本等資料
- index_doc_ids.json：向量與文件編號對照
- config.json：模型版本與資料庫設定

原始文字壓縮檔 boardgame-texts.zip 與向量資料庫不同，
不能互相替代。

## 使用工具

- Google Colab
- Sentence Transformers / EmbeddingGemma 2
- FAISS
- AISuite
- Groq：openai/gpt-oss-120b
- Gradio

## 官方資料來源

- [拉密規則書](https://rummikub.com/wp-content/uploads/2019/12/2600-English.pdf)
- [說書人規則書](https://cdn.svc.asmodee.net/production-libellud/uploads/2022/03/DIXIT_REFRESH_RULES_US-UK-AU_BD.pdf)
- [矮人礦坑規則書](https://blog.amigo-spiele.de/content/ap/rule/02402-GB-AmigoRule.pdf)

版本、適用範圍與 PDF 頁碼記錄在各份文件的 metadata 中。
矮人礦坑來源為合輯規則書，僅整理基本遊戲部分。

## 製作說明

以老師提供的 RAG01、RAG02 範例為基礎修改，
保留指定套件與版本，加入桌遊篩選、網址下載、
桌友人設，以及版本與來源頁碼展示。

製作過程使用 AI 協助討論、整理資料及修改程式，
並透過實際執行與問答測試核對結果。
