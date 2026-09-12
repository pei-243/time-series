# WTI 原油價格與波動度分析

## 專案簡介

本專案以 **WTI 原油價格**為研究對象，分析其時間序列特性，並建立 **ARIMA-GARCH 模型**進行報酬率與波動度分析。

主要內容包含：

* 探索性資料分析(Exploratory Data Analysis, EDA)
* 敘述性統計分析
* ARIMA 模型選擇與診斷
* GARCH 波動度建模建模與診斷
* 樣本外波動度預測

## 資料集

* **資料來源：** Federal Reserve Economic Data (FRED)
* **頻率：** Daily
* **期間：** 1986/01/02～2026/8/18

## 分析流程

```text
WTI 價格
    ↓
報酬率分析
    ↓
ARIMA(p,0,q)
    ↓
GARCH(p,q)
    ↓
樣本外預測
```

ARIMA 用於描述報酬率的線性動態，而 GARCH 則用於捕捉隨時間變化的波動度。

亦使用Normal與Student-t分佈比較分析不同 Innovation Distribution 對於模型配適的表現。其中，以Student-t Distribution對具有厚尾特性的報酬率資料具有較佳的配適表現。

## 最終模型

在測試的模型中，**ARIMA(8,0,6)-GARCH(1,1)-Student-t** 於 **MSE、RMSE 與 MAE** 三項樣本外預測指標皆取得最佳表現，因此選為最終模型。

## 主要發現

* WTI 價格序列具有非定態特性，而報酬率序列已達定態。
* 報酬率具有明顯的厚尾與負偏態分配。
* 資料呈現顯著的波動群聚現象。
* GARCH 能有效捕捉報酬率的時間變動波動度。
* 標準化殘差仍存在部分線性自我相關，表示平均方程仍有進一步改善的空間。

## Notebooks

* `01_eda_wti.ipynb` — 探索性資料分析
* `02_return_analysis.ipynb` — 報酬率與波動度分析
* `03_arima_garch.ipynb` — ARIMA-GARCH 建模與預測

## 使用工具

Python · Pandas · NumPy · Matplotlib · Statsmodels · pmdarima · ARCH · Scikit-learn · Jupyter Notebook
