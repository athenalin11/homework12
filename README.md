# 🎭 Vlog 多模態情緒分析

使用機器學習分析影片的語音與文字情緒，並比較跨模態一致性。

## 📋 專案簡介

本專案透過以下步驟分析 vlog 影片的情緒：

1. **音訊提取** - 從 MP4 影片中提取音訊
2. **模型訓練** - 使用 anger/happy 音檔訓練 SVM 情緒辨識模型
3. **語音情緒分析** - 從音訊的聲學特徵（韻律、音調、能量）識別情緒
4. **語音轉文字** - 使用 Google Speech Recognition API
5. **文字情緒分析** - 從文字內容中提取情緒關鍵詞
6. **跨模態比較** - 檢查語音與文字情緒是否一致

### 🎯 核心問題
**從語音識別的情緒與從文字識別的情緒是否一致？**

## 🗂️ 檔案結構

```
speech/
├── vlog_分析_精簡版.ipynb       # 主要分析 notebook
├── vlog.mp4                      # 待分析的影片檔案
├── anger/                        # 生氣情緒訓練資料（10個音檔 + valence.csv）
├── happy/                        # 開心情緒訓練資料（10個音檔 + valence.csv）
├── Anger_Happy_說明.md           # 訓練資料說明文件
├── 多模態情緒分析_說明.md        # 分析方法說明文件
├── requirements.txt              # Python 套件清單
└── README.md                     # 本檔案
```

## 🚀 快速開始

### 1. 環境設定

```bash
# 創建虛擬環境
python -m venv .venv

# 啟動虛擬環境
# macOS/Linux:
source .venv/bin/activate
# Windows:
.venv\Scripts\activate

# 安裝套件
pip install -r requirements.txt
```

### 2. 執行分析

打開 `vlog_分析_精簡版.ipynb` 並依序執行所有 cells。

關鍵步驟：
1. **環境設定** - 導入套件、設定路徑
2. **音訊提取** - 從 vlog.mp4 提取音訊
3. **模型訓練** - 使用 anger/happy 訓練 3 個 SVM 模型（約 1 分鐘）
4. **語音轉文字** - 需要網路連線（使用 Google API）
5. **多模態情緒分析** - 分析語音和文字情緒
6. **視覺化結果** - 顯示情緒比較圖表

## 📊 分析結果範例

### 語音情緒（ML 模型預測）
- **預測情緒**: 生氣/負面
- **生氣機率**: 100.0%
- **生氣強度**: 9.85/10

### 文字情緒（關鍵詞匹配）
- **預測情緒**: 平靜/中性
- **信心度**: 83.3%

### 跨模態一致性
- **結果**: ❌ 不一致
- **分析**: 語音顯示強烈負面情緒，但文字內容相對中性，反映說話者內心激動但用詞克制的複雜情緒狀態。

## 🛠️ 技術棧

### 音訊處理
- **librosa** 0.11.0 - 音訊載入、特徵提取
- **soundfile** - 音訊檔案讀寫
- **moviepy** - 影片音訊提取

### 機器學習
- **pyAudioAnalysis** 0.3.14 - 音訊特徵提取與 SVM 模型訓練
- **scikit-learn** 1.6.1 - 機器學習演算法
- **numpy** 2.0.2 - 數值運算

### 語音辨識
- **SpeechRecognition** - Google Speech API 介接

### 視覺化
- **matplotlib** 3.9.4 - 圖表繪製
- **plotly** 6.5.0 - 互動式視覺化

## 📚 專案特色

### 1. 完整的 ML 工作流程
- ✅ 資料準備（anger/happy 音檔）
- ✅ 特徵提取（MFCC、pitch、energy、ZCR 等）
- ✅ 模型訓練（SVM 分類器 + 回歸器）
- ✅ 模型應用（預測新資料）

### 2. 多模態分析
- **語音模態**: 基於聲學特徵的 ML 預測
- **文字模態**: 基於語義的關鍵詞匹配
- **跨模態整合**: 一致性檢查與差異分析

### 3. 實用性
- 可應用於：客服品質分析、心理諮詢輔助、社交媒體情緒監測
- 揭示語音與文字的情感差異（如反諷、掩飾等）

## 📖 詳細說明

- [Anger_Happy_說明.md](Anger_Happy_說明.md) - 訓練資料的作用與工作流程
- [多模態情緒分析_說明.md](多模態情緒分析_說明.md) - 分析方法與技術細節

## ⚠️ 注意事項

1. **語音轉文字需要網路連線**（使用 Google Speech Recognition API）
2. **模型訓練需要時間**（約 1 分鐘，使用 anger/happy 資料）
3. **訓練好的模型檔案**（svm2emotions 等）會自動產生在專案目錄
4. **ffmpeg 警告**可忽略（不影響 WAV 檔案處理）

## 🎓 學習重點

- 監督式學習（Supervised Learning）
- 音訊特徵工程（Audio Feature Engineering）
- 支援向量機（SVM）分類與回歸
- 多模態情緒分析（Multimodal Emotion Recognition）
- 語音訊號處理（Speech Signal Processing）

## 📄 授權

本專案為教學用途。

## 👤 作者

心理資訊學課程作業
授課教師：Tsung-Ren (Tren) Huang

---

**🌟 如果這個專案對你有幫助，歡迎給個 Star！**
