## Feature Extraction

We will create features using various Technical indicators and Lagged prices as described below. All of these features have something to offer for forcasting. Some tells us about the trend, some gives us a signal if the stock is overbought or oversold, some portrays the strength of the price trend.

#### Bollinger Bands

A Bollinger Band® is a technical analysis tool defined by a set of lines plotted two standard deviations (positively and negatively) away from a simple moving average (SMA) of the Stocks's price Bollinger Bands allow traders to monitor and take advantage of shifts in price volatilities

Main Components of a Bollinger Bands

- Upper Band: The upper band is simply two standard deviations above the moving average of a stock’s price.
- Middle Band: The middle band is simply the moving average of the stock’s price.
- Lower Band: Two standard deviations below the moving average is the lower band.

#### Simple Moving Average (SMA)

A simple moving average (SMA) calculates the average of a selected range of prices, usually closing prices, by the number of periods in that range. SMA is basically the average price of the given time period, with equal weighting given to the price of each period. Formula: SMA = ( Sum ( Price, n ) ) / n

#### Exponential moving average (EMA)

An exponential moving average (EMA) is a type of moving average (MA) that places a greater weight and significance on the most recent data points. The exponential moving average is also referred to as the exponentially weighted moving average. An exponentially weighted moving average reacts more significantly to recent price changes than a simple moving average (SMA), which applies an equal weight to all observations in the period.

#### Average true range (ATR)

The average true range (ATR) is a technical analysis indicator that measures market volatility by decomposing the entire range of an asset price for that period. ATR measures market volatility. It is typically derived from the 14-day moving average of a series of true range indicators.

#### Average Directional Index (ADX)

ADX stands for Average Directional Movement Index and can be used to help measure the overall strength of a trend. The ADX indicator is an average of expanding price range values. ADX indicates the strength of a trend in price time series. It is a combination of the negative and positive directional movements indicators computed over a period of n past days corresponding to the input window length (typically 14 days)

#### Commodity Channel Index (CCI)

Commodity Channel Index (CCI) is a momentum-based oscillator used to help determine when an investment vehicle is reaching a condition of being overbought or oversold. It is also used to assess price trend direction and strength.
**(MA=moving average)**
CCI = (typical price − ma) / (0.015 * mean deviation) typical price = (high + low + close) / 3 p = number of periods (20 commonly used) ma = moving average moving average = typical price / p mean deviation = (typical price — MA) / p

#### Rate-of-change (ROC)

ROC measures the percentage change in price between the current price and the price a certain number of periods ago.

#### Relative Strength Index (RSI)

RSI compares the size of recent gains to recent losses, it is intended to reveal the strength or weakness of a price trend from a range of closing prices over a time period.

#### William’s %R

Williams %R, also known as the Williams Percent Range, is a type of momentum indicator that moves between 0 and -100 and measures overbought and oversold levels. The Williams %R may be used to find entry and exit points in the market.

#### Stochastic %K

A stochastic oscillator is a momentum indicator comparing a particular closing price of a security to a range of its prices over a certain period of time. It compares a close price and its price interval during a period of n past days and gives a signal meaning that a stock is oversold or overbought.

### Index Funds

Stock Prices also are affeted by other Stocks and Index Funds. So for our analysis we will use 3 different Stock Index Funds -

1. Nasdaq-100 QQQ Index ETF Fund Invesco QQQ is an exchange-traded fund based on the Nasdaq-100 Index®. The Fund will, under most circumstances, consist of all of stocks in the Index. The Index includes 100 of the largest domestic and international nonfinancial companies listed on the Nasdaq Stock Market based on market capitalization
    
2. S&P 500 Index fund The S&P 500 is a stock market index that measures the stock performance of 500 large companies listed on stock exchanges in the United States.
    
3. DJIA - Dow Jones industrial Average DJIA is a stock market index that measures the stock performance of 30 large companies listed on stock exchanges in the United States







Got it. Here’s a **clean, ordered list of exactly what happens** in that last snippet — no theory, just the pipeline steps.

---

## Steps performed in the snippet (`get_IDXFunds_features`)

### 1️⃣ Print status messages

- Prints a blank line
    
- Prints a message saying index data is being fetched
    

Purpose: logging / progress visibility.

---

### 2️⃣ Fetch NASDAQ-100 ETF (QQQ) daily data

- Uses `self.ts.get_daily('QQQ')` to download full historical data
    
- Receives:
    
    - raw price DataFrame
        
    - metadata (`QQQ_info`)
        

---

### 3️⃣ Clean and prepare QQQ data

- Renames API columns to readable names
    
- Renames close price to `QQQ_Close`
    
- Sets index name to `Date`
    
- Drops unnecessary columns (`Open, High, Low, Volume`)
    
- Sorts data in ascending date order
    
- Slices data from `self.Start_Date` onward
    

---

### 4️⃣ Create lagged QQQ features

- Adds:
    
    - `QQQ(t-1)` → previous day close
        
    - `QQQ(t-2)` → 2-day lag
        
    - `QQQ(t-5)` → 5-day lag
        

---

### 5️⃣ Create QQQ moving average features

- Computes:
    
    - 10-day moving average
        
    - 20-day moving average
        
    - 50-day moving average
        

All based on `QQQ_Close`.

---

### 6️⃣ Fetch S&P 500 index (INX) daily data

- Downloads full historical data for `INX`
    

---

### 7️⃣ Clean and prepare S&P 500 data

- Renames columns
    
- Renames close price to `SnP_Close`
    
- Sets index name to `Date`
    
- Drops OHLCV except close
    
- Sorts by date
    
- Slices data from `self.Start_Date` onward
    

---

### 8️⃣ Create lagged S&P 500 features

- Adds:
    
    - `SnP(t-1)` → 1-day lag (column name has a typo in code)
        
    - `SnP(t-5)` → 5-day lag
        

---

### 9️⃣ Fetch Dow Jones Industrial Average (DJI) data

- Downloads full historical daily data
    

---

### 🔟 Clean and prepare DJIA data

- Renames columns
    
- Renames close price to `DJIA_Close`
    
- Sets index name to `Date`
    
- Drops OHLCV except close
    
- Sorts by date
    
- Slices data from `self.Start_Date` onward
    

---

### 1️⃣1️⃣ Create lagged DJIA features

- Adds:
    
    - `DJIA(t-1)` → 1-day lag (column name typo present)
        
    - `DJIA(t-5)` → 5-day lag
        

---

### 1️⃣2️⃣ Merge all index datasets

- Merges QQQ, S&P 500, and DJIA DataFrames
    
- Uses `Date` index as the join key
    
- Keeps only overlapping trading days
    

---

### 1️⃣3️⃣ Merge index features into stock dataset

- Merges the combined index features into `self.Stock`
    
- Final dataset now includes:
    
    - stock-specific features
        
    - market-wide index features
        

---

## One-line summary

> The code fetches major market indices, engineers lagged and moving-average features from them, and merges those features into the stock dataset to provide market context for modeling.

If you want, I can:

- condense this into a **single flow diagram**
    
- refactor it into a **10-line reusable function**
    
- or list **which of these steps actually add predictive value**
    

Just say the word.