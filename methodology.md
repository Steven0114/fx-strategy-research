# 📚 研究方法論與理論基礎

## 論文本文

http://thesis.lib.nccu.edu.tw/cgi-bin/gs32/gsweb.cgi?o=dallcdr&s=id=%22G0111352025%22.&searchmode=basic
論文有詳盡方法描述

## 🔬 研究概述

本研究基於經濟基本面指標實施外匯交易策略，探討宏觀經濟變數對匯率報酬的預測能力。研究實施了四種不同的投資組合配置策略：VI（基本面脆弱性指標策略）、RREVI（反向回歸增強投資策略）、CAR（進位交易策略）、REVI（回歸增強投資策略）。

## 📊 理論基礎

### 1. 購買力平價理論 (Purchasing Power Parity, PPP)
- **基本概念**：長期來看，匯率應反映兩國的相對價格水準
- **應用**：通脹率差異（CPI指標）預測匯率變動方向
- **實證意義**：高通脹國家貨幣傾向貶值

### 2. 國際收支理論 (Balance of Payments Theory)
- **經常帳餘額**：反映國家對外貿易和所得流動狀況
- **資本流動**：國際準備和淨國外資產變化影響匯率
- **預測邏輯**：經常帳赤字國家貨幣面臨貶值壓力

### 3. 利率平價理論 (Interest Rate Parity)
- **無套利條件**：遠期匯率應反映兩國利率差異
- **前瞻偏誤**：遠期匯率往往不能準確預測未來即期匯率
- **套利機會**：利用前瞻偏誤構建進位交易策略

### 4. 基本面分析理論
- **經濟指標預測**：宏觀經濟變數包含匯率變動的預測信息
- **綜合評估**：多個指標結合提供更穩健的預測
- **時間延遲**：經濟基本面數據取得存在時滯

## 🛠️ 研究方法

### 1. 數據處理方法

#### A. 國家脆弱性指標構建
```
脆弱性指標 = f(CAB/GDP, IR/GDP, NFA/Imports, CPI_3Y)
```
- **CAB/GDP**：經常帳餘額佔GDP比例
- **IR/GDP**：國際準備佔GDP比例  
- **NFA/Imports**：淨國外資產佔進口比例
- **CPI_3Y**：三年平均通脹率

#### B. 五分位數分組法
- 根據綜合脆弱性指標將國家分為5組
- Q1：預期表現最佳（最不脆弱）
- Q5：預期表現最差（最脆弱）
- 動態再平衡：每季度重新評估和分組

### 2. 迴歸分析方法

#### A. 時間序列迴歸
```
ExcessReturn[t+h] = α + β₁×CAB[t] + β₂×IR[t] + β₃×NFA[t] + β₄×CPI[t] + ε[t]
```

#### B. 滾動窗口估計
- **窗口長度**：使用歷史數據進行迴歸
- **預測頻率**：每季度更新迴歸係數
- **前瞻偏誤控制**：確保僅使用當期及以前的信息

#### C. 顯著性檢驗
- **P值門檻**：0.1（10%顯著水準）
- **條件策略**：僅當係數顯著時納入預測
- **穩健性**：避免過度擬合和雜訊影響

### 3. 策略構建方法

#### A. VI策略（基本面脆弱性指標策略）
```
預測值 = 脆弱性綜合排名
```
- **純粹基本面**：僅使用經濟指標，不含利率價差
- **直接排名**：基於綜合脆弱性指標直接分組
- **理論依據**：經濟基本面健康的國家貨幣應表現較佳

#### B. RREVI策略（推薦）
```
預測值 = -β₁×CAB - β₂×IR - β₃×NFA - β₄×CPI + (F-S)/S
```
- **反向邏輯**：對經濟基本面係數取負號
- **理論依據**：利用前瞻偏誤和市場錯誤定價
- **收斂性**：當所有係數不顯著時收斂到CAR策略

#### C. CAR策略（進位交易）
```
預測值 = (F-S)/S
```
- **純利率策略**：僅使用遠期-即期利差
- **傳統方法**：經典的進位交易策略
- **基準比較**：作為經濟基本面策略的對照組

#### D. REVI策略
```
預測值 = β₁×CAB + β₂×IR + β₃×NFA + β₄×CPI + (F-S)/S
```
- **直觀邏輯**：直接使用迴歸係數進行預測
- **理論期望**：基本面強健國家貨幣應升值

### 4. 投資組合構建

#### A. 排名機制
- 根據預測值對所有貨幣進行排名
- P1：預測表現最佳的五分之一
- P5：預測表現最差的五分之一

#### B. 權重分配
- **等權重配置**：組合內每個貨幣分配相等權重
- **再平衡頻率**：每季度調整持倉
- **交易成本**：研究未考慮實際交易成本

#### C. 長短策略
- **做多P1組合**：買入預期表現最佳的貨幣
- **做空P5組合**：賣出預期表現最差的貨幣
- **總策略報酬**：P1-P5的報酬差異

## 📈 績效評估方法

### 1. 報酬指標
- **年化報酬率**：策略的平均年化績效
- **超額報酬**：包含利率價差的總報酬
- **匯率報酬**：純匯率變動的報酬（排除利率因素）

### 2. 風險指標
- **波動度**：報酬的標準差（年化）
- **夏普比率**：風險調整後的報酬率
- **偏度**：報酬分布的偏斜程度
- **峰度**：報酬分布的尖峰程度

### 3. 穩健性檢驗
- **樣本分割**：2008年後 vs 2002年後
- **顯著期間分析**：僅分析迴歸係數顯著的期間
- **轉換矩陣**：分析投資組合持倉的穩定性

## 🔍 研究創新點

### 1. 方法論創新
- **反向策略邏輯**：RREVI策略的反向係數應用
- **動態顯著性過濾**：根據統計顯著性動態調整策略
- **多策略比較框架**：系統性比較不同策略的效果

### 2. 實證貢獻
- **綜合脆弱性指標**：整合多個宏觀經濟變數
- **均值回歸利用**：將市場異象轉化為投資機會
- **穩健性驗證**：多時間段和多指標的全面檢驗

### 3. 實務應用價值
- **策略靈活性**：可根據市場條件選擇適當策略
- **風險控制**：詳細的統計分析和風險測量
- **實施簡易性**：基於公開宏觀數據的可操作策略

## 📚 相關文獻

### 文獻
- Abhyankar, A., Sarno, L., & Valente, G. (2005). Exchange Rates and Fundamentals:
Evidence on the Economic Value of Predictability. Journal of International Economics,
66(2), 325-348.
- Ahmed, S., Coulibaly, B., & Zlate, A. (2017). International Financial Spillovers to
1Emerging Market Economies: How Important are Economic Fundamentals? Journal of
International Money and Finance, 76, 133-152.
- De Grauwe, P., & Vansteenkiste, I. (2007). Exchange Rates and Fundamentals: A Non-
Linear Relationship? International Journal of Finance & Economics, 12(1), 37-54.
- Della Corte, P., Riddiough, S. J., & Sarno, L. (2016). Volatility Risk Premia and Exchange
Rate Predictability. Journal of Financial Economics, 120(1), 21-40.
- Ehrmann, M., & Fratzscher, M. (2005). Exchange Rates and Fundamentals: New Evidence
from Real-Time Data. Journal of International Money and Finance, 24(3), 317-341.
- Engel, C., & West, K. D. (2005). Exchange Rates and Fundamentals. Journal of Political
Economy, 113(3), 485-517.
- Mark, N. C. (1995). Exchange Rates and Fundamentals: Evidence on Long-Horizon
Predictability. The American Economic Review, 85(1), 201-218.
- Menkhoff, L., Sarno, L., Schmeling, M., & Schrimpf, A. (2012). Carry Trades and Global
Foreign Exchange Volatility. The Journal of Finance, 67(2), 681-718.
- Ricci, L. A., Milesi-Ferretti, G. M., & Lee, J. (2013). Real Exchange Rates and
Fundamentals: A Cross-Country Perspective. Journal of Money, Credit and Banking,
45(5), 845-865.
- Sarno, L., & Valente, G. (2009). Exchange Rates and Fundamentals: Footloose or Evolving
Relationship? Journal of the European Economic Association, 7(4), 786-830.
- Sweeney, R. J. (2006). Mean reversion in G-10 nominal exchange rates. Journal of
Financial and Quantitative Analysis, 41(3), 685-708.
- Taylor, M. P., Peel, D. A., & Sarno, L. (2001). Nonlinear mean‐reversion in real exchange
rates: toward a solution to the purchasing power parity puzzles. International economic
review, 42(4), 1015-1042.

---
**文檔版本**：v1.0  
**最後更新**：2024年7月
**適用研究**：regression.ipynb v2.0 
