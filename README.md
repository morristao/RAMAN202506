# PLS-DA 光譜分類與 VIP 特徵選擇系統

本專案實作了使用偏最小平方判別分析（PLS-DA）結合 VIP（Variable Importance in Projection）特徵篩選的多類別光譜分類模型，針對蘇丹紅 I\~IV 分類進行訓練與視覺化。支援 `.asc` 與 `.spc` 格式，內建交叉驗證、Hamming 準確率評估與多種可視化工具。

---

## 模型簡介

此專案包含以下步驟：

1. **資料預處理**：插值與波長/強度歸一化
2. **PLS-DA 分類器**：結合 `PLSRegression` 與 `LinearDiscriminantAnalysis` 投影至可判別空間
3. **VIP 特徵選擇**：使用 VIP 分數篩選最具鑑別力的特徵點
4. **準確率評估**：
   - 一般分類準確率（Accuracy）
   - 元素級別多標籤準確率（Hamming Accuracy）
5. **可視化輸出**：
   - VIP 門檻與準確率關係圖
   - VIP 選中特徵在波長軸的位置標記圖
   - 2D PLS-DA 分類結果分佈圖

---

## 系統需求

- **Python**：3.8 以上
- **記憶體**：4GB 以上（建議 8GB+）
- **GPU**：非必要（CPU 即可）

---

## 安裝方式

建議使用虛擬環境（如 `conda`、`venv`）。

```bash
pip install -r requirements.txt
```

或手動安裝：

```bash
pip install numpy pandas scikit-learn matplotlib seaborn torch pywt
pip install spectrochempy  # 若需支援 .spc 檔
```

---

## 資料格式與輸入說明

### 支援格式：

- `.asc`：Tab 分隔的波長-強度純文字格式
- `.spc`：由 spectrochempy 讀取的二進位光譜格式

### 檔名命名規則（自動標籤對應）：

```
III+IV(1比1)-xxx.asc   → 蘇丹紅 III:50%, IV:50%
1+2(33%比66%)-xxx.spc → 蘇丹紅 I:33%, II:66%
```

標籤將自動轉換為 4 維比例向量。

---

## 輸入與輸出

### 輸入：

- 放置 `.asc` / `.spc` 檔案於下列資料夾：
  - `remix_data/`、`remix_data_2/`、`remix_data_3/`
- 可自訂 VIP 門檻範圍與最大主成分數

### 輸出：




---

## 使用方式

### 1. Clone 並安裝依賴套件

```bash
https://github.com/morristao/RAMAN202506.git
!pip install numpy
!pip install pandas
!pip install torch
!pip install torch.nn
!pip install torch.optim
!pip install matplotlib
!pip install pyspectra
!pip install PyWavelets
!pip install Seaborn
!pip install scikit-learn
```

### 2. 放置光譜資料

請將 `.asc` 或 `.spc` 檔案放至以下資料夾中：

```RAMAN
remix_data/
remix_data_2/
remix_data_3/
```

### 3. 執行 Jupyter Notebook

```bash
jupyter notebook Project_handout20250616.ipynb
```

或轉換為 Python 腳本執行：

```bash
jupyter nbconvert --to script Project_handout20250616.ipynb
python Project_handout20250616.py
```

---

## 評估指標

- **Accuracy**：整體分類準確率
- **Hamming Accuracy**：針對多成分樣本，逐元素是否分類正確的平均值
- **VIP 特徵數**：每個門檻下篩選出來的重要特徵數量

---

## 專案架構

```RAMAN202506
.
├── Project_handout20250616.ipynb     # 主程式 notebook
├── /remix_data                       # 原始光譜資料 (.asc / .spc)
├── /remix_data_2                     # 原始光譜資料 (.asc / .spc)
├── /remix_data_3                     # 原始光譜資料 (.asc / .spc)
└── README.md
```

---

## 參考資源

- [scikit-learn: PLSRegression](https://scikit-learn.org/stable/modules/generated/sklearn.cross_decomposition.PLSRegression.html)
- [SpectroChemPy](https://www.spectrochempy.fr/)
- [Hamming Loss in scikit-learn](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.hamming_loss.html)

---

## 聯絡方式

> 維護者：**LC Tao**\
> Email：`liangkingtao@gmail.com`

如有問題與建議，歡迎發起討論。
